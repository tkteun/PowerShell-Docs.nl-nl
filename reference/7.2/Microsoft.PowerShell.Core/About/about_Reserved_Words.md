---
description: Een lijst met gereserveerde woorden die niet als id's kunnen worden gebruikt, omdat ze een speciale betekenis hebben in Power shell.
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_reserved_words?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Reserved_Words
ms.openlocfilehash: 95911e328a50c173235f47a7610393124781555d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705793"
---
# <a name="about-reserved-words"></a><span data-ttu-id="75bdd-103">Over gereserveerde woorden</span><span class="sxs-lookup"><span data-stu-id="75bdd-103">About Reserved Words</span></span>

## <a name="short-description"></a><span data-ttu-id="75bdd-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="75bdd-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="75bdd-105">Een lijst met gereserveerde woorden die niet als id's kunnen worden gebruikt, omdat ze een speciale betekenis hebben in Power shell.</span><span class="sxs-lookup"><span data-stu-id="75bdd-105">Lists the reserved words that cannot be used as identifiers because they have a special meaning in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="75bdd-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="75bdd-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="75bdd-107">Er zijn bepaalde woorden met een speciale betekenis in Power shell.</span><span class="sxs-lookup"><span data-stu-id="75bdd-107">There are certain words that have special meaning in PowerShell.</span></span> <span data-ttu-id="75bdd-108">Wanneer deze woorden zonder aanhalings tekens worden weer gegeven, probeert Power shell hun speciale betekenis toe te passen in plaats van deze als teken reeksen te behandelen.</span><span class="sxs-lookup"><span data-stu-id="75bdd-108">When these words appear without quotation marks, PowerShell attempts to apply their special meaning rather than treating them as character strings.</span></span> <span data-ttu-id="75bdd-109">Als u deze woorden wilt gebruiken als parameter argumenten in een opdracht of script zonder hun speciale betekenis aan te roepen, plaatst u de gereserveerde woorden tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="75bdd-109">To use these words as parameter arguments in a command or script without invoking their special meaning, enclose the reserved words in quotation marks.</span></span>

<span data-ttu-id="75bdd-110">De volgende gereserveerde woorden zijn opgenomen in Power shell:</span><span class="sxs-lookup"><span data-stu-id="75bdd-110">The following are the reserved words in PowerShell:</span></span>

```
assembly         exit            process
base             filter          public
begin            finally         return
break            for             sequence
catch            foreach         static
class            from (*)        switch
command          function        throw
configuration    hidden          trap
continue         if              try
data             in              type
define (*)       inlinescript    until
do               interface       using
dynamicparam     module          var (*)
else             namespace       while
elseif           parallel        workflow
end              param
enum             private

(*) These keywords are reserved for future use.
```

<span data-ttu-id="75bdd-111">Verschillende taal trefwoorden, waaronder `Foreach` , `If` , `For` en `While` , hebben hun eigen Help-artikelen.</span><span class="sxs-lookup"><span data-stu-id="75bdd-111">Several language keywords, including `Foreach`, `If`, `For`, and `While`, have their own help articles.</span></span> <span data-ttu-id="75bdd-112">Als u deze wilt weer geven, typt `Get-Help about_` en voegt u het tref woord toe.</span><span class="sxs-lookup"><span data-stu-id="75bdd-112">To view them, type `Get-Help about_` and add the keyword.</span></span> <span data-ttu-id="75bdd-113">Als u bijvoorbeeld informatie wilt ophalen over de `Foreach` -instructie, typt u:</span><span class="sxs-lookup"><span data-stu-id="75bdd-113">For example, to get information about the `Foreach` statement, type:</span></span>

```powershell
Get-Help about_ForEach
```

<span data-ttu-id="75bdd-114">Voor informatie over het `Filter` overzicht of de `Return` syntaxis van de instructie typt u:</span><span class="sxs-lookup"><span data-stu-id="75bdd-114">For information about the `Filter` statement or the `Return` statement syntax, type:</span></span>

```powershell
Get-Help about_Functions
```

<span data-ttu-id="75bdd-115">Voor informatie over andere gereserveerde woorden, typt u:</span><span class="sxs-lookup"><span data-stu-id="75bdd-115">For information about other reserved words, type:</span></span>

```powershell
Get-Help <Reserved_Word>
```

> [!NOTE]
> <span data-ttu-id="75bdd-116">Niet elk gereserveerd woord heeft zijn eigen Help-artikel.</span><span class="sxs-lookup"><span data-stu-id="75bdd-116">Not every reserved word has its own help article.</span></span> <span data-ttu-id="75bdd-117">Als geen `Get-Help` artikel retourneert, kunt u zoeken naar artikelen over het gereserveerde woord met behulp van de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="75bdd-117">If `Get-Help` does not return an article, you can search for articles that talk about the reserved word using the following command:</span></span>
>
> ```powershell
> Get-Help <Reserved_Word> -Category:HelpFile
> ```

## <a name="see-also"></a><span data-ttu-id="75bdd-118">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="75bdd-118">SEE ALSO</span></span>

- [<span data-ttu-id="75bdd-119">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="75bdd-119">about_Command_Syntax</span></span>](about_Command_Syntax.md)
- [<span data-ttu-id="75bdd-120">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="75bdd-120">about_Language_Keywords</span></span>](about_Language_Keywords.md)
- [<span data-ttu-id="75bdd-121">about_Parsing</span><span class="sxs-lookup"><span data-stu-id="75bdd-121">about_Parsing</span></span>](about_Parsing.md)
- [<span data-ttu-id="75bdd-122">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="75bdd-122">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
- [<span data-ttu-id="75bdd-123">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="75bdd-123">about_Script_Blocks</span></span>](about_Script_Blocks.md)
- [<span data-ttu-id="75bdd-124">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="75bdd-124">about_Special_Characters</span></span>](about_Special_Characters.md)
