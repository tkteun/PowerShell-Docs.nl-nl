---
ms.date: 06/12/2017
title: Galerie Zoek syntaxis
description: In dit artikel wordt de gebruikers interface beschreven die wordt gebruikt om te zoeken naar inhoud in de PowerShell Gallery.
ms.openlocfilehash: 7ad486095647f99056b37c2ca1a50db099a166c0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661368"
---
# <a name="gallery-search-syntax"></a>Galerie Zoek syntaxis

U kunt de PowerShell Gallery doorzoeken met behulp [van de website van PowerShell Gallery](https://www.powershellgallery.com/). PowerShell Gallery website biedt een tekst SearchBox waar u woorden, zinsdelen en trefwoord expressies kunt gebruiken om de zoek resultaten te beperken.

## <a name="search-by-keywords"></a>Zoeken op tref woorden

```Syntax
dsc azure sql
```

Zoek pogingen om relevante documenten te vinden met alle drie tref woorden en retour neren overeenkomende documenten.

## <a name="search-using-phrases-and-keywords"></a>Zoeken met behulp van zinsdelen en tref woorden

```Syntax
"azure sql" deployment
```

Als u een woord groep tussen aanhalings tekens ("") invoert, wijzigt u de zoek opdracht om te zoeken naar de specifieke woord groep in plaats van afzonderlijke tref woorden. Overeenkomende documenten moeten doorgaans de exacte woord groep ' Azure SQL ' bevatten, met inbegrip van variaties op kapitalisatie zoals ' Azure SQL ', en bevatten meestal het woord ' implementatie '.

## <a name="filtering-on-fields"></a>Velden filteren

U kunt zoeken naar een specifieke pakket-ID (of ' id ' of ' id '), of bepaalde andere velden door voor voegsel zoek termen voor te stellen met de veld naam.

Momenteel zijn de Doorzoek bare velden ' id ', ' versie ', ' Tags ', ' Auteur ', ' eigenaar ', ' functions ', ' cmdlets ', ' DscResources ' en ' PowerShellVersion '.

- ID is de naam die u in de-console gebruikt.
- Titel is wat wordt weer gegeven aan de bovenkant van de pakket pagina in de zoek resultaten.

## <a name="examples"></a>Voorbeelden

```Syntax
ID:PSReadline
```

Hiermee zoekt u pakketten met een ID die ' PSReadline ' bevat.

```Syntax
Id:"AzureRM.Profile"
```

is een andere manier om pakketten te vinden met ' AzureRM. profile ' in hun ID-veld.

Het filter ' id ' is een overeenkomende subtekenreeks, dus als u zoekt naar het volgende:

```Syntax
Id:"azure"
```

Dit biedt resultaten die AzureRM. profile en Azure. Storage bevatten.

U kunt ook zoeken naar meerdere tref woorden in één veld.

```Syntax
id:azure tags:intellisense
```

En u kunt Zoek opdrachten voor zinsdelen uitvoeren met dubbele aanhalings tekens:

```Syntax
id:"azure.storage"
```

Om te zoeken in alle pakketten met DSC-tag.

```Syntax
Tags:DSC
```

Om te zoeken in alle pakketten met de opgegeven functie.

```Syntax
Functions:Get-TreeSize
```

Om alle pakketten met de opgegeven cmdlet te doorzoeken.

```Syntax
Cmdlets:Get-AzureRmEnvironment
```

Om te zoeken in alle pakketten met de opgegeven naam van de DSC-resource.

```Syntax
DscResources:xArchive
```

Zoeken naar alle pakketten met de opgegeven PowerShellVersion

```Syntax
PowerShellVersion:2.0
```

Ten slotte, als u een veld gebruikt dat niet wordt ondersteund, zoals opdrachten, worden deze alleen genegeerd en worden alle velden doorzocht. De volgende query

```Syntax
commands:blobs storage
```

Wordt precies hetzelfde geïnterpreteerd als deze query:

```Syntax
blobs storage
```
