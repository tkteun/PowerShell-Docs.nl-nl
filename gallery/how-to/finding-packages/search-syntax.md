---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Galerie Zoeksyntaxis
ms.openlocfilehash: 9aadb6771c85845cc3fa05cb56f0194b060d1c1b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004040"
---
# <a name="gallery-search-syntax"></a>Galerie Zoeksyntaxis

PowerShell-galerie biedt een tekst searchbox waar u woorden, zinnen en sleutelwoord expressies zoekresultaten verfijnen kunt gebruiken.

## <a name="search-by-keywords"></a>Zoeken op trefwoorden

    dsc azure sql

Zoeken wordt de aanbevolen inspanningen om te zoeken naar relevante documenten met alle 3 trefwoorden doen en overeenkomende documenten retourneren.

## <a name="search-using-phrases-and-keywords"></a>Zoeken met behulp van zinnen en trefwoorden

    "azure sql" deployment

Een zin invoeren tussen aanhalingstekens ("") Wijzig de zoekopdracht om te zoeken naar de specifieke woordgroep in plaats van afzonderlijke trefwoorden.
Overeenkomende documenten, moet de exacte woordgroep 'azure sql', met inbegrip van variaties op hoofdlettergebruik bijvoorbeeld gewoonlijk bevatten 'Azure SQL', en ook meestal het woord 'implementatie' bevatten.

## <a name="filtering-on-fields"></a>Filteren op velden

U kunt zoeken naar een specifieke pakket-ID (of 'Id' of 'id') of bepaalde andere velden door het voorvoegsel zoektermen met de veldnaam.

De doorzoekbare velden zijn momenteel 'Id', 'Version', 'Tags', 'Auteur', 'Eigenaar', 'Functies', 'Cmdlets', 'DscResources' en 'PowerShellVersion'.

[Wat is het verschil tussen ID en titel? -ID is de naam die u in de console gebruikt. De titel is wat wordt weergegeven aan de bovenkant van de pakketpagina in de lijst met zoekresultaten.]

## <a name="examples"></a>Voorbeelden

    ID:"PSReadline"
    id:"AzureRM.Profile"

zoekt naar pakketten met 'PSReadline' of 'AzureRM.Profile' in het id-veld respectievelijk.

    Id:"AzureRM.Profile"

is een andere manier om pakketten met 'AzureRM.Profile' niet vinden in het id-veld.

Het filter 'Id' is een subtekenreeks, dus als u zoekt voor het volgende:

    Id:"azure"

U krijgt de resultaten, zoals 'AzureRM.Profile' en 'Azure.Storage'.

U kunt ook zoeken naar meerdere trefwoorden in één veld. Of Combineer en velden overeen laten komen.

    id:azure tags:intellisense
    id:azure id:storage

En u kunt woordgroep zoekopdrachten uitvoeren:

    id:"azure.storage"


Om te zoeken naar alle pakketten zoekt met DSC-tag.

    Tags:"DSC"

Om te zoeken naar alle pakketten zoekt met de opgegeven functie.

    Functions:"Update-AzureRM"

Om te zoeken naar alle pakketten met de opgegeven cmdlet.

    Cmdlets:"Get-AzureRmEnvironment"

Om te zoeken naar alle pakketten met de opgegeven naam van de DSC-Resource.

    DscResources:"xArchive"

Om te zoeken naar alle pakketten zoekt met de opgegeven PowerShellVersion

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


Ten slotte, als u een veld die wordt niet ondersteund, zoals 'opdrachten', gebruiken we net negeren en zoeken naar alle velden. De volgende query uit

    commands:blobs storage

Wordt geïnterpreteerd precies hetzelfde als deze query:

    blobs storage
