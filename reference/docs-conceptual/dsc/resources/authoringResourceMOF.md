---
ms.date: 07/08/2020
keywords: DSC, Power shell, configuratie, installatie
title: Een aangepaste DSC-resource schrijven met MOF
description: Dit artikel definieert het schema voor een aangepaste DSC-resource in een MOF-bestand en implementeert de bron in een Power shell-script bestand.
ms.openlocfilehash: e79a37699c468b2c55c307c96f1c193a2c1595b3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667178"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a>Een aangepaste DSC-resource schrijven met MOF

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

In dit artikel definiëren we het schema voor een aangepaste Windows Power shell-resource voor desired state Configuration (DSC) in een MOF-bestand en implementeert u de bron in een Windows Power shell-script bestand.
Deze aangepaste resource is voor het maken en onderhouden van een website.

## <a name="creating-the-mof-schema"></a>Het MOF-schema maken

Het schema definieert de eigenschappen van uw resource die kunnen worden geconfigureerd met een DSC-configuratie script.

### <a name="folder-structure-for-a-mof-resource"></a>Mapstructuur voor een MOF-bron

Als u een aangepaste DSC-resource met een MOF-schema wilt implementeren, maakt u de volgende mapstructuur. Het MOF-schema wordt gedefinieerd in het bestand `Demo_IISWebsite.schema.mof` en het bron script is gedefinieerd in `Demo_IISWebsite.psm1` . U kunt desgewenst een psd1-bestand (module manifest) maken.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

> [!NOTE]
> U moet een map met de naam DSCResources maken in de map op het hoogste niveau en de map voor elke resource moeten dezelfde naam hebben als de resource.

### <a name="the-contents-of-the-mof-file"></a>De inhoud van het MOF-bestand

Hier volgt een voor beeld van een MOF-bestand dat kan worden gebruikt voor een aangepaste website bron. Als u dit voor beeld wilt volgen, slaat u dit schema op in een bestand en roept u het bestand aan `Demo_IISWebsite.schema.mof` .

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

Let op het volgende voor gaande code:

- `FriendlyName` Hiermee definieert u de naam die u kunt gebruiken om te verwijzen naar deze aangepaste resource in de DSC-configuratie scripts. In dit voor beeld `Website` is gelijk aan de beschrijvende naam `Archive` voor de ingebouwde archief bron.
- De klasse die u definieert voor uw aangepaste resource moet zijn afgeleid van `OMI_BaseResource` .
- De type kwalificatie, `[Key]` , op een eigenschap geeft aan dat deze eigenschap het bron exemplaar uniek identificeert. Er is ten minste één `[Key]` eigenschap vereist.
- De `[Required]` kwalificatie geeft aan dat de eigenschap vereist is (er moet een waarde worden opgegeven in een configuratie script dat gebruikmaakt van deze bron).
- De `[write]` kwalificatie geeft aan dat deze eigenschap optioneel is wanneer u de aangepaste resource in een configuratie script gebruikt. De `[read]` kwalificatie geeft aan dat een eigenschap niet kan worden ingesteld met een configuratie en alleen voor rapportage doeleinden.
- `Values` Hiermee worden de waarden die kunnen worden toegewezen aan de eigenschap, beperkt tot de lijst met waarden die zijn gedefinieerd in `ValueMap` . Zie voor meer informatie [ValueMap en waarde-kwalificaties](/windows/desktop/WmiSdk/value-map).
- Het toevoegen van een eigenschap `Ensure` met `Present` de naam waarden en `Absent` in uw resource wordt aanbevolen als een manier om een consistente stijl met ingebouwde DSC-resources te onderhouden.
- Noem het schema bestand voor uw aangepaste resource als volgt: `classname.schema.mof` , waarbij `classname` de id is gevolgd door het `class` sleutel woord in uw schema definitie.

### <a name="writing-the-resource-script"></a>Het resource script wordt geschreven

Het bron script implementeert de logica van de resource. In deze module moet u drie functies met de naam `Get-TargetResource` , `Set-TargetResource` en hebben `Test-TargetResource` . Alle drie de functies moeten een parameterset hebben die identiek is aan de set eigenschappen die zijn gedefinieerd in het MOF-schema dat u voor uw resource hebt gemaakt. In dit document wordt deze set eigenschappen aangeduid als de ' resource-eigenschappen '. Sla deze drie functies op in een bestand met de naam `<ResourceName>.psm1` . In het volgende voor beeld worden de functies opgeslagen in een bestand met de naam `Demo_IISWebsite.psm1` .

> [!NOTE]
> Wanneer u hetzelfde configuratie script voor uw resource meer dan één keer uitvoert, worden er geen fouten weer gegeven en moet de resource dezelfde status blijven als het script eenmaal uit te voeren. Om dit te bewerkstelligen, moet u ervoor zorgen dat de- `Get-TargetResource` en `Test-TargetResource` -functies de resource ongewijzigd laten en dat de `Set-TargetResource` functie meerdere keren wordt aangeroepen in een reeks met dezelfde parameter waarden, altijd gelijk is aan het aanroepen van deze.

