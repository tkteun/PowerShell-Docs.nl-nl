---
ms.date: 06/12/2017
title: Een item maken en publiceren
description: In dit artikel worden de mechanismen beschreven en de belangrijkste stappen voor het voorbereiden van een script of module, en het publiceren naar de PowerShell Gallery
ms.openlocfilehash: be846799aff71d38bdd0c98b3f43eaee5aef7798
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662505"
---
# <a name="creating-and-publishing-an-item"></a>Een item maken en publiceren

De PowerShell Gallery is de plaats voor het publiceren en delen van stabiele Power shell-modules, scripts en desired state Configuration (DSC)-resources met de bredere gebruikers community van Power shell.

In dit artikel worden de mechanismen beschreven en de belangrijkste stappen voor het voorbereiden van een script of module, en het publiceren naar de PowerShell Gallery. We raden u ten zeerste aan de [richt lijnen voor publicatie](../../concepts/publishing-guidelines.md) te bekijken om te begrijpen hoe u ervoor kunt zorgen dat de items die u publiceert, veel worden geaccepteerd door PowerShell Gallery gebruikers.

De minimale vereisten voor het publiceren van een item naar de PowerShell Gallery zijn:

- Een PowerShell Gallery-account en de bijbehorende API-sleutel hebben
- Zorg ervoor dat de vereiste meta gegevens zich in uw item bevindt
- Gebruik de Prevalidatie-hulpprogram ma's om ervoor te zorgen dat uw item gereed is voor publicatie
- Publiceer het item naar het PowerShell Gallery met behulp van de Publish-Module-en Publish-Script-opdrachten
- Reageer op vragen of problemen met betrekking tot uw object

De PowerShell Gallery accepteert Power shell-modules en Power shell-scripts. Wanneer we naar scripts verwijzen, betekenen we een Power shell-script dat één bestand is en geen deel uitmaakt van een grotere module.

## <a name="powershell-gallery-account-and-api-key"></a>PowerShell Gallery account en API-sleutel

Zie [een PowerShell Gallery account maken](creating-an-account.md) voor het instellen van uw PowerShell Gallery-account.

Zodra u een account hebt gemaakt, kunt u de API-sleutel ophalen die nodig is voor het publiceren van een item. Nadat u zich hebt aangemeld met het account, wordt de gebruikers naam weer gegeven aan de bovenkant van de PowerShell Gallery pagina's in plaats van bij het registreren. Als u op uw gebruikers naam klikt, gaat u naar de pagina Mijn account, waar u de API-sleutel vindt.

> [!IMPORTANT]
> De API-sleutel moet worden beschouwd als veilig als uw aanmeldings-en wacht woord. Met deze sleutel kunt u, of iemand anders, elk item dat u in de PowerShell Gallery bezit, bijwerken. We raden u aan de sleutel regel matig bij te werken. dit kunt u doen met behulp van de sleutel reset op uw mijn account pagina.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>Vereiste meta gegevens voor items die zijn gepubliceerd op de PowerShell Gallery

De PowerShell Gallery biedt informatie over galerie gebruikers die zijn getekend vanuit meta gegevens velden die zijn opgenomen in het script of module manifest. Het maken of wijzigen van items voor publicatie in de PowerShell Gallery heeft een kleine set vereisten voor informatie die is opgegeven in het item manifest. We raden u ten zeerste aan de sectie meta gegevens van het item van de [publicatie richtlijnen](../../concepts/publishing-guidelines.md) te bekijken om te leren hoe u de beste informatie kunt leveren aan gebruikers met uw items.

Met de cmdlets [New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest) en [New-ScriptFileInfo](/powershell/module/PowerShellGet/New-ScriptFileInfo) wordt de manifest sjabloon voor u gemaakt, met tijdelijke aanduidingen voor alle manifest elementen.

Beide manifesten hebben twee secties die belang rijk zijn voor het publiceren, het primaire-sleutel gegevens-en PSData-gebied van PrivateData. De gegevens van de primaire sleutel in een Power shell-module manifest bevinden zich alles buiten het gedeelte PrivateData. De set primaire sleutels is gekoppeld aan de versie van Power shell die in gebruik is, en niet-gedefinieerd worden niet ondersteund. PrivateData biedt ondersteuning voor het toevoegen van nieuwe sleutels, waardoor de elementen die specifiek zijn voor de PowerShell Gallery zich in PSData bevinden.

Manifest elementen die het belangrijkst zijn voor het invoeren van items die u naar de PowerShell Gallery publiceert, zijn:

