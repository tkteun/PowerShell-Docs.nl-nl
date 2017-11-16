---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: psgallery_gettingstarted
ms.openlocfilehash: d13c23cd6f9cce433cd3fe1ad5f2d00e3ef0527c
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/29/2017
---
# <a name="get-started-with-the-powershell-gallery"></a>Aan de slag met de PowerShell-galerie

## <a name="what-is-the-powershell-gallery"></a>Wat is de PowerShell-galerie?

De PowerShell-galerie is de centrale opslagplaats voor PowerShell-inhoud.
In dit vindt u nuttige PowerShell-modules met PowerShell-opdrachten en resources Desired State Configuration (DSC). U kunt ook PowerShell-scripts, kunnen sommige van deze PowerShell-werkstromen en overzicht maken van een set taken bevatten en sequentiëren voor deze taken bieden vinden.
Sommige van deze items zijn gemaakt door Microsoft en anderen zijn ontworpen door de PowerShell-community.

## <a name="requirements"></a>Vereisten

Downloaden van items uit de PowerShell-galerie in uw systeem vereist de [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module. U kunt de module PowerShellGet vinden in het volgende. U hoeft niet aan te melden bij het downloaden van items uit de PowerShell-galerie.

-   [Windows 10](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [MSI-installatieprogramma (voor PowerShell 3 en 4)](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

PowerShellGet vereist ook de [NuGet provider](http://go.microsoft.com/fwlink/?LinkId=722208) werken met de PowerShell-galerie. U wordt gevraagd voor het installeren van de provider NuGet automatisch bij het eerste gebruik van PowerShellGet als de NuGet-provider niet in een van de volgende locaties is:

- `$env:ProgramFiles\PackageManagement\ProviderAssemblies`
- `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies`

Of u kunt uitvoeren `Install-PackageProvider -Name NuGet -Force` voor het automatiseren van het downloaden en installeren van de NuGet-provider.

  
Als u een versie die ouder zijn dan 2.8.5.201 van NuGet hebt, moet u aan te roepen de volgende PowerShell-cmdlets voor het installeren en schakel over naar de nieuwste versie van het NuGet.

1.  `Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
2.  `Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
3.  De oudere versie van NuGet verwijderen uit de bovenstaande locatie is geïnstalleerd.

Zie voor meer informatie <http://oneget.org/> .

  
Opmerking: Als gevolg van wijzigingen in de indelingen verpakking, wordt aangeraden dat u bijwerken naar de nieuwste versie van PowerShellGet en PackageManagement voor het installeren van de items die onlangs zijn bijgewerkt. PowerShellGet is opgenomen in Windows 10, kunt u meer informatie over [hier](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409).
PowerShellGet maakt ook deel uit van de Windows Management Framework (WMF) 5.0, die u kunt downloaden [hier](http://go.microsoft.com/fwlink/?LinkId=398175).

## <a name="discovering-items-from-the-powershell-gallery"></a>Detectie van items van de PowerShell Gallery

U kunt items in de PowerShell-galerie vinden met behulp van de **Search** besturingselement op deze website, of door te bladeren door de pagina's Modules en -Scripts. U kunt items van de PowerShell Gallery ook vinden door het uitvoeren van de [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) en [zoeken Script](https://go.microsoft.com/fwlink/?LinkId=822322) cmdlets, afhankelijk van het itemtype met `-Repository PSGallery`.

Filteren van resultaten uit de galerie kan worden gedaan met behulp van de volgende parameters van [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) en [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)

- Naam
- AllVersions
- MinimumVersion
- RequiredVersion
- Label
- Bevat
- DscResource
- RoleCapability
- Opdracht
- Filter

U kunt uitvoeren als u alleen geïnteresseerd bent in het detecteren van specifieke DSC-resources in de galerie, de [zoeken DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) cmdlet.
[Zoeken naar DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) retourneert gegevens van de DSC-resources die zijn opgenomen in de galerie. Omdat de DSC-resources zijn altijd geleverd als onderdeel van een module, moet u nog steeds uitgevoerd [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) voor het installeren van de DSC-resources.

## <a name="learning-about-items-in-the-powershell-gallery"></a>Meer informatie over de items in de PowerShell-galerie

Zodra u een item dat u geïnteresseerd bent in hebt geïdentificeerd, kunt u meer informatie over het. U kunt dit doen door te controleren dat item specifieke pagina in de galerie. Klik op deze pagina kunt u zult kunnen zien alle van de metagegevens geüpload met het item. Deze metagegevens voor een item wordt aangeboden door de auteur van het item en is niet geverifieerd door Microsoft. De eigenaar van het item ten zeerste aan het galerie-account gebruikt voor het publiceren van het item is gekoppeld en is betrouwbaarder dan het veld Auteur.

Als u ontdekt dat een item dat u van mening bent dat niet is gepubliceerd te goeder trouw, klikt u op **misbruik melden** op de pagina van het artikel.

Als u werkt met [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) of [zoeken Script](https://go.microsoft.com/fwlink/?LinkId=822322), u kunt deze gegevens weergeven in de geretourneerde PSGetModuleInfo-object.
Bijvoorbeeld, `Find-Module -Name PSReadLine -Repository PSGallery | Get-Member` retourneert gegevens voor de module PSReadLine in de galerie.

## <a name="downloading-items-from-the-powershell-gallery"></a>Downloaden van items van de PowerShell Gallery

Bij het downloaden van items van de PowerShell Gallery raden we het volgende proces:

### <a name="inspect"></a>Controleren

Voor het downloaden van een item uit de galerie voor inspectie, voer de [opslaan-Module](https://go.microsoft.com/fwlink/?LinkId=821669) of [opslaan Script](https://go.microsoft.com/fwlink/?LinkId=822334) cmdlet, afhankelijk van het itemtype. Hiermee kunt u het item lokaal opslaan zonder het te installeren en de inhoud van het item controleren. Onthoud het opgeslagen item handmatig verwijderen.

Sommige van deze items zijn gemaakt door Microsoft en anderen zijn ontworpen door de PowerShell-community. Microsoft raadt aan dat u de inhoud en code van de items in deze galerie voorafgaand aan installatie bekijken.

Als u ontdekt dat een item dat u van mening bent dat niet is gepubliceerd te goeder trouw, klikt u op **misbruik melden** op de pagina van het artikel.

### <a name="install"></a>Installeren

Uitvoeren als u wilt installeren een item uit de galerie voor gebruik, de [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) of [Script voor installatie](https://go.microsoft.com/fwlink/?LinkId=822327) cmdlet, afhankelijk van het itemtype.

[Installatie-Module](https://go.microsoft.com/fwlink/?LinkId=821663) installeert u de module `$env:ProgramFiles\WindowsPowerShell\Modules` standaard. Hiervoor moet een administrator-account. Als u de `-Scope
CurrentUser` parameter, de module is geïnstalleerd op `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Script voor installatie](https://go.microsoft.com/fwlink/?LinkId=822327) installeert u het script `$env:ProgramFiles\WindowsPowerShell\Scripts` standaard. Hiervoor moet een administrator-account. Als u de `-Scope
CurrentUser` parameter, het script wordt geïnstalleerd op `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Standaard [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) en [Script voor installatie](https://go.microsoft.com/fwlink/?LinkId=822327) installeert de meest recente versie van een item. Voor het installeren van een oudere versie van het item toevoegen de `-RequiredVersion` parameter.

### <a name="deploy"></a>Implementeer

Voor het implementeren van een item uit de galerie PowerShell voor Azure Automation, klikt u op **implementeren in Azure Automation** op de detailpagina item. U wordt omgeleid naar de Azure-beheerportal, waar u zich aanmelden met behulp van de referenties van uw Azure-account. Houd er rekening mee dat het implementeren van items met afhankelijkheden alle afhankelijkheden voor Azure Automation inzetten. De knop 'Implementeren in Azure Automation' kan worden uitgeschakeld door het toevoegen van de **AzureAutomationNotSupported** label in de itemmetagegevens van uw.

Zie voor meer informatie over Azure Automation, de [Azure Automation-website](http://azure.microsoft.com/en-us/services/automation/).

## <a name="updating-items-from-the-powershell-gallery"></a>Bijwerken van de items van de PowerShell Gallery

Voor het bijwerken van items die zijn geïnstalleerd vanuit de PowerShell-galerie, voer de [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) of [-updatescript](http://go.microsoft.com/fwlink/?LinkId=619787) cmdlet. Wanneer uitgevoerd zonder extra parameters, [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) probeert bij te werken van elke module die is geïnstalleerd door het uitvoeren van [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663).
Om bij te werken selectief modules, voeg de `-Name` parameter.

Op dezelfde manier als uitvoert zonder extra parameters, [-updatescript](http://go.microsoft.com/fwlink/?LinkId=619787) ook probeert om te werken van elk geïnstalleerd door het uitvoeren van script [Script voor installatie](https://go.microsoft.com/fwlink/?LinkId=822327).
Voor het selectief bijwerken scripts, voeg de `-Name` parameter.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Lijst met items die u hebt geïnstalleerd vanuit de PowerShell-galerie

Als u wilt weten welke modules die u hebt geïnstalleerd vanuit de PowerShell-galerie, voer de [Get-InstalledModule](https://go.microsoft.com/fwlink/?LinkId=526863) cmdlet. Met deze opdracht worden alle van de modules die op uw systeem is geïnstalleerd en die rechtstreeks vanuit de PowerShell-galerie zijn geïnstalleerd.

Op dezelfde manier als u wilt weten welke scripts die u hebt geïnstalleerd vanuit de PowerShell-galerie, voer de [Get-InstalledScript](https://go.microsoft.com/fwlink/?LinkId=619790) cmdlet. Met deze opdracht worden alle van de scripts die op uw systeem is geïnstalleerd en die rechtstreeks van de PowerShell Gallery zijn geïnstalleerd.

