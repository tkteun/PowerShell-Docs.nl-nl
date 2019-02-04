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
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="f00c0-102">Gestructureerd objecten buiten tekenreeks uitpakken en parseren</span><span class="sxs-lookup"><span data-stu-id="f00c0-102">Extract and Parse Structured Objects out of String</span></span>

<span data-ttu-id="f00c0-103">Dit ook aanvullende functionaliteit voor introduceert de `ConvertFrom-String` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="f00c0-103">This also introduces some additional functionality for the `ConvertFrom-String` cmdlet:</span></span>

- <span data-ttu-id="f00c0-104">Hiermee verwijdert u de eigenschap van de tekst voor zover standaard.</span><span class="sxs-lookup"><span data-stu-id="f00c0-104">Removes the extent text property by default.</span></span> <span data-ttu-id="f00c0-105">U kunt opnemen met de parameter - IncludeExtent.</span><span class="sxs-lookup"><span data-stu-id="f00c0-105">You can include it with the -IncludeExtent parameter.</span></span>

- <span data-ttu-id="f00c0-106">Veel learning-algoritme voor oplossingen voor problemen van MVP en community-feedback.</span><span class="sxs-lookup"><span data-stu-id="f00c0-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

- <span data-ttu-id="f00c0-107">Een nieuwe UpdateTemplate - parameter op te slaan van de resultaten van het learning-algoritme in een opmerking in het sjabloonbestand.</span><span class="sxs-lookup"><span data-stu-id="f00c0-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="f00c0-108">Dit maakt het learning verwerken (de traagste fase) een eenmalige kosten.</span><span class="sxs-lookup"><span data-stu-id="f00c0-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="f00c0-109">Het omzetten van tekenreeks uitvoeren met een sjabloon met het gecodeerde learning-algoritme is nu nagenoeg onmiddellijke.</span><span class="sxs-lookup"><span data-stu-id="f00c0-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="f00c0-110">Gestructureerd objecten buiten tekenreeks inhoud uitpakken en parseren</span><span class="sxs-lookup"><span data-stu-id="f00c0-110">Extract and parse structured objects out of string content</span></span>

<span data-ttu-id="f00c0-111">In samenwerking met [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), een nieuwe `ConvertFrom-String` cmdlet is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="f00c0-111">In collaboration with [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), a new `ConvertFrom-String` cmdlet has been added.</span></span>

<span data-ttu-id="f00c0-112">Deze cmdlet ondersteunt twee modi: basic gescheiden parseren en automatisch gegenereerde voorbeeld gebaseerde parseren.</span><span class="sxs-lookup"><span data-stu-id="f00c0-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="f00c0-113">Gescheiden parseren, standaard, splitst de invoer op witruimte en namen van eigenschappen aan de resulterende groepen toegewezen.</span><span class="sxs-lookup"><span data-stu-id="f00c0-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="f00c0-114">U kunt het scheidingsteken aanpassen:</span><span class="sxs-lookup"><span data-stu-id="f00c0-114">You can customize the delimiter:</span></span>

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

<span data-ttu-id="f00c0-115">De cmdlet biedt ook ondersteuning voor automatisch gegenereerde voorbeeld gebaseerde parseren op basis van de [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) werk in onderzoek [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span><span class="sxs-lookup"><span data-stu-id="f00c0-115">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) research work in [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span></span>

<span data-ttu-id="f00c0-116">Als u wilt beginnen, kunt u overwegen een op tekst gebaseerde adresboek:</span><span class="sxs-lookup"><span data-stu-id="f00c0-116">To get started, consider a text-based address book:</span></span>

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

<span data-ttu-id="f00c0-117">Enkele voorbeelden kopiëren naar een bestand, dat u als de sjabloon gebruikt:</span><span class="sxs-lookup"><span data-stu-id="f00c0-117">Copy a few examples into a file, which you will use as your template:</span></span>

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

<span data-ttu-id="f00c0-118">Plaats accolades om de gegevens die u ophalen wilt, een naam geven als u dit doet.</span><span class="sxs-lookup"><span data-stu-id="f00c0-118">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="f00c0-119">Omdat de **naam** eigenschap (en de andere eigenschappen die zijn gekoppeld) kunnen meerdere keren worden weergegeven, gebruikt u een sterretje (\*) om aan te geven dat dit resulteert in meerdere records (in plaats van een aantal eigenschappen in één extraheren record):</span><span class="sxs-lookup"><span data-stu-id="f00c0-119">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

<span data-ttu-id="f00c0-120">In deze reeks voorbeelden, `ConvertFrom-String` uitvoer op basis van het object nu automatisch uit invoerbestanden met vergelijkbare structuur extraheren.</span><span class="sxs-lookup"><span data-stu-id="f00c0-120">From this set of examples, `ConvertFrom-String` can now automatically extract object-based output from input files with similar structure.</span></span>

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

<span data-ttu-id="f00c0-121">Aanvullende gegevens manipuleren op geëxtraheerde tekst, doet de **ExtentText** eigenschap bevat de onbewerkte tekst waaruit de record is opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f00c0-121">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="f00c0-122">Feedback geven over deze functie of inhoud die u ondervindt problemen bij het schrijven van voorbeelden te delen, stuur e-mail <psdmfb@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="f00c0-122">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>