- Script of module naam-die worden opgehaald uit de namen van de. PS1 voor een script of de. PSD1 voor een module.
- Versie: dit is een vereiste primaire sleutel. de indeling moet voldoen aan de SemVer-richt lijnen. Zie Aanbevolen procedures voor meer informatie.
- Auteur: dit is een vereiste primaire sleutel en bevat de naam die aan het item moet worden gekoppeld. Zie de onderstaande auteurs en eigen aren.
- Beschrijving: dit is een vereiste primaire sleutel die wordt gebruikt om een korte uitleg te geven over dit item en eventuele vereisten voor het gebruik ervan
- ProjectURI: dit is een sterk aanbevolen URI-veld in PSData dat een koppeling biedt naar een github opslag plaats of een vergelijk bare locatie waar u het item ontwikkelt
- Tags: het is een sterke aanbeveling om uw pakket te labelen op basis van de compatibiliteit met PSEditions en platformen. Zie voor meer informatie de [richt lijnen voor publicatie](../../concepts/publishing-guidelines.md#tag-your-package-with-the-compatible-pseditions-and-platforms).

Auteurs en eigen aren van PowerShell Gallery items zijn gerelateerde concepten, maar komen niet altijd overeen. Eigen aren van items zijn gebruikers met PowerShell Gallery accounts die gemachtigd zijn om het item te onderhouden. Mogelijk zijn er veel eigen aren die elk item kunnen bijwerken. De eigenaar is alleen beschikbaar via de PowerShell Gallery en gaat verloren als het item wordt gekopieerd van het ene systeem naar het andere. Auteur is een teken reeks die is ingebouwd in de manifest gegevens, zodat deze altijd deel uitmaakt van het item. De aanbevelingen voor items van micro soft-producten zijn:

- Meerdere eigen aren hebben, met ten minste één naam van het team dat het item produceert
- Laat de auteur een bekende team naam (zoals Azure SDK-team) of micro soft Corporation

## <a name="pre-validate-your-item"></a>Uw item vooraf valideren

Er zijn een aantal hulpprogram ma's die u moet uitvoeren op uw code voordat u uw item naar de PowerShell Gallery publiceert:

- [Power shell-script analyse](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), die zich in de PowerShell Gallery bevindt
- Voor modules Test-ModuleManifest die deel uitmaken van Power shell
- Voor scripts, Test-ScriptFileInfo die worden geleverd met Power shell Get

[Power shell script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) is een hulp programma voor statische code analyse waarmee uw code wordt gescand zodat deze voldoet aan de basis richtlijnen voor Power shell-code ring. Dit hulp programma identificeert veelvoorkomende en kritieke problemen in uw code en moet regel matig worden uitgevoerd tijdens de ontwikkeling om u te helpen uw item gereed te maken voor publicatie. Power shell script Analyzer bevat een lijst met problemen die zijn geïdentificeerd als fouten, waarschuwingen en informatie. Alle fouten moeten worden opgelost voordat u naar de PowerShell Gallery publiceert. Waarschuwingen moeten worden gecontroleerd en het meeste moet worden opgelost. Power shell script Analyzer wordt uitgevoerd telkens wanneer een item wordt gepubliceerd of bijgewerkt in de PowerShell Gallery. Het Galerie bewerkings team neemt contact op met de eigenaar van het item om de gevonden fouten te verhelpen.

Als de informatie in het manifest van uw item niet kan worden gelezen door de PowerShell Gallery-infra structuur, kunt u deze niet publiceren.
Met [test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest) worden veelvoorkomende problemen onderschept die ertoe leiden dat de module niet bruikbaar is wanneer deze wordt geïnstalleerd. Deze moet voor elke module worden uitgevoerd voordat deze naar de PowerShell Gallery wordt gepubliceerd.

Op dezelfde manier wordt met [test-ScriptFileInfo](/powershell/module/PowerShellGet/test-scriptfileinfo) de meta gegevens in een script gevalideerd en moeten ze worden uitgevoerd op elk script (dat afzonderlijk wordt gepubliceerd vanuit een module) voordat het naar de PowerShell Gallery wordt gepubliceerd.

## <a name="publishing-items"></a>Items publiceren

U moet de publicatie [-script](/powershell/module/PowerShellGet/publish-script) of [Publish-module](/powershell/module/PowerShellGet/publish-module) gebruiken om items te publiceren naar de PowerShell Gallery. Deze opdrachten zijn beide vereist:

- Het pad naar het item dat u wilt publiceren. Voor een module gebruikt u de map met de naam voor uw module. Als u een map opgeeft die meerdere versies van dezelfde module bevat, moet u RequiredVersion opgeven.
- Een Nuget-API-sleutel. Dit is de API-sleutel die is gevonden op de pagina Mijn account op het PowerShell Gallery.

De meeste andere opties in de opdracht regel moeten zich in de manifest gegevens bevinden voor het item dat u publiceert. u hoeft deze dus niet op te geven in de opdracht.

Om fouten te voor komen, wordt het ten zeerste aangeraden om de opdrachten te gebruiken met-WhatIf-verbose voordat ze worden gepubliceerd. Hierdoor bespaart u veel tijd, omdat elke keer dat u naar de PowerShell Gallery publiceert, het versie nummer moet worden bijgewerkt in de sectie manifest van het item.

Voor beelden zijn:

* `Publish-Module -Path ".\MyModule" -NugetAPIKey "GUID" -WhatIf -Verbose`
* `Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -WhatIf -Verbose`

Controleer de uitvoer zorgvuldig en als er geen fouten of waarschuwingen worden weer gegeven, herhaalt u de opdracht zonder-WhatIf.

Alle items die worden gepubliceerd naar de PowerShell Gallery worden gescand op virussen en worden geanalyseerd met behulp van Power shell-script analyse. Eventuele problemen die zich op dat moment voordoen, worden teruggestuurd naar de Publisher voor een oplossing.

Zodra u een item naar de PowerShell Gallery hebt gepubliceerd, moet u controleren of u feedback hebt over uw object.

- Zorg ervoor dat u het e-mail adres bewaakt dat is gekoppeld aan het account dat wordt gepubliceerd. Gebruikers en het PowerShell Gallery Operations-team geven feedback via dat account, met inbegrip van problemen met de PSSA of antivirus scans. Als het e-mail account ongeldig is of als er ernstige problemen aan het account zijn gerapporteerd en gedurende lange tijd niet zijn opgelost, kunnen de items worden beschouwd als ingetrokken en uit de PowerShell Gallery worden verwijderd zoals beschreven in de [gebruiks voorwaarden](https://www.powershellgallery.com/policies/Terms).
