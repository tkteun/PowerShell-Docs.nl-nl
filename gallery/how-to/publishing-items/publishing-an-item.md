---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Maken en publiceren van een item
ms.openlocfilehash: 7c2a2be6986bf65c168d7c3960366fac4ee31301
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189530"
---
# <a name="creating-and-publishing-an-item"></a>Maken en publiceren van een item

De PowerShell-galerie is de plaats om te publiceren en stabiele PowerShell-modules, scripts en DSC-resources delen met de bredere gebruikersgemeenschap van PowerShell.

In dit artikel bevat informatie over de mechanismen en belangrijke stappen voor het voorbereiden van een script of een module en publiceert naar de PowerShell-galerie.
We raden u wordt aangeraden de [Publishing richtlijnen](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) om te begrijpen hoe om ervoor te zorgen dat de items die u publiceert ruimere door PowerShell Gallery gebruikers worden geaccepteerd.

De minimale vereisten voor het publiceren van een item naar de galerie met PowerShell zijn:

- Een PowerShell-galerie-account hebt, en de API-sleutel die is gekoppeld aan
- Zorg dat de vereiste metagegevens uw item
- De Prevalidatie hulpprogramma's gebruiken om te controleren of dat het object is gereed om te publiceren
- Het item publiceren naar de PowerShell-galerie met de opdrachten publiceren-Module en Publish-Script
- Afhandeling van aanvragen voor vragen of opmerkingen over uw object

De PowerShell-galerie accepteert PowerShell-modules en PowerShell-scripts.
Wanneer we naar scripts verwijzen, bedoelen we een PowerShell-script is een enkel bestand en geen deel uit van een grotere module.

## <a name="powershell-gallery-account-and-api-key"></a>Account van de PowerShell-galerie en API-sleutel

Zie [maken van een PowerShell-galerie Account](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_creating_an_account) voor het instellen van uw account PowerShell Gallery.

Nadat u een account hebt gemaakt, kunt u de API-sleutel die nodig zijn voor het publiceren van een item ophalen.
Nadat u zich met het account aanmeldt, wordt uw gebruikersnaam weergegeven aan de bovenkant van de PowerShell Gallery pagina's in plaats van het Register.
Op uw gebruikersnaam te klikken gaat u naar de pagina Mijn Account waar u de API-sleutel vinden.

Opmerking: De API-sleutel moet worden behandeld als veilig als uw aanmeldingsnaam en het wachtwoord.
Met deze sleutel kunt u of iemand anders, een item die in de PowerShell-galerie van jou bijwerken.
Het is raadzaam het bijwerken van de sleutel regelmatig dat kunt u doen met sleutel opnieuw instellen op de pagina Mijn Account.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>Vereiste metagegevens voor Items die zijn gepubliceerd naar de PowerShell-galerie

De PowerShell-galerie bevat informatie voor galerie gebruikers afkomstig van metagegevensvelden die zijn opgenomen in het script of module-manifest.
Heeft een kleine set vereisten voor de opgegeven in het manifest van item maken of wijzigen van de items voor publicatie naar de PowerShell-galerie.
We raden u wordt aangeraden de sectie itemmetagegevens van de [Publishing richtlijnen](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) voor informatie over het beste informatie bieden aan gebruikers met uw items.

De [nieuw ModuleManifest](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/ModuleManifest-Reference) en [nieuw ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_new-scriptfileinfo) cmdlets de manifest-sjabloon maakt, met de tijdelijke aanduidingen voor alle elementen in het manifest.

Beide manifesten hebben twee secties die belangrijk voor publicatie zijn, de primaire sleutel gegevens en PSData gebied van de primaire sleutel gegevens in een PowerShell-module-manifest PrivateData is alles buiten de PrivateData-sectie.
De reeks primaire sleutels is gekoppeld aan de versie van PowerShell in gebruik is en niet-gedefinieerde worden niet ondersteund.
PrivateData ondersteunt het toevoegen van nieuwe sleutels, zodat de elementen die specifiek zijn voor de PowerShell-galerie in PSData.


Manifest elementen die zijn zeer belangrijk voor u naar de PowerShell-galerie publiceren-item invullen zijn:

- Script of de naam van de Module - die afkomstig zijn van de namen van de. Ps1 voor een script of de. PSD1 voor een module.
- Versie - dit is een vereiste primaire sleutel, indeling moet richtlijnen SemVer (Best Practices voor meer informatie Zie)
- Auteur: dit is een vereiste primaire sleutel en bevat de naam moet worden gekoppeld aan het item (auteurs en eigenaren, Zie hieronder)
- Beschrijving - dit is een vereiste primaire sleutel gebruikt een korte uitleg van dit item de betekenis en eventuele vereisten voor het gebruik ervan
- ProjectURI - dit is een veld zijn ten zeerste aanbevolen URI in PSData die een koppeling naar een Github-repo bevat- of soortgelijke locatie waar u ontwikkeling op het item doen

Auteurs en eigenaren van PowerShell-galerie-items zijn verwante concepten, maar niet altijd overeenkomen.
Item eigenaars zijn gebruikers met PowerShell Gallery-accounts die gemachtigd voor het onderhouden van het item. Mogelijk zijn er veel eigenaren die elk item kunnen bijwerken.
De eigenaar is alleen verkrijgbaar via de PowerShell-galerie en gaat verloren als het item wordt gekopieerd van het ene systeem naar een andere.
Auteur is een tekenreeks die is ingebouwd in de manifest-gegevens, zodat deze altijd deel uit van het item.
De aanbevelingen voor artikelen van Microsoft-producten zijn:

