---
description: Hierin wordt een taal opdracht beschreven die u kunt gebruiken om-instructies uit te voeren op basis van een voorwaardelijke test.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 3/4/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_for?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_For
ms.openlocfilehash: 28d901c62ccc17febb74412a773710f4d5b5a4be
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252622"
---
# <a name="about-for"></a><span data-ttu-id="0a63d-104">Over voor</span><span class="sxs-lookup"><span data-stu-id="0a63d-104">About For</span></span>

## <a name="short-description"></a><span data-ttu-id="0a63d-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="0a63d-105">Short description</span></span>
<span data-ttu-id="0a63d-106">Hierin wordt een taal opdracht beschreven die u kunt gebruiken om-instructies uit te voeren op basis van een voorwaardelijke test.</span><span class="sxs-lookup"><span data-stu-id="0a63d-106">Describes a language command you can use to run statements based on a conditional test.</span></span>

## <a name="long-description"></a><span data-ttu-id="0a63d-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="0a63d-107">Long description</span></span>

<span data-ttu-id="0a63d-108">De `For` instructie (ook wel een `For` lus genoemd) is een taal constructie die u kunt gebruiken om een lus te maken waarmee opdrachten in een opdracht blok worden uitgevoerd terwijl een opgegeven voor waarde wordt geëvalueerd `$true` .</span><span class="sxs-lookup"><span data-stu-id="0a63d-108">The `For` statement (also known as a `For` loop) is a language construct you can use to create a loop that runs commands in a command block while a specified condition evaluates to `$true`.</span></span>

<span data-ttu-id="0a63d-109">Een typisch gebruik van de `For` lus is het herhalen van een matrix met waarden en voor het uitvoeren van een subset van deze waarden.</span><span class="sxs-lookup"><span data-stu-id="0a63d-109">A typical use of the `For` loop is to iterate an array of values and to operate on a subset of these values.</span></span> <span data-ttu-id="0a63d-110">In de meeste gevallen kunt u een instructie gebruiken als u alle waarden in een matrix wilt herhalen `Foreach` .</span><span class="sxs-lookup"><span data-stu-id="0a63d-110">In most cases, if you want to iterate all the values in an array, consider using a `Foreach` statement.</span></span>

### <a name="syntax"></a><span data-ttu-id="0a63d-111">Syntax</span><span class="sxs-lookup"><span data-stu-id="0a63d-111">Syntax</span></span>

<span data-ttu-id="0a63d-112">Hieronder ziet u de `For` syntaxis van de instructie.</span><span class="sxs-lookup"><span data-stu-id="0a63d-112">The following shows the `For` statement syntax.</span></span>

```
for (<Init>; <Condition>; <Repeat>)
{
    <Statement list>
}
```

<span data-ttu-id="0a63d-113">De tijdelijke aanduiding **init** vertegenwoordigt een of meer opdrachten die worden uitgevoerd voordat de lus begint.</span><span class="sxs-lookup"><span data-stu-id="0a63d-113">The **Init** placeholder represents one or more commands that are run before the loop begins.</span></span> <span data-ttu-id="0a63d-114">Normaal gesp roken gebruikt u het **init** -gedeelte van de-instructie om een variabele met een begin waarde te maken en initialiseren.</span><span class="sxs-lookup"><span data-stu-id="0a63d-114">You typically use the **Init** portion of the statement to create and initialize a variable with a starting value.</span></span>

<span data-ttu-id="0a63d-115">Deze variabele wordt vervolgens de basis voor de voor waarde die in het volgende gedeelte van de instructie moet worden getest `For` .</span><span class="sxs-lookup"><span data-stu-id="0a63d-115">This variable will then be the basis for the condition to be tested in the next portion of the `For` statement.</span></span>

