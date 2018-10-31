---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Veelgestelde vragen over de PowerShell Gallery
ms.openlocfilehash: 3fa52892ce50491c040251baae8b4ae4ee3dcba0
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002869"
---
# <a name="frequently-asked-questions"></a>Veelgestelde vragen

## <a name="what-is-a-powershell-module"></a>Wat is een PowerShell-module?

Een PowerShell-module is een herbruikbare pakket op met bepaalde functionaliteit van PowerShell. Alles in PowerShell (functies, variabelen, DSC-resources, enzovoort) kan worden verpakt in modules. Modules zijn meestal mappen met specifieke typen bestanden die zijn opgeslagen op een specifiek pad. Er zijn een aantal verschillende typen er PowerShell-modules.

## <a name="what-is-a-powershell-script"></a>Wat is een PowerShell-script?

Een PowerShell-script wordt een reeks opdrachten die zijn opgeslagen in een .ps1-bestand om in te schakelen hergebruik en delen. PowerShell-werkstromen zijn ook PowerShell-scripts die beschrijven een aantal taken en volgorde van deze taken bieden. Ga voor meer informatie naar [aan de slag met PowerShell Workflow](https://technet.microsoft.com/library/jj134242.aspx).

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a>Hoe verschillen PowerShell-Scripts van PowerShell-Modules?

Modules zijn in het algemeen beter voor het delen van, maar we zijn inschakelen van script delen zodat het eenvoudiger voor u om bij te dragen van werkstromen en scripts aan de community. Zie de volgende blogs voor meer informatie:

- [Geen Scripts schrijven PowerShell-Modules schrijven](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/)
- [Understanding PowerShell-Modules](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a>Hoe kan ik publiceren naar de galerie met PowerShell?

Voordat u pakketten naar de galerie publiceren kunt, moet u een account registreren in de PowerShell Gallery. Dit is omdat een NuGetApiKey, die wordt geleverd bij de registratie voor het publiceren van pakketten vereist. Als u wilt registreren, gebruikt u uw persoonlijke, werk of schoolaccount aanmelden bij de PowerShell Gallery. Een eenmalige registratie-proces is vereist wanneer u zich aanmeldt voor de eerste keer. Daarna is uw NuGetApiKey beschikbaar op uw profielpagina.

Zodra u hebt geregistreerd in de galerie, gebruikt u de [Publish-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) of [Publish-Script](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlets voor het publiceren van uw pakket naar de galerie. Ga naar het tabblad ' Publish ' voor meer informatie over het uitvoeren van deze cmdlets of lees de [Publish-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) en [Publish-Script](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) documentatie.

**U hoeft niet te registreren of aanmelden bij de galerie te installeren of sla-pakketten.**

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-a-package-to-the-powershell-gallery-what-does-that-mean"></a>Ik heb ontvangen "kan aanvraag niet verwerken. 'De opgegeven API-sleutel is ongeldig of heeft geen machtiging voor toegang tot het opgegeven pakket.'. De externe server heeft een fout geretourneerd: (403)-verboden. " Fout bij het publiceren van een pakket naar de PowerShell Gallery. Wat moet dat betekenen?

Deze fout kan optreden voor de volgende redenen:

- **De opgegeven API-sleutel is ongeldig.**
     Zorg ervoor dat u de geldige API-sleutel van uw account hebt opgegeven. Als u uw API-sleutel, bekijk uw profielpagina.
- **Naam van het opgegeven pakket is geen eigendom van u.**
     Als u hebt gecontroleerd of uw API-sleutel juist is, wordt er een pakket met dezelfde naam als het account dat u wilt gebruiken al bestaat. Het pakket is niet-vermelde door de eigenaar, in welk geval het wordt niet weergegeven in een lijst met zoekresultaten. Om te bepalen of er al een pakket met dezelfde naam bestaat, open een browser en navigeer naar de detailpagina van het pakket: `https://www.powershellgallery.com/packages/<packageName>`. Bijvoorbeeld, navigeren door rechtstreeks naar `https://www.powershellgallery.com/packages/pester` gaat u naar de detailpagina van de module Pester, ongeacht of het niet-vermelde of niet. Als een pakket met een conflicterende naam al bestaat en niet-vermelde is, kunt u het volgende doen:
    - Selecteer een andere naam voor het pakket.
    - Neem contact op met de eigenaren van het bestaande pakket.

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a>Waarom kan ik zich niet aanmelden met mijn persoonlijke account, maar ik gisteren kan aanmelden?

Houd er rekening mee dat uw account galerie niet geschikt is voor wijzigingen naar uw primaire e-mailalias. Zie voor meer informatie, [Microsoft e-aliassen](https://windows.microsoft.com/windows/outlook/add-alias-account).

## <a name="why-dont-i-see-all-the-gallery-packages-when-i-select-all-the-category-checkboxes-on-the-packages-tab"></a>Waarom zie ik niet alle galeriepakketten wanneer ik Schakel alle selectievakjes in de categorie op het tabblad pakketten?

Als u een selectievakje categorie selecteert, worden u melding "Ik wil graag om te zien van alle pakketten in deze categorie." Alleen de pakketten in de geselecteerde categorieën worden weergegeven. Dus op dezelfde manier als u alle selectievakjes in de categorie selecteert, u zijn met de mededeling "Ik wil graag om te zien van alle pakketten in elke categorie." Maar sommige pakketten in de galerie behoren niet tot een van de categorieën die worden vermeld, zodat ze niet in de resultaten weergegeven. Als u wilt zien van alle pakketten in de galerie, schakel alle categorieën of Selecteer het tabblad pakketten opnieuw.

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a>Wat zijn de vereisten voor het publiceren van een module aan de galerie met PowerShell?

Elk soort PowerShell-module (scriptmodules, binaire modules of manifest modules) kan worden gepubliceerd naar de galerie. Voor het publiceren van een module PowerShellGet moet weten van enkele dingen die over het - de-versie, beschrijving, de auteur en hoe deze wordt in licentie gegeven. Deze informatie wordt gelezen als onderdeel van het publicatieproces van de *module-manifest* (.psd1)-bestand, of van de waarde van de [ **Publish-Module** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) van cmdlet **LicenseUri** parameter. Alle modules die zijn gepubliceerd naar de galerie moeten modulemanifesten hebben. Een module met de volgende informatie in het manifest kan worden gepubliceerd naar de galerie:

- Versie
- Beschrijving
- De auteur
- Een URI met de licentievoorwaarden van de module als deel van de **PrivateData** sectie van het manifest, of in de **LicenseUri** parameter van de [ **Publish-Module** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a>Hoe maak ik een goed ingedeelde module-manifest?

De eenvoudigste manier om te maken van een module-manifest is om uit te voeren de [ **New-ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet. In PowerShell 5.0 of hoger, nieuw-ModuleManifest genereert een goed ingedeelde module-manifest met lege velden voor nuttige metagegevens zoals **ProjectUri**, **LicenseUri**, en **Tags**. Gewoon vult u het aantal lege waarden of de gegenereerde manifest gebruiken als een voorbeeld van de juiste indeling.

Om te controleren of alle vereiste metagegevensvelden correct hebt ingevuld, gebruikt u de [ **Test ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

Voor het bijwerken van de velden van de manifest-bestand module, gebruikt u de [ **Update ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a>Wat zijn de vereisten voor het publiceren van een script naar de galerie?

Elk soort PowerShell-script (scripts of werkstromen) kan worden gepubliceerd naar de galerie. Voor het publiceren van een script, PowerShellGet moet weten van enkele dingen die over het - de-versie, beschrijving, de auteur en hoe deze wordt in licentie gegeven. Deze informatie wordt gelezen als onderdeel van het publicatieproces van het scriptbestand *PSScriptInfo* sectie, of van de waarde van de [ **Publish-Script** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) van cmdlet  **LicenseUri** parameter. Alle scripts die zijn gepubliceerd naar de galerie moeten metagegevens hebben. Elk script dat in de sectie PSScriptInfo, de volgende gegevens bevat kan worden gepubliceerd naar de galerie:

- Versie
- Beschrijving
- De auteur
- Een URI met de licentievoorwaarden van het script, hetzij als onderdeel van de **PSScriptInfo** gedeelte van het script of in de **LicenseUri** parameter van de [ **Publish-Script** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="how-do-i-search"></a>Hoe vind ik?

Typ wat u zoekt in het tekstvak in. Bijvoorbeeld, als u zoeken van modules die zijn gerelateerd aan Azure SQL wilt, typ 'azure sql'. Onze zoekmachine zoekt naar deze trefwoorden in alle gepubliceerde pakketten, met inbegrip van titels, beschrijvingen en op alle metagegevens. Vervolgens, op basis van een gewogen kwaliteit score, worden weergegeven de dichtstbijzijnde overeenkomsten. U kunt ook zoeken door specifieke veld veld: 'waarde'-syntaxis in de query voor de volgende velden:

- Labels
- Functies
- Cmdlets
- DscResources
- PowerShellVersion

Dit het geval is, bijvoorbeeld, wanneer u zoekt PowerShellVersion: '2.0' alleen resultaten die compatibel met PowerShellVersion 2.0 zijn (op basis van hun manifest module/script) wordt weergegeven.

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a>Hoe maak ik een goed ingedeelde scriptbestand?

De eenvoudigste manier om een goed ingedeelde scriptbestand maken om uit te voeren is de [ **New-ScriptFileInfo** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet. In PowerShell 5.0, New-ScriptFileInfo genereert een goed ingedeelde scriptbestand met lege velden voor nuttige metagegevens zoals **ProjectUri**, **LicenseUri**, en **Tags** . Gewoon vult u het aantal lege waarden of het gegenereerde scriptbestand gebruiken als een voorbeeld van de juiste indeling.

Om te controleren of alle vereiste metagegevensvelden correct hebt ingevuld, gebruikt u de [ **Test ScriptFileInfo** ](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

Voor het bijwerken van de metagegevensvelden script gebruikt de [ **Update ScriptFileInfo** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="what-other-types-of-powershell-modules-exist"></a>Wat andere typen PowerShell-Modules bestaat?

De term PowerShell-module verwijst ook naar de bestanden die de functionaliteit van de werkelijke implementeren. Module-scriptbestanden (.psm1) bevatten PowerShell-code. Module binaire bestanden (.dll) bevatten gecompileerde code.

Hier volgt één manier om na te denken over het: de map die de module kapselt de module is. De modulemap mag een module-manifest (.psd1) die de inhoud van de map wordt beschreven. De bestanden die daadwerkelijk werken, zijn de module scriptbestanden (.psm1) en de module binaire bestanden (.dll). DSC-resources bevinden zich in een specifieke submap en worden geïmplementeerd als script module of binaire module-bestanden.

Alle modules in de galerie modulemanifesten bevatten, en de meeste van deze modules module scriptbestanden of module binaire bestanden bevatten. De term-module kan ingewikkeld zijn vanwege deze andere betekenis. Tenzij uitdrukkelijk anders vermeld, wordt al het gebruik van de module word op deze pagina verwijzen naar de modulemap met deze bestanden.

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a>Hoe PackageManagement in verband met PowerShellGet? (Hoog niveau antwoord)

PackageManagement is een algemene interface voor het werken met een Pakketbeheer. Uiteindelijk, of u bent om met een PowerShell-modules, MSI-bestanden, Ruby gems, NuGet-pakketten of Perl modules, zou het mogelijk gebruik van PackageManagement-opdrachten (Find-pakket en Install-Package) om te zoeken en deze installeren. PackageManagement doet dit door een Pakketprovider voor elke Pakketbeheer PackageManagement aansluit. Providers die dit alles doen het echte werk; Deze inhoud ophalen van opslagplaatsen en de inhoud lokaal installeren. Pakket providers verpakken vaak gewoon rond de bestaande package manager-hulpprogramma's voor een opgegeven pakkettype.

PowerShellGet is het pakketbeheerprogramma voor PowerShell-pakketten. Er is een PSModule pakket-provider die wordt aangegeven dat PackageManagement PowerShellGet-functionaliteit. Als gevolg hiervan kunt u een van beide uitvoeren [Install-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) of Install-Package-Provider PSModule geen module te installeren vanuit de PowerShell Gallery. Bepaalde functionaliteit PowerShellGet, met inbegrip van [Update-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) en [Publish-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), kan niet worden geopend via PackageManagement-opdrachten.

Kortom, is uitsluitend PowerShellGet gericht op het met een premiumervaring voor het beheer van pakket voor de PowerShell-inhoud. PackageManagement is gericht op het blootstellen van alle pakket-management-ervaringen door een algemene set hulpprogramma's. Als u dit antwoord unsatisfying vinden, er is een lange antwoord aan de onderkant van dit document, in de **hoe PackageManagement daadwerkelijk in verband met PowerShellGet?** sectie.

Ga voor meer informatie naar de [PackageManagement-projectpagina](https://oneget.org/).

## <a name="how-does-nuget-relate-to-powershellget"></a>Hoe NuGet in verband met PowerShellGet?

De PowerShell Gallery is een gewijzigde versie van de [NuGet-galerie](https://www.nuget.org/). PowerShellGet maakt gebruik van NuGet-provider om te werken met op basis van NuGet-opslagplaatsen, zoals de PowerShell Gallery.

U kunt PowerShellGet gebruiken op basis van een geldige NuGet opslagplaats of de bestandsshare. U hoeft alleen de opslagplaats toevoegen door het uitvoeren van de [ **Register-PSRepository** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a>Betekent dat ik NuGet.exe kunt gebruiken om te werken met de galerie?

Ja.

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a>Hoe PackageManagement daadwerkelijk in verband met PowerShellGet? (Technische Details)

Achter de schermen maakt PowerShellGet intensief gebruik van PackageManagement-infrastructuur.

In de PowerShell-cmdlet-laag, [Install-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) is eigenlijk een thin wrapper rond Install-Package-Provider PSModule.

Op de laag van de provider in de PackageManagement-pakket aanroepen de provider van het pakket PSModule daadwerkelijk naar andere providers PackageManagement-pakket. Bijvoorbeeld, wanneer u werkt met NuGet op basis van galerieën (zoals de PowerShell Gallery), de PSModule Pakketprovider gebruikt de NuGet-pakket-Provider om te werken met de opslagplaats.

![PowerShellGet-architectuur](Images/powershellgetArchitecture.png)

Afbeelding 1: PowerShellGet-architectuur

## <a name="what-is-required-to-run-powershellget"></a>Wat is vereist voor het uitvoeren van PowerShellGet?

In het algemeen is het raadzaam verzamelen van de meest recente versie van PowerShellGet-module (Houd er rekening mee dat deze .NET 4.5 is vereist).

De **PowerShellGet** module vereist **PowerShell 3.0 of hoger**.

Daarom **PowerShellGet** moet een van de volgende besturingssystemen:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** vereist ook .NET Framework 4.5 of hoger. U kunt installeren .NET Framework 4.5 of hoger van [hier](https://msdn.microsoft.com/library/5a4x27ek.aspx).

## <a name="is-it-possible-to-reserve-names-for-packages-that-will-be-published-in-future"></a>Is het mogelijk om namen voor pakketten die worden gepubliceerd in de toekomst reserveren?

Het is niet mogelijk om te hurk pakketnamen. Als u denkt dat een bestaand pakket met de naam die aansluit bij uw pakket meer, probeer duurde [contact opnemen met de eigenaar van het pakket](./how-to/working-with-packages/contacting-package-owners.md). Als u hebt u geen antwoord binnen een paar weken ontvangen, kunt u contact op met ondersteuning en de PowerShell Gallery-team te bekijken in.

## <a name="how-do-i-claim-ownership-for-packages"></a>Hoe ik aanspraak op eigendomsrechten voor pakketten?

Bekijk [pakket eigenaars beheren op PowerShellGallery.com](./how-to/publishing-packages/managing-package-owners.md) voor meer informatie.

## <a name="how-do-i-deal-with-a-package-owner-who-is-violating-my-package-license"></a>Hoe ik omgaan met de eigenaar van een pakket wie is de licentie van mijn pakket schenden?

U wordt aangeraden de PowerShell-community om te werken samen om het oplossen van eventuele geschillen die mogelijk worden veroorzaakt tussen eigenaren van pakket en de eigenaren van andere pakketten.  We hebben ontworpen een [geschil omzettingsproces](./how-to/getting-support/dispute-resolution.md) die we vragen u moet uitvoeren voordat PowerShellGallery.com beheerders intercede.
