---
description: Een lijst met gereserveerde woorden die niet als id's kunnen worden gebruikt, omdat ze een speciale betekenis hebben in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_reserved_words?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Reserved_Words
ms.openlocfilehash: 928962b9bf28d95e8c037e9c09e5425ee730b172
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252237"
---
# <a name="about-reserved-words"></a><span data-ttu-id="0f203-104">Over gereserveerde woorden</span><span class="sxs-lookup"><span data-stu-id="0f203-104">About Reserved Words</span></span>

## <a name="short-description"></a><span data-ttu-id="0f203-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0f203-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="0f203-106">Een lijst met gereserveerde woorden die niet als id's kunnen worden gebruikt, omdat ze een speciale betekenis hebben in Power shell.</span><span class="sxs-lookup"><span data-stu-id="0f203-106">Lists the reserved words that cannot be used as identifiers because they have a special meaning in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="0f203-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0f203-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="0f203-108">Er zijn bepaalde woorden met een speciale betekenis in Power shell.</span><span class="sxs-lookup"><span data-stu-id="0f203-108">There are certain words that have special meaning in PowerShell.</span></span> <span data-ttu-id="0f203-109">Wanneer deze woorden zonder aanhalings tekens worden weer gegeven, probeert Power shell hun speciale betekenis toe te passen in plaats van deze als teken reeksen te behandelen.</span><span class="sxs-lookup"><span data-stu-id="0f203-109">When these words appear without quotation marks, PowerShell attempts to apply their special meaning rather than treating them as character strings.</span></span> <span data-ttu-id="0f203-110">Als u deze woorden wilt gebruiken als parameter argumenten in een opdracht of script zonder hun speciale betekenis aan te roepen, plaatst u de gereserveerde woorden tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="0f203-110">To use these words as parameter arguments in a command or script without invoking their special meaning, enclose the reserved words in quotation marks.</span></span>

<span data-ttu-id="0f203-111">De volgende gereserveerde woorden zijn opgenomen in Power shell:</span><span class="sxs-lookup"><span data-stu-id="0f203-111">The following are the reserved words in PowerShell:</span></span>

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

<span data-ttu-id="0f203-112">Verschillende taal trefwoorden, waaronder `Foreach` , `If` , `For` en `While` , hebben hun eigen Help-artikelen.</span><span class="sxs-lookup"><span data-stu-id="0f203-112">Several language keywords, including `Foreach`, `If`, `For`, and `While`, have their own help articles.</span></span> <span data-ttu-id="0f203-113">Als u deze wilt weer geven, typt `Get-Help about_` en voegt u het tref woord toe.</span><span class="sxs-lookup"><span data-stu-id="0f203-113">To view them, type `Get-Help about_` and add the keyword.</span></span> <span data-ttu-id="0f203-114">Als u bijvoorbeeld informatie wilt ophalen over de `Foreach` -instructie, typt u:</span><span class="sxs-lookup"><span data-stu-id="0f203-114">For example, to get information about the `Foreach` statement, type:</span></span>

```powershell
Get-Help about_ForEach
```

<span data-ttu-id="0f203-115">Voor informatie over het `Filter` overzicht of de `Return` syntaxis van de instructie typt u:</span><span class="sxs-lookup"><span data-stu-id="0f203-115">For information about the `Filter` statement or the `Return` statement syntax, type:</span></span>

```powershell
Get-Help about_Functions
```

<span data-ttu-id="0f203-116">Voor informatie over andere gereserveerde woorden, typt u:</span><span class="sxs-lookup"><span data-stu-id="0f203-116">For information about other reserved words, type:</span></span>

```powershell
Get-Help <Reserved_Word>
```

> [!NOTE]
> <span data-ttu-id="0f203-117">Niet elk gereserveerd woord heeft zijn eigen Help-artikel.</span><span class="sxs-lookup"><span data-stu-id="0f203-117">Not every reserved word has its own help article.</span></span> <span data-ttu-id="0f203-118">Als geen `Get-Help` artikel retourneert, kunt u zoeken naar artikelen over het gereserveerde woord met behulp van de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="0f203-118">If `Get-Help` does not return an article, you can search for articles that talk about the reserved word using the following command:</span></span>
>
> ```powershell
> Get-Help <Reserved_Word> -Category:HelpFile
> ```

## <a name="see-also"></a><span data-ttu-id="0f203-119">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="0f203-119">SEE ALSO</span></span>

- [<span data-ttu-id="0f203-120">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="0f203-120">about_Command_Syntax</span></span>](about_Command_Syntax.md)
- [<span data-ttu-id="0f203-121">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="0f203-121">about_Language_Keywords</span></span>](about_Language_Keywords.md)
- [<span data-ttu-id="0f203-122">about_Parsing</span><span class="sxs-lookup"><span data-stu-id="0f203-122">about_Parsing</span></span>](about_Parsing.md)
- [<span data-ttu-id="0f203-123">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="0f203-123">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
- [<span data-ttu-id="0f203-124">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="0f203-124">about_Script_Blocks</span></span>](about_Script_Blocks.md)
- [<span data-ttu-id="0f203-125">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="0f203-125">about_Special_Characters</span></span>](about_Special_Characters.md)
