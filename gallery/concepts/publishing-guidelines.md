---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
description: Richtlijnen voor uitgevers
title: PowerShell-galerie publiceren richtlijnen en aanbevolen procedures
ms.openlocfilehash: 64c3d607b13dce64f70f138fdee849e5baaf85df
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265566"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>PowerShellGallery publiceren richtlijnen en aanbevolen procedures

Dit onderwerp beschrijft aanbevolen stappen die worden gebruikt door de Microsoft-teams zodat de pakketten die zijn gepubliceerd naar de PowerShell-galerie algemeen wordt vastgesteld en hoge waarde bieden aan gebruikers, op basis van hoe de PowerShell-galerie manifest gegevens verwerkt en feedback van grote het aantal gebruikers van de PowerShell-galerie.
Pakketten die zijn gepubliceerd in deze richtlijnen wordt vaker worden geïnstalleerd, wordt vertrouwd, en trekt meer gebruikers.

Hieronder volgen richtlijnen voor wat een goede PowerShell Gallery-pakket, welke optionele Manifest instellingen zijn zeer belangrijk uw code met feedback van de eerste revisoren verbetering maakt en [Powershell Script Analyzer](https://aka.ms/psscriptanalyzer), versiebeheer uw module, documentatie, tests en voorbeelden voor het gebruik van wat u hebt gedeeld.
Veel van deze documentatie volgt de richtlijnen voor publicatie [Resource Modules van hoge kwaliteit DSC](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Zie voor het mechanisme van publicatie van een pakket naar de PowerShell-galerie [maken en publiceren van een pakket](/powershell/gallery/how-to/publishing-packages/publishing-a-package).

Feedback over deze richtlijnen wordt verwelkomde. Als u feedback hebt, opent u problemen in onze [Github-opslagplaats voor documentatie](https://github.com/powershell/powershell-docs/issues).

## <a name="best-practices-for-publishing-packages"></a>Aanbevolen procedures voor het publiceren van pakketten

De volgende best practices zijn wat de gebruikers van de PowerShell-galerie-items zeggen is belangrijk en staan in volgorde van prioriteit nominaal.
Pakketten die aan deze richtlijnen voldoet waarschijnlijk veel meer worden gedownload en door anderen zijn vastgesteld.

- Use PSScriptAnalyzer
- Documentatie en voorbeelden opnemen
- Reageren op feedback worden
- Modules in plaats van scripts opgeven
- Bevatten koppelingen naar een site
- Label van het pakket met de compatibel PSEdition(s) en platforms 
- Tests met uw modules bevatten
- Opnemen en/of de koppeling licentievoorwaarden
- Meld u aan uw code
- Ga als volgt [SemVer](http://semver.org/) richtlijnen voor het versiebeheer
- Gebruik van veelgebruikte tags, zoals beschreven in de galerie voor algemene PowerShell-codes
- Test publiceren met behulp van een lokale opslagplaats
- PowerShellGet gebruiken om te publiceren

Elk van deze wordt kort beschreven in de onderstaande secties.

## <a name="use-psscriptanalyzer"></a>Use PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) is een gratis statische code analysis-hulpprogramma dat werkt met PowerShell-code.
PSScriptAnalyzer wordt de meest voorkomende problemen gezien in de PowerShell-code en vaak een aanbeveling voor het oplossen van het probleem te identificeren.
Het hulpprogramma is eenvoudig te gebruiken en de problemen als fouten categoriseert (ernstig, moeten worden opgelost), waarschuwing (moeten worden beoordeeld & moet worden opgelost), en informatie (waard voor aanbevolen procedures).
Alle pakketten die zijn gepubliceerd naar de PowerShell-galerie worden gescand met PSScriptAnalyzer en eventuele fouten wordt gemeld aan de eigenaar en moeten worden opgelost.

De aanbevolen procedure is het uitvoeren van `Invoke-ScriptAnalyzer` met `-Recurse` en `-Severity` waarschuwing.

Bekijk de resultaten en zorg ervoor dat:

- Alle fouten zijn gecorrigeerd of in de documentatie van uw verholpen
- Alle waarschuwingen zijn gecontroleerd en verholpen, indien van toepassing

Gebruikers die pakketten van de PowerShell Gallery verkrijgen wordt dringend aangeraden PSScriptAnalyzer uitvoeren en evalueren van alle fouten en waarschuwingen.
Gebruikers worden doorgaans contact op met de eigenaren van het pakket als ze ziet dat er een fout gerapporteerd door PSScriptAnalyzer.
Als er een goede reden voor het pakket te houden van code die is gemarkeerd als een fout, moet u die informatie toevoegen aan de documentatie om te voorkomen dat dezelfde vraag worden beantwoord vaak.

## <a name="include-documentation-and-examples"></a>Documentatie en voorbeelden opnemen

Documentatie en voorbeelden worden de beste manier om te controleren of gebruikers kunnen profiteren van een gedeelde-code.

Documentatie is het nuttigst wat moeten worden opgenomen in de pakketten die worden gepubliceerd naar de PowerShell-galerie.
Gebruikers wordt pakketten zonder documentatie over het algemeen omzeilen, zoals het alternatief is om te lezen van de code om te begrijpen wat het pakket is en het gebruik ervan.
Er zijn verschillende artikelen over het verstrekken van documentatie met PowerShell-pakketten, waaronder:

- Richtlijnen voor het ontwikkelen van help zijn [Cmdlet helpen schrijven](https://go.microsoft.com/fwlink/?LinkID=123415)
- Maken van de help van cmdlet, dit is de beste manier om een PowerShell-script, functie of cmdlet.
  Voor informatie over het maken van de help van cmdlet beginnen met [schrijven Cmdlet helpen](https://go.microsoft.com/fwlink/?LinkID=123415).
  Zie het Help-informatie in een script toevoegen [opmerking op basis van Help over](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).
- Veel modules ook documentatie in tekstindeling zoals MarkDown-bestanden.
  Dit is vooral handig zijn wanneer er een site in Github, waar Markdown een intensief gebruikte indeling is.
  De aanbevolen procedure is het gebruik van [Markdown met een vleugje Github](https://help.github.com/categories/writing-on-github/)

Enkele voorbeelden van gebruikers hoe het pakket is bedoeld om te worden gebruikt.
Veel ontwikkelaars dicteert dat ze voorbeelden voordat documentatie om te begrijpen hoe gebruikmaken van iets bekijken.
Het aanbevolen type voorbeelden tonen basisgebruik, plus een gesimuleerde realistische gebruiksvoorbeeld en de code is goed opmerkingen.
Voorbeelden voor modules die zijn gepubliceerd naar de PowerShell-galerie moeten zich in een map van de voorbeelden in de hoofdmap van de module.

Een goede patroon voor voorbeelden vindt u in de [PSDscResource module](https://www.powershellgallery.com/packages/PSDscResources) onder de map Examples\RegistryResource.
Er zijn vier voorbeeld gebruiksvoorbeelden met een korte beschrijving boven aan elk bestand dat documenten wat wordt wordt gedemonstreerd.

## <a name="respond-to-feedback"></a>Reageren op feedback

De waarde van pakket eigenaars die goed op feedback reageren wordt zeer door de community.
Gebruikers die feedback geven feitelijke zijn belangrijk om te reageren op, zoals ze geïnteresseerd in het pakket zijn om te helpen verbeteren.

Er zijn twee methoden voor feedback beschikbaar in de galerie met PowerShell:

- Neem contact op met de eigenaar: Dit kan een gebruiker een e-mailbericht verzenden naar de eigenaar van het pakket. Als de eigenaar van een pakket, is het belangrijk om te controleren van het e-mailadres gebruikt met de PowerShell Gallery-pakketten en reageren op problemen die worden gegenereerd. Een nadeel van deze methode is dat alleen de gebruiker en de eigenaar ooit de communicatie, ziet zodat de eigenaar hebben kan om deze vraag te beantwoorden vaak.
- Opmerkingen: Pagina is aan de onderkant van het pakket een opmerkingenveld.
  Het voordeel van dit systeem is dat andere gebruikers kunnen zien de opmerkingen en reacties, waardoor het aantal keren dat een enkele vraag moet worden beantwoord.
  Als de eigenaar van een pakket wordt aanbevolen dat u de opmerkingen voor elk pakket volgt.
Zie [Feedback geven via sociale Media of opmerkingen](../how-to/working-with-packages/social-media-feedback.md) voor meer informatie over hoe u dat doet.

Zijn eigenaars die constructively op feedback reageren op prijs gesteld door de community.
De mogelijkheid gebruik in het rapport voor het aanvragen van meer informatie, indien nodig, bieden een tijdelijke oplossing of identificeren als een update wordt een probleem opgelost.

Als er ongeschikte gedrag van een van deze communicatiekanalen in acht genomen, moet u de functie rapport misbruik van de PowerShell-galerie gebruiken om het contact opnemen met de beheerders-galerie.

## <a name="modules-versus-scripts"></a>Modules Versus Scripts

Een script te delen met andere gebruikers is een goede en biedt andere voorbeelden van hoe ze hebben wellicht problemen op te lossen.
Het probleem is dat de scripts in de PowerShell-galerie één bestanden zonder afzonderlijke documentatie, voorbeelden en tests.

PowerShell-Modules hebben een mapstructuur waarmee meerdere mappen en bestanden die moeten worden opgenomen in het pakket.
Structuur van de module kunt u met inbegrip van de andere pakketten die wij in de lijst als best practices: cmdlet help, documentatie, voorbeelden en tests.
Het grootste nadeel is dat een script in een module moet worden weergegeven en als een functie gebruikt.
Zie voor meer informatie over het maken van een module [een Windows PowerShell-Module schrijven](http://go.microsoft.com/fwlink/?LinkId=144916).

Zijn er situaties waarin een script zorgt voor een betere ervaring voor de gebruiker, met name met DSC-configuraties.
Er is de aanbevolen procedure voor DSC-configuraties voor het publiceren van de configuratie als een script met een bijbehorende module met de documenten, voorbeelden en tests.
Het script geeft een lijst van de bijbehorende module met behulp van RequiredModules = @(naam van de Module).
Deze methode kan worden gebruikt bij elk script.

Zelfstandige scripts die Volg de aanbevolen procedures bieden de feitelijke waarde aan andere gebruikers.
Mits documentatie op basis van een opmerking en een koppeling naar een Site nadrukkelijk aanbevolen zijn bij het publiceren van een script naar de PowerShell-galerie.

## <a name="provide-a-link-to-a-project-site"></a>Een koppeling naar een site opgeven

Een Site-Project is waar een uitgever kan communiceren rechtstreeks met de gebruikers met hun PowerShell Gallery-pakketten.
Gebruikers liever pakketten die bieden, zoals het kan ze eenvoudiger voor informatie over het pakket.
Veel pakketten in de PowerShell-galerie in GitHub worden ontwikkeld, worden andere geleverd door organisaties met een speciale website.
Elk van deze worden site voor een beschouwd.

Een koppeling toe te voegen, wordt dit gedaan door ProjectURI als volgt in de sectie PSData van het manifest, waaronder:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

Wanneer een ProjectURI is opgegeven, wordt de PowerShell-galerie bevat een koppeling naar de Site van het Project aan de linkerkant van de pakketpagina.

## <a name="tag-your-package-with-the-compatible-pseditions-and-platforms"></a>Label van het pakket met de compatibel PSEdition(s) en platforms 

De volgende codes gebruiken om aan te tonen aan gebruikers die pakketten goed met hun omgeving werkt:

- PSEdition_Desktop: Pakketten die compatibel met Windows PowerShell zijn 
- PSEdition_Core: Pakketten die compatibel met Powershell Core zijn 
- Windows : Pakketten die compatibel zijn met het Windows-besturingssysteem
- Linux: Pakketten die compatibel zijn met het Linux-besturingssystemen 
- Mac OS: Pakketten die compatibel zijn met het Mac-besturingssysteem

## <a name="include-tests"></a>Tests opnemen

Het is belangrijk dat gebruikers, met inbegrip van tests met open source code als u deze zekerheid krijgt over wat u valideren en bevat informatie over de werking van uw code. Ook kunnen gebruikers zodat ze niet de functionaliteit van uw oorspronkelijke opsplitsen als ze de code aanpassen aan hun omgeving aanpassen.

Het is raadzaam dat de tests worden geschreven om te profiteren van het kader van de test Pester, waarbij heeft is speciaal ontworpen voor PowerShell.
Lastige is beschikbaar in [GitHub](https://github.com/Pester/Pester), wordt de [PowerShell Gallery](https://www.powershellgallery.com/packages/Pester/), en wordt in Windows 10, Windows Server 2016, WMF 5.0 en WMF 5.1 wordt geleverd.

De [Pester project-site in GitHub](https://github.com/Pester/Pester) omvat goede documentatie over het schrijven van Pester tests uit aan de slag aan aanbevolen procedures.

De doelen voor de dekking van de test worden specifiek genoemd de [Bronmodule van hoge kwaliteit documentatie](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), testen met 70% eenheid code dekking aanbevolen.

## <a name="include-andor-link-to-license-terms"></a>Opnemen en/of de koppeling licentievoorwaarden

Alle pakketten die zijn gepubliceerd naar de PowerShell-galerie moet de licentievoorwaarden opgeven of gebonden aan de licentie die is opgenomen in de [gebruiksvoorwaarden](https://www.powershellgallery.com/policies/Terms) onder "Vertonen A".
De aanbevolen aanpak voor het opgeven van een andere licentie wordt een koppeling naar de licentie die met behulp van de LicenseURI in PSData.
In het Manifest velden aanbevolen-onderwerp vindt u een voorbeeld.

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Meld u aan uw code

Ondertekening van programmacode voorziet gebruikers van het hoogste niveau van zekerheid voor die het pakket hebt gepubliceerd, en dat de kopie van de code ze verkrijgen is precies wat de uitgever uitgebracht.
Zie voor meer informatie over het algemeen voor ondertekening van programmacode, [Inleiding tot de ondertekening van programmacode](http://go.microsoft.com/fwlink/?LinkId=106296).
PowerShell ondersteunt validatie van via twee primaire benaderingen voor ondertekening van programmacode:

- Ondertekening scriptbestanden
- Een module voor het ondertekenen van catalogus

Ondertekening van bestanden met PowerShell is een goed tot stand gebrachte aanpak om ervoor te zorgen dat de code wordt uitgevoerd is geproduceerd door een betrouwbare bron en is niet gewijzigd.
Meer informatie over het ondertekenen van PowerShell-scriptbestanden wordt beschreven in de [over ondertekening](/powershell/module/microsoft.powershell.core/about/about_signing) onderwerp.
Bij overzicht kan een handtekening worden toegevoegd aan een. Ps1-bestand dat PowerShell valideert wanneer het script wordt geladen.
PowerShell worden beperkt met behulp van de [uitvoeringsbeleid](/powershell/module/microsoft.powershell.core/about/about_execution_policies) -cmdlets voor het gebruik van ondertekende scripts.

Catalogus modules ondertekening is een functie die is toegevoegd aan PowerShell in versie 5.1.
Het ondertekenen van een module wordt beschreven in de [catalogus Cmdlets](/powershell/wmf/5.1/catalog-cmdlets) onderwerp.
Bij overzicht wordt ondertekening van de catalogus gedaan door het maken van een catalogusbestand waarin een hash-waarde voor elk bestand in de module, en vervolgens ondertekent dat bestand.
De PowerShellGet publiceren-module, installatie-module opslaan-module en update-module-cmdlets wordt controleren van de handtekening om ervoor te zorgen dat geldig is en bevestig vervolgens de hash-waarde voor elk pakket overeenkomt met wat is er in de catalogus.
Als een eerdere versie van de module is geïnstalleerd op het systeem, bevestigt installatie-module dat de instantie voor het ondertekenen van voor de nieuwe versie overeenkomt met wat eerder is geïnstalleerd.
Catalogus ondertekening werkt met, maar er is geen vervanging voor ondertekening scriptbestanden. PowerShell worden handtekeningen van de catalogus niet gevalideerd tijdens het laden van een module.

## <a name="follow-semver-guidelines-for-versioning"></a>Volg de richtlijnen SemVer voor versiebeheer

[SemVer](http://semver.org/) is een openbare conventie die wordt beschreven hoe u de structuur en wijzigt u een versie zodat u eenvoudig intepretation van wijzigingen.
De versie voor het pakket moet zijn opgenomen in de manifest-gegevens.

- De versie moet worden gestructureerd als 3 numerieke blokken gescheiden door punten, zoals in 0.1.1 of 4.11.192
- Beginnen met '0' versies erop wijzen dat het pakket nog niet klaar productie is, en het eerste nummer alleen met '0' beginnen moet als dit het enige dat wordt gebruikt
- Wijzigingen in het eerste nummer (1.9.9999-2.0.0) geven aan de primaire en breken wijzigingen tussen de versies
- Wijzigingen in het tweede getal (1.1-1.2) geven functieniveau wijzigingen, zoals het toevoegen van nieuwe cmdlets naar een module
- Wijzigingen in het derde getal geven vaste wijzigingen, zoals nieuwe parameters, bijgewerkte voorbeelden of nieuwe tests
- Bij het weergeven van versies worden PowerShell de versies gesorteerd als tekenreeksen, dus 1.01.0 wordt beschouwd als groter is dan 1.001.0

PowerShell is gemaakt voordat SemVer is gepubliceerd, dus deze ondersteuning voor de meeste, maar niet alle elementen van SemVer, speciaal biedt:

- Prerelease tekenreeksen worden niet ondersteund in versienummers. Dit is handig wanneer een uitgever wil een preview-versie van een nieuwe primaire versie na het opgeven van een versie 1.0.0 leveren. Dit wordt ondersteund in een toekomstige versie van de PowerShell-galerie en PowerShellGet-cmdlets.
- Toestaan dat versietekenreeksen met 1, 2 en 4 segmenten PowerShell en de PowerShell-galerie. Veel vroege modules niet de richtlijnen hebt gevolgd en versies van het product van Microsoft build informatie zoals een 4th blokkeren van de getallen (bijvoorbeeld 5.1.14393.1066) bevatten. Een verwerkt versioning worden deze verschillen genegeerd.

## <a name="test-using-a-local-repository"></a>Testen met behulp van een lokale opslagplaats

De PowerShell-galerie, is niet ontworpen om te worden van een doel voor het testen van het publicatieproces.
De beste manier om het testen van het end-to-end-proces van publiceren naar de PowerShell-galerie is het instellen en gebruiken van uw eigen lokale opslagplaats.
Dit kan gebeuren in een aantal manieren, met inbegrip van:

- Een lokaal exemplaar van de PowerShell Gallery instellen met behulp van de [PS persoonlijke galerie project](https://github.com/PowerShell/PSPrivateGallery) in Github. Deze preview-project kunt u een exemplaar van de PowerShell-galerie die u kunt beheren en deze gebruiken voor uw tests instellen.
- Instellen van een [interne Nuget-opslagplaats](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/). Dit is vereist meer werk om in te stellen, maar heeft het voordeel van het valideren van een paar meer van de vereisten, met name valideren gebruik van een API-sleutel en het al dan niet afhankelijkheden aanwezig zijn in de doel-wanneer u publiceert.
- Een bestandsshare instellen als de test 'opslagplaats'. Dit is eenvoudig te installeren, maar omdat het een bestandsshare, de hierboven beschreven validaties zal niet plaatsvinden. Een van de mogelijke voordelen is in dit geval dat de bestandsshare wordt niet gecontroleerd voor de API-sleutel (vereist), zodat u kunt dezelfde sleutel u zou doen om te publiceren naar de PowerShell-galerie.

Met elk van deze oplossingen kunt registreren PSRepository te gebruiken voor het definiëren van een nieuwe 'opslagplaats', waarmee u in de - eigenschap van de opslagplaats voor publiceren-Module.

Een extra contactpunt over test publiceren: een pakket dat u naar de PowerShell-galerie publiceren kan niet worden verwijderd zonder hulp van het operationele team, die wordt bevestigd dat er is niets is afhankelijk van het pakket dat u wilt publiceren.
Om die reden we bieden geen ondersteuning voor de PowerShell-galerie als doel testen en neemt contact met een willekeurige uitgever die doet.

## <a name="use-powershellget-to-publish"></a>PowerShellGet gebruiken om te publiceren

Het is raadzaam dat uitgevers van de cmdlets Publish-Module en Publish-Script gebruiken wanneer u werkt met de PowerShell-galerie.
PowerShellGet is gemaakt om te helpen u belangrijke informatie over het installeren van en publiceren naar de PowerShell-galerie onthouden voorkomen.
Soms hebt uitgevers PowerShellGet overslaan en de NuGet-client of PackageManagement-cmdlets gebruiken in plaats van publiceren-Module.
Er zijn een aantal details die gemakkelijk worden gemist, wat tot een aantal aanvragen voor ondersteuning leidt.

Als er een reden is dat u kunt publiceren-Module of publiceren Script gebruiken, laat ons weten.
Bestand is een probleem in de PowerShellGet GitHub-repo en geef de details die ertoe leiden dat u NuGet of PackageManagement kiezen.

## <a name="recommended-workflow"></a>Aanbevolen workflow

De meest succesvolle aanpak die we hebben gevonden voor pakketten die worden gepubliceerd naar de PowerShell-galerie is als volgt:

- Eerste-ontwikkeling in een een open source-project-site. Het PowerShell-Team gebruik maakt van Github.
- Gebruik van feedback van de revisoren en [Powershell Script Analyzer](https://aka.ms/psscriptanalyzer) ophalen van de code naar een stabiele status
- Documentatie, bevatten zodat anderen weten hoe u uw werk gebruikt
- Test de publishing uitgevoerd met behulp van een lokale opslagplaats.
- Een stabiele of alfa-release publiceren naar de PowerShell-galerie, zorg ervoor dat u de documentatie en een koppeling naar de projectsite van uw
- Feedback verzamelen en stabiele updates publiceren naar de PowerShell-galerie herhalen op de code in uw projectsite
- Voorbeelden en Pester tests in uw project en uw module toevoegen
- Bepalen of u code wilt ondertekenen van uw pakket
- Als u denkt het project is klaar dat voor gebruik in een productieomgeving, een 1.0.0 publiceert de versie van de PowerShell-galerie
- Blijven feedback verzamelen en uw code op basis van gebruikersinvoer herhalen

