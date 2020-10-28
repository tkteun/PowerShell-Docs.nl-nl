---
ms.date: 09/11/2018
title: Pakket handmatig downloaden
description: Hierin wordt beschreven hoe u een pakket hand matig downloadt van de PowerShell Gallery.
ms.openlocfilehash: 50cd51d970bf21f8e957e60ceed2e98f306b57ab
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662279"
---
# <a name="manual-package-download"></a>Pakket handmatig downloaden

De PowerShell Gallery ondersteunt het downloaden van een pakket van de website rechtstreeks, zonder gebruik te maken van de PowerShellGet-cmdlets. U kunt elk pakket downloaden als een NuGet package ( `.nupkg` )-bestand, dat u vervolgens kunt kopiëren naar een interne opslag plaats.

> [!NOTE]
> Hand matige pakket downloads is **niet** bedoeld als vervanging voor de `Install-Module` cmdlet.
> Als u het pakket downloadt, wordt de module of het script niet geïnstalleerd. Er zijn geen afhankelijkheden opgenomen in het NuGet-pakket dat is gedownload. De volgende instructies zijn alleen bedoeld voor referentie doeleinden.

## <a name="using-manual-download-to-acquire-a-package"></a>Hand matig downloaden gebruiken om een pakket te verkrijgen

Elke pagina heeft een koppeling voor hand matig downloaden, zoals hier wordt weer gegeven:

![Pagina pakket weer geven met installatie opties](media/manual-download/packagedisplaypagewithpseditions.png)

Als u hand matig wilt downloaden, klikt u op **het onbewerkte nupkg-bestand downloaden** . Er wordt een kopie van het pakket gekopieerd naar de downloadmap voor uw browser met de naam `<name>.<version>.nupkg` .

Een NuGet-pakket is een ZIP-archief met extra bestanden met informatie over de inhoud van het pakket. In sommige browsers, zoals Internet Explorer, wordt de `.nupkg` bestands extensie automatisch vervangen door `.zip` . Als u het pakket wilt uitbreiden, wijzigt u de naam van het `.nupkg` bestand in `.zip` , indien nodig, en extraheert u vervolgens de inhoud naar een lokale map.

Een NuGet-pakket bestand bevat de volgende **NuGet-specifieke elementen** die geen deel uitmaken van de oorspronkelijke verpakte code:

- Een map met `_rels` de naam-bevat een `.rels` bestand waarin de afhankelijkheden worden weer gegeven
- Een map `package` met de naam: bevat de NuGet gegevens
- Een bestand met de naam `[Content_Types].xml` : beschrijft hoe extensies zoals PowerShellGet werken met NuGet
- Een bestand `<name>.nuspec` met de naam: bevat het meren deel van de meta gegevens

## <a name="installing-powershell-modules-from-a-nuget-package"></a>Power shell-modules installeren vanuit een NuGet-pakket

> [!NOTE]
> Deze instructies geven **niet** hetzelfde resultaat als het uitvoeren van `Install-Module` . Deze instructies voldoen aan de minimale vereisten. Deze zijn niet bedoeld als vervanging voor `Install-Module` .
> Sommige stappen die worden uitgevoerd door, `Install-Module` zijn niet opgenomen.

De eenvoudigste manier is om de NuGet-specifieke elementen uit de map te verwijderen. Als u de elementen verwijdert, blijft de Power shell-code die is gemaakt door de auteur van het pakket.
Zie voor de lijst met NuGet-elementen [hand matig downloaden gebruiken om een pakket te verkrijgen](#using-manual-download-to-acquire-a-package).

De stappen zijn als volgt:

1. Deblokkeren van het door internet gedownloade NuGet package ( `.nupkg` )-bestand, bijvoorbeeld met behulp van de `Unblock-File -Path C:\Downloads\module.nupkg` cmdlet.
1. Pak de inhoud van het NuGet-pakket uit naar een lokale map.
1. Verwijder de NuGet elementen uit de map.
1. Wijzig de naam van de map. De naam van de standaardmap is doorgaans `<name>.<version>` . De versie kan bevatten `-prerelease` als de module is gelabeld als een voorlopige versie. Wijzig de naam van de map in alleen de module. `azurerm.storage.5.0.4-preview` wordt bijvoorbeeld `azurerm.storage`.
1. Kopieer de map naar een van de mappen in de `$env:PSModulePath value` . `$env:PSModulePath` is een door punt komma's gescheiden set paden waarin Power shell naar modules moet zoeken.

> [!IMPORTANT]
> De hand matige down load bevat geen afhankelijkheden die nodig zijn voor de module. Als het pakket afhankelijkheden heeft, moeten deze op het systeem worden geïnstalleerd om deze module correct te laten werken. Het PowerShell Gallery toont alle afhankelijkheden die vereist zijn voor het pakket.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>Power shell-scripts installeren vanuit een NuGet-pakket

> [!NOTE]
> Deze instructies geven **niet** hetzelfde resultaat als het uitvoeren van `Install-Script` . Deze instructies voldoen aan de minimale vereisten. Deze zijn niet bedoeld als vervanging voor `Install-Script` .

De eenvoudigste manier is om het NuGet-pakket uit te pakken en vervolgens het script rechtstreeks te gebruiken.

De stappen zijn als volgt:

1. Deblokkeren van het door internet gedownloade NuGet package ( `.nupkg` )-bestand, bijvoorbeeld met behulp van de `Unblock-File -Path C:\Downloads\package.nupkg` cmdlet.
1. Pak de inhoud van het NuGet-pakket uit.
1. Het `.PS1` bestand in de map kan rechtstreeks vanuit deze locatie worden gebruikt.
1. U kunt de NuGet-specifieke elementen in de map verwijderen.

Zie voor de lijst met NuGet-elementen [hand matig downloaden gebruiken om een pakket te verkrijgen](#using-manual-download-to-acquire-a-package).

> [!IMPORTANT]
> De hand matige down load bevat geen afhankelijkheden die nodig zijn voor de module. Als het pakket afhankelijkheden heeft, moeten deze op het systeem worden geïnstalleerd om deze module correct te laten werken. Het PowerShell Gallery toont alle afhankelijkheden die vereist zijn voor het pakket.
