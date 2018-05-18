---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: e4588e8c69efb965cd33c273ad09a8bef8e9bf16
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="fa16f-102">Gestructureerd objecten buiten tekenreeks uitpakken en parseren</span><span class="sxs-lookup"><span data-stu-id="fa16f-102">Extract and Parse Structured Objects out of String</span></span>
<span data-ttu-id="fa16f-103">Dit brengt ook aanvullende functionaliteit voor de cmdlet ConverterenVan-tekenreeks:</span><span class="sxs-lookup"><span data-stu-id="fa16f-103">This also introduces some additional functionality for the ConvertFrom-String cmdlet:</span></span>

-   <span data-ttu-id="fa16f-104">Hiermee verwijdert u de teksteigenschap gebied standaard.</span><span class="sxs-lookup"><span data-stu-id="fa16f-104">Removes the extent text property by default.</span></span> <span data-ttu-id="fa16f-105">U kunt opnemen met de parameter - IncludeExtent.</span><span class="sxs-lookup"><span data-stu-id="fa16f-105">You can include it with the -IncludeExtent parameter.</span></span>

-   <span data-ttu-id="fa16f-106">Veel learning-algoritme foutoplossingen van MVP en community feedback.</span><span class="sxs-lookup"><span data-stu-id="fa16f-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

-   <span data-ttu-id="fa16f-107">Een nieuwe UpdateTemplate - parameter voor de resultaten van het leeralgoritme in een opmerking in het sjabloonbestand op te slaan.</span><span class="sxs-lookup"><span data-stu-id="fa16f-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="fa16f-108">Hierdoor kunt u de learning verwerken (de traagste fase) een eenmalige kosten.</span><span class="sxs-lookup"><span data-stu-id="fa16f-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="fa16f-109">Het omzetten van tekenreeks uitgevoerd met een sjabloon met de gecodeerde learning-algoritme is nu bijna onmiddellijk.</span><span class="sxs-lookup"><span data-stu-id="fa16f-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>


<a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="fa16f-110">Uitpakken en parseren van gestructureerde objecten uit de inhoud van de tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fa16f-110">Extract and parse structured objects out of string content</span></span>
----------------------------------------------------------

<span data-ttu-id="fa16f-111">In samenwerking met [Microsoft Research](http://research.microsoft.com/), een nieuwe **ConverterenVan-tekenreeks** cmdlet is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="fa16f-111">In collaboration with [Microsoft Research](http://research.microsoft.com/), a new **ConvertFrom-String** cmdlet has been added.</span></span>

<span data-ttu-id="fa16f-112">Deze cmdlet ondersteunt twee modi: basic gescheiden parseren en automatisch gegenereerd voorbeeld aangestuurde parseren.</span><span class="sxs-lookup"><span data-stu-id="fa16f-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="fa16f-113">Parseren standaard gescheiden splitst de invoer op witruimte en worden de namen van eigenschappen wordt toegewezen aan de resulterende groepen.</span><span class="sxs-lookup"><span data-stu-id="fa16f-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="fa16f-114">U kunt het scheidingsteken aanpassen:</span><span class="sxs-lookup"><span data-stu-id="fa16f-114">You can customize the delimiter:</span></span>

> <span data-ttu-id="fa16f-115">1 \[C:\\temp\] &gt; &gt; 'Hallo wereld' | ConverterenVan-tekenreeks | Format-Table-automatisch</span><span class="sxs-lookup"><span data-stu-id="fa16f-115">1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto</span></span>

<span data-ttu-id="fa16f-116">P1    P2</span><span class="sxs-lookup"><span data-stu-id="fa16f-116">P1    P2</span></span>
--    --

<span data-ttu-id="fa16f-117">De cmdlet ondersteunt ook automatisch gegenereerde voorbeeld aangestuurde parseren op basis van de [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) onderzoek werk in [Microsoft Research](http://research.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="fa16f-117">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) research work in [Microsoft Research](http://research.microsoft.com).</span></span>

<span data-ttu-id="fa16f-118">Houd rekening met een op tekst gebaseerde adresboek om te beginnen:</span><span class="sxs-lookup"><span data-stu-id="fa16f-118">To get started, consider a text-based address book:</span></span>

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

<span data-ttu-id="fa16f-119">Kopieer een paar voorbeelden naar een bestand, dat u als uw sjabloon gebruiken gaat:</span><span class="sxs-lookup"><span data-stu-id="fa16f-119">Copy a few examples into a file, which you will use as your template:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA



<span data-ttu-id="fa16f-120">Plaats accolades gebruiken om gegevens die u ophalen wilt, een naam geven als u doet dit.</span><span class="sxs-lookup"><span data-stu-id="fa16f-120">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="fa16f-121">Omdat de **naam** eigenschap (en de andere eigenschappen die zijn gekoppeld) kunnen meerdere keren worden weergegeven, gebruikt u een sterretje (\*) om aan te geven dat dit resulteert in meerdere records (in plaats van een aantal eigenschappen in te pakken op een record):</span><span class="sxs-lookup"><span data-stu-id="fa16f-121">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

<span data-ttu-id="fa16f-122">In deze reeks voorbeelden **ConverterenVan-tekenreeks** uitvoer op basis van het object automatisch nu uit invoerbestanden met vergelijkbare structuur kan extraheren.</span><span class="sxs-lookup"><span data-stu-id="fa16f-122">From this set of examples, **ConvertFrom-String** can now automatically extract object-based output from input files with similar structure.</span></span>

> <span data-ttu-id="fa16f-123">2 \[C:\\temp\]</span><span class="sxs-lookup"><span data-stu-id="fa16f-123">2 \[C:\\temp\]</span></span>
>
> <span data-ttu-id="fa16f-124">&gt;&gt; Get-inhoud. \\addresses.output.txt | ConverterenVan-tekenreeks - sjabloonbestand. \\addresses.template.txt | &gt; &gt; &gt; Format-Table-automatisch</span><span class="sxs-lookup"><span data-stu-id="fa16f-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span></span>
>
> <span data-ttu-id="fa16f-125">ExtentText naam stad status</span><span class="sxs-lookup"><span data-stu-id="fa16f-125">ExtentText                     Name               City     State</span></span>
> ----------                     ----               ----     -----
> <span data-ttu-id="fa16f-126">ANA Trujillo...                ANA Trujillo Redmond, WA Antonio Moreno...              Antonio Moreno Renton WA Thomas Hardy...                Thomas Hardy Seattle WA Pascaline Berglund...          Pascaline Berglund Redmond WA Hanna Moos...                  Hanna Moos Puyallup WA</span><span class="sxs-lookup"><span data-stu-id="fa16f-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA</span></span>

<span data-ttu-id="fa16f-127">Aanvullende gegevensmanipulatie op uitgepakte tekst, doen de **ExtentText** eigenschap bevat de onbewerkte tekst waaruit de record is opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fa16f-127">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="fa16f-128">Feedback geven over deze functie of inhoud waarvoor u problemen ondervindt schrijven voorbeelden te delen, kunt u een e-mail <psdmfb@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="fa16f-128">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>
