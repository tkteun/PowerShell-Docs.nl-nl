---
description: Hierin wordt een taal opdracht beschreven die u kunt gebruiken om overzichts lijsten uit te voeren op basis van de resultaten van een of meer voorwaardelijke tests.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_If
ms.openlocfilehash: 7f63b6f12743390608e0da72adb4098ce0583751
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252319"
---
# <a name="about-if"></a><span data-ttu-id="daf36-104">Over als</span><span class="sxs-lookup"><span data-stu-id="daf36-104">About If</span></span>

## <a name="short-description"></a><span data-ttu-id="daf36-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="daf36-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="daf36-106">Hierin wordt een taal opdracht beschreven die u kunt gebruiken om overzichts lijsten uit te voeren op basis van de resultaten van een of meer voorwaardelijke tests.</span><span class="sxs-lookup"><span data-stu-id="daf36-106">Describes a language command you can use to run statement lists based on the results of one or more conditional tests.</span></span>

## <a name="long-description"></a><span data-ttu-id="daf36-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="daf36-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="daf36-108">U kunt de- `If` instructie gebruiken om code blokken uit te voeren als een opgegeven voorwaardelijke test resulteert in waar.</span><span class="sxs-lookup"><span data-stu-id="daf36-108">You can use the `If` statement to run code blocks if a specified conditional test evaluates to true.</span></span> <span data-ttu-id="daf36-109">U kunt ook een of meer aanvullende voorwaardelijke tests opgeven die moeten worden uitgevoerd als alle voor gaande tests resulteren in ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="daf36-109">You can also specify one or more additional conditional tests to run if all the prior tests evaluate to false.</span></span> <span data-ttu-id="daf36-110">Ten slotte kunt u een extra code blok opgeven dat wordt uitgevoerd als er geen andere eerdere voorwaardelijke test wordt geëvalueerd als waar.</span><span class="sxs-lookup"><span data-stu-id="daf36-110">Finally, you can specify an additional code block that is run if no other prior conditional test evaluates to true.</span></span>

### <a name="syntax"></a><span data-ttu-id="daf36-111">Syntax</span><span class="sxs-lookup"><span data-stu-id="daf36-111">Syntax</span></span>

<span data-ttu-id="daf36-112">In het volgende voor beeld ziet u de syntaxis van de `If` instructie:</span><span class="sxs-lookup"><span data-stu-id="daf36-112">The following example shows the `If` statement syntax:</span></span>

```powershell
if (<test1>)
    {<statement list 1>}
[elseif (<test2>)
    {<statement list 2>}]
[else
    {<statement list 3>}]
```

<span data-ttu-id="daf36-113">Wanneer u een `If` -instructie uitvoert, evalueert Power shell de `<test1>` voorwaardelijke expressie als waar of onwaar.</span><span class="sxs-lookup"><span data-stu-id="daf36-113">When you run an `If` statement, PowerShell evaluates the `<test1>` conditional expression as true or false.</span></span> <span data-ttu-id="daf36-114">Als `<test1>` de waarde True is, `<statement list 1>` wordt uitgevoerd en Power shell de `If` instructie verlaat.</span><span class="sxs-lookup"><span data-stu-id="daf36-114">If `<test1>` is true, `<statement list 1>` runs, and PowerShell exits the `If` statement.</span></span> <span data-ttu-id="daf36-115">Als `<test1>` is ingesteld op False, wordt de voor waarde die is opgegeven door de voorwaardelijke instructie door Power shell geëvalueerd `<test2>` .</span><span class="sxs-lookup"><span data-stu-id="daf36-115">If `<test1>` is false, PowerShell evaluates the condition specified by the `<test2>` conditional statement.</span></span>

<span data-ttu-id="daf36-116">Als `<test2>` de waarde True is, `<statement list 2>` wordt uitgevoerd en Power shell de `If` instructie verlaat.</span><span class="sxs-lookup"><span data-stu-id="daf36-116">If `<test2>` is true, `<statement list 2>` runs, and PowerShell exits the `If` statement.</span></span> <span data-ttu-id="daf36-117">Als zowel `<test1>` als `<test2>` wordt geëvalueerd als onwaar, `<statement list 3` wordt het> code blok uitgevoerd en wordt de if-instructie door Power shell afgesloten.</span><span class="sxs-lookup"><span data-stu-id="daf36-117">If both `<test1>` and `<test2>` evaluate to false, the `<statement list 3`> code block runs, and PowerShell exits the If statement.</span></span>

