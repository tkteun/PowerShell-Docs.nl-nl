---
description: Hierin wordt beschreven hoe variabelen waarden opslaan die kunnen worden gebruikt in Power shell.
Locale: en-US
ms.date: 03/30/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variables?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Variables
ms.openlocfilehash: 6b9c80eef17838d57109e035aff9b0a099c5c2dc
ms.sourcegitcommit: 4d6ed6f7d747a9bbb3fcfcf6c981c5aa8a973a08
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/31/2021
ms.locfileid: "106072505"
---
# <a name="about-variables"></a><span data-ttu-id="75b9c-103">Over variabelen</span><span class="sxs-lookup"><span data-stu-id="75b9c-103">About Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="75b9c-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="75b9c-104">Short description</span></span>

<span data-ttu-id="75b9c-105">Hierin wordt beschreven hoe variabelen waarden opslaan die kunnen worden gebruikt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="75b9c-105">Describes how variables store values that can be used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="75b9c-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="75b9c-106">Long description</span></span>

<span data-ttu-id="75b9c-107">U kunt alle typen waarden opslaan in Power shell-variabelen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-107">You can store all types of values in PowerShell variables.</span></span> <span data-ttu-id="75b9c-108">U kunt bijvoorbeeld de resultaten van opdrachten opslaan en elementen opslaan die in opdrachten en expressies worden gebruikt, zoals namen, paden, instellingen en waarden.</span><span class="sxs-lookup"><span data-stu-id="75b9c-108">For example, store the results of commands, and store elements that are used in commands and expressions, such as names, paths, settings, and values.</span></span>

<span data-ttu-id="75b9c-109">Een variabele is een geheugen eenheid waarin waarden worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-109">A variable is a unit of memory in which values are stored.</span></span> <span data-ttu-id="75b9c-110">In Power shell worden variabelen vertegenwoordigd door teken reeksen die beginnen met een dollar teken ( `$` ), zoals `$a` , `$process` of `$my_var` .</span><span class="sxs-lookup"><span data-stu-id="75b9c-110">In PowerShell, variables are represented by text strings that begin with a dollar sign (`$`), such as `$a`, `$process`, or `$my_var`.</span></span>

<span data-ttu-id="75b9c-111">Namen van variabelen zijn niet hoofdletter gevoelig en kunnen spaties en speciale tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="75b9c-111">Variable names aren't case-sensitive, and can include spaces and special characters.</span></span> <span data-ttu-id="75b9c-112">Namen van variabelen met speciale tekens en spaties zijn echter lastig te gebruiken en moeten worden vermeden.</span><span class="sxs-lookup"><span data-stu-id="75b9c-112">But, variable names that include special characters and spaces are difficult to use and should be avoided.</span></span> <span data-ttu-id="75b9c-113">Zie [namen van variabelen die speciale tekens bevatten](#variable-names-that-include-special-characters)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="75b9c-113">For more information, see [Variable names that include special characters](#variable-names-that-include-special-characters).</span></span>

<span data-ttu-id="75b9c-114">Er zijn verschillende typen variabelen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="75b9c-114">There are several different types of variables in PowerShell.</span></span>

- <span data-ttu-id="75b9c-115">Door gebruiker gemaakte variabelen: door de gebruiker gemaakte variabelen worden gemaakt en onderhouden door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="75b9c-115">User-created variables: User-created variables are created and maintained by the user.</span></span> <span data-ttu-id="75b9c-116">De variabelen die u in de Power shell-opdracht regel maakt, bestaan standaard alleen wanneer het Power shell-venster is geopend.</span><span class="sxs-lookup"><span data-stu-id="75b9c-116">By default, the variables that you create at the PowerShell command line exist only while the PowerShell window is open.</span></span> <span data-ttu-id="75b9c-117">Wanneer het Power shell-venster wordt gesloten, worden de variabelen verwijderd.</span><span class="sxs-lookup"><span data-stu-id="75b9c-117">When the PowerShell windows is closed, the variables are deleted.</span></span> <span data-ttu-id="75b9c-118">Als u een variabele wilt opslaan, voegt u deze toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="75b9c-118">To save a variable, add it to your PowerShell profile.</span></span> <span data-ttu-id="75b9c-119">U kunt ook variabelen maken in scripts met globaal, script of lokaal bereik.</span><span class="sxs-lookup"><span data-stu-id="75b9c-119">You can also create variables in scripts with global, script, or local scope.</span></span>

- <span data-ttu-id="75b9c-120">Automatische variabelen: automatische variabelen slaan de status van Power shell op.</span><span class="sxs-lookup"><span data-stu-id="75b9c-120">Automatic variables: Automatic variables store the state of PowerShell.</span></span> <span data-ttu-id="75b9c-121">Deze variabelen worden gemaakt door Power shell en Power shell wijzigt hun waarden naar behoefte om hun nauw keurigheid te behouden.</span><span class="sxs-lookup"><span data-stu-id="75b9c-121">These variables are created by PowerShell, and PowerShell changes their values as required to maintain their accuracy.</span></span> <span data-ttu-id="75b9c-122">Gebruikers kunnen de waarde van deze variabelen niet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-122">Users can't change the value of these variables.</span></span> <span data-ttu-id="75b9c-123">De `$PSHOME` variabele slaat bijvoorbeeld het pad op naar de installatie directory van Power shell.</span><span class="sxs-lookup"><span data-stu-id="75b9c-123">For example, the `$PSHOME` variable stores the path to the PowerShell installation directory.</span></span>

  <span data-ttu-id="75b9c-124">Zie [about_Automatic_Variables](about_Automatic_Variables.md)voor meer informatie, een lijst en een beschrijving van de automatische variabelen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-124">For more information, a list, and a description of the automatic variables, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

