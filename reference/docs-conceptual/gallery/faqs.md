---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: Veelgestelde vragen over PowerShell Gallery
ms.openlocfilehash: bcbb36a9ec60d88d1ef56fd270f0ae1862d5ca6b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328873"
---
# <a name="frequently-asked-questions"></a>Veelgestelde vragen

## <a name="what-is-a-powershell-module"></a>Wat is een PowerShell-module?

Een Power shell-module is een herbruikbaar pakket met een Power shell-functionaliteit. Alles in Power shell (functies, variabelen, DSC-resources, enz.) kan worden verpakt in modules. Doorgaans zijn modules mappen met specifieke typen bestanden die zijn opgeslagen op een specifiek pad. Er zijn een aantal verschillende typen Power shell-modules.

## <a name="what-is-a-powershell-script"></a>Wat is een PowerShell-script?

Een Power shell-script is een reeks opdrachten die zijn opgeslagen in een. ps1-bestand om het opnieuw gebruiken en delen mogelijk te maken. Power shell-werk stromen zijn ook Power shell-scripts, die een overzicht maken van een reeks taken en het bepalen van sequentiëren voor deze taken. Ga voor meer informatie naar [aan de slag met Power shell-werk stroom](https://technet.microsoft.com/library/jj134242.aspx).

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a>Wat is het verschil tussen Power shell-scripts en Power shell-modules?

Modules zijn over het algemeen beter te delen, maar we scha kelen het delen van scripts in om het voor u gemakkelijker te maken om werk stromen en scripts naar de community te bijdragen. Ga voor meer informatie naar de volgende blogs:

- [Geen scripts schrijven, Power shell-modules schrijven](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/)
- [Informatie over Power shell-modules](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a>Hoe kan ik publiceren naar de PowerShell Gallery?

U moet een account registreren in de PowerShell Gallery voordat u pakketten kunt publiceren naar de galerie. Dit komt doordat voor publicatie pakketten een NuGetApiKey is vereist, dat wordt meegeleverd bij de registratie. Als u zich wilt registreren, gebruikt u uw persoonlijke, werk-of school account om u aan te melden bij de PowerShell Gallery. Een eenmalig registratie proces is vereist wanneer u zich voor de eerste keer aanmeldt. Daarna is uw NuGetApiKey beschikbaar op uw profiel pagina.

Nadat u in de galerie hebt geregistreerd, gebruikt u de cmdlets [Publish-module][] of [Publish-script][] om uw pakket naar de galerie te publiceren.
Voor meer informatie over het uitvoeren van deze cmdlets gaat u naar het tabblad publiceren of leest u de documentatie [Publish-Module][] en [Publish-Script][] .

**U hoeft zich niet te registreren of u aan te melden bij de galerie om pakketten te installeren of op te slaan.**

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-a-package-to-the-powershell-gallery-what-does-that-mean"></a>Ik heb ' kan de aanvraag niet verwerken ' ontvangen. ' De opgegeven API-sleutel is ongeldig of heeft geen machtiging voor toegang tot het opgegeven pakket. De externe server heeft een fout geretourneerd: (403) verboden. " fout bij het publiceren van een pakket naar het PowerShell Gallery. Wat houdt dat in?

Deze fout kan de volgende oorzaken hebben:

- **De opgegeven API-sleutel is ongeldig.**
     Zorg ervoor dat u de geldige API-sleutel hebt opgegeven in uw account. Als u uw API-sleutel wilt ophalen, bekijkt u de profiel pagina.
- **De opgegeven pakket naam is geen eigendom van u.**
     Als u hebt bevestigd dat uw API-sleutel juist is, bestaat er mogelijk al een pakket met dezelfde naam als de versie die u probeert te gebruiken. Het pakket is mogelijk niet meer vermeld door de eigenaar, in dat geval wordt het niet weer gegeven in de zoek resultaten. Als u wilt bepalen of er al een pakket met dezelfde naam bestaat, opent u een browser en navigeert u naar de pagina Details van het pakket: `https://www.powershellgallery.com/packages/<packageName>`. Als u bijvoorbeeld rechtstreeks naar `https://www.powershellgallery.com/packages/pester` navigeert, gaat u naar de pagina Details van de ondertekenaar, of deze niet is vermeld of niet. Als er al een pakket met een conflicterende naam bestaat en niet is vermeld, kunt u het volgende doen:
    - Selecteer een andere naam voor het pakket.
    - Neem contact op met de eigen aren van het bestaande pakket.

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a>Waarom kan ik me niet aanmelden met mijn persoonlijke account, maar ik kan me gisteren aanmelden?

Houd er rekening mee dat uw account in de galerie geen wijzigingen in uw primaire e-mail alias heeft. Zie [e-mail aliassen van micro soft](https://windows.microsoft.com/windows/outlook/add-alias-account)voor meer informatie.

## <a name="why-dont-i-see-all-the-gallery-packages-when-i-select-all-the-category-checkboxes-on-the-packages-tab"></a>Waarom zie ik niet alle galerie pakketten wanneer ik alle selectie vakjes van de categorie Selecteer op het tabblad pakketten?

Als u een categorie selectie vakje inschakelt, wordt ' Ik wil graag alle pakketten in deze categorie weer gegeven ' vermeld. Alleen de pakketten in de geselecteerde categorieën worden weer gegeven. Als u alle selectie vakjes van de categorie selecteert, wordt u dus aangegeven dat ik alle pakketten in een categorie wil zien. Sommige pakketten in de galerie behoren echter niet tot een van de vermelde categorieën, waardoor ze niet in de resultaten worden weer gegeven. Als u alle pakketten in de galerie wilt weer geven, schakelt u alle categorieën uit of selecteert u het tabblad pakketten opnieuw.

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a>Wat zijn de vereisten voor het publiceren van een module naar de PowerShell Gallery?

Elk soort Power shell-module (script modules, binaire modules of manifest modules) kan worden gepubliceerd in de galerie.
Voor het publiceren van een module moet PowerShellGet een aantal dingen kennen: de versie, beschrijving, auteur en de licentie.
Deze informatie wordt gelezen als onderdeel van het publicatie proces van het *module manifest* bestand (. psd1) of van de waarde van de **LicenseUri** -para meter van de cmdlet [Publish-module][] .
Alle modules die naar de galerie worden gepubliceerd, moeten module manifesten hebben.
Alle modules die de volgende informatie bevatten in het manifest, kunnen worden gepubliceerd in de galerie:

- Versie
- Beschrijving
- Auteur
- Een URI naar de licentie voorwaarden van de module, hetzij als onderdeel van de sectie **PrivateData** van het manifest, of in de para meter **LicenseUri** van de cmdlet [Publish-module][] .

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a>Hoe kan ik een module manifest maken dat juist is opgemaakt?

De eenvoudigste manier om een module manifest te maken, is door de cmdlet [New-ModuleManifest][] uit te voeren. In Power shell 5,0 of hoger wordt met New-ModuleManifest een module manifest met de juiste indeling gegenereerd met lege velden voor handige meta gegevens, zoals **ProjectUri**, **LicenseUri**en **Tags**. Vul de lege waarden in of gebruik het gegenereerde manifest als voor beeld van de juiste indeling.

Gebruik de cmdlet [test-ModuleManifest][] om te controleren of alle vereiste meta gegevens velden juist zijn gevuld.

Als u de velden in het manifest bestand van de module wilt bijwerken, gebruikt u de cmdlet [Update-ModuleManifest][] .

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a>Wat zijn de vereisten voor het publiceren van een script naar de galerie?

Elk type Power shell-script (scripts of werk stromen) kan worden gepubliceerd in de galerie.
Voor het publiceren van een script moet PowerShellGet enkele dingen weten over it: de versie, beschrijving, auteur en de licentie.
Deze informatie wordt gelezen als onderdeel van het publicatie proces van de sectie *PSScriptInfo* van het script bestand of van de waarde van de **LicenseUri** -para meter van de [Publish-Script][] cmdlet.
Alle scripts die naar de galerie worden gepubliceerd, moeten meta gegevens bevatten.
Elk script dat de volgende informatie bevat in de sectie PSScriptInfo, kan worden gepubliceerd in de galerie:

- Versie
- Beschrijving
- Auteur
- Een URI naar de licentie voorwaarden van het script, hetzij als onderdeel van de sectie **PSScriptInfo** van het script, of in de para meter **LicenseUri** van de cmdlet [Publish-script][] .

## <a name="how-do-i-search"></a>Hoe kan ik zoeken?

Typ wat u zoekt in het tekstvak. Als u bijvoorbeeld modules wilt zoeken die verwant zijn aan Azure SQL, typt u ' Azure SQL '. Onze zoek machine zoekt naar deze tref woorden in alle gepubliceerde pakketten, met inbegrip van titels, beschrijvingen en andere meta gegevens. Op basis van een score met een gewogen kwaliteit worden de meest overeenkomende resultaten weer gegeven. U kunt ook zoeken op specifiek veld met de syntaxis Field: ' value ' in de zoek query voor de volgende velden:

- Labels
- Functies
- Cmdlets
- DscResources
- PowerShellVersion

Als u bijvoorbeeld zoekt naar PowerShellVersion: ' 2.0 ', worden alleen de resultaten weer gegeven die compatibel zijn met PowerShellVersion 2,0 (op basis van de module/het script manifest).

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a>Hoe kan ik een correct opgemaakt script bestand maken?

De eenvoudigste manier om een goed opgemaakt script bestand te maken, is door de cmdlet [New-ScriptFileInfo][] uit te voeren. In Power shell 5,0 genereert New-ScriptFileInfo een correct opgemaakt script bestand met lege velden voor handige meta gegevens zoals **ProjectUri**, **LicenseUri**en **Tags**. Vul de lege waarden in of gebruik het gegenereerde script bestand als een voor beeld van de juiste indeling.

Gebruik de cmdlet [test-ScriptFileInfo][] om te controleren of alle vereiste meta gegevens velden juist zijn gevuld.

Als u de meta gegevens velden van het script wilt bijwerken, gebruikt u de cmdlet [Update-ScriptFileInfo][] .

## <a name="what-other-types-of-powershell-modules-exist"></a>Welke andere typen Power shell-modules bestaan er?

De term Power shell-module verwijst ook naar de bestanden waarmee de daad werkelijke functionaliteit wordt geïmplementeerd. Script module bestanden (. psm1) bevatten Power shell-code. Binaire module bestanden (. dll) bevatten gecompileerde code.

Hier volgt een van de manieren waarop u dit kunt nadenken: de map waarin de module is ingekapseld, is de map van de module. De map module kan een module manifest (. psd1) bevatten waarin de inhoud van de map wordt beschreven. De bestanden die feitelijk het werk doen, zijn de script module bestanden (. psm1) en de binaire module bestanden (. dll). DSC-resources bevinden zich in een specifieke submap en worden geïmplementeerd als script module bestanden of binaire module bestanden.

Alle modules in de galerie bevatten module manifesten en de meeste van deze modules bevatten script module bestanden of binaire module bestanden. De term module kan verwarrend zijn vanwege de verschillende betekenissen. Tenzij expliciet anders wordt vermeld, verwijst alle gebruik van de woord module op deze pagina naar de module map met deze bestanden.

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a>Wat is de relatie tussen Package Management en PowerShellGet? (Antwoord op hoog niveau)

Package Management is een gemeen schappelijke interface voor het werken met pakket beheer. Uiteindelijk, of u nu gebruikmaakt van Power shell-modules, MSIs, Ruby edelsteen, NuGet-pakketten of perl-modules, moet u de opdrachten van Package Management (zoek-package en install-package) kunnen gebruiken om ze te zoeken en te installeren. Package Management doet dit door een pakket provider te hebben voor elke pakket manager die wordt aangesloten op Package Management. Providers doen al het werkelijke werk. ze halen inhoud op uit opslag plaatsen en installeren de inhoud lokaal. Vaak verloopt pakket providers gewoon om de bestaande pakket beheer Programma's voor een bepaald pakket type.

PowerShellGet is pakket beheer voor Power shell-pakketten.
Er is een PSModule-pakket provider die PowerShellGet-functionaliteit beschikbaar maakt via package management.
Daarom kunt u [Installatie-module][] of install-package-provider PSModule uitvoeren om een module te installeren vanuit de PowerShell Gallery.
Bepaalde PowerShellGet-functies, waaronder [Update-module][] en [Publish-module][], zijn niet toegankelijk via package management-opdrachten.

In samen vatting is PowerShellGet alleen gericht op het beheer van een Premium-ervaring voor Power shell-inhoud. Package Management is gericht op het beschikbaar maken van alle pakket beheer-ervaringen via één algemene set hulpprogram ma's. Als u vindt dat dit antwoord niet voldoet, is er een lang antwoord onder aan dit document, in de sectie **Hoe heeft package management eigenlijk betrekking op de PowerShellGet?**

Ga naar de [Package Management-project pagina](https://oneget.org/)voor meer informatie.

## <a name="how-does-nuget-relate-to-powershellget"></a>Wat is de relatie tussen NuGet en PowerShellGet?

De PowerShell Gallery is een gewijzigde versie van de [NuGet-galerie](https://www.nuget.org/). PowerShellGet maakt gebruik van NuGet-provider om te werken met opslag plaatsen op basis van NuGet, zoals de PowerShell Gallery.

U kunt PowerShellGet gebruiken voor elke geldige NuGet-opslag plaats of-bestands share. U hoeft alleen de opslag plaats toe te voegen door de cmdlet [REGI ster-PSRepository][] uit te voeren.

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a>Betekent dit dat ik NuGet. exe kan gebruiken om met de galerie te werken?

Ja.

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a>Wat is de package management van de relatie met PowerShellGet? (Technische details)

Onder de motorkap maakt PowerShellGet intensief gebruik van Package Management-infra structuur.

Op de Power shell-cmdlet [Installatie-module][] in feite een smalle wrapper rondom install-package-provider PSModule.

In de laag van de package management-pakket provider roept de PSModule-pakket provider echt aan bij andere package management-pakket providers. Als u bijvoorbeeld werkt met galerieën op basis van NuGet (zoals de PowerShell Gallery), gebruikt de PSModule-pakket provider de NuGet-pakket provider om met de opslag plaats te werken.

![PowerShellGet-architectuur](Images/powershellgetArchitecture.png)

Afbeelding 1: PowerShellGet-architectuur

## <a name="what-is-required-to-run-powershellget"></a>Wat is er nodig om PowerShellGet uit te voeren?

In het algemeen raden wij aan de meest recente versie van de PowerShellGet-module te kiezen (Houd er rekening mee dat .NET 4,5 is vereist).

Voor de **PowerShellGet**-module is **PowerShell 3.0 of hoger** vereist.

Daarom vereist **PowerShellGet** een van de volgende besturingssystemen:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

Voor **PowerShellGet** is ook .NET Framework 4.5 of hoger vereist. U kunt .NET Framework 4.5 of hoger [hier](https://msdn.microsoft.com/library/5a4x27ek.aspx) installeren.

## <a name="is-it-possible-to-reserve-names-for-packages-that-will-be-published-in-future"></a>Is het mogelijk namen te reserveren voor pakketten die in de toekomst zullen worden gepubliceerd?

Het is niet mogelijk om pakket namen te squat. [Neem contact op met de eigenaar van het pakket](./how-to/working-with-packages/contacting-package-owners.md)als u denkt dat een bestaand pakket de naam heeft gehaald die aansluit bij uw pakket. Als u binnen een paar weken geen antwoord hebt ontvangen, kunt u contact opnemen met de ondersteuning en wordt het PowerShell Gallery-team erin kijken.

## <a name="how-do-i-claim-ownership-for-packages"></a>Hoe kan ik eigendom van het claimen voor pakketten?

Bekijk het [beheer van pakket eigenaren op PowerShellGallery.com](./how-to/publishing-packages/managing-package-owners.md) voor meer informatie.

## <a name="how-do-i-deal-with-a-package-owner-who-is-violating-my-package-license"></a>Hoe kan ik omgaan met een pakket eigenaar die in strijd is met mijn pakket licentie?

We raden de Power shell-community aan samen te werken om geschillen op te lossen die kunnen ontstaan tussen pakket eigenaren en de eigen aren van andere pakketten.  We hebben een proces voor het [oplossen van geschillen](./how-to/getting-support/dispute-resolution.md) opgesteld dat wij u vragen om te volgen voordat PowerShellGallery.com beheerders van tevoren te zijn.

[New-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest
[Test-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest
[Update-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/Update-ModuleManifest

[Installatie-module]: /powershell/module/PowershellGet/Install-Module
[New-ScriptFileInfo]: /powershell/module/PowershellGet/New-ScriptFileInfo
[Publish-Module]: /powershell/module/PowershellGet/Publish-Module
[Publish-Script]: /powershell/module/PowershellGet/Publish-Script
[REGI ster-PSRepository]: /powershell/module/PowershellGet/Register-PSRepository
[Test-ScriptFileInfo]: /powershell/module/PowershellGet/Test-ScriptFileInfo
[Update-Module]: /powershell/module/PowershellGet/Update-Module
[Update-ScriptFileInfo]: /powershell/module/PowershellGet/Update-ScriptFileInfo