<span data-ttu-id="0a63d-116">De tijdelijke aanduiding **voor de voor waarde** vertegenwoordigt het gedeelte van de `For` instructie dat wordt omgezet in een `$true` of `$false` **Booleaanse** waarde.</span><span class="sxs-lookup"><span data-stu-id="0a63d-116">The **Condition** placeholder represents the portion of the `For` statement that resolves to a `$true` or `$false` **Boolean** value.</span></span> <span data-ttu-id="0a63d-117">Power shell evalueert de voor waarde telkens wanneer de `For` lus wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0a63d-117">PowerShell evaluates the condition each time the `For` loop runs.</span></span> <span data-ttu-id="0a63d-118">Als de instructie is `$true` , worden de opdrachten in het opdracht blok uitgevoerd en wordt de instructie opnieuw geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="0a63d-118">If the statement is `$true`, the commands in the command block run, and the statement is evaluated again.</span></span> <span data-ttu-id="0a63d-119">Als de voor waarde nog steeds is `$true` , worden de opdrachten in de **instructie lijst** opnieuw uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0a63d-119">If the condition is still `$true`, the commands in the **Statement list** run again.</span></span> <span data-ttu-id="0a63d-120">De lus wordt herhaald totdat de voor waarde wordt gewijzigd `$false` .</span><span class="sxs-lookup"><span data-stu-id="0a63d-120">The loop is repeated until the condition becomes `$false`.</span></span>

<span data-ttu-id="0a63d-121">De tijdelijke aanduiding voor **herhalingen** bevat een of meer opdrachten, gescheiden door komma's, die worden uitgevoerd telkens wanneer de lus wordt herhaald.</span><span class="sxs-lookup"><span data-stu-id="0a63d-121">The **Repeat** placeholder represents one or more commands, separated by commas, that are executed each time the loop repeats.</span></span> <span data-ttu-id="0a63d-122">Dit wordt meestal gebruikt voor het wijzigen van een variabele die wordt getest in het onderdeel **voor waarde** van de-instructie.</span><span class="sxs-lookup"><span data-stu-id="0a63d-122">Typically, this is used to modify a variable that is tested inside the **Condition** part of the statement.</span></span>

<span data-ttu-id="0a63d-123">De tijdelijke aanduiding **lijst** bevat een verzameling van een of meer opdrachten die elke keer dat de lus wordt ingevoerd of herhaald wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0a63d-123">The **Statement list** placeholder represents a set of one or more commands that are run each time the loop is entered or repeated.</span></span> <span data-ttu-id="0a63d-124">De inhoud van de **instructie lijst** wordt omgeven door accolades.</span><span class="sxs-lookup"><span data-stu-id="0a63d-124">The contents of the **Statement list** are surrounded by braces.</span></span>

### <a name="support-for-multiple-operations"></a><span data-ttu-id="0a63d-125">Ondersteuning voor meerdere bewerkingen</span><span class="sxs-lookup"><span data-stu-id="0a63d-125">Support for multiple operations</span></span>

<span data-ttu-id="0a63d-126">De volgende syntaxis worden ondersteund voor bewerkingen met meerdere toewijzingen in de instructie **init** :</span><span class="sxs-lookup"><span data-stu-id="0a63d-126">The following syntaxes are supported for multiple assignment operations in the **Init** statement:</span></span>

```powershell
# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}
```

<span data-ttu-id="0a63d-127">De volgende syntaxis worden ondersteund voor bewerkingen met meerdere toewijzingen in de instructie **repeat** :</span><span class="sxs-lookup"><span data-stu-id="0a63d-127">The following syntaxes are supported for multiple assignment operations in the **Repeat** statement:</span></span>