- <span data-ttu-id="75b9c-125">Voorkeurs variabelen: voorkeurs variabelen slaan gebruikers voorkeuren op voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="75b9c-125">Preference variables: Preference variables store user preferences for PowerShell.</span></span> <span data-ttu-id="75b9c-126">Deze variabelen worden gemaakt door Power shell en worden gevuld met standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="75b9c-126">These variables are created by PowerShell and are populated with default values.</span></span> <span data-ttu-id="75b9c-127">Gebruikers kunnen de waarden van deze variabelen wijzigen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-127">Users can change the values of these variables.</span></span> <span data-ttu-id="75b9c-128">De `$MaximumHistoryCount` variabele bepaalt bijvoorbeeld het maximum aantal vermeldingen in de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="75b9c-128">For example, the `$MaximumHistoryCount` variable determines the maximum number of entries in the session history.</span></span>

  <span data-ttu-id="75b9c-129">Zie [about_Preference_Variables](about_Preference_Variables.md)voor meer informatie, een lijst en een beschrijving van de voorkeurs variabelen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-129">For more information, a list, and a description of the preference variables, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

## <a name="working-with-variables"></a><span data-ttu-id="75b9c-130">Werken met variabelen</span><span class="sxs-lookup"><span data-stu-id="75b9c-130">Working with variables</span></span>

<span data-ttu-id="75b9c-131">Als u een nieuwe variabele wilt maken, gebruikt u een toewijzings instructie om een waarde toe te wijzen aan de variabele.</span><span class="sxs-lookup"><span data-stu-id="75b9c-131">To create a new variable, use an assignment statement to assign a value to the variable.</span></span> <span data-ttu-id="75b9c-132">U hoeft de variabele niet te declareren voordat u deze gebruikt.</span><span class="sxs-lookup"><span data-stu-id="75b9c-132">You don't have to declare the variable before using it.</span></span> <span data-ttu-id="75b9c-133">De standaard waarde van alle variabelen is `$null` .</span><span class="sxs-lookup"><span data-stu-id="75b9c-133">The default value of all variables is `$null`.</span></span>

<span data-ttu-id="75b9c-134">Als u een lijst wilt weer geven met alle variabelen in uw Power shell-sessie, typt u `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="75b9c-134">To get a list of all the variables in your PowerShell session, type `Get-Variable`.</span></span> <span data-ttu-id="75b9c-135">De namen van variabelen worden weer gegeven zonder het voor gaande dollar `$` teken () dat wordt gebruikt om te verwijzen naar variabelen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-135">The variable names are displayed without the preceding dollar (`$`) sign that is used to reference variables.</span></span>

<span data-ttu-id="75b9c-136">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="75b9c-136">For example:</span></span>

```powershell
$MyVariable = 1, 2, 3

$Path = "C:\Windows\System32"
```

<span data-ttu-id="75b9c-137">Variabelen zijn handig om de resultaten van opdrachten op te slaan.</span><span class="sxs-lookup"><span data-stu-id="75b9c-137">Variables are useful for storing the results of commands.</span></span>

<span data-ttu-id="75b9c-138">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="75b9c-138">For example:</span></span>

```powershell
$Processes = Get-Process

