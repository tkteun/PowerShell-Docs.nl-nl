---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Aan de slag met de PowerShell Gallery
ms.openlocfilehash: 85b0a754aba25d850dc918024419318554f92b33
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225672"
---
# <a name="getting-started-with-the-powershell-gallery"></a>Aan de slag met de PowerShell Gallery

De juiste manier om pakketten te installeren vanuit de PowerShell Gallery is met de cmdlets in de [PowerShellGet](/powershell/module/powershellget) module. U hoeft zich niet aanmelden bij het downloaden van items vanuit de PowerShell Gallery.

> [!NOTE]
> Het is mogelijk een pakket rechtstreeks downloaden vanuit de PowerShell Gallery, maar dit is niet een aanbevolen aanpak.
> Zie voor meer informatie, [handmatig pakket downloaden](/powershell/gallery/how-to/working-with-packages/manual-download).

## <a name="discovering-packages-from-the-powershell-gallery"></a>Detectie van pakketten van de PowerShell Gallery

U kunt pakketten in de PowerShell Gallery vinden met behulp van de **zoeken** besturingselement op deze website, of door te bladeren door de pagina's Modules en -Scripts. U kunt pakketten vanuit de PowerShell Gallery ook vinden door te voeren de [Find-Module][] en [Find-Script][] cmdlets, afhankelijk van het itemtype met `-Repository PSGallery`.

Resultaten van de galerie filteren kan worden gedaan met behulp van de volgende parameters:

- Naam
- AllVersions
- MinimumVersion
- RequiredVersion
- Label
- Bevat
- Sleutelwoorden voor dscresource bieden
- RoleCapability
- Opdracht
- Filter

Als u alleen geïnteresseerd in het detecteren van specifieke DSC-resources in de galerie bent, kunt u uitvoeren de [Zoeken naar sleutelwoorden-dscresource bieden] cmdlet. Zoeken naar sleutelwoorden-dscresource bieden retourneert gegevens van DSC-resources die zijn opgenomen in de galerie.
Omdat de DSC-resources worden altijd geleverd als onderdeel van een module, moet u nog steeds uitgevoerd [Install-Module][] voor het installeren van de DSC-resources.

## <a name="learning-about-packages-in-the-powershell-gallery"></a>Meer informatie over pakketten in de PowerShell Gallery

Wanneer u een pakket dat u geïnteresseerd bent in hebt geïdentificeerd, kunt u meer informatie over deze. U kunt dit doen door te controleren dat pakket van specifieke pagina in de galerie. Op deze pagina kunt u zult kunnen zien van alle van de metagegevens van het pakket zijn geüpload. Deze metagegevens wordt geleverd door de auteur van het pakket, en wordt niet gecontroleerd door Microsoft. De eigenaar van het pakket is nauw verbonden met het galerie-account gebruikt voor het publiceren van het pakket, en is betrouwbaarder dan het veld ' auteur '.

Als u ontdekt een pakket dat u denkt dat niet is gepubliceerd in goed vertrouwen, klikt u op **misbruik** op de pagina van het pakket.

Als u werkt met [Find-Module][] of [Find-Script][], u kunt deze gegevens weergeven in de geretourneerde PSGetModuleInfo-object. Bijvoorbeeld uitgevoerd `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
retourneert de gegevens op de module PSReadLine in de galerie.

## <a name="downloading-packages-from-the-powershell-gallery"></a>Downloaden van pakketten van de PowerShell Gallery

We raden het volgende proces bij het downloaden van pakketten van de PowerShell Gallery:

### <a name="inspect"></a>Controleren

Als u wilt downloaden uit de galerie voor inspectie, voer een de [Save-Module][] of [Save-Script][] cmdlet, afhankelijk van het pakkettype. Hiermee kunt u het pakket lokaal opslaan zonder dat deze wordt geïnstalleerd en de pakketinhoud controleren. Vergeet niet om de opgeslagen pakket handmatig verwijderen.

Sommige van deze pakketten zijn geschreven door Microsoft en anderen worden geschreven door de PowerShell-community.
Microsoft raadt aan dat u de inhoud en code van pakketten op deze galerie voorafgaand aan installatie controleren.

Als u ontdekt een pakket dat u denkt dat niet is gepubliceerd in goed vertrouwen, klikt u op **misbruik** op de pagina van het pakket.

### <a name="install"></a>Installeren

Voor het installeren van een pakket uit de galerie voor gebruik, voer een de [Install-Module][] of [Script voor installatie][] cmdlet, afhankelijk van het pakkettype.

[Install-Module][] installeert van de module `$env:ProgramFiles\WindowsPowerShell\Modules` standaard.
Hiervoor moet een administrator-account. Als u de `-Scope CurrentUser` parameter, de module is geïnstalleerd op `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Script voor installatie][] wordt geïnstalleerd met het script `$env:ProgramFiles\WindowsPowerShell\Scripts` standaard.
Hiervoor moet een administrator-account. Als u de `-Scope CurrentUser` parameter, het script is geïnstalleerd op `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Standaard [Install-Module][] en [Script voor installatie][] installeert de meest recente versie van een pakket.
Voor het installeren van een oudere versie van het pakket, voeg de `-RequiredVersion` parameter.

### <a name="deploy"></a>Implementeer

Voor het implementeren van een pakket vanuit de PowerShell Gallery voor Azure Automation, klikt u op **implementeren in Azure Automation** op de detailpagina van het pakket. U wordt omgeleid naar de Azure-beheerportal waar u zich aanmelden met behulp van de referenties van uw Azure-account. Houd er rekening mee dat voor het implementeren van pakketten met afhankelijkheden alle afhankelijkheden voor Azure Automation implementeren. De knop 'Implementeren voor Azure Automation' kan worden uitgeschakeld door toe te voegen de **AzureAutomationNotSupported** tag in de pakketmetagegevens van uw.

Zie voor meer informatie over Azure Automation, de [Azure Automation](/azure/automation) documentatie.

## <a name="updating-packages-from-the-powershell-gallery"></a>Pakketten vanuit de PowerShell Gallery worden bijgewerkt

Voer de [Update-Module] [] of [updatescript] [] cmdlet voor het bijwerken van pakketten geïnstalleerd vanuit de PowerShell Gallery. Wanneer uitvoert zonder extra parameters, [] [-Update-Module] probeert bij te werken van elke module geïnstalleerd door te voeren [Install-Module][]. Als u wilt bijwerken selectief modules, toevoegen de `-Name` parameter.

Op dezelfde manier als uitvoert zonder eventuele extra parameters, [updatescript] [] ook probeert om bij te werken van elk script dat is geïnstalleerd door te voeren [Script voor installatie][]. Als u selectief-bijwerken scripts, wilt toevoegen de `-Name` parameter.

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>Lijst met pakketten die u hebt geïnstalleerd vanuit de PowerShell Gallery

Als u wilt weten welke modules die u hebt geïnstalleerd vanuit de PowerShell Gallery, voer de [Get-InstalledModule][] cmdlet. Met deze opdracht worden alle modules op uw systeem is geïnstalleerd die zijn geïnstalleerd rechtstreeks vanuit de PowerShell Gallery.

Op dezelfde manier als u wilt weten welke scripts die u hebt geïnstalleerd vanuit de PowerShell Gallery, voer de [Get-InstalledScript][] cmdlet. Met deze opdracht worden alle van de scripts die u hebt op uw systeem en die rechtstreeks vanuit de PowerShell Gallery zijn geïnstalleerd.

[Zoeken naar sleutelwoorden-dscresource bieden]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Script voor installatie]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
