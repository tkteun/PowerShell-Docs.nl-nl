---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: psgallery_faqs
ms.openlocfilehash: f00372d75b3e73bdc1499c3a2c8895bffb0902f9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="frequently-asked-questions"></a>Veelgestelde vragen

## <a name="what-is-a-powershell-module"></a>Wat is een PowerShell-module?

Een PowerShell-module is een herbruikbare pakket op met een PowerShell-functionaliteit. Alles in PowerShell (functies, variabelen, DSC-resources, enz.) kan worden verpakt in modules. Modules zijn meestal mappen met specifieke typen bestanden die zijn opgeslagen op een specifiek pad. Er zijn enkele verschillende soorten er PowerShell-modules.

## <a name="what-is-a-powershell-script"></a>Wat is een PowerShell-script?

Een PowerShell-script is een reeks opdrachten die zijn opgeslagen in een .ps1-bestand om in te schakelen hergebruik en delen. PowerShell-werkstromen zijn ook PowerShell-scripts, waardoor het overzicht van een verzameling taken en geef sequentiëren voor deze taken. Voor meer informatie raadpleegt u [aan de slag met PowerShell Workflow](https://technet.microsoft.com/library/jj134242.aspx).

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a>Hoe weet PowerShell-Scripts verschilt van PowerShell-Modules?

Modules zijn doorgaans beter voor het delen van, maar we inschakelt script eenvoudiger voor u werkstromen en scripts bijdragen aan de community delen. Zie de volgende blogs voor meer informatie:

- [Scripts schrijven PowerShell-Modules niet schrijven](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/)
- [Understanding PowerShell-Modules](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a>Hoe kan ik publiceren naar de PowerShell-galerie

Voordat u items naar de galerie publiceren kunt, moet u een account registreren in de PowerShell-galerie. Dit is omdat een NuGetApiKey die wordt geleverd bij de registratie publiceren items vereist. Als u wilt registreren, gebruikt u uw persoonlijke, werk of schoolaccount aan te melden bij de PowerShell-galerie. Een eenmalige registratie-proces is vereist wanneer u zich aanmeldt voor het eerst. Daarna is uw NuGetApiKey beschikbaar in uw profiel.

Zodra u hebt geregistreerd in de galerie, gebruikt u de [publiceren-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) of [publiceren Script](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlets voor het publiceren van uw object aan de galerie. Ga naar het tabblad publiceren of lezen voor meer informatie over het uitvoeren van deze cmdlets de [publiceren-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) en [publiceren Script](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) documentatie.

**U hoeft niet te registreren of aanmelden bij de galerie te installeren of items op te slaan.**

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-an-item-to-the-powershell-gallery-what-does-that-mean"></a>Ik heb ontvangen 'kan aanvraag niet verwerken. 'De opgegeven API-sleutel is ongeldig of is niet gemachtigd voor toegang tot het opgegeven pakket.'. De externe server heeft een fout geretourneerd: (403) verboden. " Fout bij het publiceren van een item naar de PowerShell-galerie. Wat moet dat betekenen?

Deze fout kan optreden vanwege de volgende redenen:

- **De opgegeven API-sleutel is ongeldig.**
     Zorg ervoor dat u de geldige API-sleutel van uw account hebt opgegeven. Als u uw API-sleutel, moet u uw profielpagina weergeven.
- **Naam van het opgegeven item is geen eigendom van u.**
     Als u hebt gecontroleerd of uw API-sleutel juist is en bestaat er al een item met dezelfde naam als het account dat u probeert te gebruiken. Het item is niet-vermelde door de eigenaar, in dat geval kan deze niet weergegeven in zoekresultaten. Open een browser om te bepalen of er al een item met dezelfde naam bestaat, en navigeer naar de pagina details van het item: `https://www.powershellgallery.com/packages/<itemName>`. Bijvoorbeeld, navigeren rechtstreeks naar `https://www.powershellgallery.com/packages/pester` gaat u naar de pagina details van de module Pester, of niet-vermelde of niet is. Als een item met een conflicterende naam al bestaat en niet-vermelde, kunt u:
    - Selecteer een andere naam voor het object.
    - Neem contact op met de eigenaren van het bestaande item.

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a>Waarom ik kan niet met mijn persoonlijke account aanmelden, maar ik gisteren kan aanmelden?

Zorg ervoor dat uw account galerie niet geschikt is voor wijzigingen in uw primaire e-mailalias. Zie voor meer informatie [Microsoft e-aliassen](https://windows.microsoft.com/windows/outlook/add-alias-account).

## <a name="why-dont-i-see-all-the-gallery-items-when-i-select-all-the-category-checkboxes-on-the-items-tab"></a>Waarom zie ik niet alle galerij-items wanneer ik de categorie selectievakjes op het tabblad Items selecteren?

Als u een categorie selectievakje selecteert, worden u mededeling "Ik zou willen zien alle items in deze categorie." Alleen de items in de geselecteerde categorieën weergegeven. Dus op dezelfde manier als u alle selectievakjes in de categorie, u zijn met de mededeling "Ik zou willen zien alle items in elke categorie." Maar een aantal items in de galerie behoren niet tot een van de categorieën weergegeven, zodat deze niet in de resultaten weergegeven. Alle items in de galerie wilt zien, schakel het selectievakje uit alle categorieën of Selecteer het tabblad Items opnieuw.

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a>Wat zijn de vereisten voor het publiceren van een module aan de PowerShell-galerie?

Elk soort PowerShell-module (scriptmodules, binaire modules of manifest modules) kan worden gepubliceerd naar de galerie. Voor het publiceren van een module PowerShellGet moet weten van enkele zaken - versie van het, beschrijving, de auteur en hoe deze wordt in licentie gegeven. Deze informatie wordt gelezen als onderdeel van het publicatieproces van de *module-manifest* (.psd1)-bestand, of van de waarde van de [ **publiceren-Module** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) van cmdlet **LicenseUri** parameter. Alle modules die zijn gepubliceerd naar de galerie moeten modulemanifesten hebben. Iedere module met de volgende informatie in het manifest kan worden gepubliceerd naar de galerie met:

- Versie
- Beschrijving
- auteur
- Een URI met de licentievoorwaarden van de module als onderdeel van de **PrivateData** sectie van het manifest, of in de **LicenseUri** parameter van de [ **publiceren-Module** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a>Hoe maak ik een correct opgemaakt module-manifest

De eenvoudigste manier om te maken van een module-manifest is om uit te voeren de [ **nieuw ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet. In PowerShell 5.0 of hoger, nieuw ModuleManifest genereert een correct opgemaakt module-manifest met lege velden voor nuttig metagegevens zoals **ProjectUri**, **LicenseUri**, en **labels**. Vul de lege waarden gewoon of gegenereerd manifest gebruiken als een voorbeeld van de juiste opmaak.

Om te controleren of alle vereiste metagegevensvelden goed hebt ingevuld, gebruikt de [ **Test ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

De module manifestbestand als velden wilt bijwerken, gebruiken de [ **Update ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a>Wat zijn de vereisten voor het publiceren van een script in de galerie?

Elk soort PowerShell-script (scripts of werkstromen) kan worden gepubliceerd naar de galerie. Voor het publiceren van een script PowerShellGet moet weten van enkele zaken - versie van het, beschrijving, de auteur en hoe deze wordt in licentie gegeven. Deze informatie wordt gelezen als onderdeel van het publicatieproces van het scriptbestand *PSScriptInfo* sectie, of van de waarde van de [ **publiceren Script** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) van cmdlet  **LicenseUri** parameter. Alle scripts die worden gepubliceerd naar de galerie moeten metagegevens hebben. Elk script dat de volgende informatie in de sectie PSScriptInfo bevat kan worden gepubliceerd naar de galerie met:

- Versie
- Beschrijving
- auteur
- Een URI met de licentievoorwaarden van het script als onderdeel van de **PSScriptInfo** gedeelte van het script of in de **LicenseUri** parameter van de [ **publiceren-Script** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="how-do-i-search"></a>Hoe kan ik zoeken?

Typ wat u zoekt in het tekstvak. Bijvoorbeeld, als u wilt zoeken naar modules die zijn gerelateerd aan Azure SQL wilt, typ 'azure sql'. Onze zoekfunctie zoekt naar deze trefwoorden in alle gepubliceerde artikelen, waaronder titels, beschrijvingen en metagegevens. Vervolgens, op basis van een gewogen quality-score, deze het meest overeenkomt met weergegeven. U kunt ook zoeken door een bepaald veld met veld: 'waarde' syntaxis in de query voor de volgende velden:

- Labels
- Functies
- Cmdlets
- DscResources
- PowerShellVersion

Zo is, bijvoorbeeld wanneer u zoekt naar PowerShellVersion: '2.0' alleen resultaten die compatibel met PowerShellVersion 2.0 zijn (op basis van het manifest van de module-script) worden weergegeven.

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a>Hoe maak ik een correct opgemaakt scriptbestand

De eenvoudigste manier om een correct opgemaakt scriptbestand maken om uit te voeren is de [ **nieuw ScriptFileInfo** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet. In PowerShell 5.0 nieuw ScriptFileInfo genereert een correct opgemaakt scriptbestand met lege velden voor nuttig metagegevens zoals **ProjectUri**, **LicenseUri**, en **labels** . Vul de lege waarden gewoon of het bestand gegenereerde script gebruiken als een voorbeeld van de juiste opmaak.

Om te controleren of alle vereiste metagegevensvelden goed hebt ingevuld, gebruikt de [ **Test ScriptFileInfo** ](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

Gebruik voor het bijwerken van het script metagegevensvelden, de [ **Update ScriptFileInfo** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="what-other-types-of-powershell-modules-exist"></a>Wat andere typen van PowerShell-Modules voorkomen?

De term PowerShell-module verwijst ook naar de bestanden die werkelijke functionaliteit implementeren. Module scriptbestanden (.psm1) bevatten PowerShell-code. Module binaire bestanden (.dll) bevatten gecompileerde code.

Hier volgt één manier om na te denken: de map die de module kapselt is de modulemap. De modulemap mag een module-manifest (.psd1) waarmee de inhoud van de map wordt beschreven. De bestanden die daadwerkelijk het werk te doen zijn de module scriptbestanden (.psm1) en de module binaire bestanden (.dll). DSC-resources bevinden zich in een specifieke submap en worden geïmplementeerd als module scriptbestanden of module binaire bestanden.

Alle modules in de galerie modulemanifesten bevatten en de meeste van deze modules scriptbestanden module of module binaire bestanden bevatten. De term-module kan verwarrend zijn vanwege deze andere betekenis. Tenzij expliciet anders vermeld, worden alle maakt gebruik van de module word op deze pagina verwijzen naar de modulemap met deze bestanden.

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a>Hoe PackageManagement relateren aan PowerShellGet? (Hoog niveau antwoord)

PackageManagement is een algemene interface voor het werken met een Pakketbeheer. Uiteindelijk, of u bent omgaan met PowerShell-modules, MSI-bestanden, Ruby gems, NuGet-pakketten of Perl modules, moet u gebruikmaken van PackageManagement opdrachten (zoek-pakket en Install-Package) om te zoeken en deze installeren. PackageManagement doet dit door een Pakketprovider voor elke Pakketbeheer PackageManagement aansluit. Providers gaat het echte werk; Deze inhoud ophalen van de opslagplaatsen en de inhoud lokaal wordt geïnstalleerd. Vaak heen pakket providers gewoon loopt de bestaande package manager-hulpprogramma's voor een opgegeven pakkettype.

PowerShellGet is de package manager voor PowerShell-items. Er is een PSModule Pakketprovider waarmee de functionaliteit PowerShellGet via PackageManagement. Als gevolg hiervan kunt u uitvoeren [Install-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) of Install-Package-Provider PSModule voor het installeren van een module van de PowerShell Gallery. Bepaalde functionaliteit PowerShellGet, met inbegrip van [Update-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) en [publiceren-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), kan niet worden geopend via PackageManagement opdrachten.

Kortom, is de PowerShellGet uitsluitend gericht op een premium pakket beheerervaring voor PowerShell inhoud hebben. PackageManagement is gericht op het blootstellen van alle pakket ervaringen met een algemene reeks hulpprogramma's. Als u dit antwoord unsatisfying vinden, er is een lang antwoord aan de onderkant van dit document, in de **hoe PackageManagement daadwerkelijk hebben betrekking op PowerShellGet?** sectie.

Voor meer informatie raadpleegt u de [PackageManagement projectpagina](https://oneget.org/).

## <a name="how-does-nuget-relate-to-powershellget"></a>Hoe NuGet relateren aan PowerShellGet?

De PowerShell-galerie is een gewijzigde versie van de [NuGet-galerie](https://www.nuget.org/). NuGet-provider PowerShellGet gebruikt voor het werken met NuGet op basis van opslagplaatsen zoals de PowerShell-galerie.

U kunt PowerShellGet gebruiken op basis van een geldige NuGet-opslagplaats of de bestandsshare. U hoeft alleen de opslagplaats toevoegen door het uitvoeren van de [ **registreren PSRepository** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a>Betekent dit dat nuget.exe staat kunt werken met de galerie?

Ja.

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a>Hoe PackageManagement daadwerkelijk hebben betrekking op PowerShellGet? (Technische Details)

Achter de schermen maakt PowerShellGet intensief gebruik van PackageManagement-infrastructuur.

Op de laag PowerShell-cmdlet [Install-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) is daadwerkelijk een thin wrapper rond Install-Package-Provider PSModule.

Op de laag van PackageManagement pakket provider roept de PSModule Pakketprovider daadwerkelijk in andere PackageManagement pakket providers. Bijvoorbeeld, wanneer u werkt met NuGet gebaseerde galerieën (zoals de PowerShell Gallery), de PSModule Pakketprovider gebruikt de NuGet-Pakketprovider werkt met de opslagplaats.

![PowerShellGet-architectuur](Images/powershellgetArchitecture.png)

Afbeelding 1: PowerShellGet architectuur

## <a name="what-is-required-to-run-powershellget"></a>Wat is vereist voor het uitvoeren van PowerShellGet?

In het algemeen is het raadzaam verzamelen van de meest recente versie van de module PowerShellGet (Let erop dat deze .NET 4.5 is vereist).

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

## <a name="is-it-possible-to-reserve-names-for-items-that-will-be-published-in-future"></a>Is het mogelijk om deze te reserveren namen voor items die in de toekomst worden gepubliceerd?

Het is niet mogelijk om te hurk itemnamen. Als u denkt dat een bestaand item heeft genomen de naam die aansluit bij uw object meer, probeer [contact opnemen met de eigenaar van het item](psgallery_contacting_item_owners.md). Als u niet antwoord binnen een paar weken ontvangen, kunt u contact op met ondersteuning en het team PowerShell Gallery ziet er het.

## <a name="how-do-i-claim-ownership-for-items-"></a>Hoe kan ik eigendom van items aanspraak maken?

Bekijk [Item eigenaars beheren op PowerShellGallery.com](Managing-Item-Owners.md) voor meer informatie.

## <a name="how-do-i-deal-with-an-item-owner-who-is-violating-my-item-license"></a>Hoe ik omgaan met de eigenaar van een item wie is mijn item licentie schenden

Wij raden de PowerShell-community samenwerken om geschillen die zich tussen item eigenaren en de eigenaren van andere items voordoen kunnen op te lossen.  We hebben ontworpen een [geschil omzettingsproces](psgallery_dispute_resolution.md) die we vragen u moet uitvoeren voordat PowerShellGallery.com beheerders intercede.