$Today = (Get-Date).DateTime
```

<span data-ttu-id="75b9c-139">Als u de waarde van een variabele wilt weer geven, typt u de naam van de variabele, voorafgegaan door een dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="75b9c-139">To display the value of a variable, type the variable name, preceded by a dollar sign (`$`).</span></span>

<span data-ttu-id="75b9c-140">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="75b9c-140">For example:</span></span>

```powershell
$MyVariable
```

```Output
1
2
3
```

```powershell
$Today
```

```Output
Tuesday, September 3, 2019 09:46:46
```

<span data-ttu-id="75b9c-141">Als u de waarde van een variabele wilt wijzigen, wijst u een nieuwe waarde toe aan de variabele.</span><span class="sxs-lookup"><span data-stu-id="75b9c-141">To change the value of a variable, assign a new value to the variable.</span></span>

<span data-ttu-id="75b9c-142">In de volgende voor beelden wordt de waarde van de variabele weer gegeven `$MyVariable` , wordt de waarde van de variabele gewijzigd, waarna de nieuwe waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="75b9c-142">The following examples display the value of the `$MyVariable` variable, changes the value of the variable, and then displays the new value.</span></span>

```powershell
$MyVariable = 1, 2, 3
$MyVariable
```

```Output
1
2
3
```

```powershell
$MyVariable = "The green cat."
$MyVariable
```

```Output
The green cat.
```

<span data-ttu-id="75b9c-143">Als u de waarde van een variabele wilt verwijderen, gebruikt u de `Clear-Variable` cmdlet of wijzigt u de waarde in `$null` .</span><span class="sxs-lookup"><span data-stu-id="75b9c-143">To delete the value of a variable, use the `Clear-Variable` cmdlet or change the value to `$null`.</span></span>

```powershell
Clear-Variable -Name MyVariable
```

```powershell
$MyVariable = $null
```

<span data-ttu-id="75b9c-144">Als u de variabele wilt verwijderen, gebruikt u [Remove-variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) of [Remove-item](xref:Microsoft.PowerShell.Management.Remove-Item).</span><span class="sxs-lookup"><span data-stu-id="75b9c-144">To delete the variable, use [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) or [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item).</span></span>

```powershell
Remove-Variable -Name MyVariable
```

```powershell
Remove-Item -Path Variable:\MyVariable
```

<span data-ttu-id="75b9c-145">Het is ook mogelijk om waarden toe te staan op meerdere variabelen met één instructie.</span><span class="sxs-lookup"><span data-stu-id="75b9c-145">It is also possible to values to multiple variables with one statement.</span></span> <span data-ttu-id="75b9c-146">In de volgende voor beelden wordt dezelfde waarde toegewezen aan meerdere variabelen:</span><span class="sxs-lookup"><span data-stu-id="75b9c-146">The following examples assigns the same value to multiple variables:</span></span>

```powershell
$a = $b = $c = 0
```

<span data-ttu-id="75b9c-147">In het volgende voor beeld worden meerdere waarden toegewezen aan meerdere variabelen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-147">The next example assigns multiple values to multiple variables.</span></span>

```powershell
$i,$j,$k = 10, "red", $true    # $i is 10, $j is "red", $k is True
$i,$j = 10, "red", $true       # $i is 10, $j is [object[]], Length 2
```

<span data-ttu-id="75b9c-148">Zie de sectie **meerdere variabelen toewijzen** van [about_Assignment_Operators](about_assignment_operators.md#assigning-multiple-variables)voor meer gedetailleerde informatie.</span><span class="sxs-lookup"><span data-stu-id="75b9c-148">For more detailed information, see the **Assigning multiple variables** section of [about_Assignment_Operators](about_assignment_operators.md#assigning-multiple-variables).</span></span>

## <a name="types-of-variables"></a><span data-ttu-id="75b9c-149">Typen variabelen</span><span class="sxs-lookup"><span data-stu-id="75b9c-149">Types of variables</span></span>

<span data-ttu-id="75b9c-150">U kunt elk type object in een variabele opslaan, met inbegrip van gehele getallen, teken reeksen, matrices en hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-150">You can store any type of object in a variable, including integers, strings, arrays, and hash tables.</span></span> <span data-ttu-id="75b9c-151">En, objecten die processen, services, gebeurtenis logboeken en computers vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-151">And, objects that represent processes, services, event logs, and computers.</span></span>

<span data-ttu-id="75b9c-152">Power shell-variabelen worden op een losse manier getypt, wat betekent dat ze niet zijn beperkt tot een bepaald type object.</span><span class="sxs-lookup"><span data-stu-id="75b9c-152">PowerShell variables are loosely typed, which means that they aren't limited to a particular type of object.</span></span> <span data-ttu-id="75b9c-153">Eén variabele kan zelfs een verzameling, of matrix, van verschillende typen objecten tegelijk bevatten.</span><span class="sxs-lookup"><span data-stu-id="75b9c-153">A single variable can even contain a collection, or array, of different types of objects at the same time.</span></span>

<span data-ttu-id="75b9c-154">Het gegevens type van een variabele wordt bepaald door de .NET-typen van de waarden van de variabele.</span><span class="sxs-lookup"><span data-stu-id="75b9c-154">The data type of a variable is determined by the .NET types of the values of the variable.</span></span> <span data-ttu-id="75b9c-155">Als u het object type van een variabele wilt weer geven, gebruikt u [Get-member](xref:Microsoft.PowerShell.Utility.Get-Member).</span><span class="sxs-lookup"><span data-stu-id="75b9c-155">To view a variable's object type, use [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member).</span></span>

<span data-ttu-id="75b9c-156">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="75b9c-156">For example:</span></span>

```powershell
$a = 12                         # System.Int32
$a = "Word"                     # System.String
$a = 12, "Word"                 # array of System.Int32, System.String
$a = Get-ChildItem C:\Windows   # FileInfo and DirectoryInfo types
```

<span data-ttu-id="75b9c-157">U kunt een type kenmerk en een cast-notatie gebruiken om ervoor te zorgen dat een variabele alleen specifieke object typen of objecten kan bevatten die kunnen worden geconverteerd naar dat type.</span><span class="sxs-lookup"><span data-stu-id="75b9c-157">You can use a type attribute and cast notation to ensure that a variable can contain only specific object types or objects that can be converted to that type.</span></span> <span data-ttu-id="75b9c-158">Als u een waarde van een ander type wilt toewijzen, probeert Power shell de waarde naar het type te converteren.</span><span class="sxs-lookup"><span data-stu-id="75b9c-158">If you try to assign a value of another type, PowerShell tries to convert the value to its type.</span></span> <span data-ttu-id="75b9c-159">Als het type niet kan worden geconverteerd, mislukt de toewijzings instructie.</span><span class="sxs-lookup"><span data-stu-id="75b9c-159">If the type can't be converted, the assignment statement fails.</span></span>

<span data-ttu-id="75b9c-160">Als u de cast-notatie wilt gebruiken, voert u een type naam tussen vier Kante haken in, vóór de naam van de variabele (aan de linkerkant van de toewijzings instructie).</span><span class="sxs-lookup"><span data-stu-id="75b9c-160">To use cast notation, enter a type name, enclosed in brackets, before the variable name (on the left side of the assignment statement).</span></span> <span data-ttu-id="75b9c-161">In het volgende voor beeld wordt een `$number` variabele gemaakt die alleen gehele getallen kan bevatten, een `$words` variabele die alleen teken reeksen kan bevatten en een `$dates` variabele die alleen **DateTime** -objecten kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="75b9c-161">The following example creates a `$number` variable that can contain only integers, a `$words` variable that can contain only strings, and a `$dates` variable that can contain only **DateTime** objects.</span></span>

```powershell
[int]$number = 8
$number = "12345"  # The string is converted to an integer.
$number = "Hello"
```

```Output
Cannot convert value "Hello" to type "System.Int32". Error: "Input string was
 not in a correct format."
