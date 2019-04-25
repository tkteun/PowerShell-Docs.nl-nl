---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: Import-DSCResource gebruiken
ms.openlocfilehash: ee0b2f0469c6507c8f0148138198597a9e57cdd7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080098"
---
# <a name="using-import-dscresource"></a>Import-DSCResource gebruiken

`Import-DScResource` is een dynamische sleutelwoord, die alleen kan worden gebruikt in een configuratie-scriptblok. De `Import-DSCResource` trefwoord dat u wilt importeren van alle resources die nodig zijn in uw configuratie. Resources onder `$pshome` automatisch worden geïmporteerd, maar het is nog steeds beschouwd als aanbevolen procedure voor het expliciet importeren van alle resources die worden gebruikt uw [configuratie](Configurations.md).

De syntaxis voor `Import-DSCResource` wordt hieronder weergegeven.  Bij het opgeven van modules met de naam, is het een vereiste om elk op een nieuwe regel weer te geven.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Parameter  |Description  |
|---------|---------|
|`-Name`|De namen van de DSC-resource die u moet importeren. Als de naam van de module is opgegeven, de opdracht wordt gezocht naar deze DSC-resources binnen deze module. de opdracht zoekt anders de DSC-resources in alle paden voor DSC-resource. Jokertekens worden ondersteund.|
|`-ModuleName`|De modulenaam of het module-specificatie.  Als u resources te importeren vanuit een module opgeeft, wordt de opdracht wordt geprobeerd enkel de resources te importeren. Als u de module alleen opgeeft, wordt met de opdracht de DSC-resources in de module geïmporteerd.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Voorbeeld: Sleutelwoorden Import-dscresource bieden in een configuratie gebruiken

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
> Meerdere waarden voor de namen van de Resource en modules in dezelfde opdracht op te geven, worden niet ondersteund. Het kan gedrag van niet-deterministisch over welke resource moet worden geladen vanaf welke module in het geval dezelfde resource in meerdere modules bestaat hebben. Onderstaande opdracht resulteert in fout tijdens de compilatie.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Dingen om te overwegen bij het gebruik van alleen de parameter Name:

- Dit is een resource-intensieve bewerking afhankelijk van het aantal modules die zijn geïnstalleerd op de machine.
- Het wordt geladen door de eerste resource gevonden met de opgegeven naam. In het geval wanneer er meer dan één resource met dezelfde naam geïnstalleerd is, de juiste resource kan worden geladen.

De aanbevolen methode is om op te geven `–ModuleName` met de `-Name` parameter, zoals hieronder wordt beschreven.

Dit gebruik heeft de volgende voordelen:

- Dit vermindert de prestatiegevolgen door het beperken van het zoekbereik voor de opgegeven resource.
- Hiermee worden de module definiëren van de resource, ervoor te zorgen dat de juiste resource wordt geladen expliciet gedefinieerd.

> [!NOTE]
> In PowerShell 5.0, DSC-resources kunnen er meerdere versies en versies kunnen worden geïnstalleerd op een computer side-by-side. Dit is geïmplementeerd door meerdere versies van een resource-module die zijn opgenomen in de modulemap met dezelfde.
> Zie voor meer informatie, [resources met meerdere versies gebruiken](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense met sleutelwoorden Import-dscresource bieden

Bij het ontwerpen van de DSC-configuratie in ISE biedt PowerShell IntelliSence voor resources en resource-eigenschappen. Resourcedefinities onder de `$pshome` modulepad worden automatisch geladen. Wanneer het importeren van resources met behulp van de `Import-DSCResource` trefwoord, de opgegeven resource-definities zijn toegevoegd en Intellisense om op te nemen van de geïmporteerde resource-schema is uitgevouwen.

![Resource Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> Begin in PowerShell 5.0, is tab-Aanvulling toegevoegd aan de ISE voor DSC-resources en hun eigenschappen. Zie voor meer informatie, [Resources](../resources/resources.md).

Bij het compileren van de configuratie van de PowerShell maakt gebruik van de geïmporteerde resourcedefinities alle resource blokken in de configuratie valideren.
Elk blok van de resource is gevalideerd, met behulp van de resource-schemadefinitie, voor de volgende regels.

- Alleen de eigenschappen die zijn gedefinieerd in het schema worden gebruikt.
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

Validatie van IntelliSense en het schema kunt u meer runbookauteur fouten worden gedetecteerd tijdens het parseren en compilatie tijd complicaties vermijden tijdens de uitvoering.

> [!NOTE]
> Elke DSC-resource kan hebben een naam en een **FriendlyName** gedefinieerd door de resource-schema. Hieronder vindt u de eerste twee regels van 'MSFT_ServiceResource.shema.mof'.
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Wanneer u deze resource in een configuratie gebruikt, kunt u **MSFT_ServiceResource** of **Service**.

## <a name="powershell-v4-and-v5-differences"></a>Verschillen in PowerShell v4 en versie 5

Er zijn meerdere verschillen u ziet bij het ontwerpen van configuraties in PowerShell 4.0 Visual Studio. PowerShell 5.0 en hoger. In deze sectie worden de verschillen die u ziet dat relevant is voor dit artikel.

### <a name="multiple-resource-versions"></a>Meerdere versies van de Resource

Installeren en gebruiken van meerdere versies van resources naast elkaar wordt niet ondersteund in PowerShell 4.0. Als u problemen met het importeren van resources in uw configuratie ziet, zorg ervoor dat u slechts één versie van de resource geïnstalleerd hebben.

In de afbeelding hieronder, twee versies van de **xPSDesiredStateConfiguration** module zijn geïnstalleerd.

![Meerdere Resource-versies opgelost](/media/multiple-resource-versions-broken.md)

Kopieer de inhoud van uw moduleversie van de gewenste naar het hoogste niveau van de modulemap.

![Meerdere Resource-versies opgelost](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Resourcelocatie

Bij het ontwerpen en -configuraties compileren, uw resources kunnen worden opgeslagen in een map die is opgegeven door uw [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). In PowerShell 4.0, vereist de LCM alle DSC-resource-modules worden opgeslagen onder 'Programma Files\WindowsPowerShell\Modules' of `$pshome\Modules`. Begin in PowerShell 5.0, deze vereiste is verwijderd en resource-modules kunnen worden opgeslagen in een map die is opgegeven door `PSModulePath`.

## <a name="see-also"></a>Zie ook

- [Resources](../resources/resources.md)