- Meerdere eigenaren, met ten minste één wordt de naam van het team dat het item; produceert hebben
- Hebben de auteur van de naam van een bekende team (zoals Team van Azure SDK) of Microsoft Corporation.


## <a name="pre-validate-your-item"></a>Het object vooraf valideren

Er zijn een paar hulpprogramma's die u uw code uitgevoerd moet voordat het publiceren van uw object naar de PowerShell-galerie:

- [PowerShell-Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), deze bevindt zich in de PowerShell-galerie
- Voor modules, Test-ModuleManifest die deel uitmaakt van PowerShell
- Voor Test-ScriptFileInfo wordt geleverd met ophalen van de PowerShell-scripts

[PowerShell-Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) is een hulpmiddel statische code die u uw code scannen gaat zodat deze voldoet aan basic PowerShell richtlijnen voor codering. Dit hulpprogramma voorkomende en kritieke problemen in uw code wordt geïdentificeerd en regelmatig tijdens het ontwikkelen van waarmee u uw item publiceren moet worden uitgevoerd.
PowerShell-Script Analyzer biedt een lijst met problemen die zijn geïdentificeerd als fouten, waarschuwingen en informatie.
Alle fouten moeten worden opgelost voordat u naar de PowerShell-galerie publiceert. Waarschuwingen moeten worden beoordeeld en de meeste moet worden opgelost.
PowerShell-Script Analyzer wordt uitgevoerd telkens wanneer een item wordt gepubliceerd of in de PowerShell-galerie bijgewerkt.
De galerie teamleden neemt contact met item eigenaren van fouten in de adressen die zijn gevonden.

Als de manifest-informatie in het object kan niet worden gelezen door de infrastructuur van de PowerShell-galerie, is het niet mogelijk om te publiceren.
[Test ModuleManifest](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-modulemanifest) veelvoorkomende problemen waardoor de module niet worden gebruikt tijdens de installatie wordt onderschept. Het moet worden uitgevoerd voor elke module voorafgaand aan publicatie naar de PowerShell-galerie.

Evenzo [Test ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_test-scriptfileinfo) valideert de metagegevens in een script en moet worden uitgevoerd op elk script (gepubliceerde afzonderlijke vanuit een module) voor publicatie naar de Powershell-galerie.


## <a name="publishing-items"></a>Publishing Items

Moet u de [publiceren Script](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_publish-script) of [publiceren-Module](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/psget_publish-module) items publiceren naar de PowerShell-galerie.
Deze opdrachten vereisen

- Het pad naar het item dat u wilt publiceren. Gebruik de map met de naam van de module voor een module. Als u een map met meerdere versies van dezelfde module opgeeft, moet u RequiredVersion opgeven.
- Een Nuget-API-sleutel. Dit is de API-sleutel gevonden op de pagina Mijn Account op de PowerShell-galerie.

De meeste andere opties op de opdrachtregel moet in de manifest-gegevens voor het item dat u publiceren wilt, dus u niet hoeft te geven in de opdracht.

Om fouten te voorkomen, is het raadzaam dat u probeert de opdrachten met - Whatif-Verbose, voordat u publiceert.
Dit bespaart veel tijd sinds telkens wanneer u publiceren naar de PowerShell-galerie, moet u het versienummer in de manifest-sectie van het item bijwerken.

Voorbeelden zijn: ' Publish-Module-pad '. \MyModule ' - RequiredVersion '0.0.1' - NugetAPIKey 'GUID' - Whatif-uitgebreide ' ' publiceren Script-pad '.\MyScriptFile.PS1' - NugetAPIKey 'GUID' - Whatif-uitgebreide '

De uitvoer zorgvuldig te controleren en als er geen fouten of waarschuwingen, herhaalt u de opdracht zonder - Whatif.

Alle items die worden gepubliceerd naar de PowerShell-galerie worden gescand op virussen en worden geanalyseerd met behulp van de PowerShell-Script Analyzer.
Eventuele problemen die ontstaan op dat moment terug naar de publisher verzonden voor naamomzetting.

Wanneer u een item hebt gepubliceerd naar de PowerShell-galerie, moet u kijken voor feedback over uw item.

- Zorg ervoor dat u het e-mailadres dat is gekoppeld aan het account dat wordt gebruikt voor het publiceren van bewaken.
Gebruikers en het PowerShell-galerie operationele team wordt feedback geven via dat account, inclusief problemen van de PSSA of antivirusprogramma scans.
Als het e-mailaccount ongeldig is, of als ernstige problemen worden gerapporteerd aan het account en links niet gedurende langere tijd wordt opgelost, items kunnen worden overwogen afgebroken en wordt verwijderd van de PowerShell Gallery zoals beschreven in onze [gebruiksvoorwaarden](https://www.powershellgallery.com/policies/Terms).
- U wordt aangeraden dat u zich abonneert op opmerkingen voor elk PowerShell-galerie-item dat u publiceert.
Hiermee kunt u een melding als iedereen opmerkingen toe te op de items in de PowerShell-galerie voegen.
Dit is optioneel, omdat hiervoor een account met LiveFyre maken.