At line:1 char:1
+ $number = "Hello"
+ ~~~~~~~~~~~~~~~~~
+ CategoryInfo          : MetadataError: (:) [],
    ArgumentTransformationMetadataException
+ FullyQualifiedErrorId : RuntimeException
```

```powershell
[string]$words = "Hello"
$words = 2       # The integer is converted to a string.
$words += 10     # The plus (+) sign concatenates the strings.
$words
```

```Output
210
```

```powershell
[datetime] $dates = "09/12/91"  # The string is converted to a DateTime object.
$dates
```

```Output
Thursday, September 12, 1991 00:00:00
```

```powershell
$dates = 10    # The integer is converted to a DateTime object.
$dates
```

```Output
Monday, January 1, 0001 00:00:00
```

## <a name="using-variables-in-commands-and-expressions"></a><span data-ttu-id="75b9c-162">Variabelen gebruiken in opdrachten en expressies</span><span class="sxs-lookup"><span data-stu-id="75b9c-162">Using variables in commands and expressions</span></span>

<span data-ttu-id="75b9c-163">Als u een variabele wilt gebruiken in een opdracht of expressie, typt u de naam van de variabele, voorafgegaan door het dollar `$` teken ().</span><span class="sxs-lookup"><span data-stu-id="75b9c-163">To use a variable in a command or expression, type the variable name, preceded by the dollar (`$`) sign.</span></span>

<span data-ttu-id="75b9c-164">Als de naam van de variabele en het dollar teken niet tussen aanhalings tekens staan, of als deze tussen dubbele aanhalings `"` tekens () zijn geplaatst, wordt de waarde van de variabele in de opdracht of expressie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="75b9c-164">If the variable name and dollar sign aren't enclosed in quotation marks, or if they're enclosed in double quotation (`"`) marks, the value of the variable is used in the command or expression.</span></span>

<span data-ttu-id="75b9c-165">Als de naam van de variabele en het dollar teken tussen enkele aanhalings `'` tekens () worden geplaatst, wordt de naam van de variabele in de expressie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="75b9c-165">If the variable name and dollar sign are enclosed in single quotation (`'`) marks, the variable name is used in the expression.</span></span>

<span data-ttu-id="75b9c-166">Zie [about_Quoting_Rules](about_Quoting_Rules.md)voor meer informatie over het gebruik van aanhalings tekens in Power shell.</span><span class="sxs-lookup"><span data-stu-id="75b9c-166">For more information about using quotation marks in PowerShell, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

<span data-ttu-id="75b9c-167">In dit voor beeld wordt de waarde van de `$PROFILE` variabele opgehaald, het pad naar het Power shell-gebruikers profiel bestand in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="75b9c-167">This example gets the value of the `$PROFILE` variable, which is the path to the PowerShell user profile file in the PowerShell console.</span></span>

```powershell
$PROFILE
```

```Output
C:\Users\User01\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
```

<span data-ttu-id="75b9c-168">In dit voor beeld worden twee opdrachten weer gegeven waarmee het Power shell-profiel in **notepad.exe** kan worden geopend.</span><span class="sxs-lookup"><span data-stu-id="75b9c-168">In this example, two commands are shown that can open the PowerShell profile in **notepad.exe**.</span></span> <span data-ttu-id="75b9c-169">Het voor beeld met dubbele aanhalings `"` tekens () maakt gebruik van de waarde van de variabele.</span><span class="sxs-lookup"><span data-stu-id="75b9c-169">The example with double-quote (`"`) marks uses the variable's value.</span></span>

```powershell
notepad $PROFILE

