---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: fcf2adf67f36edb534df3e2a849459fb20e1c2de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685618"
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a>Gestructureerd objecten buiten tekenreeks uitpakken en parseren

Dit ook aanvullende functionaliteit voor introduceert de `ConvertFrom-String` cmdlet:

- Hiermee verwijdert u de eigenschap van de tekst voor zover standaard. U kunt opnemen met de parameter - IncludeExtent.

- Veel learning-algoritme voor oplossingen voor problemen van MVP en community-feedback.

- Een nieuwe UpdateTemplate - parameter op te slaan van de resultaten van het learning-algoritme in een opmerking in het sjabloonbestand. Dit maakt het learning verwerken (de traagste fase) een eenmalige kosten. Het omzetten van tekenreeks uitvoeren met een sjabloon met het gecodeerde learning-algoritme is nu nagenoeg onmiddellijke.

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a>Gestructureerd objecten buiten tekenreeks inhoud uitpakken en parseren

In samenwerking met [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), een nieuwe `ConvertFrom-String` cmdlet is toegevoegd.

Deze cmdlet ondersteunt twee modi: basic gescheiden parseren en automatisch gegenereerde voorbeeld gebaseerde parseren.

Gescheiden parseren, standaard, splitst de invoer op witruimte en namen van eigenschappen aan de resulterende groepen toegewezen. U kunt het scheidingsteken aanpassen:

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

De cmdlet biedt ook ondersteuning voor automatisch gegenereerde voorbeeld gebaseerde parseren op basis van de [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) werk in onderzoek [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).

Als u wilt beginnen, kunt u overwegen een op tekst gebaseerde adresboek:

```
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
```

Enkele voorbeelden kopiëren naar een bestand, dat u als de sjabloon gebruikt:

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

Plaats accolades om de gegevens die u ophalen wilt, een naam geven als u dit doet. Omdat de **naam** eigenschap (en de andere eigenschappen die zijn gekoppeld) kunnen meerdere keren worden weergegeven, gebruikt u een sterretje (\*) om aan te geven dat dit resulteert in meerdere records (in plaats van een aantal eigenschappen in één extraheren record):

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

In deze reeks voorbeelden, `ConvertFrom-String` uitvoer op basis van het object nu automatisch uit invoerbestanden met vergelijkbare structuur extraheren.

```powershell
Get-Content .\addresses.output.txt | ConvertFrom-String -TemplateFile .\addresses.template.txt | Format-Table -Auto
```

```output
ExtentText                     Name               City     State
----------                     ----               ----     -----
Ana Trujillo...                Ana Trujillo       Redmond  WA
Antonio Moreno...              Antonio Moreno     Renton   WA
Thomas Hardy...                Thomas Hardy       Seattle  WA
Christina Berglund...          Christina Berglund Redmond  WA
Hanna Moos...                  Hanna Moos         Puyallup WA
```

Aanvullende gegevens manipuleren op geëxtraheerde tekst, doet de **ExtentText** eigenschap bevat de onbewerkte tekst waaruit de record is opgehaald. Feedback geven over deze functie of inhoud die u ondervindt problemen bij het schrijven van voorbeelden te delen, stuur e-mail <psdmfb@microsoft.com>.