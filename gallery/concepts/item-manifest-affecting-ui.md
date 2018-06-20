---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Item manifest waarden die invloed van de gebruikersinterface van de PowerShell-galerie
ms.openlocfilehash: 39522396b179c54b981e6292cddacec27b32506c
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/10/2018
ms.locfileid: "34048846"
---
# <a name="item-manifest-values-that-impact-the-powershell-gallery-ui"></a>Item manifest waarden die invloed van de gebruikersinterface van de PowerShell-galerie

In dit onderwerp biedt uitgevers met samenvattingsinformatie over het wijzigen van het manifest voor PowerShell Gallery publicaties zodat functies PowerShellGet-cmdlets en de gebruikersinterface van de PowerShell-galerie worden beïnvloed.
Deze inhoud is geordend op waar de wijziging wordt weergegeven, vanaf het midden en klik op het navigatiegebied aan de linkerkant. Er is een sectie meer informatie over tags dekking biedt, waarin belangrijke veelgebruikte tags labels, evenals enkele van de meer.
Er zijn twee onderwerpen vindt u voorbeelden van manifest:

- Zie voor modules, [Update Module-Manifest](https://docs.microsoft.com/powershell/gallery/psget/module/psget_update-modulemanifest)
- Zie voor scripts, [scriptbestand met metagegevens maken](https://docs.microsoft.com/powershell/gallery/psget/script/psget_new-scriptfileinfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>PowerShell-galerie functie elementen beheerd door het Manifest

De onderstaande tabel bevat de elementen van de PowerShell-galerie-item pagina gebruikersinterface die worden beheerd door de uitgever.
Elk item geeft aan of kan worden beheerd door het manifest module of script.

| UI-Element | Beschrijving | Module | Script |
| --- | --- | --- | --- |
| **titel** | Dit is de naam van het item dat is gepubliceerd naar de galerie  | Nee | Nee |
| **Versie** | De versie die wordt weergegeven is de tekenreeks in de metagegevens en een prerelease als is opgegeven. Het primaire gedeelte van de versie in een Module-manifest is de ModuleVersion. Voor een script wordt vastgesteld als. Versie. Als de tekenreeks van een prerelease-versie is opgegeven, worden deze toegevoegd aan de ModuleVersion voor modules of opgegeven als onderdeel van. De versie voor scripts. Er is voor het opgeven van prerelease tekenreeksen in de documentatie bij [modules](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/prereleasemodule), en in [scripts](https://docs.microsoft.com/en-us/powershell/gallery/psget/script/prereleasescript) | Ja | Ja |
| **Beschrijving** | Dit is de beschrijving in het manifest van de module en in de bestandenlijst voor een script is. BESCHRIJVING | Ja | Ja |
| **Vereisen dat gebruikers met licentie** | Een module kunt u vereisen dat de gebruiker een licentie accepteren door het wijzigen van de module-manifest met RequireLicenseAcceptance = $true, levert een LicenseURI en voorzien in een bestand license.txt in de hoofdmap van de modulemap. Aanvullende informatie is beschikbaar in de [vereisen licentie acceptatie](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_requires_license_acceptance) onderwerp. | Ja | Nee |
| **Opmerkingen bij de release** | Voor modules, wordt deze informatie uit de sectie ReleaseNotes onder PSData\PrivateData getekend. In de manifesten script, is de. RELEASENOTES-element. | Ja | Ja |
| **Eigenaars** | Eigenaars zijn de lijst met gebruikers in de PowerShell-galerie die een artikel kunt bijwerken. De lijst eigenaar is niet opgenomen in het manifest item. Aanvullende documentatie wordt beschreven hoe u [eigenaren van item beheren](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners). | Nee | Nee |
| **auteur** | Dit is opgenomen in het manifest van de module als de auteur en in een script manifest als. AUTEUR. Het veld auteur wordt vaak gebruikt om op te geven van een bedrijf of organisatie die zijn gekoppeld aan een item. | Ja | Ja |
| **Copyright** | Dit is het veld Copyright in het manifest van de module en. COPYRIGHT in het manifest van een script. | Ja | Ja |
| **Bestandslijst** | De lijst met bestanden is afkomstig van het pakket wanneer het wordt gepubliceerd naar de PowerShell-galerie. Het is geen instelbare door de manifest-gegevens. Opmerking: Er is een extra .nuspec-bestand worden weergegeven met elk item in de PowerShell-galerie is niet aanwezig zijn na de installatie van het item op een systeem. Dit is het manifest van de Nuget-pakket voor het item en kan worden genegeerd. | Nee | Nee |
| **Tags** | Voor modules, Tags opgenomen onder PSData\PrivateData. Voor scripts, de sectie is met het label. LABELS. Houd er rekening mee dat labels kunnen niet spaties, zelfs wanneer ze tussen aanhalingstekens. Labels hebben aanvullende vereisten en betekenis zoals verderop in dit onderwerp in het gedeelte Details van de Tag wordt beschreven. | Ja | Ja |
| **Cmdlets** | Dit is opgegeven in de module-manifest met CmdletsToExport. Houd er rekening mee dat de aanbevolen procedure wordt expliciet lijstitems in plaats van met behulp van het jokerteken ' * ', zoals die de prestaties van de load-module voor gebruikers verbeteren. | Ja | Nee |
| **Functies** | Dit is opgegeven in de module-manifest met FunctionsToExport. Houd er rekening mee dat de aanbevolen procedure wordt expliciet lijstitems in plaats van met behulp van het jokerteken ' * ', zoals die de prestaties van de load-module voor gebruikers verbeteren. | Ja | Nee |
| **DSC-Resources** | Dit is opgegeven voor modules die worden gebruikt op PowerShell versie 5.0 en hoger, in het manifest met DscResourcesToExport. Als de module moet worden gebruikt in PowerShell 4 is, moet de DSCResourcesToExport niet worden gebruikt als het is geen ondersteunde manifest sleutel. (DSC is niet beschikbaar voor PowerShell 4.) | Ja | Nee |
| **Werkstromen** | Werkstromen worden gepubliceerd naar de PowerShell-galerie als scripts en werkstromen aangemerkt (Zie [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) voor een voorbeeld) in de code. Dit wordt niet gecontroleerd door het manifest. | Nee | Nee |
| **Mogelijkheden van de rol** | Dit wordt weergegeven wanneer de module die is gepubliceerd naar de PowerShell-galerie bevat een of meer rollen capability (.psrc)-bestanden, die door JEA worden gebruikt. Zie de JEA-documentatie voor meer informatie over [rol mogelijkheden](https://docs.microsoft.com/en-us/powershell/jea/role-capabilities). | Ja | Nee |
| **PowerShell-edities** | Dit is opgegeven in een script of module-manifest. Modules die zijn ontworpen om te worden gebruikt met PowerShell 5.0 en onder dit wordt geregeld met Tags. Gebruik de tag PSEdition_Desktop voor bureaublad, en voor core, gebruikt u de tag PSEdition_Core. Voor modules die alleen op PowerShell 5.1 en hoger worden gebruikt, moet u er een sleutel CompatiblePSEditions is in het manifest van de belangrijkste. Raadpleeg voor aanvullende details over de PS-editie-functie in [de PowerShell-Get-documentatie](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/modulewithpseditionsupport). | Ja | Ja |
| **Afhankelijkheden** | Afhankelijkheden zijn de modules die zijn gedeclareerd in module als RequiredModules of in het manifest script als in de PowerShell-galerie #Requires-Module (naam). | Ja | Ja |
| **Minimale versie van Powershell** | Dit kan worden opgegeven in een module-manifest als PowerShellVersion | Ja | Nee |
| **Versiegeschiedenis** | De versiegeschiedenis weerspiegelt de updates die zijn aangebracht in een module in de PowerShell-galerie. Als een versie van een item wordt weergegeven met de functie verwijderen, wordt deze niet weergegeven in de geschiedenis, behalve voor de eigenaren van item. | Nee | Nee |
| **Project-Site** | De project-site is opgegeven voor modules in de sectie Privatedata\PSData van het manifest van de module door te geven van een ProjectURI. In het manifest script wordt het geregeld door te geven. PROJECTURI. | Ja | Ja |
| **Licentie** | Een licentie-koppeling is opgegeven voor modules in de sectie Privatedata\PSData van het manifest van de module door te geven van een LicenseURI. In het manifest script wordt het geregeld door te geven. LICENSEURI. Het is belangrijk te weten dat als een licentie niet via de LicenseURI opgegeven is of binnen een module, de gebruiksvoorwaarden voor de PowerShell-galerie geeft u de gebruiksvoorwaarden voor het item. Zie de gebruiksvoorwaarden voor meer informatie. | Ja | Ja |

## <a name="editing-item-details"></a>Details van item bewerken

De pagina bewerken van de PowerShell-galerie-item kunt uitgevers wijzigen aantal velden specifiek voor een item, weergegeven:

- Title
- Beschrijving
- Samenvatting
- Pictogram-URL
- URL van de startpagina van project
- Auteurs
- Copyright
- Labels
- Opmerkingen bij de release
- Licentie nodig

Deze aanpak is algemeen niet aanbevolen, behalve wanneer nodig om op te lossen wat wordt weergegeven voor een oudere versie van een module.
Gebruikers die de module verkrijgen ziet de metagegevens komt niet overeen met wat in de PowerShell-galerie, waardoor problemen met het item wordt weergegeven.
Dit leidt vaak in query's naar de item eigenaren van de wijziging te bevestigen.
Het is raadzaam dat elk gewenst moment dat deze aanpak wordt gebruikt, een nieuwe versie van het item moet worden gepubliceerd met de dezelfde wijzigingen.

## <a name="tag-details"></a>Details van label

Labels zijn eenvoudige tekenreeksen consumers gebruikt om items te vinden.
Labels zijn het nuttigst wanneer deze consistent worden gebruikt voor veel items die betrekking hebben op hetzelfde onderwerp. Met behulp van meerdere versies van dezelfde biedt word (bijvoorbeeld database en databases, of test en testen) gewoonlijk weinig voordeel.
Tags zijn niet hoofdlettergevoelig tekenreeksen van één woord en mag geen lege waarden bevatten. Als er een wachtwoordzin die u denkt gebruikers wordt gezocht dat naar, voegt u toe dat het item beschrijving en het in de zoekresultaten worden gevonden. Gebruik Pascal hoofdlettergebruik, afbreekstreepje, onderstrepingsteken of punt als u probeert om leesbaarheid te verbeteren. Lange, complexe en ongebruikelijke-labels maken voorzichtig zijn als ze vaak worden getypt.

Er zijn labels die belangrijk zijn te weten, als de PowerShell-galerie en PowerShellGet cmdlets ze behandelen uniek. PSEdition_Desktop PSEdition_Core zijn de specifieke voorbeelden en hierboven zijn beschreven.

Zoals eerder vermeld, worden de meeste waarde door tags bieden wanneer ze specifiek en gebruikte consistent voor veel items zijn.
Als een publisher bij het vinden van de beste labels te gebruiken, is de eenvoudigste manier om te zoeken van de PowerShell-galerie voor labels die u overweegt.
In het ideale geval zal er veel items geretourneerd en beschrijvingen van de objecten worden uitgelijnd met uw gebruik van die sleutel woord.

Hier volgen enkele veelgebruikte codes vanaf 14-12/2017 ter referentie.
In sommige gevallen zijn vergelijkbaar, maar mogelijk minder ideaal opties weergegeven naast het label.
Het is een best practice om te gebruiken van de Tag voorkeur als die leiden tot minder ruis en beter zoekresultaten voor consumenten.


| **Voorkeur label** | **Alternatieven en -opmerkingen** |
| --- | --- |
| **Azure** |  |
| **DSC** | DesiredStateConfiguration minder wenselijk is, is te lang |
| **ResourceManager** | ARM wordt gebruikt om te beschrijven van het aantal processors en mag niet worden gebruikt voor Azure Resource Manager | **DSCResourceKit** |  |
| **SQL** |  |
| **AWS** |  |
| **DSCResource** |  |
| **Automation** |  |
| **REST** |  |
| **ActiveDirectory** | AD wordt momenteel niet gebruikt door zichzelf  |
| **SQLServer** |  |
| **DBA** |  |
| **Beveiliging** | Defense is minder nauwkeurig |
| **Database** | Database (meervoud) minder wenselijk is |
| **DevOps** |  |
| **Windows** |  |
| **bouwen** |  |
| **Implementatie** | Implementeer wat minder vaak wordt gebruikt |
| **Cloud** |  |
| **GIT** |  |
| **Test** | Testen is minder wenselijk |
| **VersionControl** | Versie is minder nauwkeurig, hoewel er vaker gebruikt  |
| **Logboekregistratie** | Voorkeur gebruik van logboekregistratie als een actie |
| **Log** | Voorkeur logboek worden gebruikt als een ding |
| **Back-up** |  |
| **IaaS** |  |
| **Linux** |  |
| **IIS** |  |
| **AzureAutomation** |  |
| **Opslag** |  |
| **GitHub** |  |
| **Json** |  |
| **Exchange** |  |
| **Netwerk** | Netwerken lijkt, zijn minder vaak worden gebruikt |
| **SharePoint** |  |
| **Rapportage** | Reporting is een actie, het rapport is een ding |
| **Rapport** | Rapport is een ding |
| **WinRM** |  |
| **Bewaking** |  |
| **VSTS** |  |
| **Excel** |  |
| **Google** |  |
| **Kleur** |  |
| **DNS** |  |
| **Office365** | Office spellen verdient de voorkeur. O365 wordt minder vaak gebruikt, hoewel korter | **Gitlab** |  |
| **Pester** |  |
| **AzureAD** |  |
| **HTML** |  |
| **Hyper-V** | Hyper-v is niet zo vaak als een tag |
| **Configuratie** |  |
| **ChatOps** |  |
| **PackageManagement** |  |
| **WMI** |  |
| **Firewall** |  |
| **Docker** |  |
| **Appveyor** |  |
| **AzureRm** | Primair gebruikt voor de AzureRM-modules |
| **Zip** |  |
| **MSI** |  |
| **Mac** |  |
| **PoshBot** |  |