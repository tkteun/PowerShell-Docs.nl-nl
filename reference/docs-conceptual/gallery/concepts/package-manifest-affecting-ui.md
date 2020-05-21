---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Pakket manifest waarden die van invloed zijn op de PowerShell Gallery-gebruikers interface
ms.openlocfilehash: 460b1c67af0af81dd993a45c4f988b825dc2f3eb
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560420"
---
# <a name="package-manifest-values-that-impact-the-powershell-gallery-ui"></a>Pakket manifest waarden die van invloed zijn op de PowerShell Gallery-gebruikers interface

In dit onderwerp vindt u een overzicht van de informatie over het wijzigen van het manifest voor de PowerShell Gallery-publicaties zodat de functies van PowerShellGet-cmdlets en de PowerShell Gallery-gebruikers interface worden beïnvloed. Deze inhoud is ingedeeld op basis van waar de wijziging wordt weer gegeven, te beginnen met het middelste gedeelte en vervolgens het navigatie gebied aan de linkerkant. Er is een detail sectie met tags waarmee belang rijke Tags worden geïdentificeerd, evenals een aantal veelgebruikte tags. Er zijn twee onderwerpen die voor beelden van manifesten bieden:

- Zie voor modules het [module manifest bijwerken](/powershell/module/powershellget/Update-ModuleManifest)
- Zie [script bestand met meta gegevens maken](/powershell/module/powershellget/New-ScriptFileInfo) voor scripts

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>Onderdelen van PowerShell Gallery-onderdelen die worden beheerd door het manifest

In de volgende tabel ziet u de elementen van de gebruikers interface van de PowerShell Gallery-pakket pagina die worden beheerd door de uitgever. Elk item geeft aan of het kan worden beheerd door de module of het script manifest.

