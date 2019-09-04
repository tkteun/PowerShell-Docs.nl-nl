---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galerie, Power shell, psgallery
title: Pakket handmatig downloaden
ms.openlocfilehash: c0a96e866dfd27f9b2170ea540ec6dd0c67701fd
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215457"
---
# <a name="manual-package-download"></a>Pakket handmatig downloaden

De PowerShell Gallery ondersteunt het downloaden van een pakket van de website rechtstreeks, zonder gebruik te maken van de PowerShellGet-cmdlets. U kunt elk pakket downloaden als een NuGet package (`.nupkg`)-bestand, dat u vervolgens kunt kopiëren naar een interne opslag plaats.

> [!NOTE]
> Hand matige pakket downloads is **niet** bedoeld als vervanging voor de `Install-Module` cmdlet.
> Als u het pakket downloadt, wordt de module of het script niet geïnstalleerd. Er zijn geen afhankelijkheden opgenomen in het NuGet-pakket dat is gedownload. De volgende instructies zijn alleen bedoeld voor referentie doeleinden.

## <a name="using-manual-download-to-acquire-a-package"></a>Hand matig downloaden gebruiken om een pakket te verkrijgen

Elke pagina heeft een koppeling voor hand matig downloaden, zoals hier wordt weer gegeven:

![Hand matig downloaden](../../Images/packagedisplaypagewithpseditions.png)

Als u hand matig wilt downloaden, klikt u op **het onbewerkte nupkg-bestand downloaden**. Er wordt een kopie van het pakket gekopieerd naar de downloadmap voor uw browser met de naam `<name>.<version>.nupkg`.

Een NuGet-pakket is een ZIP-archief met extra bestanden met informatie over de inhoud van het pakket. In sommige browsers, zoals Internet Explorer, wordt de `.nupkg` bestands extensie automatisch `.zip`vervangen door. Als u het pakket wilt uitbreiden, `.nupkg` wijzigt u `.zip`de naam van het bestand in, indien nodig, en extraheert u vervolgens de inhoud naar een lokale map.

Een NuGet-pakket bestand bevat de volgende **NuGet-specifieke elementen** die geen deel uitmaken van de oorspronkelijke verpakte code:

- Een map met `_rels` de naam- `.rels` bevat een bestand waarin de afhankelijkheden worden weer gegeven
- Een map met `package` de naam: bevat de NuGet gegevens
- Een bestand met `[Content_Types].xml` de naam: beschrijft hoe extensies zoals PowerShellGet werken met NuGet
- Een bestand met `<name>.nuspec` de naam: bevat het meren deel van de meta gegevens

## <a name="installing-powershell-modules-from-a-nuget-package"></a>Power shell-modules installeren vanuit een NuGet-pakket

> [!NOTE]
> Deze instructies geven **niet** hetzelfde resultaat als het uitvoeren `Install-Module`van. Deze instructies voldoen aan de minimale vereisten. Deze zijn niet bedoeld als vervanging voor `Install-Module`.
> Sommige stappen die worden `Install-Module` uitgevoerd door, zijn niet opgenomen.

De eenvoudigste manier is om de NuGet-specifieke elementen uit de map te verwijderen. Als u de elementen verwijdert, blijft de Power shell-code die is gemaakt door de auteur van het pakket.
Zie voor de lijst met NuGet-elementen [hand matig downloaden gebruiken om een pakket te verkrijgen](#using-manual-download-to-acquire-a-package).

De stappen zijn als volgt:

1. Pak de inhoud van het NuGet-pakket uit naar een lokale map.
2. Verwijder de NuGet elementen uit de map.
3. Wijzig de naam van de map. De naam van de standaardmap is `<name>.<version>`doorgaans. De versie kan bevatten `-prerelease` als de module is gelabeld als een voorlopige versie. Wijzig de naam van de map in alleen de module. Wordt bijvoorbeeld `azurerm.storage.5.0.4-preview`. `azurerm.storage`
4. Kopieer de map naar een van de mappen in de `$env:PSModulePath value`. `$env:PSModulePath`is een door punt komma's gescheiden set paden waarin Power shell naar modules moet zoeken.

> [!IMPORTANT]
> De hand matige down load bevat geen afhankelijkheden die nodig zijn voor de module. Als het pakket afhankelijkheden heeft, moeten deze op het systeem worden geïnstalleerd om deze module correct te laten werken. Het PowerShell Gallery toont alle afhankelijkheden die vereist zijn voor het pakket.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>Power shell-scripts installeren vanuit een NuGet-pakket

> [!NOTE]
> Deze instructies geven **niet** hetzelfde resultaat als het uitvoeren `Install-Script`van. Deze instructies voldoen aan de minimale vereisten. Deze zijn niet bedoeld als vervanging voor `Install-Script`.

De eenvoudigste manier is om het NuGet-pakket uit te pakken en vervolgens het script rechtstreeks te gebruiken.

De stappen zijn als volgt:

1. Pak de inhoud van het NuGet-pakket uit.
2. Het `.PS1` bestand in de map kan rechtstreeks vanuit deze locatie worden gebruikt.
3. U kunt de NuGet-specifieke elementen in de map verwijderen.

Zie voor de lijst met NuGet-elementen [hand matig downloaden gebruiken om een pakket te verkrijgen](#using-manual-download-to-acquire-a-package).

> [!IMPORTANT]
> De hand matige down load bevat geen afhankelijkheden die nodig zijn voor de module. Als het pakket afhankelijkheden heeft, moeten deze op het systeem worden geïnstalleerd om deze module correct te laten werken. Het PowerShell Gallery toont alle afhankelijkheden die vereist zijn voor het pakket.
