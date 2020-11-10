---
description: Hierin wordt beschreven hoe u functies maakt en gebruikt in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions
ms.openlocfilehash: 2e1a94659b3a0b8368b0b2611f470a0e676edd55
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391456"
---
# <a name="about-functions"></a><span data-ttu-id="53106-104">Over Functions</span><span class="sxs-lookup"><span data-stu-id="53106-104">About Functions</span></span>

## <a name="short-description"></a><span data-ttu-id="53106-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="53106-105">Short description</span></span>

<span data-ttu-id="53106-106">Hierin wordt beschreven hoe u functies maakt en gebruikt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="53106-106">Describes how to create and use functions in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="53106-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="53106-107">Long description</span></span>

<span data-ttu-id="53106-108">Een functie is een lijst met Power shell-instructies die een naam hebben die u toewijst.</span><span class="sxs-lookup"><span data-stu-id="53106-108">A function is a list of PowerShell statements that has a name that you assign.</span></span> <span data-ttu-id="53106-109">Wanneer u een functie uitvoert, typt u de naam van de functie.</span><span class="sxs-lookup"><span data-stu-id="53106-109">When you run a function, you type the function name.</span></span> <span data-ttu-id="53106-110">De instructies in de lijst worden uitgevoerd alsof u deze hebt getypt bij de opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="53106-110">The statements in the list run as if you had typed them at the command prompt.</span></span>

<span data-ttu-id="53106-111">Functions kunnen zo eenvoudig zijn als:</span><span class="sxs-lookup"><span data-stu-id="53106-111">Functions can be as simple as:</span></span>

```powershell
function Get-PowerShellProcess { Get-Process PowerShell }
```

<span data-ttu-id="53106-112">Een functie kan ook net zo complex zijn als een cmdlet of een toepassings programma.</span><span class="sxs-lookup"><span data-stu-id="53106-112">A function can also be as complex as a cmdlet or an application program.</span></span>

<span data-ttu-id="53106-113">Net als-cmdlets kunnen functies para meters hebben.</span><span class="sxs-lookup"><span data-stu-id="53106-113">Like cmdlets, functions can have parameters.</span></span> <span data-ttu-id="53106-114">De para meters kunnen de naam, positioneel, switch of dynamische para meters zijn.</span><span class="sxs-lookup"><span data-stu-id="53106-114">The parameters can be named, positional, switch, or dynamic parameters.</span></span> <span data-ttu-id="53106-115">Functie parameters kunnen worden gelezen vanaf de opdracht regel of vanuit de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="53106-115">Function parameters can be read from the command line or from the pipeline.</span></span>

