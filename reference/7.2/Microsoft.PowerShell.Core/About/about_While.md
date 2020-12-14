---
description: Hierin wordt een taal instructie beschreven die u kunt gebruiken om een opdracht blok uit te voeren op basis van de resultaten van een voorwaardelijke test.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_while?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_While
ms.openlocfilehash: 37c277a5919ba5fc39f953e05edaf58d159f3e7c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705785"
---
# <a name="about-while"></a><span data-ttu-id="d4dc1-103">Over hoewel</span><span class="sxs-lookup"><span data-stu-id="d4dc1-103">About While</span></span>

## <a name="short-description"></a><span data-ttu-id="d4dc1-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d4dc1-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="d4dc1-105">Hierin wordt een taal instructie beschreven die u kunt gebruiken om een opdracht blok uit te voeren op basis van de resultaten van een voorwaardelijke test.</span><span class="sxs-lookup"><span data-stu-id="d4dc1-105">Describes a language statement that you can use to run a command block based on the results of a conditional test.</span></span>

## <a name="long-description"></a><span data-ttu-id="d4dc1-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d4dc1-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="d4dc1-107">De instructie while (ook wel een while-lus genoemd) is een taal constructie voor het maken van een lus waarbij opdrachten in een opdracht blok worden uitgevoerd zolang een voorwaardelijke test resulteert in waar.</span><span class="sxs-lookup"><span data-stu-id="d4dc1-107">The While statement (also known as a While loop) is a language construct for creating a loop that runs commands in a command block as long as a conditional test evaluates to true.</span></span> <span data-ttu-id="d4dc1-108">De instructie while is gemakkelijker te maken dan een for-instructie, omdat de syntaxis minder gecompliceerd is.</span><span class="sxs-lookup"><span data-stu-id="d4dc1-108">The While statement is easier to construct than a For statement because its syntax is less complicated.</span></span> <span data-ttu-id="d4dc1-109">Daarnaast is het flexibeler dan de instructie foreach, omdat u een voorwaardelijke test in de instructie while opgeeft om te bepalen hoe vaak de lus wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d4dc1-109">In addition, it is more flexible than the Foreach statement because you specify a conditional test in the While statement to control how many times the loop runs.</span></span>

<span data-ttu-id="d4dc1-110">Hieronder ziet u de syntaxis while-instructie:</span><span class="sxs-lookup"><span data-stu-id="d4dc1-110">The following shows the While statement syntax:</span></span>

```powershell
while (<condition>){<statement list>}
```

<span data-ttu-id="d4dc1-111">Wanneer u een while-instructie uitvoert, evalueert Power shell de `<condition>` sectie van de instructie voordat de sectie wordt ingevoerd `<statement list>` .</span><span class="sxs-lookup"><span data-stu-id="d4dc1-111">When you run a While statement, PowerShell evaluates the `<condition>` section of the statement before entering the `<statement list>` section.</span></span> <span data-ttu-id="d4dc1-112">Het voor waarde-gedeelte van de instructie wordt omgezet in waar of onwaar.</span><span class="sxs-lookup"><span data-stu-id="d4dc1-112">The condition portion of the statement resolves to either true or false.</span></span> <span data-ttu-id="d4dc1-113">Zolang de voor waarde waar is, voert Power shell de sectie opnieuw uit `<statement list>` .</span><span class="sxs-lookup"><span data-stu-id="d4dc1-113">As long as the condition remains true, PowerShell reruns the `<statement list>` section.</span></span>

<span data-ttu-id="d4dc1-114">De `<statement list>` sectie van de instructie bevat een of meer opdrachten die elke keer dat de lus wordt ingevoerd of herhaald worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d4dc1-114">The `<statement list>` section of the statement contains one or more commands that are run each time the loop is entered or repeated.</span></span>

<span data-ttu-id="d4dc1-115">Met de volgende instructie while worden bijvoorbeeld de getallen 1 tot en met 3 weer gegeven als de variabele $val niet is gemaakt of als de $val variabele is gemaakt en geïnitialiseerd op 0.</span><span class="sxs-lookup"><span data-stu-id="d4dc1-115">For example, the following While statement displays the numbers 1 through 3 if the $val variable has not been created or if the $val variable has been created and initialized to 0.</span></span>

```powershell
while($val -ne 3)
{
    $val++
    Write-Host $val
}
```

<span data-ttu-id="d4dc1-116">In dit voor beeld is de voor waarde ($val niet gelijk aan 3) waar wanneer $val \= 0, 1, 2.</span><span class="sxs-lookup"><span data-stu-id="d4dc1-116">In this example, the condition ($val is not equal to 3) is true while $val \= 0, 1, 2.</span></span> <span data-ttu-id="d4dc1-117">Elke keer door de lus $val wordt verhoogd met 1 met behulp van de \+ \+ unaire operator voor aflopen ($Val \+ \+ ).</span><span class="sxs-lookup"><span data-stu-id="d4dc1-117">Each time through the loop, $val is incremented by 1 using the \+\+ unary increment operator ($val\+\+).</span></span> <span data-ttu-id="d4dc1-118">De laatste keer door loop, $val \= 3.</span><span class="sxs-lookup"><span data-stu-id="d4dc1-118">The last time through the loop, $val \= 3.</span></span> <span data-ttu-id="d4dc1-119">Als $val gelijk is aan 3, wordt de voor waarde-instructie geëvalueerd als False en wordt de lus afgesloten.</span><span class="sxs-lookup"><span data-stu-id="d4dc1-119">When $val equals 3, the condition statement evaluates to false, and the loop exits.</span></span>

<span data-ttu-id="d4dc1-120">Als u deze opdracht op de Power shell-opdracht prompt handig wilt schrijven, kunt u deze op de volgende manier invoeren:</span><span class="sxs-lookup"><span data-stu-id="d4dc1-120">To conveniently write this command at the PowerShell command prompt, you can enter it in the following way:</span></span>

```powershell
while($val -ne 3){$val++; Write-Host $val}
```

<span data-ttu-id="d4dc1-121">U ziet dat de punt komma de eerste opdracht scheidt waarmee 1 wordt toegevoegd aan $val van de tweede opdracht die de waarde van $val naar de-console schrijft.</span><span class="sxs-lookup"><span data-stu-id="d4dc1-121">Notice that the semicolon separates the first command that adds 1 to $val from the second command that writes the value of $val to the console.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4dc1-122">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="d4dc1-122">SEE ALSO</span></span>

[<span data-ttu-id="d4dc1-123">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="d4dc1-123">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="d4dc1-124">about_Do</span><span class="sxs-lookup"><span data-stu-id="d4dc1-124">about_Do</span></span>](about_Do.md)

[<span data-ttu-id="d4dc1-125">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="d4dc1-125">about_Foreach</span></span>](about_Foreach.md)

[<span data-ttu-id="d4dc1-126">about_For</span><span class="sxs-lookup"><span data-stu-id="d4dc1-126">about_For</span></span>](about_For.md)

[<span data-ttu-id="d4dc1-127">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="d4dc1-127">about_Language_Keywords</span></span>](about_Language_Keywords.md)