<span data-ttu-id="daf36-118">U kunt meerdere elseif-instructies gebruiken om een reeks voorwaardelijke tests te koppelen.</span><span class="sxs-lookup"><span data-stu-id="daf36-118">You can use multiple Elseif statements to chain a series of conditional tests.</span></span> <span data-ttu-id="daf36-119">Dit betekent dat elke test alleen wordt uitgevoerd als alle vorige tests onwaar zijn.</span><span class="sxs-lookup"><span data-stu-id="daf36-119">So, that each test is run only if all the previous tests are false.</span></span>
<span data-ttu-id="daf36-120">Als u een instructie moet maken `If` die veel elseif-instructies bevat, kunt u in plaats daarvan een switch instructie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="daf36-120">If you need to create an `If` statement that contains many Elseif statements, consider using a Switch statement instead.</span></span>

<span data-ttu-id="daf36-121">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="daf36-121">Examples:</span></span>

<span data-ttu-id="daf36-122">De eenvoudigste `If` instructie bevat één opdracht en bevat geen elseif-instructies of enige else-instructies.</span><span class="sxs-lookup"><span data-stu-id="daf36-122">The simplest `If` statement contains a single command and does not contain any Elseif statements or any Else statements.</span></span> <span data-ttu-id="daf36-123">In het volgende voor beeld ziet u de meest eenvoudige vorm van de `If` instructie:</span><span class="sxs-lookup"><span data-stu-id="daf36-123">The following example shows the simplest form of the `If` statement:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
```

<span data-ttu-id="daf36-124">Als in dit voor beeld de variabele $a groter is dan 2, wordt de voor waarde geëvalueerd als waar en wordt de instructie lijst uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="daf36-124">In this example, if the $a variable is greater than 2, the condition evaluates to true, and the statement list runs.</span></span> <span data-ttu-id="daf36-125">Als $a echter kleiner is dan of gelijk is aan 2 of niet een bestaande variabele is, `If` wordt er geen bericht weer gegeven in de instructie.</span><span class="sxs-lookup"><span data-stu-id="daf36-125">However, if $a is less than or equal to 2 or is not an existing variable, the `If` statement does not display a message.</span></span>

<span data-ttu-id="daf36-126">Door een else-instructie toe te voegen, wordt een bericht weer gegeven wanneer $a kleiner is dan of gelijk is aan 2.</span><span class="sxs-lookup"><span data-stu-id="daf36-126">By adding an Else statement, a message is displayed when $a is less than or equal to 2.</span></span> <span data-ttu-id="daf36-127">Zoals in het volgende voor beeld wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="daf36-127">As the next example shows:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
else {
    Write-Host ("The value $a is less than or equal to 2," +
        " is not created or is not initialized.")
}
```

<span data-ttu-id="daf36-128">Als u dit voor beeld verder wilt verfijnen, kunt u de instructie elseif gebruiken om een bericht weer te geven wanneer de waarde van $a gelijk is aan 2.</span><span class="sxs-lookup"><span data-stu-id="daf36-128">To further refine this example, you can use the Elseif statement to display a message when the value of $a is equal to 2.</span></span> <span data-ttu-id="daf36-129">Zoals in het volgende voor beeld wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="daf36-129">As the next example shows:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
elseif ($a -eq 2) {
    Write-Host "The value $a is equal to 2."
}
else {
    Write-Host ("The value $a is less than 2 or" +
        " was not created or initialized.")
}
```

## <a name="see-also"></a><span data-ttu-id="daf36-130">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="daf36-130">SEE ALSO</span></span>

[<span data-ttu-id="daf36-131">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="daf36-131">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="daf36-132">about_Switch</span><span class="sxs-lookup"><span data-stu-id="daf36-132">about_Switch</span></span>](about_Switch.md)
