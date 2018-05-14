---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: psgallery_gettingstarted
ms.openlocfilehash: c3aafe9e76eda9acdd4787f63dc0f8c71a20d02a
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/10/2018
---
# <a name="get-started-with-the-powershell-gallery"></a>Aan de slag met de PowerShell-galerie

Downloaden van items uit de PowerShell-galerie in uw systeem vereist de [PowerShellGet](/powershell/module/powershellget) module. U kunt de module PowerShellGet vinden in het volgende. U hoeft niet aan te melden bij het downloaden van items uit de PowerShell-galerie.

## <a name="discovering-items-from-the-powershell-gallery"></a>Detectie van items van de PowerShell Gallery

U kunt items in de PowerShell-galerie vinden met behulp van de **Search** besturingselement op deze website, of door te bladeren door de pagina's Modules en -Scripts. U kunt items van de PowerShell Gallery ook vinden door het uitvoeren van de [Find-Module][] en [zoeken Script][] cmdlets, afhankelijk van het itemtype met `-Repository PSGallery`.

Filteren van resultaten uit de galerie kan worden gedaan met behulp van de volgende parameters:

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

U kunt uitvoeren als u alleen geïnteresseerd bent in het detecteren van specifieke DSC-resources in de galerie, de [zoeken DscResource] cmdlet. Zoeken naar DscResource retourneert gegevens van DSC-resources die zijn opgenomen in de galerie.
Omdat de DSC-resources zijn altijd geleverd als onderdeel van een module, moet u nog steeds uitgevoerd [Install-Module][] voor het installeren van de DSC-resources.

## <a name="learning-about-items-in-the-powershell-gallery"></a>Meer informatie over de items in de PowerShell-galerie

Zodra u een item dat u geïnteresseerd bent in hebt geïdentificeerd, kunt u meer informatie over het. U kunt dit doen door te controleren dat item specifieke pagina in de galerie. Klik op deze pagina kunt u zult kunnen zien alle van de metagegevens geüpload met het item. Deze metagegevens voor een item wordt aangeboden door de auteur van het item en is niet geverifieerd door Microsoft. De eigenaar van het item ten zeerste aan het galerie-account gebruikt voor het publiceren van het item is gekoppeld en is betrouwbaarder dan het veld Auteur.

Als u ontdekt dat een item dat u van mening bent dat niet is gepubliceerd te goeder trouw, klikt u op **misbruik melden** op de pagina van het artikel.

Als u werkt met [Find-Module][] of [zoeken Script][], u kunt deze gegevens weergeven in de geretourneerde PSGetModuleInfo-object. Bijvoorbeeld, `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` retourneert gegevens voor de module PSReadLine in de galerie.

## <a name="downloading-items-from-the-powershell-gallery"></a>Downloaden van items van de PowerShell Gallery

Bij het downloaden van items van de PowerShell Gallery raden we het volgende proces:

### <a name="inspect"></a>Controleren

Voor het downloaden van een item uit de galerie voor inspectie, voer de [opslaan-Module][] of [opslaan Script][] cmdlet, afhankelijk van het itemtype. Hiermee kunt u het item lokaal opslaan zonder het te installeren en de inhoud van het item controleren. Onthoud het opgeslagen item handmatig verwijderen.

Sommige van deze items zijn gemaakt door Microsoft en anderen zijn ontworpen door de PowerShell-community.
Microsoft raadt aan dat u de inhoud en code van de items in deze galerie voorafgaand aan installatie bekijken.

Als u ontdekt dat een item dat u van mening bent dat niet is gepubliceerd te goeder trouw, klikt u op **misbruik melden** op de pagina van het artikel.

### <a name="install"></a>Installeren

Uitvoeren als u wilt installeren een item uit de galerie voor gebruik, de [Install-Module][] of [Script voor installatie][] cmdlet, afhankelijk van het itemtype.

[Install-Module][] installeert u de module `$env:ProgramFiles\WindowsPowerShell\Modules` standaard.
Hiervoor moet een administrator-account. Als u de `-Scope CurrentUser` parameter, de module is geïnstalleerd op `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Script voor installatie][] installeert u het script `$env:ProgramFiles\WindowsPowerShell\Scripts` standaard.
Hiervoor moet een administrator-account. Als u de `-Scope CurrentUser` parameter, het script wordt geïnstalleerd op `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Standaard [Install-Module][] en [Script voor installatie][] installeert de meest recente versie van een item.
Voor het installeren van een oudere versie van het item toevoegen de `-RequiredVersion` parameter.

### <a name="deploy"></a>Implementeer

Voor het implementeren van een item uit de galerie PowerShell voor Azure Automation, klikt u op **implementeren in Azure Automation** op de detailpagina item. U wordt omgeleid naar de Azure-beheerportal, waar u zich aanmelden met behulp van de referenties van uw Azure-account. Houd er rekening mee dat het implementeren van items met afhankelijkheden alle afhankelijkheden voor Azure Automation inzetten. De knop 'Implementeren in Azure Automation' kan worden uitgeschakeld door het toevoegen van de **AzureAutomationNotSupported** label in de itemmetagegevens van uw.

Zie voor meer informatie over Azure Automation, de [Azure Automation](/azure/automation) documentatie.

## <a name="updating-items-from-the-powershell-gallery"></a>Bijwerken van de items van de PowerShell Gallery

Om bij te werken items geïnstalleerd vanuit de PowerShell-galerie, voer de [Update-Module] [] of [updatescript] [] cmdlet. Wanneer uitvoert zonder extra parameters, [] [Update-Module] probeert bij te werken van elke module die is geïnstalleerd door het uitvoeren van [Install-Module][]. Om bij te werken selectief modules, voeg de `-Name` parameter.

Op dezelfde manier als uitvoert zonder extra parameters, [] [updatescript] ook probeert om te werken elk geïnstalleerd door het uitvoeren van script [Script voor installatie][]. Voor het selectief bijwerken scripts, voeg de `-Name` parameter.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Lijst met items die u hebt geïnstalleerd vanuit de PowerShell-galerie

Als u wilt weten welke modules die u hebt geïnstalleerd vanuit de PowerShell-galerie, voer de [Get-InstalledModule][] cmdlet. Met deze opdracht worden alle van de modules die op uw systeem is geïnstalleerd en die rechtstreeks vanuit de PowerShell-galerie zijn geïnstalleerd.

Op dezelfde manier als u wilt weten welke scripts die u hebt geïnstalleerd vanuit de PowerShell-galerie, voer de [Get-InstalledScript][] cmdlet. Met deze opdracht worden alle van de scripts die op uw systeem is geïnstalleerd en die rechtstreeks van de PowerShell Gallery zijn geïnstalleerd.

[zoeken DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[zoeken Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Script voor installatie]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[opslaan-Module]: /powershell/module/powershellget/Save-Module
[opslaan Script]: /powershell/module/powershellget/Save-Script