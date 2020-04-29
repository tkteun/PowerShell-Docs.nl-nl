---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: Galerie Zoek syntaxis
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71329153"
---
# <a name="gallery-search-syntax"></a>Galerie Zoek syntaxis

U kunt de PowerShell Gallery doorzoeken met behulp [van de website van PowerShell Gallery](https://www.powershellgallery.com/).
PowerShell Gallery website biedt een tekst SearchBox waar u woorden, zinsdelen en trefwoord expressies kunt gebruiken om de zoek resultaten te beperken.

## <a name="search-by-keywords"></a>Zoeken op tref woorden

    dsc azure sql

Zoek pogingen om relevante documenten te vinden met alle drie tref woorden en retour neren overeenkomende documenten.

## <a name="search-using-phrases-and-keywords"></a>Zoeken met behulp van zinsdelen en tref woorden

    "azure sql" deployment

Als u een woord groep tussen aanhalings tekens ("") invoert, wijzigt u de zoek opdracht om te zoeken naar de specifieke woord groep in plaats van afzonderlijke tref woorden.
Overeenkomende documenten moeten doorgaans de exacte woord groep ' Azure SQL ' bevatten, met inbegrip van variaties op kapitalisatie zoals ' Azure SQL ', en bevatten meestal het woord ' implementatie '.

## <a name="filtering-on-fields"></a>Velden filteren

U kunt zoeken naar een specifieke pakket-ID (of ' id ' of ' id '), of bepaalde andere velden door voor voegsel zoek termen voor te stellen met de veld naam.

Momenteel zijn de Doorzoek bare velden ' id ', ' versie ', ' Tags ', ' Auteur ', ' eigenaar ', ' functions ', ' cmdlets ', ' DscResources ' en ' PowerShellVersion '.

[Wat is het verschil tussen ID en titel? ID is de naam die u in de-console gebruikt. Titel wordt weer gegeven boven aan de pakket pagina in Zoek resultaten.]

## <a name="examples"></a>Voorbeelden

    ID:PSReadline
    
Hiermee zoekt u pakketten met een ID die ' PSReadline ' bevat.

    Id:"AzureRM.Profile"

is een andere manier om pakketten te vinden met ' AzureRM. profile ' in hun ID-veld.

Het filter ' id ' is een overeenkomende subtekenreeks, dus als u zoekt naar het volgende:

    Id:"azure"

Dit biedt resultaten die AzureRM. profile en Azure. Storage bevatten.

U kunt ook zoeken naar meerdere tref woorden in één veld. 

    id:azure tags:intellisense

En u kunt Zoek opdrachten voor zinsdelen uitvoeren met dubbele aanhalings tekens:

    id:"azure.storage"

Om te zoeken in alle pakketten met DSC-tag.

    Tags:DSC

Om te zoeken in alle pakketten met de opgegeven functie.

    Functions:Get-TreeSize

Om alle pakketten met de opgegeven cmdlet te doorzoeken.

    Cmdlets:Get-AzureRmEnvironment

Om te zoeken in alle pakketten met de opgegeven naam van de DSC-resource.

    DscResources:xArchive

Zoeken naar alle pakketten met de opgegeven PowerShellVersion

    PowerShellVersion:2.0

Ten slotte, als u een veld gebruikt dat niet wordt ondersteund, zoals opdrachten, worden deze alleen genegeerd en worden alle velden doorzocht. De volgende query

    commands:blobs storage

Wordt precies hetzelfde geïnterpreteerd als deze query:

    blobs storage