```powershell
# Comma separated assignment expressions.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; ($i++), ($j++))
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $($i++;$j++))
{
    "`$i:$i"
    "`$j:$j"
}
```

> [!NOTE]
> <span data-ttu-id="0a63d-128">Andere bewerkingen dan vóór of na het uitvoeren van een incrementeel werken mogelijk niet met alle-syntaxis.</span><span class="sxs-lookup"><span data-stu-id="0a63d-128">Operations other than pre or post increment may not work with all syntaxes.</span></span>

<span data-ttu-id="0a63d-129">Voor meerdere **voor waarden** worden logische Opera tors gebruikt, zoals wordt getoond in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="0a63d-129">For multiple **Conditions** use logical operators as demonstrated by the following example.</span></span>

```powershell
for (($i = 0), ($j = 0); $i -lt 10 -and $j -lt 10; $i++,$j++)
{
    "`$i:$i"
    "`$j:$j"
}
```

<span data-ttu-id="0a63d-130">Zie [about_Logical_Operators](about_Logical_Operators.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0a63d-130">For more information, see [about_Logical_Operators](about_Logical_Operators.md).</span></span>

### <a name="examples"></a><span data-ttu-id="0a63d-131">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="0a63d-131">Examples</span></span>

<span data-ttu-id="0a63d-132">Een instructie vereist mini maal `For` het haakje rond het **init** , de **voor waarde** en het **herhaalde** gedeelte van de instructie en een opdracht omgeven door accolades in het **overzichts** deel van de instructie.</span><span class="sxs-lookup"><span data-stu-id="0a63d-132">At a minimum, a `For` statement requires the parenthesis surrounding the **Init** , **Condition** , and **Repeat** part of the statement and a command surrounded by braces in the **Statement list** part of the statement.</span></span>

<span data-ttu-id="0a63d-133">Houd er rekening mee dat de komende voor beelden opzettelijk code weer geven buiten de- `For` instructie.</span><span class="sxs-lookup"><span data-stu-id="0a63d-133">Note that the upcoming examples intentionally show code outside the `For` statement.</span></span> <span data-ttu-id="0a63d-134">In latere voor beelden is code geïntegreerd in de- `For` instructie.</span><span class="sxs-lookup"><span data-stu-id="0a63d-134">In later examples, code is integrated into the `For` statement.</span></span>

<span data-ttu-id="0a63d-135">Met de volgende `For` instructie wordt de waarde van de variabele bijvoorbeeld continu weer gegeven `$i` totdat u de opdracht hand matig uitbreekt door op CTRL + C te drukken.</span><span class="sxs-lookup"><span data-stu-id="0a63d-135">For example, the following `For` statement continually displays the value of the `$i` variable until you manually break out of the command by pressing CTRL+C.</span></span>

```powershell
$i = 1
for (;;)
{
    Write-Host $i
}
```

<span data-ttu-id="0a63d-136">U kunt extra opdrachten toevoegen aan de lijst met overzichten, zodat de waarde van `$i` wordt verhoogd met 1 telkens wanneer de lus wordt uitgevoerd, zoals in het volgende voor beeld wordt getoond.</span><span class="sxs-lookup"><span data-stu-id="0a63d-136">You can add additional commands to the statement list so that the value of `$i` is incremented by 1 each time the loop is run, as the following example shows.</span></span>

```powershell
for (;;)
{
    $i++; Write-Host $i
}
```

<span data-ttu-id="0a63d-137">Totdat u de opdracht opbreekt door op CTRL + C te drukken, wordt door deze instructie voortdurend de waarde van de variabele weer gegeven `$i` wanneer deze wordt verhoogd met 1 telkens wanneer de lus wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0a63d-137">Until you break out of the command by pressing CTRL+C, this statement will continually display the value of the `$i` variable as it is incremented by 1 each time the loop is run.</span></span>

<span data-ttu-id="0a63d-138">In plaats van de waarde van de variabele te wijzigen in het overzichts deel van het `For` overzicht, kunt u het **herhalings** gedeelte van de `For` instructie als volgt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="0a63d-138">Rather than change the value of the variable in the statement list part of the `For` statement, you can use the **Repeat** portion of the `For` statement instead, as follows.</span></span>

```powershell
$i=1
for (;;$i++)
{
    Write-Host $i
}
```

<span data-ttu-id="0a63d-139">Deze instructie wordt pas voor onbepaalde tijd herhaald als u de opdracht uitbreekt door op CTRL + C te drukken.</span><span class="sxs-lookup"><span data-stu-id="0a63d-139">This statement will still repeat indefinitely until you break out of the command by pressing CTRL+C.</span></span>

<span data-ttu-id="0a63d-140">U kunt de `For` lus beëindigen met een *voor waarde*.</span><span class="sxs-lookup"><span data-stu-id="0a63d-140">You can terminate the `For` loop using a *condition*.</span></span> <span data-ttu-id="0a63d-141">U kunt een voor waarde plaatsen met behulp van het **voor waarde** -gedeelte van de `For` instructie.</span><span class="sxs-lookup"><span data-stu-id="0a63d-141">You can place a condition using the **Condition** portion of the `For` statement.</span></span> <span data-ttu-id="0a63d-142">De `For` lus wordt beëindigd wanneer de voor waarde wordt geëvalueerd `$false` .</span><span class="sxs-lookup"><span data-stu-id="0a63d-142">The `For` loop terminates when the condition evaluates to `$false`.</span></span>

<span data-ttu-id="0a63d-143">In het volgende voor beeld `For` wordt de lus uitgevoerd terwijl de waarde van `$i` kleiner dan of gelijk aan 10 is.</span><span class="sxs-lookup"><span data-stu-id="0a63d-143">In the following example, the `For` loop runs while the value of `$i` is less than or equal to 10.</span></span>

```powershell
$i=1
for(;$i -le 10;$i++)
{
    Write-Host $i
}
```

<span data-ttu-id="0a63d-144">In plaats van het maken en initialiseren van de variabele buiten de `For` -instructie kunt u deze taak in de `For` lus uitvoeren met behulp van het gedeelte **init** van de- `For` instructie.</span><span class="sxs-lookup"><span data-stu-id="0a63d-144">Instead of creating and initializing the variable outside the `For` statement, you can perform this task inside the `For` loop by using the **Init** portion of the `For` statement.</span></span>

```powershell
for($i=1; $i -le 10; $i++){Write-Host $i}
```

<span data-ttu-id="0a63d-145">U kunt regel terugloop gebruiken in plaats van punt komma's om de **initialisatie** , **voor waarde** en **herhaling** delen van de instructie te beperken `For` .</span><span class="sxs-lookup"><span data-stu-id="0a63d-145">You can use carriage returns instead of semicolons to delimit the **Init** , **Condition** , and **Repeat** portions of the `For` statement.</span></span> <span data-ttu-id="0a63d-146">In het volgende voor beeld ziet `For` u een die gebruikmaakt van deze alternatieve syntaxis.</span><span class="sxs-lookup"><span data-stu-id="0a63d-146">The following example shows a `For` that uses this alternative syntax.</span></span>

```powershell
for ($i = 0
  $i -lt 10
  $i++){
  $i
}
```

<span data-ttu-id="0a63d-147">Deze alternatieve vorm van de `For` instructie werkt in Power shell-script bestanden en de Power shell-opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="0a63d-147">This alternative form of the `For` statement works in PowerShell script files and at the PowerShell command prompt.</span></span> <span data-ttu-id="0a63d-148">Het is echter gemakkelijker om de `For` syntaxis van de instructie te gebruiken met punt komma's wanneer u interactieve opdrachten invoert bij de opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="0a63d-148">However, it is easier to use the `For` statement syntax with semicolons when you enter interactive commands at the command prompt.</span></span>

<span data-ttu-id="0a63d-149">De `For` lus is flexibeler dan de `Foreach` lus, omdat u hiermee waarden in een matrix of verzameling kunt verhogen met behulp van patronen.</span><span class="sxs-lookup"><span data-stu-id="0a63d-149">The `For` loop is more flexible than the `Foreach` loop because it allows you to increment values in an array or collection by using patterns.</span></span> <span data-ttu-id="0a63d-150">In het volgende voor beeld `$i` wordt de variabele verhoogd met 2 in het **herhalings** gedeelte van de- `For` instructie.</span><span class="sxs-lookup"><span data-stu-id="0a63d-150">In the following example, the `$i` variable is incremented by 2 in the **Repeat** portion of the `For` statement.</span></span>

```powershell
for ($i = 0; $i -le 20; $i += 2)
{
    Write-Host $i
}
```

<span data-ttu-id="0a63d-151">De `For` lus kan ook op één regel worden geschreven, zoals in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="0a63d-151">The `For` loop can also be written on one line as in the following example.</span></span>

```powershell
for ($i = 0; $i -lt 10; $i++) { Write-Host $i }
```

## <a name="see-also"></a><span data-ttu-id="0a63d-152">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="0a63d-152">SEE ALSO</span></span>

[<span data-ttu-id="0a63d-153">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="0a63d-153">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="0a63d-154">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="0a63d-154">about_Foreach</span></span>](about_Foreach.md)