| UI-element | Beschrijving | Module | Script |
| --- | --- | --- | --- |
| **Titel** | Dit is de naam van het pakket dat naar de galerie wordt gepubliceerd  | Nee | Nee |
| **Versie** | De weer gegeven versie is de versie teken reeks in de meta gegevens en een prerelease als is opgegeven. Het primaire deel van de versie in een module manifest is het ModuleVersion. Voor een script wordt dit aangeduid als. Versie. Als er een teken reeks voor de voorlopige versie is opgegeven, wordt deze toegevoegd aan de ModuleVersion voor modules of opgegeven als onderdeel van. VERSIE voor scripts. Er is documentatie voor het opgeven van voorlopige teken reeksen in [modules](module-prerelease-support.md)en in [scripts](script-prerelease-support.md) | Ja | Ja |
| **Beschrijving** | Dit is de beschrijving in het module manifest en in een script bestand manifest. BESCHRIJVINGEN | Ja | Ja |
| **Acceptatie van de licentie vereisen** | Een module kan vereisen dat de gebruiker een licentie accepteert door het module manifest te wijzigen met RequireLicenseAcceptance = $true, een LicenseURI op te geven en een License. txt-bestand op te geven in de hoofdmap van de module map. Meer informatie is beschikbaar in het onderwerp een [acceptatie van licenties nodig](../how-to/working-with-packages/packages-that-require-license-acceptance.md) . | Ja | Nee |
| **Releaseopmerkingen** | Voor-modules wordt deze informatie opgehaald uit de sectie ReleaseNotes onder PSData\PrivateData. In script manifesten is dit de. RELEASENOTES-element. | Ja | Ja |
| **Eigenaren** | Eigen aren zijn de lijst met gebruikers in de PowerShell Gallery die een pakket kunnen bijwerken. De lijst met eigen aren is niet opgenomen in het pakket manifest. In aanvullende documentatie wordt beschreven hoe u [item eigenaren beheert](../how-to/publishing-packages/managing-package-owners.md). | Nee | Nee |
| **Auteur** | Dit is opgenomen in het module manifest als auteur en in een script manifest als. Lijsten. Het veld Auteur wordt vaak gebruikt om een bedrijf of organisatie op te geven dat is gekoppeld aan een pakket. | Ja | Ja |
| **Gegevens** | Dit is het copyright veld in het module manifest en. COPYRIGHT in een script manifest. | Ja | Ja |
| **File List** | De lijst met bestanden wordt uit het pakket gehaald wanneer het is gepubliceerd naar de PowerShell Gallery. Het kan niet worden bestuurd door de informatie in het manifest. Opmerking: er is een extra. nuspec-bestand dat wordt vermeld bij elk pakket in het PowerShell Gallery dat niet aanwezig is na installatie van het pakket op een systeem. Dit is het Nuget-pakket manifest voor het pakket en kan worden genegeerd. | Nee | Nee |
| **Tags** | Voor modules worden tags opgenomen onder PSData\PrivateData. Voor scripts is de sectie gelabeld. Koptags. Houd er rekening mee dat Tags geen spaties kunnen bevatten, zelfs als ze zich in een aanhalings teken bevinden. Labels hebben aanvullende vereisten en betekenissen, die verderop in dit onderwerp worden beschreven in de sectie Label Details. | Ja | Ja |
| **Cmdlets** | Dit wordt in het module manifest beschreven met behulp van CmdletsToExport. Houd er rekening mee dat de best practice expliciet de items moet vermelden, in plaats van het Joker teken ' * ' te gebruiken, omdat de prestaties van de load module voor gebruikers worden verbeterd. | Ja | Nee |
| **Functions** | Dit wordt in het module manifest beschreven met behulp van FunctionsToExport. Houd er rekening mee dat de best practice expliciet de items moet vermelden, in plaats van het Joker teken ' * ' te gebruiken, omdat de prestaties van de load module voor gebruikers worden verbeterd. | Ja | Nee |
| **DSC-resources** | Voor modules die worden gebruikt in Power shell-versie 5,0 en hoger, wordt dit in het manifest opgenomen met DscResourcesToExport. Als de module moet worden gebruikt in Power Shell 4, mag de DSCResourcesToExport niet worden gebruikt omdat deze geen ondersteunde manifest sleutel is. (DSC is niet beschikbaar vóór Power Shell 4.) | Ja | Nee |
| **Werkstromen** | Werk stromen worden gepubliceerd op de PowerShell Gallery als scripts en geïdentificeerd als werk stromen (Zie [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) voor een voor beeld) in de code. Dit wordt niet beheerd door het manifest. | Nee | Nee |
| **Functie mogelijkheden** | Dit wordt weer gegeven wanneer de module die naar het PowerShell Gallery is gepubliceerd, een of meer functie-psrc-bestanden bevat die door JEA worden gebruikt. Raadpleeg de JEA-documentatie voor meer informatie over [functie mogelijkheden](/powershell/scripting/learn/remoting/jea/role-capabilities). | Ja | Nee |
| **PowerShell-edities** | Dit is opgegeven in een script of module manifest. Voor modules die zijn ontworpen voor gebruik met Power shell 5,0 en lager, wordt dit bepaald met behulp van tags. Gebruik voor bureau blad het label PSEdition_Desktop en gebruik voor kernen de tag PSEdition_Core. Voor modules die alleen worden gebruikt in Power shell 5,1 en hoger, is er een CompatiblePSEditions-sleutel in het hoofd manifest. Raadpleeg de functie van de PS-editie in [de Power shell-documentatie ophalen](module-psedition-support.md)voor meer informatie. | Ja | Ja |
| **Afhankelijkheden** | Afhankelijkheden zijn de modules in de PowerShell Gallery die zijn gedeclareerd in de module als RequiredModules of in het script manifest als #Requires – module (naam). | Ja | Ja |
| **Minimale Power shell-versie** | Dit kan in een module manifest worden opgegeven als PowerShellVersion | Ja | Nee |
| **Versie geschiedenis** | De versie geschiedenis weerspiegelt de updates die zijn aangebracht in een module in de PowerShell Gallery. Als een versie van een pakket verborgen is met behulp van de functie verwijderen, wordt het niet weer gegeven in de versie geschiedenis, behalve de eigen aren van het pakket. | Nee | Nee |
| **Project site** | De project site wordt opgegeven voor modules in de sectie Privatedata\PSData van het module manifest door een ProjectURI op te geven. In het script manifest wordt gecontroleerd door het opgeven van. PROJECTURI. | Ja | Ja |
| **Licentie** | Er wordt een licentie koppeling voor modules opgegeven in de sectie Privatedata\PSData van het module manifest door een LicenseURI op te geven. In het script manifest wordt gecontroleerd door het opgeven van. LICENSEURI. Het is belang rijk om te weten dat als er geen licentie wordt opgegeven via de LicenseURI of binnen een module, de gebruiks voorwaarden voor het pakket worden opgegeven voor de PowerShell Gallery. Zie de gebruiks voorwaarden voor meer informatie. | Ja | Ja |
| **Pictogram** | Er kan een pictogram worden opgegeven voor elk pakket in de PowerShell Gallery door de vlag IconURI in het script manifest op te geven of in de sectie Privatedata-PSData van het module manifest. De IconURI moet verwijzen naar een afbeelding van 32x32 met transparantie achtergrond. De URI **moet** een directe afbeeldings-URL zijn en **mag niet** naar een webpagina met de installatie kopie of een bestand in het PowerShell Gallery-pakket gaan. | Ja | Ja |

## <a name="editing-package-details"></a>Pakket Details bewerken

Op de pagina pakket bewerken PowerShell Gallery kunnen uitgevers verschillende velden wijzigen die worden weer gegeven voor een pakket, met name:

- Titel
- Beschrijving
- Samenvatting
- Pictogram-URL
- URL van de start pagina van project
- Auteurs
- Copyright
- Tags
- Releaseopmerkingen
- Licentie vereisen

