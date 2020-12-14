---
description: Hierin wordt een taal opdracht beschreven die u kunt gebruiken om overzichts lijsten uit te voeren op basis van de resultaten van een of meer voorwaardelijke tests.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_If
ms.openlocfilehash: 04c610af36e17c02d2440ab79b7de5330e5063ab
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705908"
---
# <a name="about-if"></a><span data-ttu-id="d245d-103">Over als</span><span class="sxs-lookup"><span data-stu-id="d245d-103">About If</span></span>

## <a name="short-description"></a><span data-ttu-id="d245d-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d245d-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="d245d-105">Hierin wordt een taal opdracht beschreven die u kunt gebruiken om overzichts lijsten uit te voeren op basis van de resultaten van een of meer voorwaardelijke tests.</span><span class="sxs-lookup"><span data-stu-id="d245d-105">Describes a language command you can use to run statement lists based on the results of one or more conditional tests.</span></span>

## <a name="long-description"></a><span data-ttu-id="d245d-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d245d-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="d245d-107">U kunt de- `If` instructie gebruiken om code blokken uit te voeren als een opgegeven voorwaardelijke test resulteert in waar.</span><span class="sxs-lookup"><span data-stu-id="d245d-107">You can use the `If` statement to run code blocks if a specified conditional test evaluates to true.</span></span> <span data-ttu-id="d245d-108">U kunt ook een of meer aanvullende voorwaardelijke tests opgeven die moeten worden uitgevoerd als alle voor gaande tests resulteren in ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="d245d-108">You can also specify one or more additional conditional tests to run if all the prior tests evaluate to false.</span></span> <span data-ttu-id="d245d-109">Ten slotte kunt u een extra code blok opgeven dat wordt uitgevoerd als er geen andere eerdere voorwaardelijke test wordt geëvalueerd als waar.</span><span class="sxs-lookup"><span data-stu-id="d245d-109">Finally, you can specify an additional code block that is run if no other prior conditional test evaluates to true.</span></span>

### <a name="syntax"></a><span data-ttu-id="d245d-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="d245d-110">Syntax</span></span>

<span data-ttu-id="d245d-111">In het volgende voor beeld ziet u de syntaxis van de `If` instructie:</span><span class="sxs-lookup"><span data-stu-id="d245d-111">The following example shows the `If` statement syntax:</span></span>

```powershell
if (<test1>)
    {<statement list 1>}
[elseif (<test2>)
    {<statement list 2>}]
[else
    {<statement list 3>}]
```

<span data-ttu-id="d245d-112">Wanneer u een `If` -instructie uitvoert, evalueert Power shell de `<test1>` voorwaardelijke expressie als waar of onwaar.</span><span class="sxs-lookup"><span data-stu-id="d245d-112">When you run an `If` statement, PowerShell evaluates the `<test1>` conditional expression as true or false.</span></span> <span data-ttu-id="d245d-113">Als `<test1>` de waarde True is, `<statement list 1>` wordt uitgevoerd en Power shell de `If` instructie verlaat.</span><span class="sxs-lookup"><span data-stu-id="d245d-113">If `<test1>` is true, `<statement list 1>` runs, and PowerShell exits the `If` statement.</span></span> <span data-ttu-id="d245d-114">Als `<test1>` is ingesteld op False, wordt de voor waarde die is opgegeven door de voorwaardelijke instructie door Power shell geëvalueerd `<test2>` .</span><span class="sxs-lookup"><span data-stu-id="d245d-114">If `<test1>` is false, PowerShell evaluates the condition specified by the `<test2>` conditional statement.</span></span>

<span data-ttu-id="d245d-115">Als `<test2>` de waarde True is, `<statement list 2>` wordt uitgevoerd en Power shell de `If` instructie verlaat.</span><span class="sxs-lookup"><span data-stu-id="d245d-115">If `<test2>` is true, `<statement list 2>` runs, and PowerShell exits the `If` statement.</span></span> <span data-ttu-id="d245d-116">Als zowel `<test1>` als `<test2>` wordt geëvalueerd als onwaar, `<statement list 3` wordt het> code blok uitgevoerd en wordt de if-instructie door Power shell afgesloten.</span><span class="sxs-lookup"><span data-stu-id="d245d-116">If both `<test1>` and `<test2>` evaluate to false, the `<statement list 3`> code block runs, and PowerShell exits the If statement.</span></span>

<span data-ttu-id="d245d-117">U kunt meerdere elseif-instructies gebruiken om een reeks voorwaardelijke tests te koppelen.</span><span class="sxs-lookup"><span data-stu-id="d245d-117">You can use multiple Elseif statements to chain a series of conditional tests.</span></span> <span data-ttu-id="d245d-118">Dit betekent dat elke test alleen wordt uitgevoerd als alle vorige tests onwaar zijn.</span><span class="sxs-lookup"><span data-stu-id="d245d-118">So, that each test is run only if all the previous tests are false.</span></span>
<span data-ttu-id="d245d-119">Als u een instructie moet maken `If` die veel elseif-instructies bevat, kunt u in plaats daarvan een switch instructie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d245d-119">If you need to create an `If` statement that contains many Elseif statements, consider using a Switch statement instead.</span></span>

<span data-ttu-id="d245d-120">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="d245d-120">Examples:</span></span>