Gebruik in de `Get-TargetResource` functie-implementatie de belangrijkste eigenschaps waarden van de bron die zijn opgegeven als para meters om de status van het opgegeven bron exemplaar te controleren. Deze functie moet een hash-tabel retour neren met een lijst van alle bron eigenschappen als sleutels en de werkelijke waarden van deze eigenschappen als de bijbehorende waarden. De volgende code bevat een voor beeld.

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance
# specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <#
          Insert logic that uses the mandatory parameter values to get the website and
          assign it to a variable called $Website
          Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise
        #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
            Name = $Website.Name
            Ensure = $ensureResult
            PhysicalPath = $Website.physicalPath
            State = $Website.state
            ID = $Website.id
            ApplicationPool = $Website.applicationPool
            Protocol = $Website.bindings.Collection.protocol
            Binding = $Website.bindings.Collection.bindingInformation
        }

        $getTargetResourceResult
}
```

Afhankelijk van de waarden die zijn opgegeven voor de bron eigenschappen in het configuratie script, `Set-TargetResource` moet u een van de volgende handelingen uitvoeren:

- Een nieuwe website maken
- Een bestaande website bijwerken
- Een bestaande website verwijderen

In het volgende voor beeld ziet u dit.

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <#
        If Ensure is set to "Present" and the website specified in the mandatory input parameters
          does not exist, then create it using the specified parameter values
        Else, if Ensure is set to "Present" and the website does exist, then update its properties
          to match the values provided in the non-mandatory parameter values
        Else, if Ensure is set to "Absent" and the website does not exist, then do nothing
        Else, if Ensure is set to "Absent" and the website does exist, then delete the website
    #>
}
```

Ten slotte `Test-TargetResource` moet de functie dezelfde para meter ingesteld hebben als `Get-TargetResource` en `Set-TargetResource` . Controleer in uw implementatie van de `Test-TargetResource` status van het bron exemplaar dat is opgegeven in de sleutel parameters. Als de werkelijke status van het bron exemplaar niet overeenkomt met de waarden die zijn opgegeven in de parameterset, retour neren `$false` . Als dat niet het geval is, retour neren `$true` .

Met de volgende code wordt de `Test-TargetResource` functie geïmplementeerd.

```powershell
function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([System.Boolean])]
    param
    (
        [ValidateSet("Present","Absent")]
        [System.String]
        $Ensure,

        [parameter(Mandatory = $true)]
        [System.String]
        $Name,

        [parameter(Mandatory = $true)]
        [System.String]
        $PhysicalPath,

        [ValidateSet("Started","Stopped")]
        [System.String]
        $State,

        [System.String[]]
        $Protocol,

        [System.String[]]
        $BindingData,

        [System.String]
        $ApplicationPool
    )

    # Get the current state
    $currentState = Get-TargetResource -Ensure $Ensure -Name $Name -PhysicalPath $PhysicalPath -State $State -ApplicationPool $ApplicationPool -BindingInfo $BindingInfo -Protocol $Protocol

    # Write-Verbose "Use this cmdlet to deliver information about command processing."

    # Write-Debug "Use this cmdlet to write debug information while troubleshooting."

    # Include logic to
    $result = [System.Boolean]
    # Add logic to test whether the website is present and its status matches the supplied
    # parameter values. If it does, return true. If it does not, return false.
    $result
}
```

> [!NOTE]
> Voor eenvoudiger fout opsporing gebruikt u de `Write-Verbose` cmdlet in uw implementatie van de vorige drie functies. Met deze cmdlet wordt tekst naar de uitgebreide berichten stroom geschreven. De uitgebreide berichten stroom wordt standaard niet weer gegeven, maar u kunt deze weer geven door de waarde van de **$VerbosePreference** variabele te wijzigen of door de **uitgebreide** para meter in de DSC-cmdlets = New te gebruiken.

### <a name="creating-the-module-manifest"></a>Het module manifest maken

Ten slotte gebruikt `New-ModuleManifest` u de cmdlet om een `<ResourceName>.psd1` bestand voor uw aangepaste resource module te definiëren. Wanneer u deze cmdlet aanroept, verwijst u naar het script module bestand (. psm1) dat wordt beschreven in de vorige sectie. Include `Get-TargetResource` , `Set-TargetResource` en `Test-TargetResource` in de lijst met functies die moeten worden geëxporteerd. Hier volgt een voor beeld van een manifest bestand.

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a>PsDscRunAsCredential ondersteunen

> [!Note]
> **PsDscRunAsCredential** wordt ondersteund in power shell 5,0 en hoger.

De eigenschap **PsDscRunAsCredential** kan worden gebruikt in [DSC-configuratie](../configurations/configurations.md) bron blok om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties. Zie [DSC uitvoeren met gebruikers referenties](../configurations/runAsUser.md)voor meer informatie.

Voor toegang tot de gebruikers context vanuit een aangepaste resource kunt u de automatische variabele gebruiken `$PsDscContext` .

Met de volgende code wordt bijvoorbeeld de gebruikers context geschreven waarmee de resource wordt uitgevoerd naar de uitgebreide uitvoer stroom:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a>Het knoop punt opnieuw opstarten

Als voor de acties die in de `Set-TargetResource` functie worden uitgevoerd, opnieuw moet worden opgestart, kunt u een globale vlag gebruiken om te geven dat de LCM het knoop punt opnieuw moet opstarten. Het opnieuw opstarten vindt direct nadat de `Set-TargetResource` functie is voltooid.

Voeg in de `Set-TargetResource` functie de volgende regel code toe.

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

Om het knoop punt opnieuw op te starten, moet de **RebootNodeIfNeeded** -vlag worden ingesteld op `$true` .
De **ActionAfterReboot** -instelling moet ook worden ingesteld op **ContinueConfiguration** . Dit is de standaard waarde. Zie [de lokale Configuration Manager configureren](../managing-nodes/metaConfig.md)of [de lokale Configuration Manager configureren (v4)](../managing-nodes/metaConfig4.md)voor meer informatie over het configureren van de LCM.
