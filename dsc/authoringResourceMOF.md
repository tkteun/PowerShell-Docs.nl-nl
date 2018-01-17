---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Schrijven van een aangepaste DSC-resource met MOF
ms.openlocfilehash: c416fd7cac80d37f1ca1393fa644b4bc15743724
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a>Schrijven van een aangepaste DSC-resource met MOF

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

In dit onderwerp wordt het schema voor de aangepaste resource van een Windows PowerShell Desired State Configuration (DSC) definiëren in een MOF-bestand, en implementeren van de resource in een Windows PowerShell-scriptbestand. Deze aangepaste resource wordt voor het maken en onderhouden van een website.

## <a name="creating-the-mof-schema"></a>Maken van het MOF-schema

Het schema definieert de eigenschappen van de bron die kunnen worden geconfigureerd door een DSC-configuratiescript.

### <a name="folder-structure-for-a-mof-resource"></a>Mapstructuur voor een MOF-bron

Voor het implementeren van een aangepaste DSC-resource met een MOF-schema, maken de volgende mapstructuur. Het MOF-schema is gedefinieerd in het bestand Demo_IISWebsite.schema.mof en het resource-script is gedefinieerd in Demo_IISWebsite.psm1. U kunt desgewenst een module-manifest (psd1)-bestand maken.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

Houd er rekening mee dat het nodig zijn voor het maken van een map met de naam DSCResources onder de hoofdmap is en dat de map voor elke resource moet dezelfde naam als de bron.

### <a name="the-contents-of-the-mof-file"></a>De inhoud van het MOF-bestand

Hier volgt een voorbeeld van de MOF-bestand dat kan worden gebruikt voor de bron van een aangepaste website. Wilt u dit voorbeeld, dit schema opslaan in een bestand en het bestand *Demo_IISWebsite.schema.mof*.

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

* `FriendlyName`definieert de naam die u gebruiken kunt om te verwijzen naar deze aangepaste resource in scripts voor DSC-configuratie. In dit voorbeeld `Website` komt overeen met de beschrijvende naam `Archive` voor de ingebouwde archief-resource.
* De klasse die u definieert voor de aangepaste resource moet worden afgeleid van `OMI_BaseResource`.
* De kwalificatie type `[Key]`op een eigenschap aangeeft dat deze eigenschap een unieke identificatie van de resource-instantie. Ten minste één `[Key]` eigenschap is vereist.
* De `[Required]` kwalificatie geeft aan dat de eigenschap vereist is (er moet een waarde worden opgegeven in een configuratiescript dat gebruikmaakt van deze bron).
* De `[write]` kwalificatie geeft aan dat deze eigenschap optioneel is bij het gebruik van de aangepaste resource in een configuratiescript. De `[read]` kwalificatie geeft aan dat een eigenschap kan niet worden ingesteld door een configuratie en is alleen voor rapportagedoeleinden.
* `Values`Hiermee beperkt u de waarden die kunnen worden toegewezen aan de eigenschap aan de lijst met waarden die zijn gedefinieerd in `ValueMap`. Zie voor meer informatie [ValueMap en waarde-kwalificaties bevat](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).
* Met inbegrip van een eigenschap genaamd `Ensure` met waarden `Present` en `Absent` in de bron, wordt aanbevolen als een manier om een consistente stijl met ingebouwde DSC-resources te onderhouden.
* Naam van het schemabestand voor uw aangepaste resource als volgt: `classname.schema.mof`, waarbij `classname` is de id die volgt de `class` -sleutelwoord in de schemadefinitie van de.

### <a name="writing-the-resource-script"></a>De resource-script schrijven

Het script resource implementeert de logica van de resource. U moet drie functies aangeroepen opnemen in deze module **Get-TargetResource**, **Set TargetResource**, en **Test TargetResource**. Alle drie functies moeten rekening houden met een parameterset die identiek is aan de set eigenschappen die zijn gedefinieerd in het MOF-schema dat u hebt gemaakt voor uw resource. In dit document, wordt deze reeks eigenschappen aangeduid als de "broneigenschappen'. Deze drie functies in een bestand genaamd Store <ResourceName>.psm1. In het volgende voorbeeld worden de functies worden opgeslagen in een bestand met de naam Demo_IISWebsite.psm1.

> **Opmerking**: wanneer u de dezelfde configuratiescript op uw resource meer dan één keer uitvoeren, u geen fouten ontvangt en de bron in dezelfde staat blijven moet als het eenmaal uitvoeren van het script. U doet dit door ervoor te zorgen dat uw **Get-TargetResource** en **Test TargetResource** functies laat de bron niet worden gewijzigd en dat aanroepen van de **Set-TargetResource**werken meer dan één keer in een reeks met dezelfde parameter waarden is altijd gelijk is aan één keer aangeroepen.

In de **Get-TargetResource** implementatie werkt, de belangrijkste bron eigenschapswaarden die beschikbaar zijn als parameters gebruiken om te controleren van de status van het exemplaar van de opgegeven bron. Deze functie moet een hashtabel waarin de broneigenschappen als sleutels en de werkelijke waarden van deze eigenschappen als de bijbehorende waarden retourneren. De volgende code geeft een voorbeeld.

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

Afhankelijk van de waarden die zijn opgegeven voor de resource-eigenschappen in het configuratiescript de **Set TargetResource** moet een van de volgende dingen doen:

* Een nieuwe website maken
* Bijwerken van een bestaande website
* Verwijderen van een bestaande website

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

Ten slotte de **Test TargetResource** functie moet rekening houden met dezelfde parameterset als **Get-TargetResource** en **Set TargetResource**. Bij de implementatie van **Test TargetResource**, Controleer de status van de resource-instantie die is opgegeven in de belangrijkste parameters. Als de huidige status van het exemplaar van de resource komt niet overeen met de opgegeven waarden in de parameterset, geretourneerd **$false**. Anders retourneren **$true**.

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

**Opmerking**: voor gemakkelijker foutopsporing, gebruikt u de **Write-Verbose** cmdlet in uw implementatie van de vorige drie functies. 
>Deze cmdlet schrijft tekst naar de uitgebreide berichtenstroom. 
>Standaard de uitgebreide berichtenstroom niet wordt weergegeven, maar kunt u deze weergeven door het wijzigen van de waarde van de **$VerbosePreference** variabele of met behulp van de **uitgebreid** parameter in de DSC-cmdlets = new.

### <a name="creating-the-module-manifest"></a>Maken van de module-manifest

Gebruik tot slot de **nieuw ModuleManifest** cmdlet voor het definiëren van een <ResourceName>.psd1-bestand voor uw aangepaste resource-module. Als u deze cmdlet aanroept, verwijzen naar het scriptbestand voor module (.psm1) die worden beschreven in de vorige sectie. Omvatten **Get-TargetResource**, **Set TargetResource**, en **Test TargetResource** in de lijst met functies om te exporteren. Hier volgt een voorbeeld-manifestbestand.

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

De **PsDscRunAsCredential** eigenschap kan worden gebruikt [DSC-configuraties](configurations.md) resource blok om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties.
Zie voor meer informatie [DSC uitgevoerd met gebruikersreferenties](runAsUser.md).

Voor toegang tot de gebruikerscontext van binnen een aangepaste bron, kunt u de automatische variabele `$PsDscContext`.

De volgende code zou bijvoorbeeld de gebruikerscontext waaronder de bron wordt uitgevoerd naar de uitgebreide uitvoerstroom schrijven:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```




