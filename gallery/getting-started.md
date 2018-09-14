---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Aan de slag met de PowerShell Gallery
ms.openlocfilehash: 39998df1a2bf9363dd008dc96a802157c8d691d7
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523028"
---
# <a name="get-started-with-the-powershell-gallery"></a>Aan de slag met de PowerShell Gallery

De juiste manier voor het installeren van items vanuit de PowerShell Gallery is met de cmdlets in de [PowerShellGet](/powershell/module/powershellget) module. U hoeft zich niet aanmelden bij het downloaden van items vanuit de PowerShell Gallery.

> [!NOTE]
> Het is mogelijk een pakket rechtstreeks downloaden vanuit de PowerShell Gallery, maar dit is niet een aanbevolen aanpak. Zie voor meer informatie, [handmatig pakket downloaden](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).  


## <a name="discovering-items-from-the-powershell-gallery"></a>Detectie van items uit de PowerShell Gallery

U kunt items in de PowerShell Gallery zoeken met behulp van de **zoeken** besturingselement op deze website, of door te bladeren door de pagina's Modules en -Scripts. U kunt ook items uit de PowerShell Gallery vinden door te voeren de [Find-Module][] en [Find-Script][] cmdlets, afhankelijk van het itemtype met `-Repository PSGallery`.

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

## <a name="learning-about-items-in-the-powershell-gallery"></a>Meer informatie over de items in de PowerShell-galerie

Wanneer u een item dat u geïnteresseerd bent in hebt geïdentificeerd, kunt u meer informatie over deze. U kunt dit doen door te controleren van specifieke pagina in de galerie van het artikel. Op deze pagina kunt u zult kunnen zien van alle van de metagegevens van het item zijn geüpload. Deze metagegevens voor een item wordt geleverd door de auteur van het item en wordt niet gecontroleerd door Microsoft. De eigenaar van het item is nauw verbonden met het galerie-account gebruikt voor het publiceren van het item en is betrouwbaarder dan het veld ' auteur '.

Als u ontdekt een item dat u denkt dat niet is gepubliceerd in goed vertrouwen, klikt u op **misbruik** op de pagina van het artikel.

Als u werkt met [Find-Module][] of [Find-Script][], u kunt deze gegevens weergeven in de geretourneerde PSGetModuleInfo-object. Bijvoorbeeld uitgevoerd `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
retourneert de gegevens op de module PSReadLine in de galerie.

## <a name="downloading-items-from-the-powershell-gallery"></a>Downloaden van items uit de PowerShell Gallery

We raden het volgende proces wanneer het downloaden van items uit de galerie met PowerShell:

### <a name="inspect"></a>Controleren

Voor het downloaden van een item uit de galerie voor inspectie, voer een de [Save-Module][] of [Save-Script][] cmdlet, afhankelijk van het itemtype. Hiermee kunt u het item lokaal opslaan zonder dat deze wordt geïnstalleerd, en de inhoud van het item controleren. Vergeet niet om het opgeslagen item handmatig verwijderen.

Sommige van deze items zijn gemaakt door Microsoft en anderen worden geschreven door de PowerShell-community.
Microsoft raadt aan dat u de inhoud en code van items in deze galerie voorafgaand aan installatie controleren.

Als u ontdekt een item dat u denkt dat niet is gepubliceerd in goed vertrouwen, klikt u op **misbruik** op de pagina van het artikel.

### <a name="install"></a>Installeren

Voor het installeren van een item uit de galerie voor gebruik, voer een de [Install-Module][] of [Script voor installatie][] cmdlet, afhankelijk van het itemtype.

[Install-Module][] installeert van de module `$env:ProgramFiles\WindowsPowerShell\Modules` standaard.
Hiervoor moet een administrator-account. Als u de `-Scope CurrentUser` parameter, de module is geïnstalleerd op `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Script voor installatie][] wordt geïnstalleerd met het script `$env:ProgramFiles\WindowsPowerShell\Scripts` standaard.
Hiervoor moet een administrator-account. Als u de `-Scope CurrentUser` parameter, het script is geïnstalleerd op `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Standaard [Install-Module][] en [Script voor installatie][] installeert de meest recente versie van een item.
Toevoegen voor het installeren van een oudere versie van het item, de `-RequiredVersion` parameter.

### <a name="deploy"></a>Implementeer

Voor het implementeren van een item uit de galerie met PowerShell voor Azure Automation, klikt u op **implementeren in Azure Automation** op de pagina met details van item. U wordt omgeleid naar de Azure-beheerportal, waar u zich aanmelden met behulp van de referenties van uw Azure-account. Houd er rekening mee dat items met afhankelijkheden implementeren alle afhankelijkheden voor Azure Automation implementeert. De knop 'Implementeren voor Azure Automation' kan worden uitgeschakeld door toe te voegen de **AzureAutomationNotSupported** tag in de itemmetagegevens van het.

Zie voor meer informatie over Azure Automation, de [Azure Automation](/azure/automation) documentatie.

## <a name="updating-items-from-the-powershell-gallery"></a>Bijwerken van items uit de PowerShell Gallery

Om bij te werken items hebt geïnstalleerd vanuit PowerShell Gallery, voer de [Update-Module] [] of [updatescript] []-cmdlet. Wanneer uitvoert zonder extra parameters, [] [-Update-Module] probeert bij te werken van elke module geïnstalleerd door te voeren [Install-Module][]. Als u wilt bijwerken selectief modules, toevoegen de `-Name` parameter.

Op dezelfde manier als uitvoert zonder eventuele extra parameters, [updatescript] [] ook probeert om bij te werken van elk script dat is geïnstalleerd door te voeren [Script voor installatie][]. Als u selectief-bijwerken scripts, wilt toevoegen de `-Name` parameter.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Lijst met items die u hebt geïnstalleerd vanuit de PowerShell Gallery

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