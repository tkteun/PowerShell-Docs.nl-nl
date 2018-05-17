---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Nieuwe scenario's en onderdelen in WMF 5.1
ms.openlocfilehash: 77b439e61c5802f8ddbc4a0f39923cc8c0c36fe9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="new-scenarios-and-features-in-wmf-51"></a>Nieuwe scenario's en onderdelen in WMF 5.1

> Opmerking: Deze informatie is voorlopig en kan worden gewijzigd.

## <a name="powershell-editions"></a>PowerShell-edities

Vanaf versie 5.1 is PowerShell beschikbaar in verschillende edities die staan voor verschillende functies en platformcompatibiliteit.

- **Desktop-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een volledige footprint zoals Server Core en Windows Desktop.
- **Core-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een verminderde footprint zoals Nano Server en Windows IoT.

**Meer informatie over het gebruik van PowerShell-edities**

- [Actieve versie van PowerShell met $PSVersionTable bepalen](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Get-Module resultaten door met de parameter PSEdition CompatiblePSEditions filteren](/powershell/module/microsoft.powershell.core/get-module)
- [Voorkomen dat de uitvoering van script tenzij uitvoeren op een compatibele versie van PowerShell](/powershell/gallery/psget/script/scriptwithpseditionsupport)
- [Een module compatibiliteit met bepaalde versies van PowerShell declareren](/powershell/gallery/psget/module/modulewithpseditionsupport)

## <a name="catalog-cmdlets"></a>Catalogus-Cmdlets

Twee nieuwe cmdlets toegevoegd de [Microsoft.PowerShell.Security](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security) module; deze genereren en bestanden voor Windows-catalogus te valideren.

### <a name="new-filecatalog"></a>Nieuwe FileCatalog
--------------------------------

Nieuwe FileCatalog maakt een Windows-catalogusbestand voor mappen en bestanden.
Dit catalogusbestand bevat hashes voor alle bestanden in de opgegeven paden.
De set mappen samen met de bijbehorende catalogusbestand voor deze mappen, kunnen gebruikers distribueren.
Deze informatie is nuttig om te valideren of de wijzigingen voor de mappen zijn aangebracht sinds de aanmaaktijd van de catalogus.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Catalogus versie 1 en 2 worden ondersteund.
De SHA1-hash-algoritme voor het maken van bestands-hashes; maakt gebruik van versie 1 SHA256 maakt gebruik van versie 2.
Catalogusversie 2 van de wordt niet ondersteund op *Windows Server 2008 R2* of *Windows 7*.
U moet catalogusversie 2 van de gebruiken voor *Windows 8*, *Windows Server 2012*, en latere besturingssystemen.

![](../images/NewFileCatalog.jpg)

Hiermee maakt u het catalogusbestand.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Als u wilt controleren of de integriteit van catalogusbestand (Pester.cat in bovenstaande voorbeeld), meld u aan met behulp van [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.

### <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

Test FileCatalog valideert de catalogus die vertegenwoordigt een reeks mappen.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Deze cmdlet worden alle bestanden-hashes vergeleken en hun relatieve paden te vinden in *catalogus* met toepassingsgroepen op *schijf*.
Als er een discrepantie tussen het bestands-hashes en paden gedetecteerd wordt de status als *ValidationFailed*.
Gebruikers kunnen deze informatie ophalen met behulp van de *-gedetailleerde* parameter.
Er wordt ook weergegeven ondertekenen status van de catalogus in *handtekening* -eigenschap hebben die gelijk is aan het aanroepen [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet uit op het catalogusbestand.
Gebruikers kunnen ook een bestand tijdens de validatie overslaan met behulp van de *- FilesToSkip* parameter.

## <a name="module-analysis-cache"></a>Module Analysis-Cache

Beginnen met WMF 5.1, biedt PowerShell controle over het bestand dat wordt gebruikt voor cachegegevens over een module, zoals de opdrachten die zijn geëxporteerd.

Deze cache wordt standaard opgeslagen in het bestand `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
De cache is doorgaans lezen bij het opstarten tijdens het zoeken naar een opdracht en geschreven in een achtergrondthread enige tijd opnieuw nadat een module is geïmporteerd.

Als u wilt wijzigen van de standaardlocatie van de cache, de `$env:PSModuleAnalysisCachePath` omgevingsvariabele voordat u start PowerShell.
Wijzigingen in deze omgevingsvariabele wordt alleen van invloed op de onderliggende processen.
De waarde moet een volledig pad (inclusief bestandsnaam) zijn dat PowerShell gemachtigd is te maken en bestanden schrijven name.
Schakel de bestandscache van deze waarde instelt op een ongeldige locatie, bijvoorbeeld:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Hiermee stelt het pad naar een ongeldige apparaat.
Als PowerShell kan niet naar het pad schrijven, geen fout wordt geretourneerd, maar u kunt zien die fouten rapporteren met behulp van een traceerders:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Bij het schrijven van de cache wordt PowerShell voor modules die niet meer bestaan om te voorkomen dat een onnodig groot cache gecontroleerd.
Soms zijn deze controles niet wenselijk in dat geval kunt u deze uitschakelen door in te stellen:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Instellen van deze omgevingsvariabele wordt onmiddellijk van kracht in het huidige proces.

## <a name="specifying-module-version"></a>Moduleversie opgeven

In WMF 5.1 `using module` gedraagt zich dezelfde manier als andere constructies module-gerelateerde in PowerShell.
Voorheen moest u geen manier om op te geven van een bepaalde moduleversie; Als er meerdere versies aanwezig is, resulteert dit in een fout.

In een WMF 5.1:

- U kunt [ModuleSpecification-Constructor (hashtabel)](https://msdn.microsoft.com/library/jj136290).
Deze hashtabel heeft dezelfde indeling als `Get-Module -FullyQualifiedName`.

**Voorbeeld:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- Als er meerdere versies van de module, PowerShell wordt de **dezelfde resolutie logica** als `Import-Module` en niet een plaatsingsfout--hetzelfde gedrag als `Import-Module` en `Import-DscResource`.

## <a name="improvements-to-pester"></a>Verbeteringen in lastige

In WMF 5.1, de versie van Pester die wordt geleverd met PowerShell is bijgewerkt van 3.3.5 naar 3.4.0 met de toevoeging van het doorvoeren https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, die zorgt voor betere gedrag voor Pester op Nano Server.

U kunt de wijzigingen in versies 3.3.5-3.4.0 bekijken door te inspecteren van het bestand ChangeLog.md op: https://github.com/pester/Pester/blob/master/CHANGELOG.md
