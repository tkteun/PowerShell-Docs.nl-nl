---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Nieuwe scenario's en onderdelen in WMF 5.1
ms.openlocfilehash: b00069aad7422f86d1462a62a6c4bc8a91e46705
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085429"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a>Nieuwe scenario's en onderdelen in WMF 5.1

> Opmerking: Deze informatie is voorlopig en kan worden gewijzigd.

## <a name="powershell-editions"></a>PowerShell-edities

Vanaf versie 5.1 is PowerShell beschikbaar in verschillende edities die staan voor verschillende functies en platformcompatibiliteit.

- **Desktop-editie:** Gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows, zoals Server Core- en Windows Desktop volledige footprint.
- **Core-editie:** Gebaseerd op .NET Core en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows, zoals Nano Server en Windows IoT verminderde footprint.

**Meer informatie over het gebruik van PowerShell-edities**

- [Actieve editie van PowerShell met behulp van $PSVersionTable bepalen](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Resultaten van de Get-Module door met de parameter PSEdition CompatiblePSEditions te filteren](/powershell/module/microsoft.powershell.core/get-module)
- [Scriptuitvoering wordt voorkomen tenzij uitvoert op een compatibele versie van PowerShell](/powershell/gallery/concepts/script-psedition-support)
- [Declareer de compatibiliteit van een module met specifieke versies van PowerShell](/powershell/gallery/concepts/module-psedition-support)

## <a name="catalog-cmdlets"></a>Catalogus-Cmdlets

Twee nieuwe-cmdlets zijn toegevoegd de [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) module; deze genereren en bestanden van Windows-catalogus te valideren.

### <a name="new-filecatalog"></a>Nieuwe FileCatalog
--------------------------------

Nieuwe FileCatalog Hiermee maakt u een Windows-catalogusbestand voor set van bestanden en mappen.
Dit catalogusbestand bevat-hashes voor alle bestanden in de opgegeven paden.
Gebruikers kunnen de set van mappen, samen met de bijbehorende catalogusbestand voor deze mappen distribueren.
Deze informatie is nuttig om te valideren of eventuele wijzigingen worden aangebracht aan de mappen sinds de aanmaaktijd van de catalogus.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Versies 1 en 2 van de catalogus worden ondersteund.
Versie 1 gebruikt de SHA1-hash-algoritme voor het maken van bestands-hashes; SHA256 maakt gebruik van versie 2.
Catalogusversie 2 wordt niet ondersteund op *Windows Server 2008 R2* of *Windows 7*.
Moet u catalogusversie 2 van de op *Windows 8*, *Windows Server 2012*, en latere besturingssystemen.

![](../images/NewFileCatalog.jpg)

Hiermee maakt u het catalogusbestand.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Om te controleren of de integriteit van catalogusbestand (Pester.cat in bovenstaande voorbeeld), meld u aan met behulp van [Set AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet.

### <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

Test-FileCatalog valideert de catalogus voor een set van mappen.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Deze cmdlet worden alle bestanden-hashes vergeleken en hun relatieve paden te vinden *catalogus* met resources op *schijf*.
Als er overeenkomende bestands-hashes en paden gedetecteerd wordt de status als *ValidationFailed*.
Gebruikers kunnen al deze gegevens ophalen met behulp van de *-gedetailleerde* parameter.
Er wordt ook weergegeven ondertekenings status van de catalogus in *handtekening* eigenschap die gelijk is aan het aanroepen [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet uit op de catalog-bestand.
Gebruikers kunnen ook een bestand tijdens de validatie overslaan met behulp van de *- FilesToSkip* parameter.

## <a name="module-analysis-cache"></a>Module Analysis Cache

Beginnen met WMF 5.1, biedt PowerShell controle over het bestand dat wordt gebruikt om cachegegevens over een module, zoals de opdrachten die zijn geëxporteerd.

Standaard worden deze cache wordt opgeslagen in het bestand `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
De cache doorgaans bij het opstarten tijdens het zoeken naar een opdracht wordt gelezen en geschreven op een achtergrond-thread enige tijd opnieuw uit nadat een module is geïmporteerd.

Als u wilt de standaardlocatie van de cache wijzigen, stelt de `$env:PSModuleAnalysisCachePath` omgevingsvariabele voordat u begint met PowerShell.
Wijzigingen in deze omgevingsvariabele wordt alleen van invloed op de onderliggende processen.
De waarde moet een naam een volledig pad (inclusief bestandsnaam) zijn dat PowerShell gemachtigd is om het maken en bestanden te schrijven.
Als u wilt uitschakelen bestandscache, deze waarde instelt op een ongeldige locatie, bijvoorbeeld:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Hiermee stelt het pad naar een ongeldige apparaatnaam.
Als PowerShell kan niet naar het pad schrijven, er wordt geen fout wordt geretourneerd, maar u kunt zien die fouten rapporteren met behulp van een traceringstoken:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Bij het schrijven van de cache wordt PowerShell-modules die niet meer aanwezig zijn om te voorkomen dat een onnodig groot cache controleren.
Soms zijn deze controles niet wenselijk in dat geval kunt u deze uitschakelen door in te stellen:

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

In WMF 5.1, de versie van Pester die wordt geleverd met PowerShell is bijgewerkt van 3.3.5 naar 3.4.0, met de toevoeging van het doorvoeren https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, die zorgt voor een betere gedrag voor Pester op Nano Server.

U kunt de wijzigingen in versie 3.3.5-3.4.0 bekijken door te inspecteren van het bestand ChangeLog.md op: https://github.com/pester/Pester/blob/master/CHANGELOG.md
