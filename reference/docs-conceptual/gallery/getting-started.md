---
ms.date: 06/12/2017
title: Aan de slag met de PowerShell Gallery
description: In dit artikel wordt uitgelegd hoe u aan de slag gaat met de PowerShell Gallery-en de PowerShellGet-cmdlets
ms.openlocfilehash: 02d84c64e39245b2a16c03029982796a74301bd6
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661414"
---
# <a name="getting-started-with-the-powershell-gallery"></a>Aan de slag met de PowerShell Gallery

De PowerShell Gallery is een pakket opslagplaats met scripts, modules en DSC-resources die u kunt downloaden en gebruiken. U kunt de-cmdlets in de [PowerShellGet](/powershell/module/powershellget) -module gebruiken om pakketten van de PowerShell Gallery te installeren. U hoeft zich niet aan te melden om items van de PowerShell Gallery te downloaden.

> [!NOTE]
> Het is mogelijk om een pakket rechtstreeks van de PowerShell Gallery te downloaden, maar dit is geen aanbevolen benadering. Zie [hand matig pakket downloaden](how-to/working-with-packages/manual-download.md)voor meer informatie.

## <a name="discovering-packages-from-the-powershell-gallery"></a>Pakketten detecteren van de PowerShell Gallery

U kunt pakketten vinden in de PowerShell Gallery met behulp van het besturings element **zoeken** op de [Start pagina](https://www.powershellgallery.com)van de PowerShell Gallery of door de modules en scripts te bladeren op de [pagina pakketten](https://www.powershellgallery.com/packages). U kunt ook pakketten van de PowerShell Gallery vinden door de cmdlets [zoeken-module][], [zoeken-dscresource bieden]en [Zoeken-script][] uit te voeren, afhankelijk van het type pakket, met `-Repository PSGallery` .

U kunt de resultaten van de galerie filteren met behulp van de volgende para meters:

- Naam
- AllVersions
- MinimumVersion
- RequiredVersion
- Label
- Includes
- Dscresource bieden
- RoleCapability
- Opdracht
- Filteren

Als u alleen geïnteresseerd bent in het detecteren van specifieke DSC-resources in de galerie, kunt u de cmdlet [Find-dscresource bieden][] uitvoeren. Find-DscResource retourneert gegevens over DSC-resources die zijn opgenomen in de galerie. Omdat DSC-resources altijd worden geleverd als onderdeel van een module, moet u nog steeds [install-module][] uitvoeren om die DSC-resources te installeren.

## <a name="learning-about-packages-in-the-powershell-gallery"></a>Meer informatie over pakketten in de PowerShell Gallery

Zodra u een pakket hebt geïdentificeerd waarin u bent geïnteresseerd, kunt u meer informatie hierover vinden. U kunt dit doen door te controleren of de specifieke pagina van het pakket in de galerie. Op deze pagina ziet u alle meta gegevens die zijn geüpload met het pakket. Deze meta gegevens worden gegeven door de auteur van het pakket en worden niet geverifieerd door micro soft. De eigenaar van het pakket is zeer gebonden aan het galerij-account dat wordt gebruikt voor het publiceren van het pakket en is betrouwbaarder dan het veld Auteur.

Als u een pakket detecteert waarvan u denkt dat het niet goed trouw is gepubliceerd, klikt u op **misbruik melden** op de pagina van het pakket.

Als u [Zoek-module][] of [Zoeken-script][]uitvoert, kunt u deze gegevens weer geven in het geretourneerde PSGetModuleInfo-object. Als u bijvoorbeeld uitvoert, worden `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` gegevens in de PSReadLine-module in de galerie geretourneerd.

## <a name="downloading-packages-from-the-powershell-gallery"></a>Pakketten downloaden van de PowerShell Gallery

We raden het volgende proces aan bij het downloaden van pakketten van de PowerShell Gallery:

### <a name="inspect"></a>Inspecteren

Als u een pakket wilt downloaden uit de galerie voor inspectie, voert u de cmdlet [Save-module][] of [Save-script][] uit, afhankelijk van het type pakket. Zo kunt u het pakket lokaal opslaan zonder het te installeren en de inhoud van het pakket controleren. Vergeet niet om het opgeslagen pakket hand matig te verwijderen.

Sommige van deze pakketten zijn gemaakt door micro soft en andere zijn gemaakt door de Power shell-community. Micro soft raadt u aan de inhoud en code van pakketten in deze galerie te controleren voordat u de installatie gaat installeren.

Als u een pakket detecteert waarvan u denkt dat het niet goed trouw is gepubliceerd, klikt u op **misbruik melden** op de pagina van het pakket.

### <a name="install"></a>Installeren

Als u een pakket wilt installeren uit de galerie, voert u de [installatie-module][] of de cmdlet [install-script][] uit, afhankelijk van het type pakket.

[Install-module][] installeert standaard de module `$env:ProgramFiles\WindowsPowerShell\Modules` .
Hiervoor is een beheerders account vereist. Als u de `-Scope CurrentUser` para meter toevoegt, wordt de module geïnstalleerd in `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

Met [install-script][] wordt het script `$env:ProgramFiles\WindowsPowerShell\Scripts` standaard geïnstalleerd.
Hiervoor is een beheerders account vereist. Als u de `-Scope CurrentUser` para meter toevoegt, wordt het script geïnstalleerd in `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Standaard installeert [install-module][] en [install-script][] de meest recente versie van een pakket. Als u een oudere versie van het pakket wilt installeren, voegt u de `-RequiredVersion` para meter toe.

### <a name="deploy"></a>Implementeren

Als u een pakket wilt implementeren vanuit het PowerShell Gallery naar Azure Automation, klikt u op **Azure Automation** en klikt u vervolgens op **implementeren in azure Automation** op de pagina pakket Details. U wordt omgeleid naar de Azure-Beheerportal waar u zich aanmeldt met behulp van de referenties van uw Azure-account. Houd er rekening mee dat het implementeren van pakketten met afhankelijkheden alle afhankelijkheden van Azure Automation implementeert. De knop implementeren naar Azure Automation kan worden uitgeschakeld door het label **AzureAutomationNotSupported** toe te voegen aan de meta gegevens van uw pakket.

Raadpleeg de [Azure Automation](/azure/automation) -documentatie voor meer informatie over Azure Automation.

## <a name="updating-packages-from-the-powershell-gallery"></a>De pakketten van de PowerShell Gallery worden bijgewerkt

Als u pakketten wilt bijwerken die zijn geïnstalleerd vanaf de PowerShell Gallery, voert u de cmdlet [Update-module][] of [update-script][] uit. Wanneer u zonder aanvullende para meters uitvoert, probeert [Update module][] alle modules bij te werken die zijn geïnstalleerd door de [installatie-module][]uit te voeren. Als u de modules selectief wilt bijwerken, voegt u de `-Name` para meter toe.

Op dezelfde manier wordt bij het uitvoeren van een [update script][] ook geprobeerd alle scripts die zijn geïnstalleerd door het [installatie script][]uit te voeren, wanneer u uitvoert zonder aanvullende para meters. Als u scripts selectief wilt bijwerken, voegt u de `-Name` para meter toe.

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>Pakketten weer geven die u hebt geïnstalleerd via de PowerShell Gallery

Voer de cmdlet [Get-InstalledModule][] uit om erachter te komen welke modules zijn geïnstalleerd op de PowerShell Gallery. Met deze opdracht worden alle modules op uw systeem weer gegeven die rechtstreeks van de PowerShell Gallery zijn geïnstalleerd.

Voer de cmdlet [Get-InstalledScript][] uit om erachter te komen welke scripts zijn geïnstalleerd op de PowerShell Gallery. Met deze opdracht worden alle scripts die u op uw systeem hebt geïnstalleerd, rechtstreeks vanuit de PowerShell Gallery weer gegeven.

## <a name="network-access-to-the-powershell-gallery"></a>Netwerk toegang tot de PowerShell Gallery

De PowerShell Gallery gebruikt de volgende hostnamen.

- `psg-prod-eastus.azureedge.net` -de CDN-hostnaam
- `devopsgallerystorage.blob.core.windows.net` -de hostnaam van het opslag account
- `*.powershellgallery.com` -de website

Deze hostnamen moeten worden toegevoegd aan de lijst toestaan waarmee de toegang vanuit uw netwerk wordt beheerd.

[Zoeken-Dscresource bieden]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Zoeken-script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Installatie-module]: /powershell/module/powershellget/Install-Module
[Install-script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
[Update-Module]: /powershell/module/powershellget/Update-Module
[Update-script]: /powershell/module/powershellget/Update-Script
