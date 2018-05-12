---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: Galerie Zoeksyntaxis
ms.openlocfilehash: 4c0e357957ef970826ee90868db78ac07a14c804
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/10/2018
---
# <a name="gallery-search-syntax"></a>Galerie Zoeksyntaxis

PowerShell Gallery biedt een tekst searchbox waar u woorden, zinnen en sleutelwoord expressies gebruiken kunt om de zoekresultaten te beperken.

## <a name="search-by-keywords"></a>Zoeken met trefwoorden

    dsc azure sql

Zoekopdracht doen haar uiterste best om relevante documenten met alle 3 trefwoorden te zoeken, en overeenkomende documenten retourneren.

## <a name="search-using-phrases-and-keywords"></a>Zoeken met zinnen en trefwoorden

    "azure sql" deployment

Een wachtwoordzin invoeren tussen aanhalingstekens ("") Wijzig de zoekopdracht op zoek naar de specifieke zinsdeel in plaats van afzonderlijke trefwoorden.
Documenten die overeenkomt met moet de exacte woordgroep 'azure sql', met inbegrip van variaties op hoofdlettergebruik bijvoorbeeld meestal bevatten 'Azure SQL', en ook meestal het woord 'implementatie' bevatten.

## <a name="filtering-on-fields"></a>Filteren op velden

U kunt zoeken naar een specifiek item-ID (of 'Id' of 'id') of bepaalde andere velden door Mining zoektermen met de naam van het veld.

De doorzoekbare velden zijn momenteel 'Id', 'Version', 'Labels', 'Auteur', 'Eigenaar', 'Functies', 'Cmdlets', 'DscResources' en 'PowerShellVersion'.

[Wat is het verschil tussen ID en titel? ID is de naam die u in de console gebruikt. Titel is wat wordt weergegeven boven aan de pagina item in de zoekresultaten.]

## <a name="examples"></a>Voorbeelden

    ID:"PSReadline"
    id:"AzureRM.Profile"

zoekt respectievelijk artikelen met 'PSReadline' of 'AzureRM.Profile' in het id-veld.

    Id:"AzureRM.Profile"

is een andere manier om items met 'AzureRM.Profile' niet vinden in het id-veld.

Het filter 'Id' is een subtekenreeks, dus als u zoekt naar het volgende:

    Id:"azure"

U krijgt resultaten zoals 'AzureRM.Profile' en 'Azure.Storage'.

U kunt ook zoeken naar meerdere trefwoorden in één veld. Of meng en velden overeenkomen.

    id:azure tags:intellisense
    id:azure id:storage

En u kunt woordgroep zoekopdrachten uitvoeren:

    id:"azure.storage"


Om te zoeken in alle items met DSC-tag.

    Tags:"DSC"

Om te zoeken in alle items met de opgegeven functie.

    Functions:"Update-AzureRM"

Om te zoeken in alle items met de opgegeven cmdlet.

    Cmdlets:"Get-AzureRmEnvironment"

Om te zoeken in alle items met de opgegeven naam van de DSC-Resource.

    DscResources:"xArchive"

Alle items met de opgegeven PowerShellVersion zoeken

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


Ten slotte, als u een veld die wordt niet ondersteund, zoals 'opdrachten', gebruiken we net negeren, en zoeken van alle velden. Zodat de volgende query

    commands:blobs storage

Is geïnterpreteerd exact hetzelfde zijn als deze query:

    blobs storage