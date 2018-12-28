---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Een aangepaste DSC-resource met MOF schrijven
ms.openlocfilehash: 2dcdeb49b50e23bc8b9d87293ebb8d8ec5e7b57d
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403900"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a>Een aangepaste DSC-resource met MOF schrijven

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

In dit onderwerp, we het schema voor een aangepaste Windows PowerShell Desired State Configuration (DSC)-bron in een MOF-bestand definiëren en implementeren van de resource in een Windows PowerShell-scriptbestand. Deze aangepaste resource is voor het maken en onderhouden van een website.

## <a name="creating-the-mof-schema"></a>Het maken van het MOF-schema

Het schema bepaalt de eigenschappen van de resource die kunnen worden geconfigureerd door een script voor DSC-configuratie.

### <a name="folder-structure-for-a-mof-resource"></a>Mapstructuur voor een MOF-resource

Voor het implementeren van een aangepaste DSC-resource met een MOF-schema, maken de volgende mapstructuur. Het MOF-schema is gedefinieerd in het bestand Demo_IISWebsite.schema.mof en het resource-script is gedefinieerd in Demo_IISWebsite.psm1. U kunt eventueel een module-manifest (psd1)-bestand maken.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

Houd er rekening mee dat het nodig zijn om te maken van een map met de naam DSCResources onder de map op het hoogste niveau is, en dat de map voor elke resource moet dezelfde naam als de resource.

### <a name="the-contents-of-the-mof-file"></a>De inhoud van het MOF-bestand

Hieronder volgt een voorbeeld van de MOF-bestand dat kan worden gebruikt voor de resource van een aangepaste website. Als u wilt volgen in het volgende voorbeeld, dit schema in een bestand opslaan en aanroepen van het bestand *Demo_IISWebsite.schema.mof*.

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

Houd rekening met de volgende met betrekking tot de vorige code:

* `FriendlyName` bepaalt de naam die u gebruiken kunt om te verwijzen naar deze aangepaste resource in scripts voor DSC-configuratie. In dit voorbeeld `Website` is gelijk aan de beschrijvende naam `Archive` voor de ingebouwde archiefresource.
* De klasse die u definieert voor uw aangepaste resource moet zijn afgeleid van `OMI_BaseResource`.
* De kwalificatie type `[Key]`op een eigenschap geeft aan dat deze eigenschap unieke identificatie van de resource-instantie. Ten minste één `[Key]` eigenschap is vereist.
* De `[Required]` kwalificatie geeft aan dat de eigenschap vereist is (er moet een waarde worden opgegeven in een script voor de configuratie die gebruikmaakt van deze resource).
* De `[write]` kwalificatie geeft aan dat deze eigenschap optioneel is bij het gebruik van de aangepaste resource in een configuratiescript. De `[read]` kwalificatie geeft aan dat een eigenschap kan niet worden ingesteld door een configuratie, en is alleen voor rapportagedoeleinden.
* `Values` beperkt de waarden die kunnen worden toegewezen aan de eigenschap aan de lijst met waarden die zijn gedefinieerd `ValueMap`. Zie voor meer informatie, [ValueMap en waarde kwalificaties](/windows/desktop/WmiSdk/value-map).
* Met inbegrip van een eigenschap met de naam `Ensure` met waarden `Present` en `Absent` in de bron wordt aanbevolen als een manier voor het onderhouden van een consistente stijl met ingebouwde DSC-resources.
* Noem het schemabestand voor uw aangepaste resources als volgt: `classname.schema.mof`, waarbij `classname` is de id die volgt op de `class` sleutelwoord in uw schemadefinitie.

### <a name="writing-the-resource-script"></a>Schrijven van de resource-scripts

De resource-script implementeert de logica van de resource. In deze module, moet u drie functies met de naam opnemen **Get-TargetResource**, **Set TargetResource**, en **Test TargetResource**. Alle drie de functies neemt een parameterset die identiek is aan de set eigenschappen die zijn gedefinieerd in het MOF-schema dat u hebt gemaakt voor uw resource. In dit document, wordt deze reeks eigenschappen aangeduid als het "resource-eigenschappen." Deze drie functies in een bestand met de naam Store <ResourceName>.psm1. In het volgende voorbeeld worden de functies worden opgeslagen in een bestand met de naam Demo_IISWebsite.psm1.

