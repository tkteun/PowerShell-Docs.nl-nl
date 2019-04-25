---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Pakket manifest waarden die van invloed zijn op de UI van de PowerShell-galerie
ms.openlocfilehash: cedf81df8de29c54ef559a800d654305029491ec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084705"
---
# <a name="package-manifest-values-that-impact-the-powershell-gallery-ui"></a>Pakket manifest waarden die van invloed zijn op de UI van de PowerShell-galerie

In dit onderwerp biedt uitgevers met beknopte informatie over het wijzigen van het manifest voor de PowerShell Gallery-publicaties zodat de functies van PowerShellGet-cmdlets en de PowerShell Gallery-gebruikersinterface worden beïnvloed. Deze inhoud is geordend op waar de wijziging wordt weergegeven, beginnen met het middengedeelte en klik op het navigatiegebied aan de linkerkant. Er is een sectie voor meer informatie over dekking tags, waarin belangrijke tags, evenals enkele van de meer gangbare tags. Er zijn twee onderwerpen vindt u voorbeelden van manifest:

- Zie voor modules, [Update Module-Manifest](/powershell/module/powershellget/Update-ModuleManifest)
- Zie voor scripts, [scriptbestand met metagegevens maken](/powershell/module/powershellget/New-ScriptFileInfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>PowerShell Gallery functie elementen bepaald door het Manifest

De onderstaande tabel bevat de elementen van de PowerShell Gallery-pagina van het pakket gebruikersinterface die worden beheerd door de uitgever. Elk item wordt aangegeven als kan worden beheerd door de module of het script het manifest.

| UI-Element | Description | Module | Script |
| --- | --- | --- | --- |
| **Titel** | Dit is de naam van het pakket dat wordt gepubliceerd naar de galerie  | Nee | Nee |
| **Versie** | De versie die wordt weergegeven is de tekenreeks in de metagegevens en een voorlopige als is opgegeven. De primaire deel van de versie in een Module-manifest is de ModuleVersion. Voor een script, wordt dit aangeduid als. Versie. Als een tekenreeks prerelease-versie is opgegeven, wordt deze toegevoegd aan de ModuleVersion voor modules, of als onderdeel van de opgegeven. De versie voor scripts. Er is voor het opgeven van prerelease tekenreeksen in de documentatie bij [modules](module-prerelease-support.md), en in [scripts](script-prerelease-support.md) | Ja | Ja |
| **Beschrijving** | Dit is de beschrijving in de module-manifest en in een script bestand manifest is. BESCHRIJVING | Ja | Ja |
| **Acceptatie van de licentie vereisen** | Een module kan vereisen dat de gebruiker akkoord gaat met een licentie, door het wijzigen van de module-manifest met RequireLicenseAcceptance = $true, leveren een LicenseURI en bieden een license.txt-bestand in de hoofdmap van de modulemap. Aanvullende informatie is beschikbaar in de [acceptatie van de licentie vereisen](../how-to/working-with-packages/packages-that-require-license-acceptance.md) onderwerp. | Ja | Nee |
| **Opmerkingen bij de release** | Voor modules, wordt deze informatie uit de sectie ReleaseNotes onder PSData\PrivateData getekend. In de manifesten script, is het. RELEASENOTES-element. | Ja | Ja |
| **Eigenaren** | Eigenaren zijn de lijst met gebruikers in de PowerShell-galerie die u kunt een pakket bijwerken. De lijst met eigenaren is niet opgenomen in het manifest van het pakket. Aanvullende documentatie wordt beschreven hoe u [itemeigenaars beheren](../how-to/publishing-packages/managing-package-owners.md). | Nee | Nee |
| **De auteur** | Dit is opgenomen in de module-manifest als de auteur en in een manifest van het script als. DE AUTEUR. Het veld ' auteur ' wordt vaak gebruikt om op te geven van een bedrijf of organisatie die zijn gekoppeld aan een pakket. | Ja | Ja |
| **Copyright** | Dit is het auteursrecht-veld in de module-manifest en. COPYRIGHT in een manifest van het script. | Ja | Ja |
| **FileList** | De lijst met bestanden wordt getekend van het pakket wanneer het wordt gepubliceerd naar de PowerShell Gallery. Het is niet beheerd door de manifest-informatie. Opmerking: Er is een extra .nuspec-bestand worden weergegeven met elk pakket in de PowerShell-galerie die is niet aanwezig na de installatie van het pakket op een systeem. Dit is het manifest van het Nuget-pakket voor het pakket, en kan worden genegeerd. | Nee | Nee |
| **Tags** | Voor modules, worden Tags opgenomen onder PSData\PrivateData. Voor scripts, wordt de sectie gelabeld. MET TAGS. Let op: tags mag geen spaties bevatten, zelfs wanneer ze zich in de aanhalingstekens. Tags zijn aanvullende vereisten en betekenis, die verderop in dit onderwerp in het gedeelte Details van de Tag worden beschreven. | Ja | Ja |
| **Cmdlets** | Dit is opgegeven in de module-manifest CmdletsToExport gebruiken. Houd er rekening mee dat de aanbevolen procedure is om expliciet de items weer te geven in plaats van met behulp van het jokerteken ' * ', zoals die de prestaties van de load-module voor gebruikers verbeteren. | Ja | Nee |
| **Functies** | Dit is opgegeven in de module-manifest FunctionsToExport gebruiken. Houd er rekening mee dat de aanbevolen procedure is om expliciet de items weer te geven in plaats van met behulp van het jokerteken ' * ', zoals die de prestaties van de load-module voor gebruikers verbeteren. | Ja | Nee |
| **DSC-Resources** | Voor modules die worden gebruikt op de PowerShell-versie 5.0 en hoger, wordt dit in het manifest met behulp van DscResourcesToExport geboden. Als de module moet worden gebruikt in PowerShell 4, moet de DSCResourcesToExport niet worden gebruikt omdat het is geen ondersteunde manifest-sleutel. (DSC is niet beschikbaar voor PowerShell 4.) | Ja | Nee |
| **Werkstromen** | Werkstromen zijn gepubliceerd in de PowerShell Gallery als scripts, en is geïdentificeerd als werkstromen (Zie [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) voor een voorbeeld) in de code. Dit niet wordt beheerd door het manifest. | Nee | Nee |
| **Rolmogelijkheden** | Dit wordt weergegeven wanneer de module die is gepubliceerd naar de PowerShell Gallery bevat een of meer rollen capability (.psrc)-bestanden, die worden gebruikt door JEA. Zie de JEA-documentatie voor meer informatie over [rolmogelijkheden](/powershell/jea/role-capabilities). | Ja | Nee |
| **PowerShell-edities** | Dit is opgegeven in een script of een module-manifest. Modules die zijn ontworpen om te worden gebruikt met PowerShell 5.0 en onder dit wordt bepaald met behulp van labels. Gebruik de tag PSEdition_Desktop voor bureaublad, en voor core, gebruikt u de tag PSEdition_Core. Voor modules die worden gebruikt alleen in PowerShell 5.1 en hoger, is er een CompatiblePSEditions sleutel in het manifest van de belangrijkste. Voor extra details, raadpleegt u de functie PS-editie in [de PowerShell-Get-documentatie](module-psedition-support.md). | Ja | Ja |
| **Afhankelijkheden** | Afhankelijkheden zijn de modules in de PowerShell Gallery die zijn gedefinieerd in een van beide de module als RequiredModules of in het manifest van het script als #Requires-Module (naam). | Ja | Ja |
| **Minimale versie van PowerShell** | Dit kan worden opgegeven in een module-manifest als PowerShellVersion | Ja | Nee |
| **Versiegeschiedenis** | De versiegeschiedenis weerspiegelt de updates die zijn aangebracht in een module in de PowerShell Gallery. Als een versie van een pakket is verborgen met behulp van de functie verwijderen, zal dit niet worden weergegeven in de versiegeschiedenis, behalve voor de eigenaren van het pakket. | Nee | Nee |
| **Project-Site** | Site van het project is opgegeven voor modules in de sectie Privatedata\PSData van de module-manifest door een ProjectURI op te geven. In het manifest van het script, wordt dit bepaald door het op te geven. PROJECTURI. | Ja | Ja |
| **Licentie** | De koppeling van een licentie is opgegeven voor modules in de sectie Privatedata\PSData van de module-manifest door een LicenseURI op te geven. In het manifest van het script, wordt dit bepaald door het op te geven. LICENSEURI. Het is belangrijk te weten dat als een licentie niet via de LicenseURI opgegeven is of binnen een module, geef de gebruiksvoorwaarden voor de PowerShell Gallery vervolgens de gebruiksvoorwaarden voor het pakket. Zie de gebruiksvoorwaarden voor meer informatie. | Ja | Ja |
| **Icon** | Een pictogram kan worden opgegeven voor een pakket in de PowerShell-galerie door op te geven van de markering IconURI in het manifest van het script of in de sectie Privatedata PSData van de module-manifest. De IconURI moet verwijzen naar de installatiekopie van een 32 x 32 met transparantie achtergrond. De URI **moet** worden van een directe afbeeldings-URL en **moet niet** gaat u naar een webpagina met de installatiekopie of een bestand in de PowerShell Gallery-pakket. | Ja | Ja |


## <a name="editing-package-details"></a>Pakketdetails bewerken

De pagina pakket bewerken van PowerShell-galerie kan uitgevers te wijzigen welke velden worden weergegeven voor een pakket specifiek aantal:

- Titel
- Description
- Samenvatting
- Pictrogram-URL
- URL van startpagina van project
- Auteurs
- Copyright
- Tags
- Opmerkingen bij de release
- Licentie vereist

Deze benadering is niet in het algemeen wordt aangeraden, behalve wanneer die nodig zijn om op te lossen wat wordt weergegeven voor een oudere versie van een module. Gebruikers die de module verkrijgen ziet de metagegevens komt niet overeen met wat wordt weergegeven in de PowerShell Gallery, waardoor de bezorgdheid over het pakket. Dit leidt vaak in query's naar de pakket-eigenaren de wijziging te bevestigen. Het is raadzaam dat telkens wanneer die deze methode wordt gebruikt, een nieuwe versie van het pakket moet worden gepubliceerd met de dezelfde wijzigingen.

## <a name="tag-details"></a>Details van label

Tags zijn eenvoudige tekenreeksen consumenten gebruiken om te vinden van pakketten. Tags zijn het nuttigst wanneer ze in veel pakketten met betrekking tot hetzelfde onderwerp consistent worden gebruikt. Met behulp van meerdere versies van hetzelfde biedt woord (bijvoorbeeld database en -databases, of test en testen) doorgaans weinig voordeel. Labels zijn niet hoofdlettergevoelig tekenreeksen van één woord en mag geen lege waarden bevatten. Als er een wachtwoordzin die u denkt dat zoekt naar gebruikers, die aan de beschrijving van het pakket toevoegen en deze wordt gevonden in de lijst met zoekresultaten. Pascal hoofdlettergebruik, streepje, onderstrepingsteken of punt gebruiken als u probeert om leesbaarheid te verbeteren.
Voorzichtig zijn met het maken van lange, complexe en ongebruikelijke tags, zoals ze worden vaak verkeerd gespelde.

Er zijn labels die zijn belangrijk om te weten, als de PowerShell Gallery en PowerShellGet cmdlets ze behandelen uniek. PSEdition_Desktop PSEdition_Core zijn de specifieke voorbeelden en hierboven zijn beschreven.

Zoals eerder vermeld, Geef labels de meeste waarde wanneer ze specifieke en gebruikte consistent op veel pakketten zijn. Als een uitgever bij het vinden van de beste labels te gebruiken, is de eenvoudigste methode om te zoeken naar de PowerShell Gallery voor tags die u overweegt. In het ideale geval zullen er veel pakketten geretourneerd en de beschrijvingen van het pakket wordt in overeenstemming met uw gebruik van die sleutel woord.

Ter referentie: Hier vindt u enkele veelgebruikte tags vanaf 14-12-2017. In sommige gevallen zijn vergelijkbaar, maar wellicht minder ideaal opties die worden weergegeven naast het label. Dit is een aanbevolen procedure om te gebruiken van de Tag bij voorkeur als die leiden tot minder ruis en betere zoekresultaten voor consumenten.

| Gewenste tag | Alternatieven en opmerkingen |
| --- | --- |
| Azure |  |
| DSC | DesiredStateConfiguration minder wenselijk is, is te lang |
| ResourceManager | ARM wordt gebruikt om te beschrijven van de groep van processors die zijn en mag niet worden gebruikt voor Azure Resource Manager |
| DSCResourceKit |  |
| SQL |  |
| AWS |  |
| DSCResource |  |
| Automatisering |  |
| REST |  |
| ActiveDirectory- | AD wordt momenteel niet gebruikt door zelf  |
| SQLServer |  |
| DBA |  |
| Beveiliging | Defense is minder nauwkeurig |
| Database | Databases (meervoud) is minder wenselijk |
| DevOps |  |
| Windows |  |
| Ontwikkelen |  |
| Implementatie | Implementeer wat minder vaak wordt gebruikt |
| Cloud |  |
| GIT |  |
| Test | Testen is minder wenselijk |
| VersionControl | Versie is minder nauwkeurig, hoewel er vaker gebruikt  |
| Logboekregistratie | Voorkeur gebruik van de logboekregistratie als actie |
| Logboek | Logboek voorkeur worden gebruikt als een ding |
| Back-up |  |
| IaaS |  |
| Linux |  |
| IIS |  |
| AzureAutomation |  |
| Opslag |  |
| GitHub |  |
| Json |  |
| Exchange |  |
| Netwerk | Netwerken is vergelijkbaar, minder vaak worden gebruikt |
| SharePoint |  |
| Rapportage | Rapportage is een actie, het rapport is een ding |
| Rapport | Rapport is een ding |
| WinRM |  |
| Bewaking |  |
| VSTS |  |
| Excel |  |
| Google |  |
| Kleur |  |
| DNS |  |
| Office365 | Office spellen verdient de voorkeur. O365 wordt minder vaak gebruikt, hoewel kortere |
| Gitlab |  |
| Pester |  |
| AzureAD |  |
| HTML-CODE |  |
| Hyper-V | Hyper-v is het minder gebruikelijk als een label |
| Configuratie |  |
| ChatOps |  |
| PackageManagement |  |
| WMI (Engelstalig) |  |
| Firewall |  |
| Docker |  |
| Appveyor |  |
| AzureRm | Primair gebruikt voor de AzureRM-modules |
| Postcode |  |
| MSI |  |
| MacOS |  |
| PoshBot |  |