notepad "$PROFILE"
```

<span data-ttu-id="75b9c-170">In de volgende voor beelden worden enkele aanhalings `'` tekens () gebruikt die de variabele behandelen als letterlijke tekst.</span><span class="sxs-lookup"><span data-stu-id="75b9c-170">The following examples use single-quote (`'`) marks that treat the variable as literal text.</span></span>

```powershell
'$PROFILE'
```

```Output
$PROFILE
```

```powershell
'Use the $PROFILE variable.'
```

```Output
Use the $PROFILE variable.
```

## <a name="variable-names-that-include-special-characters"></a><span data-ttu-id="75b9c-171">Namen van variabelen die speciale tekens bevatten</span><span class="sxs-lookup"><span data-stu-id="75b9c-171">Variable names that include special characters</span></span>

<span data-ttu-id="75b9c-172">Namen van variabelen beginnen met een dollar ( `$` ) teken en kunnen alfanumerieke tekens en speciale tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="75b9c-172">Variable names begin with a dollar (`$`) sign and can include alphanumeric characters and special characters.</span></span> <span data-ttu-id="75b9c-173">De lengte van de variabele naam wordt alleen beperkt door het beschik bare geheugen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-173">The variable name length is limited only by available memory.</span></span>

<span data-ttu-id="75b9c-174">De best practice is dat namen van variabelen alleen alfanumerieke tekens en het onderstrepings `_` teken () bevatten.</span><span class="sxs-lookup"><span data-stu-id="75b9c-174">The best practice is that variable names include only alphanumeric characters and the underscore (`_`) character.</span></span> <span data-ttu-id="75b9c-175">Namen van variabelen die spaties en andere speciale tekens bevatten, zijn lastig te gebruiken en moeten worden vermeden.</span><span class="sxs-lookup"><span data-stu-id="75b9c-175">Variable names that include spaces and other special characters, are difficult to use and should be avoided.</span></span>

<span data-ttu-id="75b9c-176">Alfanumerieke namen van variabelen kunnen de volgende tekens bevatten:</span><span class="sxs-lookup"><span data-stu-id="75b9c-176">Alphanumeric variable names can contain these characters:</span></span>

- <span data-ttu-id="75b9c-177">Unicode-tekens uit deze categorieën: **Lu**, **ll**, **lt**, **LM**, **lo** of **ND**.</span><span class="sxs-lookup"><span data-stu-id="75b9c-177">Unicode characters from these categories: **Lu**, **Ll**, **Lt**, **Lm**, **Lo**, or **Nd**.</span></span>
- <span data-ttu-id="75b9c-178">Onderstrepings `_` teken ().</span><span class="sxs-lookup"><span data-stu-id="75b9c-178">Underscore (`_`) character.</span></span>
- <span data-ttu-id="75b9c-179">Vraag teken ( `?` )-teken.</span><span class="sxs-lookup"><span data-stu-id="75b9c-179">Question mark (`?`) character.</span></span>

<span data-ttu-id="75b9c-180">De volgende lijst bevat de beschrijvingen van de Unicode-categorie.</span><span class="sxs-lookup"><span data-stu-id="75b9c-180">The following list contains the Unicode category descriptions.</span></span> <span data-ttu-id="75b9c-181">Zie [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="75b9c-181">For more information, see [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory).</span></span>

- <span data-ttu-id="75b9c-182">**Lu** -UppercaseLetter</span><span class="sxs-lookup"><span data-stu-id="75b9c-182">**Lu** - UppercaseLetter</span></span>
- <span data-ttu-id="75b9c-183">**Ll** -LowercaseLetter</span><span class="sxs-lookup"><span data-stu-id="75b9c-183">**Ll** - LowercaseLetter</span></span>
- <span data-ttu-id="75b9c-184">**Lt** -TitlecaseLetter</span><span class="sxs-lookup"><span data-stu-id="75b9c-184">**Lt** - TitlecaseLetter</span></span>
- <span data-ttu-id="75b9c-185">**LM** -ModifierLetter</span><span class="sxs-lookup"><span data-stu-id="75b9c-185">**Lm** - ModifierLetter</span></span>
- <span data-ttu-id="75b9c-186">**Lo** -OtherLetter</span><span class="sxs-lookup"><span data-stu-id="75b9c-186">**Lo** - OtherLetter</span></span>
- <span data-ttu-id="75b9c-187">**ND** -DecimalDigitNumber</span><span class="sxs-lookup"><span data-stu-id="75b9c-187">**Nd** - DecimalDigitNumber</span></span>

<span data-ttu-id="75b9c-188">Als u een naam van een variabele wilt maken of weer geven die spaties of speciale tekens bevat, moet u de naam van de variabele tussen accolades ( `{}` ) plaatsen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-188">To create or display a variable name that includes spaces or special characters, enclose the variable name with the curly braces (`{}`) characters.</span></span>
<span data-ttu-id="75b9c-189">De accolades direct Power shell om de tekens van de naam van de variabele te interpreteren als letterlijke waarden.</span><span class="sxs-lookup"><span data-stu-id="75b9c-189">The curly braces direct PowerShell to interpret the variable name's characters as literals.</span></span>

<span data-ttu-id="75b9c-190">Namen van speciale teken variabelen kunnen de volgende tekens bevatten:</span><span class="sxs-lookup"><span data-stu-id="75b9c-190">Special character variable names can contain these characters:</span></span>

- <span data-ttu-id="75b9c-191">Elk Unicode-teken, met de volgende uitzonde ringen:</span><span class="sxs-lookup"><span data-stu-id="75b9c-191">Any Unicode character, with the following exceptions:</span></span>
  - <span data-ttu-id="75b9c-192">Het accolade `}` teken () sluiten (U + 007D).</span><span class="sxs-lookup"><span data-stu-id="75b9c-192">The closing curly brace (`}`) character (U+007D).</span></span>
  - <span data-ttu-id="75b9c-193">Het apostroffen ( `` ` `` )-teken (U + 0060).</span><span class="sxs-lookup"><span data-stu-id="75b9c-193">The backtick (`` ` ``) character (U+0060).</span></span> <span data-ttu-id="75b9c-194">De apostroffen wordt gebruikt om Unicode-tekens te escapen zodat ze als letterlijke waarden worden behandeld.</span><span class="sxs-lookup"><span data-stu-id="75b9c-194">The backtick is used to escape Unicode characters so they're treated as literals.</span></span>

<span data-ttu-id="75b9c-195">Power Shell heeft gereserveerde variabelen `$$` , zoals,, `$?` `$^` en `$_` die alfanumerieke en speciale tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="75b9c-195">PowerShell has reserved variables such as `$$`, `$?`, `$^`, and `$_` that contain alphanumeric and special characters.</span></span> <span data-ttu-id="75b9c-196">Zie [about_Automatic_Variables](about_automatic_variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="75b9c-196">For more information, see [about_Automatic_Variables](about_automatic_variables.md).</span></span>

<span data-ttu-id="75b9c-197">Met de volgende opdracht wordt bijvoorbeeld de variabele met de naam gemaakt `save-items` .</span><span class="sxs-lookup"><span data-stu-id="75b9c-197">For example, the following command creates the variable named `save-items`.</span></span> <span data-ttu-id="75b9c-198">De accolades ( `{}` ) zijn nodig omdat de naam van de variabele een afbreek streepje () met een `-` speciaal teken bevat.</span><span class="sxs-lookup"><span data-stu-id="75b9c-198">The curly braces (`{}`) are needed because variable name includes a hyphen (`-`) special character.</span></span>

```powershell
${save-items} = "a", "b", "c"
${save-items}
```

```Output
a
b
c
```

<span data-ttu-id="75b9c-199">Met de volgende opdracht worden de onderliggende items in de map opgehaald die wordt vertegenwoordigd door de `ProgramFiles(x86)` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="75b9c-199">The following command gets the child items in the directory that is represented by the `ProgramFiles(x86)` environment variable.</span></span>

```powershell
Get-ChildItem ${env:ProgramFiles(x86)}
```

<span data-ttu-id="75b9c-200">Als u wilt verwijzen naar een naam van een variabele die accolades bevat, plaatst u de naam van de variabele tussen accolades en gebruikt u het apostroffen-teken om de accolades te escapen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-200">To reference a variable name that includes braces, enclose the variable name in braces, and use the backtick character to escape the braces.</span></span> <span data-ttu-id="75b9c-201">Als u bijvoorbeeld een variabele met de naam `this{value}is` type wilt maken:</span><span class="sxs-lookup"><span data-stu-id="75b9c-201">For example, to create a variable named `this{value}is` type:</span></span>

```powershell
${this`{value`}is} = "This variable name uses braces and backticks."
${this`{value`}is}
```

```Output
This variable name uses braces and backticks.
```

## <a name="variables-and-scope"></a><span data-ttu-id="75b9c-202">Variabelen en bereik</span><span class="sxs-lookup"><span data-stu-id="75b9c-202">Variables and scope</span></span>

<span data-ttu-id="75b9c-203">Variabelen zijn standaard alleen beschikbaar in het bereik waarin ze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="75b9c-203">By default, variables are only available in the scope in which they're created.</span></span>

<span data-ttu-id="75b9c-204">Een variabele die u in een functie hebt gemaakt, is bijvoorbeeld alleen beschikbaar in de functie.</span><span class="sxs-lookup"><span data-stu-id="75b9c-204">For example, a variable that you create in a function is available only within the function.</span></span> <span data-ttu-id="75b9c-205">Een variabele die u in een script maakt, is alleen beschikbaar in het script.</span><span class="sxs-lookup"><span data-stu-id="75b9c-205">A variable that you create in a script is available only within the script.</span></span> <span data-ttu-id="75b9c-206">Als u het script met de punt-bron, wordt de variabele toegevoegd aan het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="75b9c-206">If you dot-source the script, the variable is added to the current scope.</span></span> <span data-ttu-id="75b9c-207">Zie [about_Scopes](about_Scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="75b9c-207">For more information, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="75b9c-208">U kunt een bereik wijzigings functie gebruiken om het standaard bereik van de variabele te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-208">You can use a scope modifier to change the default scope of the variable.</span></span> <span data-ttu-id="75b9c-209">Met de volgende expressie maakt u een variabele met de naam `Computers` .</span><span class="sxs-lookup"><span data-stu-id="75b9c-209">The following expression creates a variable named `Computers`.</span></span> <span data-ttu-id="75b9c-210">De variabele heeft een globaal bereik, zelfs wanneer deze in een script of functie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="75b9c-210">The variable has a global scope, even when it's created in a script or function.</span></span>

```powershell
$Global:Computers = "Server01"
```

<span data-ttu-id="75b9c-211">Voor elk script of elke opdracht die uit de sessie wordt uitgevoerd, hebt u de `Using` bereik wijzigings functie nodig om variabele waarden van het aanroepende sessie bereik in te sluiten, zodat out of Session-code er toegang toe heeft.</span><span class="sxs-lookup"><span data-stu-id="75b9c-211">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span>

<span data-ttu-id="75b9c-212">Zie [about_Remote_Variables](about_Remote_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="75b9c-212">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="saving-variables"></a><span data-ttu-id="75b9c-213">Variabelen opslaan</span><span class="sxs-lookup"><span data-stu-id="75b9c-213">Saving variables</span></span>

<span data-ttu-id="75b9c-214">Variabelen die u maakt, zijn alleen beschikbaar in de sessie waarin u ze maakt.</span><span class="sxs-lookup"><span data-stu-id="75b9c-214">Variables that you create are available only in the session in which you create them.</span></span> <span data-ttu-id="75b9c-215">Ze gaan verloren wanneer u uw sessie sluit.</span><span class="sxs-lookup"><span data-stu-id="75b9c-215">They're lost when you close your session.</span></span>

<span data-ttu-id="75b9c-216">Als u de variabele wilt maken in elke Power shell-sessie die u start, voegt u de variabele toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="75b9c-216">To create the variable in every PowerShell session that you start, add the variable to your PowerShell profile.</span></span>

<span data-ttu-id="75b9c-217">Als u bijvoorbeeld de waarde van de `$VerbosePreference` variabele in elke Power shell-sessie wilt wijzigen, voegt u de volgende opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="75b9c-217">For example, to change the value of the `$VerbosePreference` variable in every PowerShell session, add the following command to your PowerShell profile.</span></span>

```powershell
$VerbosePreference = "Continue"
```

<span data-ttu-id="75b9c-218">U kunt deze opdracht toevoegen aan uw Power shell-profiel door het bestand te openen `$PROFILE` in een tekst editor, zoals **notepad.exe**.</span><span class="sxs-lookup"><span data-stu-id="75b9c-218">You can add this command to your PowerShell profile by opening the `$PROFILE` file in a text editor, such as **notepad.exe**.</span></span> <span data-ttu-id="75b9c-219">Zie [about_Profiles](about_Profiles.md)voor meer informatie over Power shell-profielen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-219">For more information about PowerShell profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="the-variable-drive"></a><span data-ttu-id="75b9c-220">De variabele: station</span><span class="sxs-lookup"><span data-stu-id="75b9c-220">The Variable: drive</span></span>

<span data-ttu-id="75b9c-221">De provider van de Power shell-variabele maakt een `Variable:` station dat eruitziet en fungeert als een bestandssysteem station, maar bevat de variabelen in uw sessie en hun waarden.</span><span class="sxs-lookup"><span data-stu-id="75b9c-221">The PowerShell Variable provider creates a `Variable:` drive that looks and acts like a file system drive, but it contains the variables in your session and their values.</span></span>

<span data-ttu-id="75b9c-222">Als u het station wilt wijzigen `Variable:` , gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="75b9c-222">To change to the `Variable:` drive, use the following command:</span></span>

```powershell
Set-Location Variable:
```

<span data-ttu-id="75b9c-223">`Variable:`Gebruik de `Get-Item` cmdlets of om de items en variabelen in het station weer te geven `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="75b9c-223">To list the items and variables in the `Variable:` drive, use the `Get-Item` or `Get-ChildItem` cmdlets.</span></span>