> **Houd er rekening mee**: Wanneer u de dezelfde configuratiescript voor uw resource meer dan één keer uitvoert, ontvangt u geen fouten en de resource moet blijven in dezelfde staat als het script is één keer uitgevoerd. U doet dit door ervoor te zorgen dat uw **Get-TargetResource** en **Test TargetResource** functies laat de bron niet gewijzigd en deze aan te roepen de **Set-TargetResource**werken meer dan één keer in een reeks met dezelfde parameter waarden is altijd gelijk is aan één keer aanroepen.

In de **Get-TargetResource** functie-implementatie, de belangrijkste resource eigenschapswaarden die zijn opgegeven als parameters gebruiken om te controleren of de status van de opgegeven resource-exemplaar. Deze functie moet een hash-tabel met een lijst met alle resource-eigenschappen als sleutels en de werkelijke waarden van deze eigenschappen als de bijbehorende waarden retourneren. De volgende code geeft een voorbeeld.

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
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

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name;
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }

        $getTargetResourceResult;
}
```

Afhankelijk van de waarden die zijn opgegeven voor de resource-eigenschappen in het configuratiescript van de **Set TargetResource** moet een van de volgende handelingen uit:

* Een nieuwe website maken
* Een bestaande website bijwerken
* Een bestaande website verwijderen

Het volgende voorbeeld ziet u dit.

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

    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

Ten slotte de **Test TargetResource** functie moet rekening houden met de dezelfde parameter is ingesteld als **Get-TargetResource** en **Set TargetResource**. Bij de implementatie van **Test TargetResource**, Controleer de status van de resource-exemplaar dat is opgegeven in de belangrijke parameters. Als de huidige status van het exemplaar van de resource komt niet overeen met de opgegeven waarden in de parameter is ingesteld, retourneren **$false**. Anders **$true**.

De volgende code implementeert de **Test TargetResource** functie.

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

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result
}
```

**Houd er rekening mee**: Voor eenvoudiger foutopsporing, gebruikt u de **Write-Verbose** cmdlet in uw implementatie van de vorige drie functies.
>Deze cmdlet schrijft tekst naar de uitgebreide berichtenstroom.
>Standaard wordt de uitgebreide berichtenstroom niet weergegeven, maar u kunt deze weergeven door het wijzigen van de waarde van de **$VerbosePreference** variabele of met behulp van de **uitgebreid** parameter in de DSC-cmdlets = nieuw.

### <a name="creating-the-module-manifest"></a>Het maken van de module-manifest

Gebruik tot slot de **New-ModuleManifest** cmdlet voor het definiëren van een <ResourceName>.psd1-bestand voor uw aangepaste resource-module. Als u deze cmdlet aanroepen, verwijst naar het scriptbestand voor module (.psm1) die worden beschreven in de vorige sectie. Opnemen **Get-TargetResource**, **Set TargetResource**, en **Test TargetResource** in de lijst met functies om te exporteren. Hieronder volgt een voorbeeld van de manifest-bestand.

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

## <a name="supporting-psdscrunascredential"></a>Ondersteunende PsDscRunAsCredential

>**Opmerking:** **PsDscRunAsCredential** wordt ondersteund in PowerShell 5.0 en hoger.

De **PsDscRunAsCredential** eigenschap kan worden gebruikt [DSC-configuraties](../configurations/configurations.md) resource blokkeren om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties.
Zie voor meer informatie, [DSC uitvoeren met gebruikersreferenties](../configurations/runAsUser.md).

U kunt de automatische variabele gebruiken voor toegang tot de gebruikerscontext uit binnen een aangepaste resource, `$PsDscContext`.

Bijvoorbeeld schrijft de volgende code de gebruikerscontext waarmee de resource wordt uitgevoerd naar de stroom uitgebreide uitvoer:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```