<span data-ttu-id="53106-116">Functies kunnen waarden retour neren die kunnen worden weer gegeven, toegewezen aan variabelen of worden door gegeven aan andere functies of cmdlets.</span><span class="sxs-lookup"><span data-stu-id="53106-116">Functions can return values that can be displayed, assigned to variables, or passed to other functions or cmdlets.</span></span> <span data-ttu-id="53106-117">U kunt ook een retour waarde opgeven met behulp van het `return` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="53106-117">You can also specify a return value using the `return` keyword.</span></span> <span data-ttu-id="53106-118">Het `return` tref woord heeft geen invloed op of onderdrukt andere uitvoer die is geretourneerd door de functie.</span><span class="sxs-lookup"><span data-stu-id="53106-118">The `return` keyword does not affect or suppress other output returned from your function.</span></span> <span data-ttu-id="53106-119">Het `return` sleutel woord verlaat echter de functie op die regel.</span><span class="sxs-lookup"><span data-stu-id="53106-119">However, the `return` keyword exits the function at that line.</span></span> <span data-ttu-id="53106-120">Zie [about_Return](about_Return.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="53106-120">For more information, see [about_Return](about_Return.md).</span></span>

<span data-ttu-id="53106-121">De instructie lijst van de functie kan verschillende typen instructie lijsten bevatten met de tref woorden `Begin` , `Process` en `End` .</span><span class="sxs-lookup"><span data-stu-id="53106-121">The function's statement list can contain different types of statement lists with the keywords `Begin`, `Process`, and `End`.</span></span> <span data-ttu-id="53106-122">Deze instructie geeft een andere ingangs invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="53106-122">These statement lists handle input from the pipeline differently.</span></span>

<span data-ttu-id="53106-123">Een filter is een speciaal soort functie die gebruikmaakt van het `Filter` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="53106-123">A filter is a special kind of function that uses the `Filter` keyword.</span></span>

<span data-ttu-id="53106-124">Functies kunnen ook fungeren als-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="53106-124">Functions can also act like cmdlets.</span></span> <span data-ttu-id="53106-125">U kunt een functie maken die werkt op dezelfde manier als een cmdlet zonder `C#` Program meren te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="53106-125">You can create a function that works just like a cmdlet without using `C#` programming.</span></span> <span data-ttu-id="53106-126">Zie [about_Functions_Advanced](about_Functions_Advanced.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="53106-126">For more information, see [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="53106-127">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="53106-127">Syntax</span></span>

<span data-ttu-id="53106-128">Hier volgt de syntaxis voor een functie:</span><span class="sxs-lookup"><span data-stu-id="53106-128">The following is the syntax for a function:</span></span>

```
function [<scope:>]<name> [([type]$parameter1[,[type]$parameter2])]
{
  param([type]$parameter1 [,[type]$parameter2])
  dynamicparam {<statement list>}
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

<span data-ttu-id="53106-129">Een functie omvat de volgende items:</span><span class="sxs-lookup"><span data-stu-id="53106-129">A function includes the following items:</span></span>

- <span data-ttu-id="53106-130">Een `Function` tref woord</span><span class="sxs-lookup"><span data-stu-id="53106-130">A `Function` keyword</span></span>
- <span data-ttu-id="53106-131">Een bereik (optioneel)</span><span class="sxs-lookup"><span data-stu-id="53106-131">A scope (optional)</span></span>
- <span data-ttu-id="53106-132">Een naam die u selecteert</span><span class="sxs-lookup"><span data-stu-id="53106-132">A name that you select</span></span>
- <span data-ttu-id="53106-133">Een wille keurig aantal benoemde para meters (optioneel)</span><span class="sxs-lookup"><span data-stu-id="53106-133">Any number of named parameters (optional)</span></span>
- <span data-ttu-id="53106-134">Een of meer Power shell-opdrachten tussen accolades `{}`</span><span class="sxs-lookup"><span data-stu-id="53106-134">One or more PowerShell commands enclosed in braces `{}`</span></span>

<span data-ttu-id="53106-135">Zie about_Functions_Advanced_Parameters voor meer informatie over het `Dynamicparam` tref woord en dynamische para meters in functies. [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)</span><span class="sxs-lookup"><span data-stu-id="53106-135">For more information about the `Dynamicparam` keyword and dynamic parameters in functions, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

## <a name="simple-functions"></a><span data-ttu-id="53106-136">Eenvoudige functies</span><span class="sxs-lookup"><span data-stu-id="53106-136">Simple Functions</span></span>

<span data-ttu-id="53106-137">Functies hoeven niet ingewikkeld te zijn om nuttig te zijn.</span><span class="sxs-lookup"><span data-stu-id="53106-137">Functions do not have to be complicated to be useful.</span></span> <span data-ttu-id="53106-138">De eenvoudigste functies hebben de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="53106-138">The simplest functions have the following format:</span></span>

```
function <function-name> {statements}
```

<span data-ttu-id="53106-139">Met de volgende functie wordt Power shell bijvoorbeeld gestart met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="53106-139">For example, the following function starts PowerShell with the Run as Administrator option.</span></span>

```powershell
function Start-PSAdmin {Start-Process PowerShell -Verb RunAs}
```

<span data-ttu-id="53106-140">Als u de functie wilt gebruiken, typt u: `Start-PSAdmin`</span><span class="sxs-lookup"><span data-stu-id="53106-140">To use the function, type: `Start-PSAdmin`</span></span>

<span data-ttu-id="53106-141">Als u instructies wilt toevoegen aan de functie, typt u elke instructie op een aparte regel of gebruikt u een punt komma `;` om de instructies van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="53106-141">To add statements to the function, type each statement on a separate line, or use a semi-colon `;` to separate the statements.</span></span>

<span data-ttu-id="53106-142">Met de volgende functie vindt u bijvoorbeeld alle `.jpg` bestanden in de mappen van de huidige gebruiker die na de begin datum zijn gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="53106-142">For example, the following function finds all `.jpg` files in the current user's directories that were changed after the start date.</span></span>

```powershell
function Get-NewPix
{
  $start = Get-Date -Month 1 -Day 1 -Year 2010
  $allpix = Get-ChildItem -Path $env:UserProfile\*.jpg -Recurse
  $allpix | Where-Object {$_.LastWriteTime -gt $Start}
}
```

<span data-ttu-id="53106-143">U kunt een werkset met handige kleine functies maken.</span><span class="sxs-lookup"><span data-stu-id="53106-143">You can create a toolbox of useful small functions.</span></span> <span data-ttu-id="53106-144">Voeg deze functies toe aan uw Power shell-profiel, zoals beschreven in [about_Profiles](about_Profiles.md) en verderop in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="53106-144">Add these functions to your PowerShell profile, as described in [about_Profiles](about_Profiles.md) and later in this topic.</span></span>

## <a name="function-names"></a><span data-ttu-id="53106-145">Functie namen</span><span class="sxs-lookup"><span data-stu-id="53106-145">Function Names</span></span>

<span data-ttu-id="53106-146">U kunt een wille keurige naam toewijzen aan een functie, maar functies die u met anderen deelt, moeten voldoen aan de naamgevings regels die tot stand zijn gebracht voor alle Power shell-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="53106-146">You can assign any name to a function, but functions that you share with others should follow the naming rules that have been established for all PowerShell commands.</span></span>

<span data-ttu-id="53106-147">De namen van functies moeten bestaan uit een combi natie van woorden en zelfstandig naam woord waarin de bewerking de actie identificeert die de functie uitvoert en het zelfstandig naam woord identificeert het item waarop de cmdlet de actie uitvoert.</span><span class="sxs-lookup"><span data-stu-id="53106-147">Functions names should consist of a verb-noun pair in which the verb identifies the action that the function performs and the noun identifies the item on which the cmdlet performs its action.</span></span>

<span data-ttu-id="53106-148">Functies moeten de standaard woorden gebruiken die zijn goedgekeurd voor alle Power shell-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="53106-148">Functions should use the standard verbs that have been approved for all PowerShell commands.</span></span> <span data-ttu-id="53106-149">Met deze termen kunnen we onze opdracht namen eenvoudig, consistent en eenvoudig voor gebruikers begrijpen.</span><span class="sxs-lookup"><span data-stu-id="53106-149">These verbs help us to keep our command names simple, consistent, and easy for users to understand.</span></span>

<span data-ttu-id="53106-150">Zie [goedgekeurde werk woorden](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) in de Microsoft docs voor meer informatie over de standaard-Power shell-termen.</span><span class="sxs-lookup"><span data-stu-id="53106-150">For more information about the standard PowerShell verbs, see [Approved Verbs](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) in the Microsoft Docs.</span></span>

## <a name="functions-with-parameters"></a><span data-ttu-id="53106-151">Functies met para meters</span><span class="sxs-lookup"><span data-stu-id="53106-151">Functions with Parameters</span></span>

<span data-ttu-id="53106-152">U kunt para meters gebruiken met functies, zoals benoemde para meters, positionele para meters, Switch parameters en dynamische para meters.</span><span class="sxs-lookup"><span data-stu-id="53106-152">You can use parameters with functions, including named parameters, positional parameters, switch parameters, and dynamic parameters.</span></span> <span data-ttu-id="53106-153">Zie [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)voor meer informatie over dynamische para meters in functies.</span><span class="sxs-lookup"><span data-stu-id="53106-153">For more information about dynamic parameters in functions, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="named-parameters"></a><span data-ttu-id="53106-154">Benoemde para meters</span><span class="sxs-lookup"><span data-stu-id="53106-154">Named Parameters</span></span>

<span data-ttu-id="53106-155">U kunt een wille keurig aantal benoemde para meters definiëren.</span><span class="sxs-lookup"><span data-stu-id="53106-155">You can define any number of named parameters.</span></span> <span data-ttu-id="53106-156">U kunt een standaard waarde voor benoemde para meters toevoegen, zoals verderop in dit onderwerp wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="53106-156">You can include a default value for named parameters, as described later in this topic.</span></span>

<span data-ttu-id="53106-157">U kunt para meters definiëren in de accolades met behulp `Param` van het tref woord, zoals wordt weer gegeven in de volgende voorbeeld syntaxis:</span><span class="sxs-lookup"><span data-stu-id="53106-157">You can define parameters inside the braces using the `Param` keyword, as shown in the following sample syntax:</span></span>

```
function <name> {
  param ([type]$parameter1[,[type]$parameter2])
  <statement list>
}
```

<span data-ttu-id="53106-158">U kunt ook para meters definiëren buiten de accolades zonder het `Param` sleutel woord, zoals wordt weer gegeven in de volgende voorbeeld syntaxis:</span><span class="sxs-lookup"><span data-stu-id="53106-158">You can also define parameters outside the braces without the `Param` keyword, as shown in the following sample syntax:</span></span>

```powershell
function <name> [([type]$parameter1[,[type]$parameter2])] {
  <statement list>
}
```

<span data-ttu-id="53106-159">Hieronder ziet u een voor beeld van deze alternatieve syntaxis.</span><span class="sxs-lookup"><span data-stu-id="53106-159">Below is an example of this alternative syntax.</span></span>

```powershell
Function Add-Numbers($one, $two) {
    $one + $two
}
```

<span data-ttu-id="53106-160">Hoewel de eerste methode de voor keur heeft, is er geen verschil tussen deze twee methoden.</span><span class="sxs-lookup"><span data-stu-id="53106-160">While the first method is preferred, there is no difference between these two methods.</span></span>

<span data-ttu-id="53106-161">Wanneer u de functie uitvoert, wordt de waarde die u opgeeft voor een para meter toegewezen aan een variabele die de parameter naam bevat.</span><span class="sxs-lookup"><span data-stu-id="53106-161">When you run the function, the value you supply for a parameter is assigned to a variable that contains the parameter name.</span></span> <span data-ttu-id="53106-162">De waarde van die variabele kan worden gebruikt in de functie.</span><span class="sxs-lookup"><span data-stu-id="53106-162">The value of that variable can be used in the function.</span></span>

<span data-ttu-id="53106-163">Het volgende voor beeld is een functie met de naam `Get-SmallFiles` .</span><span class="sxs-lookup"><span data-stu-id="53106-163">The following example is a function called `Get-SmallFiles`.</span></span> <span data-ttu-id="53106-164">Deze functie heeft een `$Size` para meter.</span><span class="sxs-lookup"><span data-stu-id="53106-164">This function has a `$Size` parameter.</span></span> <span data-ttu-id="53106-165">De functie geeft alle bestanden weer die kleiner zijn dan de waarde van de `$Size` para meter en sluit mappen uit:</span><span class="sxs-lookup"><span data-stu-id="53106-165">The function displays all the files that are smaller than the value of the `$Size` parameter, and it excludes directories:</span></span>

```powershell
function Get-SmallFiles {
  Param($Size)
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

<span data-ttu-id="53106-166">In de functie kunt u de variabele gebruiken `$Size` . Dit is de naam die voor de para meter is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="53106-166">In the function, you can use the `$Size` variable, which is the name defined for the parameter.</span></span>

<span data-ttu-id="53106-167">Als u deze functie wilt gebruiken, typt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="53106-167">To use this function, type the following command:</span></span>

```powershell
Get-SmallFiles -Size 50
```

<span data-ttu-id="53106-168">U kunt ook een waarde opgeven voor een benoemde para meter zonder de parameter naam.</span><span class="sxs-lookup"><span data-stu-id="53106-168">You can also enter a value for a named parameter without the parameter name.</span></span>
<span data-ttu-id="53106-169">De volgende opdracht geeft bijvoorbeeld hetzelfde resultaat als een opdracht die de **grootte** parameter benoemt:</span><span class="sxs-lookup"><span data-stu-id="53106-169">For example, the following command gives the same result as a command that names the **Size** parameter:</span></span>

```powershell
Get-SmallFiles 50
```

<span data-ttu-id="53106-170">Als u een standaard waarde voor een para meter wilt definiëren, typt u een gelijkteken en de waarde na de parameter naam, zoals wordt weer gegeven in de volgende variant van het `Get-SmallFiles` voor beeld:</span><span class="sxs-lookup"><span data-stu-id="53106-170">To define a default value for a parameter, type an equal sign and the value after the parameter name, as shown in the following variation of the `Get-SmallFiles` example:</span></span>

```powershell
function Get-SmallFiles ($Size = 100) {
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

<span data-ttu-id="53106-171">Als u `Get-SmallFiles` zonder waarde typt, wijst de functie 100 toe aan `$size` .</span><span class="sxs-lookup"><span data-stu-id="53106-171">If you type `Get-SmallFiles` without a value, the function assigns 100 to `$size`.</span></span> <span data-ttu-id="53106-172">Als u een waarde opgeeft, gebruikt de functie die waarde.</span><span class="sxs-lookup"><span data-stu-id="53106-172">If you provide a value, the function uses that value.</span></span>

<span data-ttu-id="53106-173">U kunt desgewenst een korte Help-teken reeks opgeven die de standaard waarde van uw para meter beschrijft door het kenmerk **PSDefaultValue** toe te voegen aan de beschrijving van de para meter en de eigenschap **Help** van **PSDefaultValue** op te geven.</span><span class="sxs-lookup"><span data-stu-id="53106-173">Optionally, you can provide a brief help string that describes the default value of your parameter, by adding the **PSDefaultValue** attribute to the description of your parameter, and specifying the **Help** property of **PSDefaultValue**.</span></span> <span data-ttu-id="53106-174">Als u een Help-teken reeks wilt opgeven die de standaard waarde (100) van de para meter **Size** in de `Get-SmallFiles` functie beschrijft, voegt u het kenmerk **PSDefaultValue** toe, zoals in het volgende voor beeld wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="53106-174">To provide a help string that describes the default value (100) of the **Size** parameter in the `Get-SmallFiles` function, add the **PSDefaultValue** attribute as shown in the following example.</span></span>

```powershell
function Get-SmallFiles {
  param (
      [PSDefaultValue(Help = '100')]
      $Size = 100
  )
}
```

<span data-ttu-id="53106-175">Zie [PSDefaultValue kenmerk members](/dotnet/api/system.management.automation.psdefaultvalueattribute)(Engelstalig) voor meer informatie over de kenmerk klasse **PSDefaultValue** .</span><span class="sxs-lookup"><span data-stu-id="53106-175">For more information about the **PSDefaultValue** attribute class, see [PSDefaultValue Attribute Members](/dotnet/api/system.management.automation.psdefaultvalueattribute).</span></span>

### <a name="positional-parameters"></a><span data-ttu-id="53106-176">Positionele para meters</span><span class="sxs-lookup"><span data-stu-id="53106-176">Positional Parameters</span></span>

<span data-ttu-id="53106-177">Een positionele para meter is een para meter zonder parameter naam.</span><span class="sxs-lookup"><span data-stu-id="53106-177">A positional parameter is a parameter without a parameter name.</span></span> <span data-ttu-id="53106-178">Power shell gebruikt de volg orde van de parameter waarde om elke parameter waarde te koppelen aan een para meter in de functie.</span><span class="sxs-lookup"><span data-stu-id="53106-178">PowerShell uses the parameter value order to associate each parameter value with a parameter in the function.</span></span>

<span data-ttu-id="53106-179">Wanneer u positionele para meters gebruikt, typt u een of meer waarden achter de functie naam.</span><span class="sxs-lookup"><span data-stu-id="53106-179">When you use positional parameters, type one or more values after the function name.</span></span> <span data-ttu-id="53106-180">Positionele parameter waarden worden toegewezen aan de `$args` matrix variabele.</span><span class="sxs-lookup"><span data-stu-id="53106-180">Positional parameter values are assigned to the `$args` array variable.</span></span>
<span data-ttu-id="53106-181">De waarde die volgt op de naam van de functie wordt toegewezen aan de eerste positie in de `$args` matrix `$args[0]` .</span><span class="sxs-lookup"><span data-stu-id="53106-181">The value that follows the function name is assigned to the first position in the `$args` array, `$args[0]`.</span></span>

<span data-ttu-id="53106-182">Met de volgende `Get-Extension` functie wordt de `.txt` bestandsnaam extensie toegevoegd aan een bestands naam die u opgeeft:</span><span class="sxs-lookup"><span data-stu-id="53106-182">The following `Get-Extension` function adds the `.txt` file name extension to a file name that you supply:</span></span>

```powershell
function Get-Extension {
  $name = $args[0] + ".txt"
  $name
}
```

```powershell
Get-Extension myTextFile
```

```Output
myTextFile.txt
```

### <a name="switch-parameters"></a><span data-ttu-id="53106-183">Switch parameters</span><span class="sxs-lookup"><span data-stu-id="53106-183">Switch Parameters</span></span>

<span data-ttu-id="53106-184">Een schakel optie is een para meter waarvoor geen waarde is vereist.</span><span class="sxs-lookup"><span data-stu-id="53106-184">A switch is a parameter that does not require a value.</span></span> <span data-ttu-id="53106-185">In plaats daarvan typt u de naam van de functie, gevolgd door de naam van de para meter switch.</span><span class="sxs-lookup"><span data-stu-id="53106-185">Instead, you type the function name followed by the name of the switch parameter.</span></span>

<span data-ttu-id="53106-186">Als u een para meter switch wilt definiëren, geeft u het type `[switch]` voor de parameter naam op, zoals in het volgende voor beeld wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="53106-186">To define a switch parameter, specify the type `[switch]` before the parameter name, as shown in the following example:</span></span>

```powershell
function Switch-Item {
  param ([switch]$on)
  if ($on) { "Switch on" }
  else { "Switch off" }
}
```

<span data-ttu-id="53106-187">Wanneer u de `On` para meter switch na de functie naam typt, wordt de functie ' activeren op ' weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="53106-187">When you type the `On` switch parameter after the function name, the function displays "Switch on".</span></span> <span data-ttu-id="53106-188">Zonder de para meter switch wordt ' switch uitgeschakeld ' weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="53106-188">Without the switch parameter, it displays "Switch off".</span></span>

```powershell
Switch-Item -on
```

```Output
Switch on
```

```powershell
Switch-Item
```

```Output
Switch off
```

<span data-ttu-id="53106-189">U kunt ook een **Booleaanse** waarde toewijzen aan een switch wanneer u de functie uitvoert, zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="53106-189">You can also assign a **Boolean** value to a switch when you run the function, as shown in the following example:</span></span>

```powershell
Switch-Item -on:$true
```

```Output
Switch on
```

```powershell
Switch-Item -on:$false
```

```Output
Switch off
```

## <a name="using-splatting-to-represent-command-parameters"></a><span data-ttu-id="53106-190">Splatting gebruiken om opdracht parameters weer te geven</span><span class="sxs-lookup"><span data-stu-id="53106-190">Using Splatting to Represent Command Parameters</span></span>

<span data-ttu-id="53106-191">U kunt splatting gebruiken om de para meters van een opdracht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="53106-191">You can use splatting to represent the parameters of a command.</span></span> <span data-ttu-id="53106-192">Deze functie is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="53106-192">This feature is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="53106-193">Gebruik deze techniek in functies die opdrachten in de sessie aanroepen.</span><span class="sxs-lookup"><span data-stu-id="53106-193">Use this technique in functions that call commands in the session.</span></span> <span data-ttu-id="53106-194">U hoeft de opdracht parameters niet te declareren of te inventariseren, of u kunt de functie wijzigen als de opdracht parameter wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="53106-194">You do not need to declare or enumerate the command parameters, or change the function when command parameters change.</span></span>

<span data-ttu-id="53106-195">Met de volgende voorbeeld functie wordt de `Get-Command` cmdlet aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="53106-195">The following sample function calls the `Get-Command` cmdlet.</span></span> <span data-ttu-id="53106-196">De opdracht wordt gebruikt `@Args` om de para meters van te vertegenwoordigen `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="53106-196">The command uses `@Args` to represent the parameters of `Get-Command`.</span></span>

```powershell
function Get-MyCommand { Get-Command @Args }
```

<span data-ttu-id="53106-197">U kunt alle para meters van gebruiken `Get-Command` Wanneer u de functie aanroept `Get-MyCommand` .</span><span class="sxs-lookup"><span data-stu-id="53106-197">You can use all of the parameters of `Get-Command` when you call the `Get-MyCommand` function.</span></span> <span data-ttu-id="53106-198">De para meters en parameter waarden worden door gegeven aan de opdracht met `@Args` .</span><span class="sxs-lookup"><span data-stu-id="53106-198">The parameters and parameter values are passed to the command using `@Args`.</span></span>

```powershell
Get-MyCommand -Name Get-ChildItem
```

```Output
CommandType     Name                ModuleName
-----------     ----                ----------
Cmdlet          Get-ChildItem       Microsoft.PowerShell.Management
```

<span data-ttu-id="53106-199">De `@Args` functie maakt gebruik `$Args` van de automatische para meter, die niet-gedeclareerde cmdlet-para meters en waarden van de resterende argumenten vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="53106-199">The `@Args` feature uses the `$Args` automatic parameter, which represents undeclared cmdlet parameters and values from remaining arguments.</span></span>

<span data-ttu-id="53106-200">Zie [about_Splatting](about_Splatting.md)voor meer informatie over splatting.</span><span class="sxs-lookup"><span data-stu-id="53106-200">For more information about splatting, see [about_Splatting](about_Splatting.md).</span></span>

## <a name="piping-objects-to-functions"></a><span data-ttu-id="53106-201">Pijpleiding objecten naar functions</span><span class="sxs-lookup"><span data-stu-id="53106-201">Piping Objects to Functions</span></span>

<span data-ttu-id="53106-202">Elke functie kan invoer uit de pijp lijn nemen.</span><span class="sxs-lookup"><span data-stu-id="53106-202">Any function can take input from the pipeline.</span></span> <span data-ttu-id="53106-203">U kunt bepalen hoe een functie invoer van de pijp lijn verwerkt met `Begin` , `Process` en `End` sleutel woorden.</span><span class="sxs-lookup"><span data-stu-id="53106-203">You can control how a function processes input from the pipeline using `Begin`, `Process`, and `End` keywords.</span></span> <span data-ttu-id="53106-204">Met de volgende voorbeeld syntaxis worden de drie tref woorden weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="53106-204">The following sample syntax shows the three keywords:</span></span>

```
function <name> {
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

<span data-ttu-id="53106-205">De `Begin` lijst met overzichten wordt slechts één keer uitgevoerd, aan het begin van de functie.</span><span class="sxs-lookup"><span data-stu-id="53106-205">The `Begin` statement list runs one time only, at the beginning of the function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53106-206">Als uw functie een `Begin` , `Process` of `End` blok, definieert, moet al uw code zich in die blokken bevinden.</span><span class="sxs-lookup"><span data-stu-id="53106-206">If your function defines a `Begin`, `Process` or `End` block, all of your code must reside inside those blocks.</span></span> <span data-ttu-id="53106-207">Als *een* van de blokken is gedefinieerd, wordt er geen code buiten de blokken herkend.</span><span class="sxs-lookup"><span data-stu-id="53106-207">No code will be recognized outside the blocks if *any* of the blocks are defined.</span></span>

<span data-ttu-id="53106-208">De `Process` lijst met overzichten wordt één keer uitgevoerd voor elk object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="53106-208">The `Process` statement list runs one time for each object in the pipeline.</span></span>
<span data-ttu-id="53106-209">Terwijl het `Process` blok wordt uitgevoerd, wordt elk pijplijn object toegewezen aan de `$_` Automatische variabele, één pijplijn object tegelijk.</span><span class="sxs-lookup"><span data-stu-id="53106-209">While the `Process` block is running, each pipeline object is assigned to the `$_` automatic variable, one pipeline object at a time.</span></span>

<span data-ttu-id="53106-210">Nadat de functie alle objecten in de pijp lijn heeft ontvangen, `End` wordt de lijst met overzichten één keer uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="53106-210">After the function receives all the objects in the pipeline, the `End` statement list runs one time.</span></span> <span data-ttu-id="53106-211">Als Nee `Begin` , `Process` of als `End` tref woorden worden gebruikt, worden alle instructies behandeld, zoals een `End` lijst met overzichten.</span><span class="sxs-lookup"><span data-stu-id="53106-211">If no `Begin`, `Process`, or `End` keywords are used, all the statements are treated like an `End` statement list.</span></span>

<span data-ttu-id="53106-212">De volgende functie maakt gebruik van het `Process` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="53106-212">The following function uses the `Process` keyword.</span></span> <span data-ttu-id="53106-213">De functie geeft voor beelden uit de pijp lijn weer:</span><span class="sxs-lookup"><span data-stu-id="53106-213">The function displays examples from the pipeline:</span></span>

```powershell
function Get-Pipeline
{
  process {"The value is: $_"}
}
```

<span data-ttu-id="53106-214">Als u deze functie wilt demonstreren, geeft u een lijst met getallen op, gescheiden door komma's, zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="53106-214">To demonstrate this function, enter an list of numbers separated by commas, as shown in the following example:</span></span>

```powershell
1,2,4 | Get-Pipeline
```

```Output
The value is: 1
The value is: 2
The value is: 4
```

<span data-ttu-id="53106-215">Wanneer u een functie in een pijp lijn gebruikt, worden de objecten die naar de functie worden geleid, toegewezen aan de `$input` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="53106-215">When you use a function in a pipeline, the objects piped to the function are assigned to the `$input` automatic variable.</span></span> <span data-ttu-id="53106-216">De functie voert instructies uit met het `Begin` sleutel woord voordat er objecten uit de pijp lijn worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="53106-216">The function runs statements with the `Begin` keyword before any objects come from the pipeline.</span></span> <span data-ttu-id="53106-217">De functie voert instructies uit met het `End` sleutel woord nadat alle objecten zijn ontvangen van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="53106-217">The function runs statements with the `End` keyword after all the objects have been received from the pipeline.</span></span>

<span data-ttu-id="53106-218">In het volgende voor beeld wordt de `$input` Automatische variabele met `Begin` en `End` tref woorden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="53106-218">The following example shows the `$input` automatic variable with `Begin` and `End` keywords.</span></span>

```powershell
function Get-PipelineBeginEnd
{
  begin {"Begin: The input is $input"}
  end {"End:   The input is $input" }
}
```

<span data-ttu-id="53106-219">Als deze functie wordt uitgevoerd met behulp van de pijp lijn, worden de volgende resultaten weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="53106-219">If this function is run by using the pipeline, it displays the following results:</span></span>

```powershell
1,2,4 | Get-PipelineBeginEnd
```

```Output
Begin: The input is
End:   The input is 1 2 4
```

<span data-ttu-id="53106-220">Wanneer de `Begin` instructie wordt uitgevoerd, heeft de functie niet de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="53106-220">When the `Begin` statement runs, the function does not have the input from the pipeline.</span></span> <span data-ttu-id="53106-221">De `End` instructie wordt uitgevoerd nadat de functie de waarden heeft.</span><span class="sxs-lookup"><span data-stu-id="53106-221">The `End` statement runs after the function has the values.</span></span>

<span data-ttu-id="53106-222">Als de functie een `Process` tref woord heeft, wordt elk object in `$input` verwijderd uit `$input` en toegewezen aan `$_` .</span><span class="sxs-lookup"><span data-stu-id="53106-222">If the function has a `Process` keyword, each object in `$input` is removed from `$input` and assigned to `$_`.</span></span> <span data-ttu-id="53106-223">In het volgende voor beeld wordt een `Process` instructie lijst weer geven:</span><span class="sxs-lookup"><span data-stu-id="53106-223">The following example has a `Process` statement list:</span></span>

```powershell
function Get-PipelineInput
{
  process {"Processing:  $_ " }
  end {"End:   The input is: $input" }
}
```

<span data-ttu-id="53106-224">In dit voor beeld wordt elk object dat naar de functie is gesluisd, verzonden naar de `Process` lijst met instructies.</span><span class="sxs-lookup"><span data-stu-id="53106-224">In this example, each object that is piped to the function is sent to the `Process` statement list.</span></span> <span data-ttu-id="53106-225">De `Process` instructies worden op elk object uitgevoerd, één object per keer.</span><span class="sxs-lookup"><span data-stu-id="53106-225">The `Process` statements run on each object, one object at a time.</span></span> <span data-ttu-id="53106-226">De `$input` Automatische variabele is leeg wanneer de functie het `End` tref woord bereikt.</span><span class="sxs-lookup"><span data-stu-id="53106-226">The `$input` automatic variable is empty when the function reaches the `End` keyword.</span></span>

```powershell
1,2,4 | Get-PipelineInput
```

```Output
Processing:  1
Processing:  2
Processing:  4
End:   The input is:
```

<span data-ttu-id="53106-227">Zie [using enumeraties](about_Automatic_Variables.md#using-enumerators) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="53106-227">For more information, see [Using Enumerators](about_Automatic_Variables.md#using-enumerators)</span></span>

## <a name="filters"></a><span data-ttu-id="53106-228">Filters</span><span class="sxs-lookup"><span data-stu-id="53106-228">Filters</span></span>

<span data-ttu-id="53106-229">Een filter is een type functie dat wordt uitgevoerd op elk object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="53106-229">A filter is a type of function that runs on each object in the pipeline.</span></span> <span data-ttu-id="53106-230">Een filter lijkt op een functie met alle instructies in een `Process` blok.</span><span class="sxs-lookup"><span data-stu-id="53106-230">A filter resembles a function with all its statements in a `Process` block.</span></span>

<span data-ttu-id="53106-231">De syntaxis van een filter is als volgt:</span><span class="sxs-lookup"><span data-stu-id="53106-231">The syntax of a filter is as follows:</span></span>

```
filter [<scope:>]<name> {<statement list>}
```

<span data-ttu-id="53106-232">Het volgende filter neemt logboek vermeldingen van de pijp lijn en vervolgens wordt het hele item of alleen het bericht gedeelte van de vermelding weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="53106-232">The following filter takes log entries from the pipeline and then displays either the whole entry or only the message portion of the entry:</span></span>

```powershell
filter Get-ErrorLog ([switch]$message)
{
  if ($message) { Out-Host -InputObject $_.Message }
  else { $_ }
}
```

## <a name="function-scope"></a><span data-ttu-id="53106-233">Functie bereik</span><span class="sxs-lookup"><span data-stu-id="53106-233">Function Scope</span></span>

<span data-ttu-id="53106-234">Een functie bestaat in het bereik waarin deze is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="53106-234">A function exists in the scope in which it was created.</span></span>

<span data-ttu-id="53106-235">Als een functie deel uitmaakt van een script, is de functie beschikbaar voor instructies binnen dat script.</span><span class="sxs-lookup"><span data-stu-id="53106-235">If a function is part of a script, the function is available to statements within that script.</span></span> <span data-ttu-id="53106-236">Een functie in een script is standaard niet beschikbaar op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="53106-236">By default, a function in a script is not available at the command prompt.</span></span>

<span data-ttu-id="53106-237">U kunt het bereik van een functie opgeven.</span><span class="sxs-lookup"><span data-stu-id="53106-237">You can specify the scope of a function.</span></span> <span data-ttu-id="53106-238">De functie wordt bijvoorbeeld toegevoegd aan het globale bereik in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="53106-238">For example, the function is added to the global scope in the following example:</span></span>

```powershell
function global:Get-DependentSvs {
  Get-Service | Where-Object {$_.DependentServices}
}
```

<span data-ttu-id="53106-239">Wanneer een functie zich in het globale bereik bevindt, kunt u de functie gebruiken in scripts, in functies en op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="53106-239">When a function is in the global scope, you can use the function in scripts, in functions, and at the command line.</span></span>

<span data-ttu-id="53106-240">Functions maken normaal een bereik.</span><span class="sxs-lookup"><span data-stu-id="53106-240">Functions normally create a scope.</span></span> <span data-ttu-id="53106-241">De items die zijn gemaakt in een functie, zoals variabelen, bestaan alleen in het functie bereik.</span><span class="sxs-lookup"><span data-stu-id="53106-241">The items created in a function, such as variables, exist only in the function scope.</span></span>

<span data-ttu-id="53106-242">Zie [about_Scopes](about_Scopes.md)voor meer informatie over het bereik in Power shell.</span><span class="sxs-lookup"><span data-stu-id="53106-242">For more information about scope in PowerShell, see [about_Scopes](about_Scopes.md).</span></span>

## <a name="finding-and-managing-functions-using-the-function-drive"></a><span data-ttu-id="53106-243">Functies zoeken en beheren met behulp van de functie: station</span><span class="sxs-lookup"><span data-stu-id="53106-243">Finding and Managing Functions Using the Function: Drive</span></span>

<span data-ttu-id="53106-244">Alle functies en filters in Power shell worden automatisch opgeslagen in het `Function:` station.</span><span class="sxs-lookup"><span data-stu-id="53106-244">All the functions and filters in PowerShell are automatically stored in the `Function:` drive.</span></span> <span data-ttu-id="53106-245">Dit station wordt weer gegeven door de Power shell- **functie** provider.</span><span class="sxs-lookup"><span data-stu-id="53106-245">This drive is exposed by the PowerShell **Function** provider.</span></span>

<span data-ttu-id="53106-246">Wanneer u verwijst naar het `Function:` station, typt u een dubbele punt na **functie** , net zoals u zou doen bij het verwijzen naar de `C` of het `D` station van een computer.</span><span class="sxs-lookup"><span data-stu-id="53106-246">When referring to the `Function:` drive, type a colon after **Function** , just as you would do when referencing the `C` or `D` drive of a computer.</span></span>

<span data-ttu-id="53106-247">Met de volgende opdracht worden alle functies in de huidige sessie van Power shell weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="53106-247">The following command displays all the functions in the current session of PowerShell:</span></span>

```powershell
Get-ChildItem function:
```

<span data-ttu-id="53106-248">De opdrachten in de functie worden opgeslagen als een script blok in de eigenschap definitie van de functie.</span><span class="sxs-lookup"><span data-stu-id="53106-248">The commands in the function are stored as a script block in the definition property of the function.</span></span> <span data-ttu-id="53106-249">Als u bijvoorbeeld de opdrachten wilt weer geven in de Help-functie die wordt geleverd met Power shell, typt u:</span><span class="sxs-lookup"><span data-stu-id="53106-249">For example, to display the commands in the Help function that comes with PowerShell, type:</span></span>

```powershell
(Get-ChildItem function:help).Definition
```

<span data-ttu-id="53106-250">U kunt ook de volgende syntaxis gebruiken.</span><span class="sxs-lookup"><span data-stu-id="53106-250">You can also use the following syntax.</span></span>

```powershell
$function:help
```

<span data-ttu-id="53106-251">`Function:`Zie het Help-onderwerp voor de **functie** provider voor meer informatie over het station.</span><span class="sxs-lookup"><span data-stu-id="53106-251">For more information about the `Function:` drive, see the help topic for the **Function** provider.</span></span> <span data-ttu-id="53106-252">Typ `Get-Help Function`.</span><span class="sxs-lookup"><span data-stu-id="53106-252">Type `Get-Help Function`.</span></span>

## <a name="reusing-functions-in-new-sessions"></a><span data-ttu-id="53106-253">Functies opnieuw gebruiken in nieuwe sessies</span><span class="sxs-lookup"><span data-stu-id="53106-253">Reusing Functions in New Sessions</span></span>

<span data-ttu-id="53106-254">Wanneer u een functie typt bij de Power shell-opdracht prompt, wordt de functie onderdeel van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="53106-254">When you type a function at the PowerShell command prompt, the function becomes part of the current session.</span></span> <span data-ttu-id="53106-255">Het is beschikbaar totdat de sessie is beëindigd.</span><span class="sxs-lookup"><span data-stu-id="53106-255">It is available until the session ends.</span></span>

<span data-ttu-id="53106-256">Als u de functie in alle Power shell-sessies wilt gebruiken, voegt u de functie toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="53106-256">To use your function in all PowerShell sessions, add the function to your PowerShell profile.</span></span> <span data-ttu-id="53106-257">Zie [about_Profiles](about_Profiles.md)voor meer informatie over profielen.</span><span class="sxs-lookup"><span data-stu-id="53106-257">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="53106-258">U kunt de functie ook opslaan in een Power shell-script bestand.</span><span class="sxs-lookup"><span data-stu-id="53106-258">You can also save your function in a PowerShell script file.</span></span> <span data-ttu-id="53106-259">Typ uw functie in een tekst bestand en sla het bestand op met de `.ps1` bestandsnaam extensie.</span><span class="sxs-lookup"><span data-stu-id="53106-259">Type your function in a text file, and then save the file with the `.ps1` file name extension.</span></span>

## <a name="writing-help-for-functions"></a><span data-ttu-id="53106-260">Help-informatie over functies schrijven</span><span class="sxs-lookup"><span data-stu-id="53106-260">Writing Help for Functions</span></span>

<span data-ttu-id="53106-261">De `Get-Help` cmdlet krijgt hulp bij functies, evenals voor cmdlets, providers en scripts.</span><span class="sxs-lookup"><span data-stu-id="53106-261">The `Get-Help` cmdlet gets help for functions, as well as for cmdlets, providers, and scripts.</span></span> <span data-ttu-id="53106-262">Als u hulp wilt krijgen voor een functie, typt u `Get-Help` gevolgd door de naam van de functie.</span><span class="sxs-lookup"><span data-stu-id="53106-262">To get help for a function, type `Get-Help` followed by the function name.</span></span>

<span data-ttu-id="53106-263">Als u bijvoorbeeld hulp voor de functie wilt weer geven `Get-MyDisks` , typt u:</span><span class="sxs-lookup"><span data-stu-id="53106-263">For example, to get help for the `Get-MyDisks` function, type:</span></span>

```powershell
Get-Help Get-MyDisks
```

<span data-ttu-id="53106-264">U kunt op een van de volgende twee manieren hulp voor een functie schrijven:</span><span class="sxs-lookup"><span data-stu-id="53106-264">You can write help for a function by using either of the two following methods:</span></span>

- <span data-ttu-id="53106-265">Help voor functies Comment-Based</span><span class="sxs-lookup"><span data-stu-id="53106-265">Comment-Based Help for Functions</span></span>

  <span data-ttu-id="53106-266">Maak een Help-onderwerp met behulp van speciale tref woorden in de opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="53106-266">Create a help topic by using special keywords in the comments.</span></span> <span data-ttu-id="53106-267">Als u op opmerkingen gebaseerde hulp voor een functie wilt maken, moeten de opmerkingen aan het begin of einde van de hoofd tekst van de functie of op de regels vóór het gereserveerde woord function worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="53106-267">To create comment-based help for a function, the comments must be placed at the beginning or end of the function body or on the lines preceding the function keyword.</span></span> <span data-ttu-id="53106-268">Zie [about_Comment_Based_Help](about_Comment_Based_Help.md)voor meer informatie over op opmerkingen gebaseerde Help.</span><span class="sxs-lookup"><span data-stu-id="53106-268">For more information about comment-based help, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span>

- <span data-ttu-id="53106-269">Help voor functies XML-Based</span><span class="sxs-lookup"><span data-stu-id="53106-269">XML-Based Help for Functions</span></span>

  <span data-ttu-id="53106-270">Maak een Help-onderwerp op basis van XML, zoals het type dat doorgaans voor cmdlets wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="53106-270">Create an XML-based help topic, such as the type that is typically created for cmdlets.</span></span> <span data-ttu-id="53106-271">Help op basis van XML is vereist als u Help-onderwerpen in meerdere talen onderlokaliseert.</span><span class="sxs-lookup"><span data-stu-id="53106-271">XML-based help is required if you are localizing help topics into multiple languages.</span></span>

  <span data-ttu-id="53106-272">Als u de functie wilt koppelen aan het Help-onderwerp met XML, gebruikt u het `.ExternalHelp` tref woord Help op basis van opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="53106-272">To associate the function with the XML-based help topic, use the `.ExternalHelp` comment-based help keyword.</span></span> <span data-ttu-id="53106-273">Zonder dit sleutel woord `Get-Help` kan het Help-onderwerp van de functie niet worden gevonden en wordt aanroepen naar `Get-Help` voor de functie retourneert alleen automatisch gegenereerde Help.</span><span class="sxs-lookup"><span data-stu-id="53106-273">Without this keyword, `Get-Help` cannot find the function help topic and calls to `Get-Help` for the function return only auto-generated help.</span></span>

  <span data-ttu-id="53106-274">Zie about_Comment_Based_Help voor meer informatie over het `ExternalHelp` tref [about_Comment_Based_Help](about_Comment_Based_Help.md)woord.</span><span class="sxs-lookup"><span data-stu-id="53106-274">For more information about the `ExternalHelp` keyword, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span> <span data-ttu-id="53106-275">Zie [instructies voor het schrijven van cmdlets](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)voor meer informatie over Help op basis van XML.</span><span class="sxs-lookup"><span data-stu-id="53106-275">For more information about XML-based help, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="see-also"></a><span data-ttu-id="53106-276">Zie tevens</span><span class="sxs-lookup"><span data-stu-id="53106-276">See also</span></span>

[<span data-ttu-id="53106-277">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="53106-277">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="53106-278">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="53106-278">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="53106-279">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="53106-279">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="53106-280">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="53106-280">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="53106-281">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="53106-281">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="53106-282">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="53106-282">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="53106-283">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="53106-283">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="53106-284">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="53106-284">about_Parameters</span></span>](about_Parameters.md)

[<span data-ttu-id="53106-285">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="53106-285">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="53106-286">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="53106-286">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="53106-287">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="53106-287">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="53106-288">about_Function_provider</span><span class="sxs-lookup"><span data-stu-id="53106-288">about_Function_provider</span></span>](about_Function_provider.md)
