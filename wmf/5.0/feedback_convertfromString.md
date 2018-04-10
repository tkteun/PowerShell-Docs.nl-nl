---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: cedda61241df4965fe5db723f03e3497f046fa44
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a>Gestructureerd objecten buiten tekenreeks uitpakken en parseren
Dit brengt ook aanvullende functionaliteit voor de cmdlet ConverterenVan-tekenreeks:

-   Hiermee verwijdert u de teksteigenschap gebied standaard. U kunt opnemen met de parameter - IncludeExtent.

-   Veel learning-algoritme foutoplossingen van MVP en community feedback.

-   Een nieuwe UpdateTemplate - parameter voor de resultaten van het leeralgoritme in een opmerking in het sjabloonbestand op te slaan. Hierdoor kunt u de learning verwerken (de traagste fase) een eenmalige kosten. Het omzetten van tekenreeks uitgevoerd met een sjabloon met de gecodeerde learning-algoritme is nu bijna onmiddellijk.


<a name="extract-and-parse-structured-objects-out-of-string-content"></a>Uitpakken en parseren van gestructureerde objecten uit de inhoud van de tekenreeks
----------------------------------------------------------

In samenwerking met [Microsoft Research](http://research.microsoft.com/), een nieuwe **ConverterenVan-tekenreeks** cmdlet is toegevoegd.

Deze cmdlet ondersteunt twee modi: basic gescheiden parseren en automatisch gegenereerd voorbeeld aangestuurde parseren.

Parseren standaard gescheiden splitst de invoer op witruimte en worden de namen van eigenschappen wordt toegewezen aan de resulterende groepen. U kunt het scheidingsteken aanpassen:

> 1 \[C:\\temp\] &gt; &gt; 'Hallo wereld' | ConverterenVan-tekenreeks | Format-Table-automatisch

P1    P2
--    --

De cmdlet ondersteunt ook automatisch gegenereerde voorbeeld aangestuurde parseren op basis van de [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) onderzoek werk in [Microsoft Research](http://research.microsoft.com).

Houd rekening met een op tekst gebaseerde adresboek om te beginnen:

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA

Kopieer een paar voorbeelden naar een bestand, dat u als uw sjabloon gebruiken gaat:

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA



Plaats accolades gebruiken om gegevens die u ophalen wilt, een naam geven als u doet dit. Omdat de **naam** eigenschap (en de andere eigenschappen die zijn gekoppeld) kunnen meerdere keren worden weergegeven, gebruikt u een sterretje (\*) om aan te geven dat dit resulteert in meerdere records (in plaats van een aantal eigenschappen in te pakken op een record):

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

In deze reeks voorbeelden **ConverterenVan-tekenreeks** uitvoer op basis van het object automatisch nu uit invoerbestanden met vergelijkbare structuur kan extraheren.

> 2 \[C:\\temp\]
>
> &gt;&gt; Get-inhoud. \\addresses.output.txt | ConverterenVan-tekenreeks - sjabloonbestand. \\addresses.template.txt | &gt; &gt; &gt; Format-Table-automatisch
>
> ExtentText naam stad status
> ----------                     ----               ----     -----
> ANA Trujillo...                ANA Trujillo Redmond, WA Antonio Moreno...              Antonio Moreno Renton WA Thomas Hardy...                Thomas Hardy Seattle WA Pascaline Berglund...          Pascaline Berglund Redmond WA Hanna Moos...                  Hanna Moos Puyallup WA

Aanvullende gegevensmanipulatie op uitgepakte tekst, doen de **ExtentText** eigenschap bevat de onbewerkte tekst waaruit de record is opgehaald. Feedback geven over deze functie of inhoud waarvoor u problemen ondervindt schrijven voorbeelden te delen, kunt u een e-mail <psdmfb@microsoft.com>.