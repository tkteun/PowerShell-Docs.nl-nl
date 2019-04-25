---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Het maken en publiceren van een item
ms.openlocfilehash: 0e0f871b5d43508735e396224fdfd1a29b1e91c0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084127"
---
# <a name="creating-and-publishing-an-item"></a>Het maken en publiceren van een item

De PowerShell Gallery is de plek om te publiceren en stabiele PowerShell-modules, scripts en DSC-resources delen met de bredere gebruikersgemeenschap van PowerShell.

In dit artikel bevat informatie over de mechanics en belangrijke stappen voor het voorbereiden van een script of een module en deze publiceren naar de PowerShell Gallery. We raden ten zeerste aan dat u bekijkt de [Publicatierichtlijnen](../../concepts/publishing-guidelines.md) wilt weten hoe u om ervoor te zorgen dat de items die u publiceert grotere schaal worden geaccepteerd door gebruikers van de PowerShell Gallery.

De minimale vereisten voor het publiceren van een item naar de PowerShell Gallery zijn:

- Een PowerShell Gallery-account hebt en de API-sleutel die is gekoppeld aan deze
- Zorg ervoor dat metagegevens vereist is in uw artikel
- De eerste validatie-hulpprogramma's gebruiken om te controleren of dat het object is gereed om te publiceren
- Het item publiceren naar de PowerShell-galerie met de opdrachten Publish-Module en Publish-Script
- Reageren op vragen of opmerkingen over uw item

De PowerShell Gallery accepteert PowerShell-modules en PowerShell-scripts. Wanneer we naar scripts verwijzen, bedoelen we een PowerShell-script dat een enkel bestand is en geen deel uitmaakt van een grotere module.

## <a name="powershell-gallery-account-and-api-key"></a>PowerShell Gallery-Account en API-sleutel

Zie [het maken van een Account van de galerie met PowerShell](/powershell/gallery/how-to/publishing-packages/creating-an-account) voor informatie over het instellen van uw account PowerShell Gallery.

Als u een account hebt gemaakt, krijgt u de API-sleutel die nodig zijn voor het publiceren van een item. Nadat u zich aan met het account, wordt uw gebruikersnaam wordt weergegeven aan de bovenkant van de PowerShell Gallery-pagina's in plaats van Register. Op uw gebruikersnaam te klikken gaat u naar de pagina Mijn Account waar u de API-sleutel vinden.

Opmerking: De API-sleutel moet zo veilig als uw gebruikersnaam en wachtwoord worden behandeld.
Met deze sleutel kunt u of iemand anders, een item die in de PowerShell Gallery van jou bijwerken.
Het is raadzaam het bijwerken van de sleutel regelmatig, die kan worden uitgevoerd met behulp van de sleutel opnieuw instellen op de pagina My Account.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>Vereiste metagegevens voor objecten die zijn gepubliceerd naar de PowerShell Gallery

De PowerShell Gallery bevat informatie voor galerie-gebruikers die zijn opgehaald uit de metagegevensvelden die zijn opgenomen in het script of een module-manifest. Het maken of wijzigen van artikelen voor publicatie naar de PowerShell Gallery heeft een klein aantal vereisten voor de opgegeven in het itemmanifest van het.
We raden ten zeerste aan dat u de sectie met metagegevens van controleren de [Publicatierichtlijnen](../../concepts/publishing-guidelines.md) voor meer informatie over hoe u de beste informatie biedt aan gebruikers met uw items.

De [New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest) en [New-ScriptFileInfo](/powershell/module/PowerShellGet/New-ScriptFileInfo) cmdlets wordt de manifest-sjabloon maken bij u past, met tijdelijke aanduidingen voor alle elementen in het manifest.

Beide manifesten hebben twee secties die belangrijk voor het publiceren van de primaire sleutel gegevens en PSData gebied van PrivateData zijn. De primaire sleutel gegevens in een PowerShell-module-manifest is alles wat buiten de PrivateData-sectie. De set met primaire sleutels is gekoppeld aan de versie van PowerShell wordt gebruikt en niet-gedefinieerde worden niet ondersteund. PrivateData ondersteunt het toevoegen van nieuwe sleutels, zodat de elementen die specifiek zijn voor de PowerShell Gallery in PSData.


Manifest elementen belangrijkste in te vullen voor u naar de PowerShell-galerie publiceren-item zijn:

