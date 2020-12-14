---
description: Voert een lijst met instructies uit met een of meer keren, afhankelijk van de voor waarde while of until.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_do?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Do
ms.openlocfilehash: 412a13669e86df5804dd74d75fcb5b4389192c79
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706109"
---
# <a name="about-do"></a><span data-ttu-id="11444-103">Over doen</span><span class="sxs-lookup"><span data-stu-id="11444-103">About Do</span></span>

## <a name="short-description"></a><span data-ttu-id="11444-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="11444-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="11444-105">Voert een lijst met instructies uit met een of meer keren, afhankelijk van de voor waarde while of until.</span><span class="sxs-lookup"><span data-stu-id="11444-105">Runs a statement list one or more times, subject to a While or Until condition.</span></span>

## <a name="long-description"></a><span data-ttu-id="11444-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="11444-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="11444-107">Het sleutel woord do werkt met het sleutel woord while of het sleutel woord until om de instructies in een script blok uit te voeren, onder voor waarde.</span><span class="sxs-lookup"><span data-stu-id="11444-107">The Do keyword works with the While keyword or the Until keyword to run the statements in a script block, subject to a condition.</span></span> <span data-ttu-id="11444-108">In tegens telling tot de lus while, voert het script blok in een do-lus altijd ten minste één keer uit.</span><span class="sxs-lookup"><span data-stu-id="11444-108">Unlike the related While loop, the script block in a Do loop always runs at least once.</span></span>

<span data-ttu-id="11444-109">Een lus **-while** is een verscheidenheid van de while-lus.</span><span class="sxs-lookup"><span data-stu-id="11444-109">A **Do-While** loop is a variety of the While loop.</span></span> <span data-ttu-id="11444-110">In een lus **-while** wordt de voor waarde geëvalueerd nadat het script blok is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="11444-110">In a **Do-While** loop, the condition is evaluated after the script block has run.</span></span> <span data-ttu-id="11444-111">Net als bij een while-lus wordt het script blok herhaald, zolang de voor waarde resulteert in waar.</span><span class="sxs-lookup"><span data-stu-id="11444-111">As in a While loop, the script block is repeated as long as the condition evaluates to true.</span></span>

<span data-ttu-id="11444-112">Net als **bij** een lus wordt een **do-until-** lus altijd ten minste één keer uitgevoerd voordat de voor waarde wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="11444-112">Like a **Do-While** loop, a **Do-Until** loop always runs at least once before the condition is evaluated.</span></span> <span data-ttu-id="11444-113">Het script blok kan echter alleen worden uitgevoerd als de voor waarde ONWAAR is.</span><span class="sxs-lookup"><span data-stu-id="11444-113">However, the script block runs only while the condition is false.</span></span>

<span data-ttu-id="11444-114">De zoek woorden *continue* en outcontrol *flow kunnen* worden gebruikt in een **do-while-** lus of in een **do-until-** lus.</span><span class="sxs-lookup"><span data-stu-id="11444-114">The *Continue* and *Break* flow control keywords can be used in a **Do-While** loop or in a **Do-Until** loop.</span></span>

### <a name="syntax"></a><span data-ttu-id="11444-115">Syntax</span><span class="sxs-lookup"><span data-stu-id="11444-115">Syntax</span></span>

<span data-ttu-id="11444-116">Hieronder ziet u de syntaxis van de instructie **do-while** :</span><span class="sxs-lookup"><span data-stu-id="11444-116">The following shows the syntax of the **Do-While** statement:</span></span>

```powershell
do {<statement list>} while (<condition>)
```

<span data-ttu-id="11444-117">Hieronder ziet u de syntaxis van de instructie **do-until** :</span><span class="sxs-lookup"><span data-stu-id="11444-117">The following shows the syntax of the **Do-Until** statement:</span></span>

```powershell
do {<statement list>} until (<condition>)
```

<span data-ttu-id="11444-118">De lijst met instructies bevat een of meer instructies die worden uitgevoerd elke keer dat de lus wordt ingevoerd of herhaald.</span><span class="sxs-lookup"><span data-stu-id="11444-118">The statement list contains one or more statements that run each time the loop is entered or repeated.</span></span>

<span data-ttu-id="11444-119">Het voor waarde-gedeelte van de instructie wordt omgezet in waar of onwaar.</span><span class="sxs-lookup"><span data-stu-id="11444-119">The condition portion of the statement resolves to true or false.</span></span>

### <a name="example"></a><span data-ttu-id="11444-120">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="11444-120">Example</span></span>

<span data-ttu-id="11444-121">In het volgende voor beeld van de instructie do worden de items in een matrix geteld, totdat het item met de waarde 0 wordt bereikt.</span><span class="sxs-lookup"><span data-stu-id="11444-121">The following example of a Do statement counts the items in an array until it reaches an item with a value of 0.</span></span>

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } while ($x[$a] -ne 0)
C:\PS> $count
3
```

<span data-ttu-id="11444-122">In het volgende voor beeld wordt het sleutel woord until gebruikt.</span><span class="sxs-lookup"><span data-stu-id="11444-122">The following example uses the Until keyword.</span></span> <span data-ttu-id="11444-123">Merk op dat de operator niet gelijk is aan ( `-ne` ) wordt vervangen door de operator equal to ( `-eq` ).</span><span class="sxs-lookup"><span data-stu-id="11444-123">Notice that the not equal to operator (`-ne`) is replaced by the equal to operator (`-eq`).</span></span>

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } until ($x[$a] -eq 0)
C:\PS> $count
3
```

<span data-ttu-id="11444-124">In het volgende voor beeld worden alle waarden van een matrix geschreven, waarbij elke waarde die kleiner is dan nul, wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="11444-124">The following example writes all the values of an array, skipping any value that is less than zero.</span></span>

```powershell
do {
  if ($x[$a] -lt 0) { continue }
  Write-Host $x[$a]
}
while (++$a -lt 10)
```

## <a name="see-also"></a><span data-ttu-id="11444-125">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="11444-125">SEE ALSO</span></span>

[<span data-ttu-id="11444-126">about_While</span><span class="sxs-lookup"><span data-stu-id="11444-126">about_While</span></span>](about_While.md)

[<span data-ttu-id="11444-127">about_Operators</span><span class="sxs-lookup"><span data-stu-id="11444-127">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="11444-128">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="11444-128">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)

[<span data-ttu-id="11444-129">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="11444-129">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="11444-130">about_Break</span><span class="sxs-lookup"><span data-stu-id="11444-130">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="11444-131">about_Continue</span><span class="sxs-lookup"><span data-stu-id="11444-131">about_Continue</span></span>](about_Continue.md)

