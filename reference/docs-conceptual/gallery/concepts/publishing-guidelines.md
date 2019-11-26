---
ms.date: 06/12/2017
contributor: JKeithB, SydneyhSmith
keywords: Galerie, Power shell, cmdlet, psgallery
description: Richt lijnen voor uitgevers
title: Richt lijnen voor publicatie PowerShell Gallery en aanbevolen procedures
ms.openlocfilehash: 9047e938ab961c68e225c9029e52403c40afbe26
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417685"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>Richt lijnen voor publicatie van PowerShellGallery en aanbevolen procedures

In dit artikel worden de aanbevolen stappen beschreven die door micro soft-teams worden gebruikt om ervoor te zorgen dat de pakketten die zijn gepubliceerd op de PowerShell Gallery, algemeen worden goedgekeurd en hoge waarde bieden aan gebruikers, op basis van de manier waarop de PowerShell Gallery manifest gegevens en feedback van grote aantal PowerShell Gallery gebruikers. Pakketten die worden gepubliceerd na deze richt lijnen zullen waarschijnlijker worden geïnstalleerd, vertrouwd en aantrekken meer gebruikers.

Hieronder vindt u richt lijnen voor wat een goed PowerShell Gallery pakket is, welke optionele manifest instellingen het belangrijkst zijn, hoe u uw code kunt verbeteren met feedback van de eerste revisoren en [Power shell script Analyzer](https://aka.ms/psscriptanalyzer), versie beheer van uw module, Documentatie, tests en voor beelden voor het gebruik van wat u hebt gedeeld. Veel van deze documentatie volgt de richt lijnen voor het publiceren van [DSC-resource modules van hoge kwaliteit](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Zie [een pakket maken en publiceren](../how-to/publishing-packages/publishing-a-package.md)voor de mechanismen voor het publiceren van een pakket naar de PowerShell Gallery.

Feedback over deze richt lijnen is welkom. Als u feedback hebt, kunt u problemen openen in onze [documentatie opslagplaats voor github](https://github.com/powershell/powershell-docs/issues).

## <a name="best-practices-for-publishing-packages"></a>Aanbevolen procedures voor het publiceren van pakketten

De volgende aanbevolen procedures zijn wat de gebruikers van PowerShell Gallery-items betekenen, en worden vermeld in de volg orde nominale prioriteit. Pakketten die voldoen aan deze richt lijnen, worden waarschijnlijk veel vaker gedownload en goedgekeurd door anderen.

- PSScriptAnalyzer gebruiken
- Documentatie en voor beelden toevoegen
- Reageren op feedback
- Geef modules op in plaats van scripts
- Koppelingen naar een project site opgeven
- Voorzie uw pakket van de compatibele PSEdition (s) en platforms
- Testen toevoegen aan uw modules
- Toevoegen en/of koppelen aan licentie voorwaarden
- Uw code ondertekenen
- Volg de [SemVer](https://semver.org/) -richt lijnen voor versie beheer
- Algemene Tags gebruiken, zoals beschreven in algemene PowerShell Gallery Tags
- Publicatie testen met een lokale opslag plaats
- PowerShellGet gebruiken om te publiceren

Elk van deze wordt kort beschreven in de onderstaande secties.

## <a name="use-psscriptanalyzer"></a>PSScriptAnalyzer gebruiken

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) is een gratis hulp programma voor statische code analyse dat kan worden uitgevoerd op Power shell-code. **PSScriptAnalyzer** identificeert de meest voorkomende problemen die in Power shell-code worden weer gegeven en vaak een aanbeveling om het probleem op te lossen. Het hulp programma is eenvoudig te gebruiken en categoriseert de problemen als fouten (ernstig, moeten worden geadresseerd), waarschuwing (moet worden gecontroleerd en moet worden opgelost) en informatie (voor aanbevolen procedures wordt uitgecheckt). Alle pakketten die naar het PowerShell Gallery worden gepubliceerd, worden gescand met **PSScriptAnalyzer**en eventuele fouten worden weer gegeven aan de eigenaar en moeten worden verholpen.

Het best practice moet `Invoke-ScriptAnalyzer` uitvoeren met `-Recurse` en `-Severity` waarschuwing.

Bekijk de resultaten en zorg ervoor dat:

- Alle fouten worden gecorrigeerd of behandeld in de documentatie.
- Alle waarschuwingen worden beoordeeld en zo nodig opgelost.

Gebruikers die pakketten downloaden van de PowerShell Gallery worden ten zeerste aanbevolen om **PSScriptAnalyzer** uit te voeren en alle fouten en waarschuwingen te evalueren. Gebruikers zijn zeer waarschijnlijk contact met pakket eigen aars als ze zien dat er een fout is gemeld door **PSScriptAnalyzer**. Als er een goede reden voor uw pakket is om code te houden die als een fout wordt gemarkeerd, voegt u die informatie toe aan uw documentatie om te voor komen dat u dezelfde vraag meermaals beantwoordt.

## <a name="include-documentation-and-examples"></a>Documentatie en voor beelden toevoegen

Documentatie en voor beelden zijn de beste manier om ervoor te zorgen dat gebruikers gebruik kunnen maken van gedeelde code.

Documentatie is het nuttigst voor het toevoegen van pakketten die zijn gepubliceerd op de PowerShell Gallery.
Gebruikers zullen pakketten zonder documentatie overs Laan, omdat het alternatief is om de code te lezen om te begrijpen wat het pakket is en hoe het kan worden gebruikt. Er zijn verschillende artikelen beschikbaar over het bieden van documentatie met Power shell-pakketten, waaronder:

- Richt lijnen voor het leveren van Help-informatie [over het schrijven van cmdlets](https://go.microsoft.com/fwlink/?LinkID=123415).
- Help voor cmdlets maken: dit is de beste benadering voor elke Power shell-script,-functie of-cmdlet.
  Voor informatie over het maken van Help voor cmdlets, begint u met [het schrijven van Help voor cmdlets](https://go.microsoft.com/fwlink/?LinkID=123415).
  Zie [informatie over op opmerkingen gebaseerde Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)als u hulp wilt toevoegen in een script.
- Veel modules bevatten ook documentatie in tekst indeling, zoals bestanden voor de korting. Dit kan bijzonder nuttig zijn wanneer er sprake is van een project site in GitHub, waarbij prijs verlaging een intensief gebruikte indeling is. De best practice is het gebruik van [GitHube prijs verlaging](https://help.github.com/categories/writing-on-github/).

Voor beelden laten zien gebruikers hoe het pakket is bedoeld om te worden gebruikt. Veel ontwikkel aars zeggen dat ze voor beelden bekijken voordat ze worden gebruikt om te begrijpen hoe ik iets kan gebruiken. De beste typen voor beelden tonen het basis gebruik, plus een gesimuleerde realistische use-case, en de code is goed commentaar. Voor beelden van modules die naar het PowerShell Gallery worden gepubliceerd, moeten zich in een map met voor beelden in de module root bevindt.

Een goed patroon voor voor beelden vindt u in de [module PSDscResource](https://www.powershellgallery.com/packages/PSDscResources) in de map `Examples\RegistryResource`. Er zijn vier voorbeeld cases met een korte beschrijving boven aan elk bestand dat documenteert wat wordt aangetoond.

## <a name="manage-dependencies"></a>Afhankelijkheden beheren

Het is belang rijk om modules op te geven waarvan uw module afhankelijk is in het module manifest. Hierdoor hoeft de eind gebruiker zich geen zorgen te maken over het installeren van de juiste versies van de modules waarvan u afhankelijk bent. Als u afhankelijke modules wilt opgeven, moet u het vereiste module veld gebruiken in het module manifest. Hiermee worden alle vermelde modules in de globale omgeving geladen voordat de module wordt geïmporteerd, tenzij ze al zijn geladen. Sommige modules kunnen bijvoorbeeld al zijn geladen door een andere module. Het is ook mogelijk om een specifieke versie op te geven die moet worden geladen met behulp van het veld **RequiredVersion** in plaats van het veld **ModuleVersion** . Wanneer u **ModuleVersion**gebruikt, wordt de nieuwste versie geladen die beschikbaar is met een minimum van de opgegeven versie. Als u het veld **RequiredVersion** niet gebruikt om een specifieke versie op te geven, is het belang rijk om versie-updates te controleren naar de vereiste module. Het is vooral belang rijk dat u op de hoogte bent van eventuele wijzigingen die van invloed kunnen zijn op de gebruikers ervaring met uw module.

```powershell
Example: RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})

Example: RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})
```

## <a name="respond-to-feedback"></a>Reageren op feedback

Pakket eigen aars die op de juiste manier reageren op feedback, zijn zeer waard door de community. Gebruikers die feitelijke feedback bieden, zijn belang rijk om te reageren op, aangezien ze voldoende zijn in het pakket om het te helpen verbeteren.

Er zijn twee feedback methoden beschikbaar in de PowerShell Gallery:

- Eigenaar van contact persoon: Hiermee kan een gebruiker een e-mail verzenden naar de eigenaar van het pakket. Als pakket eigenaar is het belang rijk om het e-mail adres dat wordt gebruikt met de PowerShell Gallery-pakketten te controleren en te reageren op problemen die zijn opgetreden. Het enige nadeel van deze methode is dat alleen de gebruiker en de eigenaar ooit de communicatie kunnen zien, zodat de eigenaar mogelijk dezelfde vraag meermaals moet beantwoorden.
- Opmerkingen: aan de onderkant van de pakket pagina is een **opmerkings** veld. Het voor deel van dit systeem is dat andere gebruikers de opmerkingen en reacties kunnen zien, waardoor het aantal keren dat een enkele vraag moet worden beantwoord, kleiner wordt. Als pakket eigenaar wordt u ten zeerste aangeraden de opmerkingen voor elk pakket te volgen. Zie [feedback geven via sociale media of opmerkingen](../how-to/working-with-packages/social-media-feedback.md) voor meer informatie over hoe u dit doet.

Eigen aren die reageren op feedback constructively worden door de Community gewaardeerd. Gebruik de verkoop kans in het rapport om meer informatie aan te vragen. Als dat nodig is, kunt u een tijdelijke oplossing opgeven of vaststellen of een update een probleem corrigeert.

Als er ongepast gedrag wordt waargenomen vanuit een van deze communicatie kanalen, gebruikt u de functie misbruik melden van de PowerShell Gallery om contact op te nemen met de beheerder van de galerie.

## <a name="modules-versus-scripts"></a>Modules versus scripts

Het delen van een script met andere gebruikers is geweldig en biedt andere voor beelden van het oplossen van problemen die ze kunnen hebben. Het probleem is dat scripts in de PowerShell Gallery één bestand zijn zonder afzonderlijke documentatie, voor beelden en tests.

Power shell-modules hebben een mapstructuur waarmee meerdere mappen en bestanden kunnen worden opgenomen in het pakket. De structuur van de module maakt het mogelijk om de andere pakketten te gebruiken die we als best practices aanbieden: cmdlet Help, Documentatie, voor beelden en tests. Het grootste nadeel is dat een script in een module moet worden weer gegeven en gebruikt als een functie. Zie [een Windows Power shell-module schrijven](/powershell/scripting/developer/module/writing-a-windows-powershell-module)voor meer informatie over het maken van een module.

Er zijn situaties waarin een script een betere ervaring biedt voor de gebruiker, met name met DSC-configuraties. De best practice voor DSC-configuraties is het publiceren van de configuratie als een script met een bijbehorende module die de docs, voor beelden en tests bevat. Het script bevat een lijst met de bijbehorende module met behulp van `RequiredModules = @(Name of the Module)`. Deze aanpak kan worden gebruikt met elk script.

Zelfstandige scripts die de andere aanbevolen procedures volgen, bieden echte waarde aan andere gebruikers. Het is raadzaam om op opmerkingen gebaseerde documentatie en een koppeling naar een project site te bieden bij het publiceren van een script naar de PowerShell Gallery.

## <a name="provide-a-link-to-a-project-site"></a>Een koppeling naar een project site opgeven

Een project site is waar een uitgever rechtstreeks kan communiceren met de gebruikers van hun PowerShell Gallery-pakketten. Gebruikers geven de voor keur aan pakketten die dit leveren, omdat ze hiermee gemakkelijker informatie over het pakket kunnen ophalen. Veel pakketten in de PowerShell Gallery zijn ontwikkeld in GitHub, maar andere worden door organisaties voorzien van een specifieke webhost. Elk van deze kan worden beschouwd als een project site.

Het toevoegen van een koppeling wordt uitgevoerd door ProjectURI in het gedeelte PSData van het manifest als volgt op te nemen:

```
  # A URL to the main website for this project.
  ProjectUri = 'https://github.com/powershell/powershell'
```

Wanneer er een ProjectURI wordt gegeven, bevat de PowerShell Gallery een koppeling naar de project site aan de linkerkant van de pakket pagina.

## <a name="tag-your-package-with-the-compatible-pseditions-and-platforms"></a>Voorzie uw pakket van de compatibele PSEdition (s) en platforms

Gebruik de volgende tags om te laten zien welke gebruikers pakketten goed kunnen gebruiken met hun omgeving:

- PSEdition_Desktop: pakketten die compatibel zijn met Windows Power shell
- PSEdition_Core: pakketten die compatibel zijn met Power shell core
- Windows: pakketten die compatibel zijn met het Windows-besturings systeem
- Linux: pakketten die compatibel zijn met Linux-besturings systemen
- MacOS: pakketten die compatibel zijn met het Mac-besturings systeem

Door uw pakket te labelen met de compatibele platform (s), wordt het opgenomen in de galerie Zoek filters in het linkerdeel venster van de zoek resultaten. Als u uw pakket host op GitHub, kunt u, wanneer u uw pakket labelt, ook profiteren van onze [PowerShell Gallery Compatibility shields](https://img.shields.io/powershellgallery/p/:packageName.svg)
![Compatibility Shield](../Images/CosmosDB.svg).

## <a name="include-tests"></a>Tests toevoegen

Het is belang rijk voor gebruikers, met inbegrip van tests met open-source code, dat ze de zekerheid geven over wat u valideert, en biedt informatie over de werking van uw code. Gebruikers kunnen er ook voor zorgen dat ze de oorspronkelijke functionaliteit niet afleiden als ze uw code aanpassen aan hun omgeving.

Het wordt ten zeerste aanbevolen dat tests worden geschreven om te profiteren van het ziekte-test raamwerk dat speciaal is ontworpen voor Power shell. De ziekte is beschikbaar in [github](https://github.com/Pester/Pester), de [PowerShell Gallery](https://www.powershellgallery.com/packages/Pester/), en wordt geleverd in Windows 10, Windows Server 2016, WMF 5,0 en WMF 5,1.

De ondergeschikte [project site in github](https://github.com/Pester/Pester) bevat goede documentatie over het schrijven van ziekte tests, van aan de slag met best practices.

De doelen voor de test dekking worden in de documentatie voor de [resource module met hoge kwaliteit](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md)genoemd, met 70% eenheids test code dekking aanbevolen.

## <a name="include-andor-link-to-license-terms"></a>Toevoegen en/of koppelen aan licentie voorwaarden

Alle pakketten die naar het PowerShell Gallery worden gepubliceerd, moeten de licentie voorwaarden opgeven of gebonden zijn aan de licentie die is opgenomen in de [gebruiks voorwaarden](https://www.powershellgallery.com/policies/Terms) onder **een**. De beste manier om een andere licentie op te geven, is door een koppeling naar de licentie te geven met behulp van de **LicenseURI** in **PSData**. Zie voor meer informatie [packages-manifest en Galerie-gebruikers interface](package-manifest-affecting-ui.md).

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Uw code ondertekenen

Het ondertekenen van programma code biedt gebruikers het hoogste garantie niveau voor wie het pakket heeft gepubliceerd, en dat de kopie van de code die ze verwerven precies overeenkomt met de uitgever. Zie [Inleiding tot ondertekening van programma code](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))voor meer informatie over het in het algemeen ondertekenen van programma code.
Power shell ondersteunt validatie van ondertekening van programma code via twee primaire benaderingen:

- Script bestanden ondertekenen
- Catalogus ondertekenen van een module

Het ondertekenen van Power Shell-bestanden is een goed opgebouwde benadering om ervoor te zorgen dat de code die wordt uitgevoerd, is geproduceerd met een betrouw bare bron en niet is gewijzigd. Meer informatie over het ondertekenen van Power shell-script bestanden wordt behandeld in het artikel [over ondertekening](/powershell/module/microsoft.powershell.core/about/about_signing) . In overzicht kan een hand tekening worden toegevoegd aan een `.PS1` bestand dat door Power shell wordt gevalideerd wanneer het script wordt geladen. Power shell kan worden beperkt met behulp van de-cmdlets voor het uitvoeren van het [beleid](/powershell/module/microsoft.powershell.core/about/about_execution_policies) om te zorgen voor het gebruik van ondertekende scripts.

Modules voor catalogus ondertekening is een functie die is toegevoegd aan Power shell in versie 5,1. Het ondertekenen van een module wordt behandeld in het artikel [Catalog-cmdlets](/powershell/scripting/wmf/5.1/catalog-cmdlets) . In overzicht wordt de ondertekening van de catalogus uitgevoerd door een catalogus bestand te maken dat een hash-waarde voor elk bestand in de module bevat en dat bestand vervolgens te ondertekenen.

Met de cmdlets **PowerShellGet** `Publish-Module`, `Install-Module`en `Update-Module` wordt de hand tekening gecontroleerd om te controleren of deze geldig is. Controleer vervolgens of de hash-waarde voor elk pakket overeenkomt met wat er in de catalogus staat. `Save-Module` een hand tekening niet valideren. Als er een eerdere versie van de module op het systeem is geïnstalleerd, wordt in `Install-Module` bevestigd dat de handtekening instantie voor de nieuwe versie overeenkomt met wat eerder is geïnstalleerd. `Install-Module` en `Update-Module` gebruiken de hand tekening voor een `.PSD1` bestand als het pakket niet is ondertekend door een catalogus. Catalogus ondertekening werkt met, maar vervangt geen handtekeningen script bestanden. Power shell valideert catalogus handtekeningen tijdens het laden van de module niet.

## <a name="follow-semver-guidelines-for-versioning"></a>Volg de SemVer-richt lijnen voor versie beheer

[SemVer](https://semver.org/) is een open bare Conventie die beschrijft hoe een versie moet worden gestructureerd en gewijzigd, zodat de wijzigingen eenvoudig kunnen worden geïnterpreteerd. De versie voor uw pakket moet worden opgenomen in de manifest gegevens.

- De versie moet zijn gestructureerd als drie numerieke blokken, gescheiden door punten, zoals in `0.1.1` of `4.11.192`.
- Versies die beginnen met `0` geven aan dat het pakket nog niet gereed is voor productie en dat het eerste nummer alleen begint met `0` als dat het enige getal is dat wordt gebruikt.
- Wijzigingen in het eerste aantal (`1.9.9999` naar `2.0.0`) geven aan dat de versies belang rijk zijn en dat de wijzigingen worden opgesplitst.
- Wijzigingen in het tweede getal (`1.1` naar `1.2`) geven wijzigingen op functie niveau aan, zoals het toevoegen van nieuwe cmdlets aan een module.
- Wijzigingen in het derde nummer wijzen op niet-brekende wijzigingen, zoals nieuwe para meters, bijgewerkte voor beelden of nieuwe tests.
- Wanneer versies worden vermeld, sorteert Power shell de versies als teken reeksen, zodat `1.01.0` worden beschouwd als groter dan `1.001.0`.

Power shell is gemaakt voordat SemVer werd gepubliceerd, waardoor ondersteuning wordt geboden voor de meeste, maar niet alle elementen van SemVer, met name:

- Prerelease-teken reeksen worden niet ondersteund in versie nummers. Dit is handig wanneer een uitgever een preview-versie van een nieuwe primaire versie wil leveren na het leveren van een-`1.0.0`. Dit wordt in een toekomstige versie van de PowerShell Gallery-en **PowerShellGet** -cmdlets ondersteund.
- Power shell en de PowerShell Gallery versie teken reeksen met 1, 2 en 4 segmenten toestaan. Veel vroege modules voldoen niet aan de richt lijnen en de product releases van micro soft bevatten bouw gegevens als een 4e blok cijfers (bijvoorbeeld `5.1.14393.1066`). Vanuit een oogpunt van versie beheer worden deze verschillen genegeerd.

## <a name="test-using-a-local-repository"></a>Testen met een lokale opslag plaats

De PowerShell Gallery is niet ontworpen om een doel te zijn voor het testen van het publicatie proces. De beste manier om het end-to-end proces van publiceren naar het PowerShell Gallery te testen, is door uw eigen lokale opslag plaats in te stellen en te gebruiken. Dit kan op verschillende manieren worden gedaan, waaronder:

- Stel een lokale PowerShell Gallery-instantie in met behulp van het PS-project in de [persoonlijke galerie](https://github.com/PowerShell/PSPrivateGallery) in github. Dit preview-project helpt u bij het instellen van een exemplaar van de PowerShell Gallery dat u kunt beheren en gebruiken voor uw tests.
- Stel een [interne Nuget-opslag plaats](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/)in.
  Hiervoor moet meer werk worden ingesteld, maar heeft het voor deel dat er een aantal meer vereisten wordt gevalideerd, met name het gebruik van een API-sleutel en of er afhankelijkheden in het doel aanwezig zijn wanneer u publiceert.
- Stel een bestands share in als test **opslagplaats**. Dit is eenvoudig te configureren, maar omdat het een bestands share is, zullen de hierboven vermelde validaties niet worden uitgevoerd. Een potentiële voor deel in dit geval is dat de bestands share niet de vereiste API-sleutel controleert, zodat u dezelfde sleutel kunt gebruiken die u gebruikt om naar de PowerShell Gallery te publiceren.

Gebruik `Register-PSRepository` om een van deze oplossingen te definiëren een nieuwe **opslag plaats**die u gebruikt in de para meter `-Repository` voor `Publish-Module`.

Een extra punt over het testen van publicaties: elk pakket dat u naar de PowerShell Gallery publiceert, kan niet worden verwijderd zonder hulp van het operations-team, dat ervoor zorgt dat niets afhankelijk is van het pakket dat u wilt publiceren. Daarom bieden we geen ondersteuning voor de PowerShell Gallery als test doel en nemen ze contact op met elke uitgever.

## <a name="use-powershellget-to-publish"></a>PowerShellGet gebruiken om te publiceren

Het wordt ten zeerste aanbevolen dat uitgevers de `Publish-Module`-en `Publish-Script`-cmdlets gebruiken wanneer ze met de PowerShell Gallery werken. **PowerShellGet** is gemaakt om u te helpen voor komen dat u belang rijke informatie over de installatie van en publiceert op de PowerShell Gallery. In sommige gevallen hebben uitgevers ervoor gekozen om **PowerShellGet** over te slaan en de **NuGet** -client of **Package Management** -cmdlets te gebruiken, in plaats van `Publish-Module`. Er zijn een aantal details die eenvoudig worden gemist, wat leidt tot een aantal ondersteunings aanvragen.

Als er een reden is dat u `Publish-Module` of `Publish-Script`niet kunt gebruiken, laat het ons dan weten.
Verstrek een probleem in de **PowerShellGet** github opslag plaats en geef de details op die ervoor zorgen dat u **NuGet** of **Package Management**kunt kiezen.

## <a name="recommended-workflow"></a>Aanbevolen werk stroom

De meest succes volle aanpak voor pakketten die zijn gepubliceerd op de PowerShell Gallery, is als volgt:

- Doe de eerste ontwikkeling in een open-source project site. Het Power shell-team maakt gebruik van GitHub.
- Gebruik feedback van revisoren en [Power shell script Analyzer](https://aka.ms/psscriptanalyzer) om de code naar stabiele status te krijgen.
- Neem documentatie op, zodat anderen weten hoe u uw werk kunt gebruiken.
- Test de publicatie actie met een lokale opslag plaats.
- Publiceer een stabiele of alpha-versie naar de PowerShell Gallery en zorg ervoor dat u de documentatie toevoegt en een koppeling maakt naar uw project site.
- Verzamel feedback en herhaal de code in uw project site en publiceer stabiele updates naar het PowerShell Gallery.
- Voeg voor beelden en Ziekteloze tests toe in uw project en uw module.
- Bepaal of u code wilt ondertekenen van uw pakket.
- Wanneer u denkt dat het project gereed is voor gebruik in een productie omgeving, publiceert u een `1.0.0` versie naar de PowerShell Gallery.
- Blijf feedback verzamelen en herhaal uw code op basis van gebruikers invoer.
