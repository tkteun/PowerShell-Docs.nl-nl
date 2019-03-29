---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
description: Richtlijnen voor uitgevers
title: PowerShell Gallery richtlijnen en aanbevolen procedures publiceren
ms.openlocfilehash: 1cd0140cc208949e13d23331b23a58ffc374430b
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623905"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>PowerShellGallery richtlijnen en aanbevolen procedures publiceren

Dit onderwerp wordt beschreven aanbevolen stappen die worden gebruikt door Microsoft-teams om te controleren of de pakketten die zijn gepubliceerd naar de PowerShell Gallery algemeen wordt vastgesteld en hoge waarde biedt aan gebruikers, op basis van hoe de PowerShell Gallery manifest gegevens verwerkt en feedback van grote het aantal gebruikers van de PowerShell Gallery.
Pakketten die zijn gepubliceerd in deze richtlijnen volgt kans om te worden geïnstalleerd, worden vertrouwd, en meer gebruikers aan te trekken.

Hieronder volgen richtlijnen voor het waaruit een goede PowerShell Gallery-pakket, welke instellingen zijn optioneel Manifest het belangrijkst zijn, het verbeteren van uw code met feedback van de eerste revisoren en [Powershell-Script Analyzer](https://aka.ms/psscriptanalyzer), versiebeheer uw module, documentatie, tests en voorbeelden voor het gebruik van wat u hebt gedeeld.
Veel van deze documentatie volgt de richtlijnen voor publicatie [Modules van hoge kwaliteit DSC-Resource](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Zie voor het mechanisme van het publiceren van een pakket naar de PowerShell Gallery, [maken en publiceren van een pakket](/powershell/gallery/how-to/publishing-packages/publishing-a-package).

Feedback over deze richtlijnen wordt verwelkomde. Als u feedback hebt, opent u problemen in onze [Github-opslagplaats voor documentatie](https://github.com/powershell/powershell-docs/issues).

## <a name="best-practices-for-publishing-packages"></a>Aanbevolen procedures voor het publiceren van pakketten

De volgende aanbevolen procedures zijn wat de gebruikers van de items van de PowerShell Gallery zegt is belangrijk en vindt u in de volgorde van prioriteit nominale.
Pakketten die aan deze richtlijnen voldoet, zijn veel vaker zal worden gedownload en worden vastgesteld door anderen.

- Use PSScriptAnalyzer
- Documentatie en voorbeelden
- Reageren op feedback
- Bieden van modules in plaats van scripts
- Vindt u koppelingen naar de projectsite van een
- Label van het pakket met de compatibel PSEdition(s) en platforms
- Tests met uw modules bevatten
- Opgenomen en/of te koppelen aan licentievoorwaarden
- Meld u aan uw code
- Ga als volgt [SemVer](http://semver.org/) richtlijnen voor versiebeheer
- Gebruik van veelgebruikte tags, zoals beschreven in de galerie voor algemene PowerShell-codes
- Publiceren met behulp van een lokale opslagplaats testen
- PowerShellGet gebruiken om te publiceren

Elk van deze wordt kort beschreven in de volgende secties.

## <a name="use-psscriptanalyzer"></a>Use PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) is een hulpmiddel gratis statische code die geschikt is voor PowerShell-code.
PSScriptAnalyzer identificeert de meest voorkomende problemen die in de PowerShell-code, en vaak een aanbeveling voor het oplossen van het probleem.
Het hulpprogramma is eenvoudig te gebruiken en de problemen als fouten worden gecategoriseerd (ernstig, moeten worden opgelost), waarschuwing (moet worden gecontroleerd en moet worden opgelost), en informatie (waard voor aanbevolen procedures).
Alle pakketten die zijn gepubliceerd in PowerShell Gallery, worden gescand met behulp van PSScriptAnalyzer en eventuele fouten worden gerapporteerd aan de eigenaar en moeten worden opgelost.

De aanbevolen procedure is om uit te voeren `Invoke-ScriptAnalyzer` met `-Recurse` en `-Severity` waarschuwing.

Bekijk de resultaten en zorg ervoor dat:

- Alle fouten zijn gecorrigeerd of behandeld in de documentatie
- Alle waarschuwingen worden bekeken en opgelost, indien van toepassing

Gebruikers die pakketten vanuit de PowerShell Gallery verkrijgen zijn ten zeerste aangeraden PSScriptAnalyzer uitvoeren en evalueren van alle fouten en waarschuwingen.
Gebruikers zijn zeer waarschijnlijk contact opnemen met de eigenaren van het pakket als ze zien dat er een fout gemeld door PSScriptAnalyzer is.
Als er een dwingende redenen voor het pakket te houden van code die is gemarkeerd als een fout, kunt u die gegevens toevoegen aan uw documentatie om te voorkomen dat de dezelfde vraag beantwoorden vaak.

## <a name="include-documentation-and-examples"></a>Documentatie en voorbeelden

Documentatie en voorbeelden zijn de beste manier om te controleren of gebruikers kunnen profiteren van een gedeelde code.

Documentatie is het nuttigst wat om op te nemen in pakketten die zijn gepubliceerd naar de PowerShell Gallery.
Gebruikers wordt in het algemeen-pakketten zonder documentatie, overslaan als het alternatief is om te lezen van de code voor meer informatie over wat het pakket is en het gebruik ervan.
Er zijn verschillende artikelen over het bieden van documentatie met PowerShell-pakketten, met inbegrip van:

- Richtlijnen voor het ontwikkelen van Help-informatie zich in [Cmdlet helpen schrijven](https://go.microsoft.com/fwlink/?LinkID=123415)
- Het met het maken van de help van de cmdlet, dit is de beste manier om een PowerShell-script, functie of cmdlet.
  Voor meer informatie over het maken van de help van de cmdlet start met [schrijven Cmdlet helpen](https://go.microsoft.com/fwlink/?LinkID=123415).
  Zie het Help-informatie in een script toevoegen [over opmerking op basis van Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).
- Veel modules ook documentatie in tekstindeling, zoals MarkDown-bestanden.
  Dit kan vooral nuttig zijn wanneer er een site in Github, waar Markdown een intensief gebruikte indeling is.
  De aanbevolen procedure is om te gebruiken [Github-flavored Markdown](https://help.github.com/categories/writing-on-github/)

Voorbeelden van gebruikers hoe het pakket is bedoeld om te worden gebruikt.
Veel ontwikkelaars wordt zeggen dat ze voorbeelden voordat u de documentatie bij om te begrijpen hoe u iets bekijken.
Het aanbevolen type voorbeelden tonen basisgebruik, plus een gesimuleerde realistische use case en de code is goed opmerkingen.
Voorbeelden voor gepubliceerd naar de PowerShell Gallery-modules moeten zich in een map van de voorbeelden in de hoofdmap van de module.

Een goede patroon voor voorbeelden kunt u vinden in de [PSDscResource module](https://www.powershellgallery.com/packages/PSDscResources) onder de map Examples\RegistryResource.
Er worden vier voorbeeld gebruikt met een korte beschrijving aan de bovenkant van elk bestand dat is wat wordt aangetoond documenten.

## <a name="respond-to-feedback"></a>Reageren op feedback

De waarde van pakket-eigenaren die goed op feedback reageren wordt zeer door de community.
Gebruikers die feedback geven feitelijke zijn belangrijk om te reageren op, zoals ze geïnteresseerd in het pakket zijn om te helpen verbeteren.

Er zijn twee methoden voor feedback beschikbaar in de PowerShell Gallery:

- Neem contact op met de eigenaar: Dit kan een gebruiker een e-mailbericht verzenden naar de eigenaar van het pakket. Als de eigenaar van een pakket, is het belangrijk om te controleren van het e-mailadres gebruikt in combinatie met de PowerShell Gallery-pakketten en reageren op problemen die worden gegenereerd. Een nadeel van deze methode is dat alleen de gebruiker en de eigenaar ooit de communicatie, zien zodat de eigenaar van de mogelijk moet u de dezelfde vraag worden beantwoord vaak.
- Opmerkingen: Pagina is aan de onderkant van het pakket met een opmerkingenveld.
  Het voordeel van dit systeem is dat andere gebruikers kunnen zien de opmerkingen en -antwoorden, waardoor het aantal keren dat die een enkele vraag moet worden beantwoord.
  Als de eigenaar van een pakket, is het raadzaam dat u de opmerkingen voor elk pakket volgt.
Zie [Feedback geven via Socialemedia of opmerkingen](../how-to/working-with-packages/social-media-feedback.md) voor meer informatie over hoe u dat doet.

Eigenaren die op feedback constructively reageren worden gewaardeerd door de community.
De mogelijkheid in het rapport wilt aanvragen van meer informatie, indien nodig, bieden een tijdelijke oplossing gebruiken of identificeren als een update wordt een probleem opgelost.

Als er ongepast gedrag waargenomen van één van deze communicatiekanalen, gebruikt u de functie misbruik van de PowerShell Gallery contact opnemen met de galerie-beheerders.

## <a name="modules-versus-scripts"></a>Modules ten opzichte van Scripts

Een script delen met andere gebruikers is erg handig en biedt andere voorbeelden van hoe ze hebben wellicht problemen op te lossen.
Het probleem is dat scripts in de PowerShell Gallery enkele bestanden zonder afzonderlijke documentatie, voorbeelden en tests.

PowerShell-Modules zijn een structuur waarmee u kunt meerdere mappen en bestanden die moeten worden opgenomen in het pakket.
Structuur van de module kunt u met inbegrip van de andere pakketten die we aanbieden als best practices: cmdlet help, documentatie, voorbeelden en tests.
Het grootste nadeel is dat een script in een module moet worden weergegeven en als een functie gebruikt.
Zie voor meer informatie over het maken van een module [schrijven van een Windows PowerShell-Module](http://go.microsoft.com/fwlink/?LinkId=144916).

Er zijn situaties waarin een script een betere ervaring voor de gebruiker, met name met DSC-configuraties biedt.
De aanbevolen procedure voor DSC-configuraties is voor het publiceren van de configuratie als een script met een bijbehorende module met de documenten, voorbeelden en tests.
Het script geeft een lijst van de bijbehorende module met behulp van RequiredModules = @(naam van de Module).
Deze methode kan worden gebruikt bij elk script.

Werkelijke waarde bieden zelfstandige scripts die de aanbevolen procedures volgen aan andere gebruikers.
Hiervoor bieden op basis van een opmerking documentatie en een koppeling naar de Site van een Project sterk aanbevolen wordt bij het publiceren van een script in PowerShell Gallery.

## <a name="provide-a-link-to-a-project-site"></a>Een koppeling naar de projectsite van een

De Site van een Project is waar een uitgever kan communiceren rechtstreeks met de gebruikers van de PowerShell Gallery-pakketten.
Gebruikers liever pakketten met dit, aangezien deze voor informatie over het pakket gemakkelijker kunt.
Groot aantal pakketten in de PowerShell Gallery in GitHub worden ontwikkeld, worden andere door organisaties met een speciale website geleverd.
Elk van deze kan worden beschouwd als een site.

Een koppeling toe te voegen, wordt dit gedaan door ProjectURI te nemen in de sectie PSData van het manifest als volgt:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

Wanneer een ProjectURI is opgegeven, wordt de PowerShell Gallery bevat een koppeling naar de Site van het Project aan de linkerkant van de pakketpagina.

## <a name="tag-your-package-with-the-compatible-pseditions-and-platforms"></a>Label van het pakket met de compatibel PSEdition(s) en platforms

De volgende codes gebruiken om te demonstreren aan gebruikers die pakketten goed met hun omgeving werkt:

- PSEdition_Desktop: Pakketten die compatibel met Windows PowerShell zijn
- PSEdition_Core: Pakketten die compatibel met PowerShell Core zijn
- Windows : Pakketten die compatibel zijn met het Windows-besturingssysteem
- Linux: Pakketten die compatibel zijn met het Linux-besturingssystemen
- MacOS: Pakketten die compatibel zijn met het Mac-besturingssysteem

Door het labelen van het pakket met de compatibel platform (s) het opgenomen in de galerie zoekfilters in het linkerdeelvenster van de lijst met zoekresultaten. Als u het pakket op GitHub, host wanneer u het pakket een label, u kunt ook rekening houden met profiteren van onze [PowerShell Gallery compatibele schilden](https://img.shields.io/powershellgallery/p/:packageName.svg) 
![compatibiliteit shield](https://img.shields.io/powershellgallery/p/CosmosDB.svg).  

## <a name="include-tests"></a>Tests opnemen

Het is belangrijk dat gebruikers, met inbegrip van tests met open-source code als het biedt hen assurance over wat u valideren, en vindt u informatie over de werking van uw code. Ook kunnen gebruikers zodat ze de functionaliteit van uw oorspronkelijke niet defect raken als ze uw code om aan te passen in hun omgeving kunnen wijzigen.

Het is raadzaam dat tests om te profiteren van het framework voor het testen van Pester, die is ontworpen voor PowerShell worden geschreven.
Lastige is beschikbaar in [GitHub](https://github.com/Pester/Pester), wordt de [PowerShell Gallery](https://www.powershellgallery.com/packages/Pester/), en wordt geleverd in Windows 10, Windows Server 2016, WMF 5.0 en WMF 5.1.

De [Pester project-site in GitHub](https://github.com/Pester/Pester) goede documentatie over het schrijven van Pester tests, van beginnende gebruikers tot aanbevolen procedures omvat.

De doelen voor testdekkingsgraad worden specifiek genoemd de [documentatie van hoge kwaliteit Resource Module](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), testen met 70% eenheid code dekking aanbevolen.

## <a name="include-andor-link-to-license-terms"></a>Opgenomen en/of te koppelen aan licentievoorwaarden

Alle pakketten die zijn gepubliceerd in PowerShell Gallery, moet de licentievoorwaarden opgeven of afhankelijk zijn van de licentie die is opgenomen in de [gebruiksvoorwaarden](https://www.powershellgallery.com/policies/Terms) onder 'Bewijsstuk A'.
De beste manier voor het opgeven van een andere licentie is een koppeling naar de licentie die met behulp van de LicenseURI in PSData.
U vindt een voorbeeld in het onderwerp van het Manifest van de velden aanbevolen.

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Meld u aan uw code

Ondertekening van programmacode biedt gebruikers met het hoogste niveau van zekerheid voor die het pakket hebt gepubliceerd, en dat de kopie van de code ze verkrijgen is precies wat de uitgever die zijn uitgebracht.
Zie voor meer informatie over het algemeen voor ondertekening van programmacode, [Inleiding tot de ondertekening van programmacode](http://go.microsoft.com/fwlink/?LinkId=106296).
PowerShell ondersteunt validatie van via twee primaire methoden voor ondertekening van programmacode:

- Scriptbestanden ondertekenen
- Een module voor het ondertekenen van catalogus

Ondertekening van de PowerShell-bestanden is een gevestigde benadering aan het waarborgen van de code wordt uitgevoerd door een betrouwbare bron is gemaakt, en is niet gewijzigd.
Meer informatie over het ondertekenen van PowerShell-script-bestanden wordt beschreven in de [over ondertekening](/powershell/module/microsoft.powershell.core/about/about_signing) onderwerp.
In het overzicht van kan een handtekening worden toegevoegd aan een. Ps1-bestand dat PowerShell valideert wanneer het script wordt geladen.
PowerShell kan worden beperkt met behulp van de [uitvoeringsbeleid](/powershell/module/microsoft.powershell.core/about/about_execution_policies) cmdlets voor het gebruik van ondertekende scripts.

Catalogus modules ondertekening is een functie die wordt toegevoegd aan PowerShell in versie 5.1.
Het ondertekenen van een module wordt beschreven in de [catalogus-Cmdlets](/powershell/wmf/5.1/catalog-cmdlets) onderwerp.
In het overzicht van wordt het ondertekenen van de catalogus uitgevoerd door het maken van een catalogusbestand, waarin een hash-waarde voor elk bestand in de module, en vervolgens dat bestand in te schrijven.
De PowerShellGet publiceren-module, install-module, save-module en update-module-cmdlets wordt controleren van de handtekening om te controleren of dat de parameter is geldig en Bevestig dat de hash-waarde voor elk pakket dat overeenkomt met wat is er in de catalogus.
Als een eerdere versie van de module is geïnstalleerd op het systeem, wordt er install-module bevestigen dat de instantie voor het ondertekenen van voor de nieuwe versie overeenkomt met wat eerder is geïnstalleerd.
Ondertekening van de catalogus met werkt, maar is geen vervanging voor ondertekenen scriptbestanden. PowerShell komt niet overeen voor catalogus handtekeningen tijdens het laden van een module.

## <a name="follow-semver-guidelines-for-versioning"></a>Volg de richtlijnen voor versiebeheer SemVer

[SemVer](http://semver.org/) is een openbare te gebruiken die wordt beschreven hoe u te structureren en een versie zodat u gemakkelijk te vertalen van de wijzigingen te wijzigen.
De versie voor het pakket moet worden opgenomen in het manifest gegevens.

- De versie moet worden gestructureerd als 3 numerieke blokken, gescheiden door punten, zoals in 0.1.1 of 4.11.192
- Beginnen met "0" versies aangeven dat het pakket nog niet klaar voor productie is en het eerste getal alleen met '0' beginnen mag als dat het enige dat wordt gebruikt
- Wijzigingen in het eerste getal (1.9.9999-2.0.0) geven belangrijke en belangrijke wijzigingen tussen de versies
- Wijzigingen in het tweede getal (1.1-1.2) wijzen op niveau van de functie wijzigingen, zoals het toevoegen van nieuwe-cmdlets aan een module
- Wijzigingen in het derde getal aangeven vaste wijzigingen, zoals de parameters voor nieuwe, bijgewerkte voorbeelden of nieuwe tests
- Wanneer versies wordt weergegeven, wordt PowerShell de versies gesorteerd als tekenreeksen, zodat 1.01.0 wordt beschouwd als groter dan 1.001.0

PowerShell is gemaakt voordat SemVer is gepubliceerd, zodat het ondersteuning voor de meeste, maar niet alle elementen van SemVer, speciaal biedt:

- Voorlopige tekenreeksen worden niet ondersteund in versienummers. Dit is handig als een uitgever wil een preview-versie van een nieuwe primaire versie na het opgeven van een versie 1.0.0 leveren. Dit wordt ondersteund in een toekomstige versie van de PowerShell Gallery en PowerShellGet-cmdlets.
- PowerShell en de PowerShell Gallery kunt versietekenreeksen met 1, 2 en 4 segmenten. Veel vroege modules niet voldeed aan de richtlijnen en versies van het product van Microsoft build informatie zoals een 4e blokkeren van de getallen (bijvoorbeeld 5.1.14393.1066) bevatten. Versiebeheer vanuit het oogpunt, van worden deze verschillen genegeerd.

## <a name="test-using-a-local-repository"></a>Test met behulp van een lokale opslagplaats

De PowerShell Gallery is niet ontworpen om te worden van een doel voor het testen van het publicatieproces.
De beste manier om te testen de end-to-end-proces van publiceren naar de PowerShell Gallery is het instellen en gebruiken van uw eigen lokale opslagplaats.
Dit kan worden gedaan in een aantal manieren, met inbegrip van:

- Instellen van een lokaal exemplaar van de PowerShell Gallery, met behulp van de [PS particuliere galerie project](https://github.com/PowerShell/PSPrivateGallery) in Github. Dit project preview kunt u een exemplaar van de PowerShell-galerie die u kunt beheren en het gebruik voor de tests uitgevoerd.
- Instellen van een [interne Nuget opslagplaats](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/). Dit is vereist meer werk om in te stellen, maar heeft het voordeel van de validatie van enkele meer van de vereisten, met name valideren gebruik van een API-sleutel en -of afhankelijkheden aanwezig zijn in de doel-wanneer u publiceert.
- Een bestandsshare instellen als de test 'opslagplaats'. Dit is eenvoudig om in te stellen, maar omdat dit een bestandsshare, de hierboven aangegeven validaties wordt niet plaatsvinden. Een mogelijke voordeel is in dit geval dat de bestandsshare controleert niet of de API-sleutel (vereist), zodat u kunt dezelfde sleutel u wilt publiceren naar de PowerShell Gallery.

Met een van deze oplossingen, Register-PSRepository te gebruiken voor het definiëren van een nieuwe '-opslagplaats', die u in de - eigenschap van de opslagplaats voor Publish-Module.

Één aanvullende punt over test publiceren: een pakket dat u naar de PowerShell Gallery publiceert kan niet worden verwijderd zonder hulp van het operationele team, die bevestigen zal dat er niets is afhankelijk van het pakket dat u wilt publiceren.
Om die reden we bieden geen ondersteuning voor de PowerShell Gallery als een doel voor testen en neemt contact met een willekeurige uitgever die doet.

## <a name="use-powershellget-to-publish"></a>PowerShellGet gebruiken om te publiceren

Het is raadzaam dat uitgevers de cmdlets Publish-Module en Publish-Script gebruiken bij het werken met de PowerShell Gallery.
PowerShellGet is gemaakt om te voorkomen dat belangrijke informatie over het installeren van en publiceren naar de PowerShell Gallery onthouden.
Soms kunnen hebt uitgevers PowerShellGet overslaan en de NuGet-client of PackageManagement-cmdlets gebruiken in plaats van publiceren-Module.
Er zijn een aantal aspecten die eenvoudig gemist worden, wat tot een verscheidenheid aan aanvragen voor ondersteuning leidt.

Als er een reden is dat u Publish-Module of Publish-Script niet gebruiken, laat het ons weten.
Bestand is een probleem in de PowerShellGet-GitHub-opslagplaats en geef de details die ertoe leiden dat u om NuGet of PackageManagement te kiezen.

## <a name="recommended-workflow"></a>Aanbevolen workflow

De meest succesvolle benadering die we hebben gevonden voor pakketten die zijn gepubliceerd naar de PowerShell Gallery is als volgt:

- Eerste-ontwikkeling in moet een de site van een open source-project. Het PowerShell-Team maakt gebruik van Github.
- Gebruik van feedback van de revisoren en [Powershell-Script Analyzer](https://aka.ms/psscriptanalyzer) om op te halen van de code naar een stabiele status
- Documentatie, bevatten, zodat anderen weten hoe u uw werk
- Test de publishing actie uitgevoerd met een lokale opslagplaats.
- Een stabiele of Alpha-release publiceren naar de PowerShell Gallery, zorg ervoor dat u de documentatie en een koppeling naar de projectsite van uw
- Verzamelen van feedback en herhalen op de code in uw project-site en vervolgens stabiel updates publiceren naar de PowerShell Gallery
- Voorbeelden en Pester tests in de module en uw project toevoegen
- Beslissen of u om code te wilt ondertekenen van uw pakket
- Als u denkt het project is klaar dat voor gebruik in een productieomgeving, publiceert u een 1.0.0 versie naar de PowerShell Gallery
- Doorgaan met het verzamelen van feedback en herhalen op uw code op basis van de invoer van de gebruiker