```powershell
Get-ChildItem Variable:
```

<span data-ttu-id="75b9c-224">Als u de waarde van een bepaalde variabele wilt ophalen, gebruikt u de notatie File System om de naam van het station en de naam van de variabele op te geven.</span><span class="sxs-lookup"><span data-stu-id="75b9c-224">To get the value of a particular variable, use file system notation to specify the name of the drive and the name of the variable.</span></span> <span data-ttu-id="75b9c-225">`$PSCulture`Gebruik bijvoorbeeld de volgende opdracht om de automatische variabele op te halen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-225">For example, to get the `$PSCulture` automatic variable, use the following command.</span></span>

```powershell
Get-Item Variable:\PSCulture
```

```Output
Name                           Value
----                           -----
PSCulture                      en-US
```

<span data-ttu-id="75b9c-226">Als u meer informatie over het `Variable:` station en de Power shell-variabele provider wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="75b9c-226">To display more information about the `Variable:` drive and the PowerShell Variable provider, type:</span></span>

```powershell
Get-Help Variable
```

## <a name="variable-syntax-with-provider-paths"></a><span data-ttu-id="75b9c-227">Variabele syntaxis met provider paden</span><span class="sxs-lookup"><span data-stu-id="75b9c-227">Variable syntax with provider paths</span></span>

