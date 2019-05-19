---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Opmerkingen bij de Release van de WMF 5.x
ms.openlocfilehash: 8bdc423234cf0b104b72b1bee1de35e50783d8a4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856397"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>Windows Management Framework (WMF) 5.x Release Notes

## <a name="wmf-50-changes"></a>WMF 5.0 wordt gewijzigd

- PowerShell 5.0 voegt een nieuwe gestructureerde **informatie** stream
- Verbeteringen aan DSC, met inbegrip van vier nieuwe DSC-resources:
  - WindowsFeatureSet
  - WindowsOptionalFeatureSet
  - ServiceSet
  - ProcessSet
- Toegevoegde Just Enough Administration om in te schakelen op rollen gebaseerd beheer via externe communicatie van PowerShell
- PowerShell 5.0 breidt de taal om op te nemen van de gebruiker gedefinieerde klassen en opsommingen
- Verbeterde functies in PowerShell ISE en extra foutopsporing op afstand foutopsporing
- De PowerShellGet en PackageManagement-modules toegevoegd
- Uitgebreide logboekregistratie voor PowerShell-script en transcripties
- Cmdlets voor Cryptographic Message-syntaxis toevoegen
- WMF 5.0 bevat de NetworkSwitchManager-module voor Windows
- De module Microsoft.PowerShell.ODataUtils toegevoegd
- Er is ondersteuning toegevoegd voor Software Inventory Logging (SIL)
- Nieuwe server of -cmdlets in reactie op aanvragen van gebruikers en problemen bijwerken

## <a name="wmf-51-changes"></a>WMF 5.1 wordt gewijzigd

WMF 5.1 omvat de PowerShell-, WMI-, WinRM- en Software Inventory Logging (SIL)-onderdelen die zijn uitgebracht met Windows Server 2016. WMF 5.1 kan worden geïnstalleerd op Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 en 2012 R2, en biedt verschillende verbeteringen ten opzichte van WMF 5.0 met inbegrip van:

- Er zijn nieuwe cmdlets
- PowerShellGet-verbeteringen, waaronder het afdwingen van ondertekende modules en het installeren van JEA-modules
- Ondersteuning in PackageManagement toegevoegd voor Containers, CBS Setup, EXE-installatie en CAB-pakketten
- Verbeteringen in foutopsporing voor DSC- en PowerShell-klassen
- Beveiligingsverbeteringen, waaronder de handhaving van door catalogus ondertekende modules die afkomstig zijn van de pull-server, gebruikt in combinatie met PowerShellGet-cmdlets
- Antwoorden op een aantal gebruikersaanvragen en -problemen

## <a name="powershell-editions"></a>PowerShell-edities

Vanaf versie 5.1 is is PowerShell beschikbaar in de verschillende edities, op basis van verschillende functies en platformcompatibiliteit.

- **Desktop-editie:** Gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows, zoals Server Core- en Windows Desktop volledige footprint.
- **Core-editie:** Gebaseerd op .NET Core en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows, zoals Nano Server en Windows IoT verminderde footprint.

### <a name="learn-more-about-using-powershell-editions"></a>Meer informatie over het gebruik van PowerShell-edities

- [Actieve editie van PowerShell met behulp van $PSVersionTable bepalen](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Resultaten van de Get-Module door met de parameter PSEdition CompatiblePSEditions te filteren](/powershell/module/microsoft.powershell.core/get-module)
- [Scriptuitvoering wordt voorkomen tenzij uitvoert op een compatibele versie van PowerShell](/powershell/gallery/concepts/script-psedition-support)
- [Declareer de compatibiliteit van een module met specifieke versies van PowerShell](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>Module Analysis Cache

Beginnen met WMF 5.1, biedt PowerShell controle over het bestand dat wordt gebruikt om cachegegevens over een module, zoals de opdrachten die zijn geëxporteerd.

Standaard worden deze cache wordt opgeslagen in het bestand `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. De cache doorgaans bij het opstarten tijdens het zoeken naar een opdracht wordt gelezen en geschreven op een achtergrond-thread enige tijd opnieuw uit nadat een module is geïmporteerd.

Als u wilt de standaardlocatie van de cache wijzigen, stelt de `$env:PSModuleAnalysisCachePath` omgevingsvariabele voordat u begint met PowerShell. Wijzigingen in deze omgevingsvariabele wordt alleen van invloed op de onderliggende processen. De waarde moet een naam een volledig pad (inclusief bestandsnaam) zijn dat PowerShell gemachtigd is om het maken en bestanden te schrijven. Als u wilt uitschakelen bestandscache, deze waarde instelt op een ongeldige locatie, bijvoorbeeld:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Hiermee stelt het pad naar een ongeldige apparaatnaam. Als PowerShell kan niet naar het pad schrijven, er wordt geen fout wordt geretourneerd, maar u kunt zien die fouten rapporteren met behulp van een traceringstoken:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Bij het schrijven van de cache wordt PowerShell-modules die niet meer aanwezig zijn om te voorkomen dat een onnodig groot cache controleren. Soms zijn deze controles niet wenselijk in dat geval kunt u deze uitschakelen door in te stellen:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Instellen van deze omgevingsvariabele wordt onmiddellijk van kracht in het huidige proces.

## <a name="specifying-module-version"></a>Moduleversie opgeven

In WMF 5.1, `using module` gedrag net als andere constructies met betrekking tot module in PowerShell.
Voorheen moest u geen enkele manier om op te geven van een bepaalde moduleversie; Als er meerdere versies aanwezig waren, dit heeft een fout gegenereerd.

In WMF 5.1:

- U kunt [ModuleSpecification Constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).
  Deze hashtabel heeft dezelfde indeling als `Get-Module -FullyQualifiedName`.

  **Voorbeeld:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- Als er meerdere versies van de module, PowerShell wordt gebruikt de **dezelfde resolutie logica** als `Import-Module` en niet een plaatsingsfout--hetzelfde gedrag als `Import-Module` en `Import-DscResource`.

## <a name="improvements-to-pester"></a>Verbeteringen voor lastige

In WMF 5.1, is de versie van Pester die wordt geleverd met PowerShell uit 3.3.5 bijgewerkt naar 3.4.0.
Deze update kunt beter gedrag voor Pester op Nano Server.

U kunt de wijzigingen in het kader van bestrijding bekijken door te inspecteren de [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) in de GitHub-opslagplaats.