Deze methode wordt niet doorgaans aanbevolen, behalve wanneer dit nodig is om te corrigeren wat wordt weer gegeven voor een oudere versie van een module. Gebruikers die de module hebben verkregen, zien dat de meta gegevens niet overeenkomen met wat er wordt weer gegeven in de PowerShell Gallery, wat het probleem met het pakket veroorzaakt. Dit leidt vaak tot het controleren van de wijziging met betrekking tot de eigen aren van het pakket. Het is raadzaam dat elke keer dat deze methode wordt gebruikt, een nieuwe versie van het pakket met dezelfde wijzigingen moet worden gepubliceerd.

## <a name="tag-details"></a>Label Details

Tags zijn eenvoudige teken reeksen die consumenten gebruiken om pakketten te vinden. Labels zijn het handigst wanneer ze consistent worden gebruikt in veel pakketten die betrekking hebben op hetzelfde onderwerp. Het gebruik van meerdere versies van hetzelfde woord (bijvoorbeeld data bases en data bases, of testen en testen) biedt doorgaans weinig voor delen. Tags zijn niet-hoofdletter gevoelige teken reeksen en kunnen geen lege waarden bevatten. Als er een woord groep is die u vermoedt dat gebruikers worden gezocht, voegt u deze toe aan de pakket beschrijving en wordt het gevonden in de zoek resultaten. Gebruik Pascal-behuizing, afbreek streepjes, onderstrepings tekens of punten als u de Lees baarheid wilt verbeteren.
Wees voorzichtig met het maken van lange, complexe en ongebruikelijke Tags, omdat deze vaak foutief zijn gespeld.

Er zijn tags die belang rijk zijn om te noteren, omdat de cmdlets PowerShell Gallery en PowerShellGet deze uniek behandelen. PSEdition_Desktop en PSEdition_Core zijn de specifieke voor beelden en worden hierboven beschreven.

Zoals hierboven vermeld, bieden Tags de hoogste waarde wanneer ze specifiek zijn en worden ze consistent gebruikt in veel pakketten. Als een uitgever probeert de beste Tags te vinden die moeten worden gebruikt, is de eenvoudigste manier om de PowerShell Gallery te doorzoeken op Tags die u overweegt. In het ideale geval worden er veel pakketten geretourneerd en worden de pakket beschrijvingen uitgelijnd met uw gebruik van die sleutel woord.

Ter referentie zijn hier enkele meestgebruikte Tags vanaf 12/14/2017. In sommige gevallen zijn er vergelijk bare, maar mogelijk minder ideale opties naast het label. Het is een best practice om de voorkeurs code te gebruiken, wat leidt tot minder ruis en betere Zoek resultaten voor gebruikers.

| Voorkeurs label | Alternatieven en opmerkingen |
| --- | --- |
| Azure |  |
| DSC | DesiredStateConfiguration is minder wenselijk, het is te lang |
| ResourceManager | ARM wordt gebruikt voor het beschrijven van een groep processors en mag niet worden gebruikt voor Azure Resource Manager |
| DSCResourceKit |  |
| SQL |  |
| AWS |  |
| DSCResource |  |
| Automation |  |
| REST |  |
| Active Directory | AD wordt momenteel niet door zichzelf gebruikt  |
| Server |  |
| DBA |  |
| Beveiliging | Verdediging is minder nauw keurig |
| Database | Data bases (plural) zijn minder wenselijk |
| DevOps |  |
| Windows |  |
| Ontwikkelen |  |
| Implementatie | Implementeren wordt iets minder vaak gebruikt |
| Cloud |  |
| GIT |  |
| Testen | Testen is minder wenselijk |
| Sioncontrol | De versie is minder nauw keurig, maar wordt vaker gebruikt  |
| Logboekregistratie | Voorkeurs gebruik van logboek registratie als een actie |
| Logboek | Gebruik van logboek als voor keur |
| Backup |  |
| IaaS |  |
| Linux |  |
| IIS |  |
| AzureAutomation |  |
| Storage |  |
| GitHub |  |
| Json |  |
| Exchange |  |
| Netwerk | Netwerken zijn vergelijkbaar, minder vaak gebruikt |
| SharePoint |  |
| Rapportage | Rapportage is een actie, een ding van het rapport |
| Rapport | Het rapport is een ding |
| WinRM |  |
| Bewaking |  |
| VSTS |  |
| Excel |  |
| Google |  |
| Kleur |  |
| DNS |  |
| Office365 | Office heeft de voor keur. O365 wordt minder vaak gebruikt, maar kortere |
| Gitlab |  |
| Pester |  |
| AzureAD |  |
| HTML |  |
| Hyper-V | Hyper-v is minder gangbaar dan een tag |
| Configuratie |  |
| ChatOps |  |
| PackageManagement |  |
| WMI |  |
| Firewall |  |
| Docker |  |
| Appveyor |  |
| AzureRm | Wordt hoofd zakelijk gebruikt voor de AzureRM-modules |
| Zip |  |
| MSI |  |
| MacOS |  |
| PoshBot |  |
