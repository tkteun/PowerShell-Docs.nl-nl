---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie, setup
title: Import-DSCResource gebruiken
ms.openlocfilehash: f22c741969b1429074e7307a00a5c014cf563089
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265498"
---
# <a name="using-import-dscresource"></a>Import-DSCResource gebruiken

`Import-DScResource` is een dynamische trefwoord, kan alleen worden gebruikt in een configuratie-scriptblok. De `Import-DSCResource` sleutelwoord voor het importeren van alle resources die nodig is in uw configuratie. Resources onder `$phsome` automatisch worden geïmporteerd, maar nog steeds de beste expliciet importeren van alle resources die worden gebruikt in uw [configuratie](Configurations.md).

De syntaxis voor `Import-DSCResource` worden hieronder weergegeven.  Wanneer u modules opgeeft met de naam, is het een vereiste voor een lijst met elk op een nieuwe regel.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Parameter  |Description  |
|---------|---------|
|`-Name`|De namen van de DSC-resource die u moet importeren. Als de naam van de module is opgegeven, zoekt u de opdracht voor deze DSC-resources binnen deze module; de opdracht zoekt anders de DSC-resources in alle paden voor DSC-resource. Jokertekens worden ondersteund.|
|`-ModuleName`|De modulenaam of module-specificatie.  Als u bronnen om te importeren vanuit een module opgeeft, probeert de opdracht alleen de resources importeren. Als u de module alleen opgeeft, wordt de opdracht de DSC-resources in de module geïmporteerd.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Voorbeeld: Importeren DSCResource gebruiken in een configuratie

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry
    
    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> Het opgeven van meerdere waarden voor de namen van de Resource en modules in dezelfde opdracht worden niet ondersteund. Deze kan niet-deterministisch gedrag over welke resource moet worden geladen vanuit welke module als dezelfde resource in meerdere modules bestaat hebben. Onderstaande opdracht resulteert in fout tijdens de compilatie.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Aandachtspunten bij gebruik van alleen de parameter Name:

- Dit is een bronintensieve bewerking afhankelijk van het aantal modules geïnstalleerd op de machine.
- Het wordt geladen door de eerste resource met de opgegeven naam gevonden. In het geval wanneer er meer dan één resource met dezelfde naam geïnstalleerd, de verkeerde bron kan worden geladen.

Het aanbevolen gebruik is om op te geven `–ModuleName` met de `-Name` parameter, zoals hieronder wordt beschreven.

Dit gebruik heeft de volgende voordelen:

- Vermindert de invloed op de prestaties door het beperken van het zoekbereik voor de opgegeven resource.
- Expliciet Hiermee definieert u de module voor het definiëren van de resource, zodat de juiste resource is geladen.

> [!NOTE]
> In PowerShell 5.0 DSC-resources mogelijk meerdere versies en versies kunnen worden geïnstalleerd op een computer naast elkaar. Dit wordt geïmplementeerd door meerdere versies van een resource-module die zijn opgenomen in dezelfde modulemap.
> Zie voor meer informatie [door resources met meerdere versies](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense met importeren DSCResource

Bij het ontwerpen van de DSC-configuratie in ISE biedt PowerShell IntelliSence voor resources en broneigenschappen. Resourcedefinities onder de `$pshome` pad module worden automatisch geladen. Wanneer het importeren van resources met behulp van de `Import-DSCResource` sleutelwoord, de opgegeven resourcedefinities worden toegevoegd en Intellisense is uitgebreid met de geïmporteerde resource-schema.

![Resource Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> U begint in PowerShell 5.0, is tab-Aanvulling toegevoegd aan de ISE voor DSC-resources en de bijbehorende eigenschappen. Zie voor meer informatie [Resources](../resources/resources.md).

Bij het compileren van de configuratie van de PowerShell maakt gebruik van de geïmporteerde resourcedefinities alle resource blokken in de configuratie valideren.
Elk blok van de resource is gevalideerd met behulp van de resource-schemadefinitie, voor de volgende regels.

- Alleen eigenschappen die in het schema worden gebruikt.
- De gegevenstypen voor elke eigenschap zijn correct.
- Eigenschappen van de sleutels worden opgegeven.
- Er is geen alleen-lezen eigenschap wordt gebruikt.
- Validatie van waarde toegewezen typen.

Houd rekening met de volgende configuratie:

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

Compileren van deze configuratie leidt tot een fout.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

IntelliSense en schema-validatie kunt u meer fouten tijdens het parseren en compilatie tijd, catch problemen te vermijden tijdens de uitvoering.

> [!NOTE]
> Elke DSC-resource kan hebben een naam en een **FriendlyName** gedefinieerd door de resource-schema. Hieronder vindt u de eerste twee regels van 'MSFT_ServiceResource.shema.mof'.
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Wanneer u deze bron in een configuratie gebruikt, kunt u opgeven **MSFT_ServiceResource** of **Service**.

## <a name="powershell-v4-and-v5-differences"></a>PowerShell v4 en v5 verschillen

Er zijn meerdere verschillen u ziet bij het ontwerpen van configuraties in de vs PowerShell 4.0. PowerShell 5.0 en hoger. Deze sectie worden de verschillen markeren dat u relevant zijn voor dit artikel ziet.

### <a name="multiple-resource-versions"></a>Meerdere versies van de Resource

Installeren en gebruiken van meerdere versies van resources gelijktijdige werden niet ondersteund in PowerShell 4.0. Als u problemen met het importeren van resources in uw configuratie ziet, zorg ervoor dat u slechts één versie van de resource die is geïnstalleerd.

In de afbeelding hieronder twee versies van de **xPSDesiredStateConfiguration** module zijn geïnstalleerd.

![Meerdere Resource-versies vast](/media/multiple-resource-versions-broken.md)

Kopieer de inhoud van uw moduleversie van de gewenste naar het hoogste niveau van de modulemap.

![Meerdere Resource-versies vast](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Resourcelocatie

Bij het ontwerpen en configuraties compileren, uw resources kunnen worden opgeslagen in een map die is opgegeven door uw [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). In PowerShell 4.0 vereist de LCM alle DSC-resource-modules moeten worden opgeslagen onder 'Programma Files\WindowsPowerShell\Modules' of `$pshome\Modules`. Vanaf PowerShell 5.0 is deze vereiste is verwijderd en resource-modules kunnen worden opgeslagen in een map die is opgegeven door `PSModulePath`.

## <a name="see-also"></a>Zie ook

- [Resources](../resources/resources.md)