<span data-ttu-id="75b9c-228">U kunt een pad naar een provider voor voegsel met het dollar ( `$` )-teken en toegang krijgen tot de inhoud van elke provider die de [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) -interface implementeert.</span><span class="sxs-lookup"><span data-stu-id="75b9c-228">You can prefix a provider path with the dollar (`$`) sign, and access the content of any provider that implements the [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span></span>

<span data-ttu-id="75b9c-229">De volgende ingebouwde Power shell-providers ondersteunen deze notatie:</span><span class="sxs-lookup"><span data-stu-id="75b9c-229">The following built-in PowerShell providers support this notation:</span></span>

- [<span data-ttu-id="75b9c-230">about_Environment_Provider</span><span class="sxs-lookup"><span data-stu-id="75b9c-230">about_Environment_Provider</span></span>](about_Environment_Provider.md)
- [<span data-ttu-id="75b9c-231">about_Variable_Provider</span><span class="sxs-lookup"><span data-stu-id="75b9c-231">about_Variable_Provider</span></span>](about_Variable_Provider.md)
- [<span data-ttu-id="75b9c-232">about_Function_Provider</span><span class="sxs-lookup"><span data-stu-id="75b9c-232">about_Function_Provider</span></span>](about_Function_Provider.md)
- [<span data-ttu-id="75b9c-233">about_Alias_Provider</span><span class="sxs-lookup"><span data-stu-id="75b9c-233">about_Alias_Provider</span></span>](about_Alias_Provider.md)

## <a name="the-variable-cmdlets"></a><span data-ttu-id="75b9c-234">De variabele-cmdlets</span><span class="sxs-lookup"><span data-stu-id="75b9c-234">The variable cmdlets</span></span>

<span data-ttu-id="75b9c-235">Power shell bevat een set cmdlets die zijn ontworpen voor het beheren van variabelen.</span><span class="sxs-lookup"><span data-stu-id="75b9c-235">PowerShell includes a set of cmdlets that are designed to manage variables.</span></span>

<span data-ttu-id="75b9c-236">Als u de cmdlets wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="75b9c-236">To list the cmdlets, type:</span></span>

```powershell
Get-Command -Noun Variable
```

<span data-ttu-id="75b9c-237">Als u hulp wilt krijgen voor een specifieke cmdlet, typt u:</span><span class="sxs-lookup"><span data-stu-id="75b9c-237">To get help for a specific cmdlet, type:</span></span>

```powershell
Get-Help <cmdlet-name>
```

| <span data-ttu-id="75b9c-238">Naam van cmdlet</span><span class="sxs-lookup"><span data-stu-id="75b9c-238">Cmdlet Name</span></span>       | <span data-ttu-id="75b9c-239">Description</span><span class="sxs-lookup"><span data-stu-id="75b9c-239">Description</span></span>                                |
| ---------------   | ------------------------------------------ |
| `Clear-Variable`  | <span data-ttu-id="75b9c-240">Hiermee verwijdert u de waarde van een variabele.</span><span class="sxs-lookup"><span data-stu-id="75b9c-240">Deletes the value of a variable.</span></span>           |
| `Get-Variable`    | <span data-ttu-id="75b9c-241">Hiermee worden de variabelen in de huidige console opgehaald.</span><span class="sxs-lookup"><span data-stu-id="75b9c-241">Gets the variables in the current console.</span></span> |
| `New-Variable`    | <span data-ttu-id="75b9c-242">Hiermee maakt u een nieuwe variabele.</span><span class="sxs-lookup"><span data-stu-id="75b9c-242">Creates a new variable.</span></span>                    |
| `Remove-Variable` | <span data-ttu-id="75b9c-243">Hiermee verwijdert u een variabele en de bijbehorende waarde.</span><span class="sxs-lookup"><span data-stu-id="75b9c-243">Deletes a variable and its value.</span></span>          |
| `Set-Variable`    | <span data-ttu-id="75b9c-244">Wijzigt de waarde van een variabele.</span><span class="sxs-lookup"><span data-stu-id="75b9c-244">Changes the value of a variable.</span></span>           |

## <a name="see-also"></a><span data-ttu-id="75b9c-245">Zie ook</span><span class="sxs-lookup"><span data-stu-id="75b9c-245">See also</span></span>

[<span data-ttu-id="75b9c-246">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="75b9c-246">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="75b9c-247">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="75b9c-247">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="75b9c-248">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="75b9c-248">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="75b9c-249">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="75b9c-249">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="75b9c-250">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="75b9c-250">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="75b9c-251">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="75b9c-251">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="75b9c-252">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="75b9c-252">about_Remote_Variables</span></span>](about_Remote_Variables.md)