<span data-ttu-id="d245d-121">De eenvoudigste `If` instructie bevat één opdracht en bevat geen elseif-instructies of enige else-instructies.</span><span class="sxs-lookup"><span data-stu-id="d245d-121">The simplest `If` statement contains a single command and does not contain any Elseif statements or any Else statements.</span></span> <span data-ttu-id="d245d-122">In het volgende voor beeld ziet u de meest eenvoudige vorm van de `If` instructie:</span><span class="sxs-lookup"><span data-stu-id="d245d-122">The following example shows the simplest form of the `If` statement:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
```

<span data-ttu-id="d245d-123">Als in dit voor beeld de variabele $a groter is dan 2, wordt de voor waarde geëvalueerd als waar en wordt de instructie lijst uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d245d-123">In this example, if the $a variable is greater than 2, the condition evaluates to true, and the statement list runs.</span></span> <span data-ttu-id="d245d-124">Als $a echter kleiner is dan of gelijk is aan 2 of niet een bestaande variabele is, `If` wordt er geen bericht weer gegeven in de instructie.</span><span class="sxs-lookup"><span data-stu-id="d245d-124">However, if $a is less than or equal to 2 or is not an existing variable, the `If` statement does not display a message.</span></span>

<span data-ttu-id="d245d-125">Door een else-instructie toe te voegen, wordt een bericht weer gegeven wanneer $a kleiner is dan of gelijk is aan 2.</span><span class="sxs-lookup"><span data-stu-id="d245d-125">By adding an Else statement, a message is displayed when $a is less than or equal to 2.</span></span> <span data-ttu-id="d245d-126">Zoals in het volgende voor beeld wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="d245d-126">As the next example shows:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
else {
    Write-Host ("The value $a is less than or equal to 2," +
        " is not created or is not initialized.")
}
```

<span data-ttu-id="d245d-127">Als u dit voor beeld verder wilt verfijnen, kunt u de instructie elseif gebruiken om een bericht weer te geven wanneer de waarde van $a gelijk is aan 2.</span><span class="sxs-lookup"><span data-stu-id="d245d-127">To further refine this example, you can use the Elseif statement to display a message when the value of $a is equal to 2.</span></span> <span data-ttu-id="d245d-128">Zoals in het volgende voor beeld wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="d245d-128">As the next example shows:</span></span>

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

### <a name="using-the-ternary-operator-syntax"></a><span data-ttu-id="d245d-129">De syntaxis van de ternaire operator gebruiken</span><span class="sxs-lookup"><span data-stu-id="d245d-129">Using the ternary operator syntax</span></span>

<span data-ttu-id="d245d-130">Power shell 7,0 heeft een nieuwe syntaxis geïntroduceerd met behulp van de ternaire operator.</span><span class="sxs-lookup"><span data-stu-id="d245d-130">PowerShell 7.0 introduced a new syntax using the ternary operator.</span></span> <span data-ttu-id="d245d-131">Het volgt de syntaxis van C# ternaire Opera tors:</span><span class="sxs-lookup"><span data-stu-id="d245d-131">It follows the C# ternary operator syntax:</span></span>

```Syntax
<condition> ? <if-true> : <if-false>
```

<span data-ttu-id="d245d-132">De ternaire operator gedraagt zich als de vereenvoudigde `if-else` instructie.</span><span class="sxs-lookup"><span data-stu-id="d245d-132">The ternary operator behaves like the simplified `if-else` statement.</span></span> <span data-ttu-id="d245d-133">De `<condition>` expressie wordt geëvalueerd en het resultaat wordt geconverteerd naar een Booleaanse waarde om te bepalen welke vertakking vervolgens moet worden geëvalueerd:</span><span class="sxs-lookup"><span data-stu-id="d245d-133">The `<condition>` expression is evaluated and the result is converted to a boolean to determine which branch should be evaluated next:</span></span>

- <span data-ttu-id="d245d-134">De `<if-true>` expressie wordt uitgevoerd als de `<condition>` expressie True is</span><span class="sxs-lookup"><span data-stu-id="d245d-134">The `<if-true>` expression is executed if the `<condition>` expression is true</span></span>
- <span data-ttu-id="d245d-135">De `<if-false>` expressie wordt uitgevoerd als de `<condition>` expressie onwaar is</span><span class="sxs-lookup"><span data-stu-id="d245d-135">The `<if-false>` expression is executed if the `<condition>` expression is false</span></span>

<span data-ttu-id="d245d-136">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d245d-136">For example:</span></span>

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

<span data-ttu-id="d245d-137">In dit voor beeld is de waarde van `$message` ' Path exists ' bij het `Test-Path` retour neren `$true` .</span><span class="sxs-lookup"><span data-stu-id="d245d-137">In this example, the value of `$message` is "Path exists" when `Test-Path` returns `$true`.</span></span> <span data-ttu-id="d245d-138">Wanneer `Test-Path` retourneert `$false` , is de waarde van `$message` is "pad niet gevonden".</span><span class="sxs-lookup"><span data-stu-id="d245d-138">When `Test-Path` returns `$false`, the value of `$message` is "Path not found".</span></span>

```powershell
$service = Get-Service BITS
$service.Status -eq 'Running' ? (Stop-Service $service) : (Start-Service $service)
```

<span data-ttu-id="d245d-139">Als in dit voor beeld de service wordt uitgevoerd, wordt deze gestopt en als de status niet wordt **uitgevoerd**, wordt deze gestart.</span><span class="sxs-lookup"><span data-stu-id="d245d-139">In this example, if the service is running, it is stopped, and if its status is not **Running**, it is started.</span></span>

## <a name="see-also"></a><span data-ttu-id="d245d-140">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="d245d-140">SEE ALSO</span></span>

[<span data-ttu-id="d245d-141">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="d245d-141">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="d245d-142">about_Switch</span><span class="sxs-lookup"><span data-stu-id="d245d-142">about_Switch</span></span>](about_Switch.md)