- Script of de naam van de Module - die zijn opgehaald uit de namen van de. Ps1 voor een script of het. PSD1 voor een module.
- Versie - dit is een vereiste primaire sleutel, indeling moet SemVer richtlijnen volgen. Zie de aanbevolen procedures voor meer informatie.
- Auteur: dit is een vereiste primaire sleutel, en bevat de naam moet worden gekoppeld aan het item.
Zie auteurs en eigenaren van onderstaande.
- Beschrijving: dit is een vereiste primaire sleutel gebruikt om te kort wordt uitgelegd wat dit item doet en eventuele vereisten voor het gebruik ervan
- ProjectURI - dit is een ten zeerste aanbevolen URI-veld in PSData waarmee een koppeling naar een Github-opslagplaats of soortgelijke locatie waar het doen van ontwikkeling op het item
- Labels - het wordt sterk aanbevolen voor het taggen van uw pakket op basis van de compatibiliteit met PSEditions en platforms. Zie voor meer informatie, de [Publicatierichtlijnen](../../concepts/publishing-guidelines.md#tag-your-package-with-the-compatible-pseditions-and-platforms).

Auteurs en eigenaren van de PowerShell Gallery items verwante concepten zijn echter niet altijd overeenkomen. Itemeigenaars zijn gebruikers met PowerShell Gallery-accounts die gemachtigd voor het onderhouden van het item. Mogelijk zijn er veel eigenaren die elk item kunnen bijwerken. De eigenaar is alleen beschikbaar vanuit de PowerShell Gallery en wordt verbroken als het item wordt gekopieerd van het ene systeem naar een andere. De auteur van is een tekenreeks is die is ingebouwd in het manifest gegevens, dus het is altijd onderdeel van het item. De aanbevelingen voor artikelen van Microsoft-producten zijn:

- Meerdere eigenaars, met ten minste één wordt de naam van het team dat het item produceert hebben
- De auteur van de naam van een bekende team (zoals Azure SDK-Team) of Microsoft Corporation


## <a name="pre-validate-your-item"></a>Het object vooraf valideren

Er zijn een paar hulpprogramma's die u uitvoeren op basis van uw code wilt voor het publiceren van uw item naar de PowerShell Gallery:

- [PowerShell-Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), deze bevindt zich in de PowerShell Gallery
- Voor modules, Test-ModuleManifest die deel uitmaakt van PowerShell
- Voor Test-ScriptFileInfo wordt geleverd met PowerShell-Get-scripts

[PowerShell-Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) is een hulpmiddel statische code die uw code om ervoor te zorgen dat deze worden gescand voldoet aan de eenvoudige PowerShell richtlijnen coderen. Dit hulpprogramma voorkomende en kritieke problemen in uw code wordt geïdentificeerd en regelmatig tijdens de ontwikkeling kunt u het item aan de slag met het publiceren moet worden uitgevoerd. PowerShell-Script Analyzer biedt een lijst met problemen geïdentificeerd als fouten, waarschuwingen en informatie. Alle fouten moeten worden opgelost voordat u naar de PowerShell Gallery publiceert. Waarschuwingen moeten worden gecontroleerd en de meeste moet worden opgelost. PowerShell-Script Analyzer wordt uitgevoerd telkens wanneer een item wordt gepubliceerd of in de PowerShell Gallery bijgewerkt. De galerie operationele team zal contact opnemen met itemeigenaars adres fouten die zijn gevonden.

Als de manifest-gegevens in uw item kan niet worden gelezen door de PowerShell Gallery-infrastructuur, wordt het niet mogelijk om te publiceren.
[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest) wordt catch veelvoorkomende problemen die kan leiden de module dat ertoe kan niet worden gebruikt wanneer deze is geïnstalleerd. Deze moet worden uitgevoerd voor elke module voordat u publiceert naar de PowerShell Gallery.

Evenzo, [Test ScriptFileInfo](/powershell/module/PowerShellGet/test-scriptfileinfo) valideert de metagegevens in een script, en moeten worden uitgevoerd op elk script (gepubliceerde is gescheiden van een module) voordat u publiceert naar de PowerShell Gallery.


## <a name="publishing-items"></a>Publiceren Items

Moet u de [Publish-Script](/powershell/module/PowerShellGet/publish-script) of [Publish-Module](/powershell/module/PowerShellGet/publish-module) items publiceren naar de PowerShell Gallery. Deze opdrachten vereisen:

- Het pad naar het item dat u wilt publiceren. Voor een module, gebruikt u de map met de naam van uw module. Als u een map met meerdere versies van dezelfde module opgeeft, moet u RequiredVersion opgeven.
- Een Nuget-API-sleutel. Dit is de API-sleutel gevonden op de pagina Mijn Account op de PowerShell Gallery.

De meeste van de andere opties op de opdrachtregel moet zich in het manifest gegevens voor het item dat u publiceren wilt, zodat u niet nodig om op te geven ze in de opdracht.

Om fouten te voorkomen, het is raadzaam dat u probeert de opdrachten met - WhatIf-Verbose, voordat u publiceert. Dit bespaart veel tijd sinds telkens wanneer u publiceren naar de PowerShell Gallery, moet u het versienummer in de manifest-sectie van het item bijwerken.

Voorbeelden zijn:

* `Publish-Module -Path ".\MyModule" -NugetAPIKey "GUID" -WhatIf -Verbose`
* `Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -WhatIf -Verbose`

De uitvoer zorgvuldig te controleren, en als er geen fouten of waarschuwingen, herhaalt u de opdracht zonder - WhatIf.

Alle items die worden gepubliceerd naar de PowerShell Gallery worden gescand op virussen en geanalyseerd met behulp van de PowerShell-Script Analyzer. Eventuele problemen die ontstaan op dat moment terug naar de publisher verzonden voor naamomzetting.

Wanneer u een item naar de PowerShell Gallery hebt gepubliceerd, moet u om te bekijken voor feedback over uw item.

- Zorg ervoor dat u het e-mailadres dat is gekoppeld aan het account dat wordt gebruikt om te publiceren bewaken. Gebruikers en het team van de PowerShell Gallery-bewerkingen krijgt feedback via dat account, met inbegrip van problemen uit de PSSA of antivirus scans. Als het e-mailaccount ongeldig is, of als ernstige problemen worden gerapporteerd aan het account en links niet gedurende langere tijd wordt opgelost, items kunnen worden beschouwd als afgeschaft en wordt verwijderd uit de PowerShell Gallery, zoals beschreven in onze [gebruiksvoorwaarden](https://www.powershellgallery.com/policies/Terms).
- U wordt aangeraden dat u zich abonneert op opmerkingen voor elk PowerShell Gallery-item dat u publiceert. Hiermee kunt u een melding als iedereen op de items in de PowerShell Gallery opmerkingen. Dit is optioneel, omdat hiervoor een account met LiveFyre maken.
