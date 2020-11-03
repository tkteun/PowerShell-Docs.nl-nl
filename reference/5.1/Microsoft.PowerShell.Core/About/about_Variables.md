---
description: Hierin wordt beschreven hoe variabelen waarden opslaan die kunnen worden gebruikt in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variables?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Variables
ms.openlocfilehash: 59a611cf49635f0391d3f3cc18bcf6d06a688638
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252733"
---
# <a name="about-variables"></a><span data-ttu-id="affcd-104">Over variabelen</span><span class="sxs-lookup"><span data-stu-id="affcd-104">About Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="affcd-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="affcd-105">Short description</span></span>

<span data-ttu-id="affcd-106">Hierin wordt beschreven hoe variabelen waarden opslaan die kunnen worden gebruikt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="affcd-106">Describes how variables store values that can be used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="affcd-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="affcd-107">Long description</span></span>

<span data-ttu-id="affcd-108">U kunt alle typen waarden opslaan in Power shell-variabelen.</span><span class="sxs-lookup"><span data-stu-id="affcd-108">You can store all types of values in PowerShell variables.</span></span> <span data-ttu-id="affcd-109">U kunt bijvoorbeeld de resultaten van opdrachten opslaan en elementen opslaan die in opdrachten en expressies worden gebruikt, zoals namen, paden, instellingen en waarden.</span><span class="sxs-lookup"><span data-stu-id="affcd-109">For example, store the results of commands, and store elements that are used in commands and expressions, such as names, paths, settings, and values.</span></span>

<span data-ttu-id="affcd-110">Een variabele is een geheugen eenheid waarin waarden worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="affcd-110">A variable is a unit of memory in which values are stored.</span></span> <span data-ttu-id="affcd-111">In Power shell worden variabelen vertegenwoordigd door teken reeksen die beginnen met een dollar teken ( `$` ), zoals `$a` , `$process` of `$my_var` .</span><span class="sxs-lookup"><span data-stu-id="affcd-111">In PowerShell, variables are represented by text strings that begin with a dollar sign (`$`), such as `$a`, `$process`, or `$my_var`.</span></span>

<span data-ttu-id="affcd-112">Namen van variabelen zijn niet hoofdletter gevoelig en kunnen spaties en speciale tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="affcd-112">Variable names aren't case-sensitive, and can include spaces and special characters.</span></span> <span data-ttu-id="affcd-113">Namen van variabelen met speciale tekens en spaties zijn echter lastig te gebruiken en moeten worden vermeden.</span><span class="sxs-lookup"><span data-stu-id="affcd-113">But, variable names that include special characters and spaces are difficult to use and should be avoided.</span></span> <span data-ttu-id="affcd-114">Zie [namen van variabelen die speciale tekens bevatten](#variable-names-that-include-special-characters)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="affcd-114">For more information, see [Variable names that include special characters](#variable-names-that-include-special-characters).</span></span>

<span data-ttu-id="affcd-115">Er zijn verschillende typen variabelen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="affcd-115">There are several different types of variables in PowerShell.</span></span>

- <span data-ttu-id="affcd-116">Door gebruiker gemaakte variabelen: door de gebruiker gemaakte variabelen worden gemaakt en onderhouden door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="affcd-116">User-created variables: User-created variables are created and maintained by the user.</span></span> <span data-ttu-id="affcd-117">De variabelen die u in de Power shell-opdracht regel maakt, bestaan standaard alleen wanneer het Power shell-venster is geopend.</span><span class="sxs-lookup"><span data-stu-id="affcd-117">By default, the variables that you create at the PowerShell command line exist only while the PowerShell window is open.</span></span> <span data-ttu-id="affcd-118">Wanneer het Power shell-venster wordt gesloten, worden de variabelen verwijderd.</span><span class="sxs-lookup"><span data-stu-id="affcd-118">When the PowerShell windows is closed, the variables are deleted.</span></span> <span data-ttu-id="affcd-119">Als u een variabele wilt opslaan, voegt u deze toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="affcd-119">To save a variable, add it to your PowerShell profile.</span></span> <span data-ttu-id="affcd-120">U kunt ook variabelen maken in scripts met globaal, script of lokaal bereik.</span><span class="sxs-lookup"><span data-stu-id="affcd-120">You can also create variables in scripts with global, script, or local scope.</span></span>

- <span data-ttu-id="affcd-121">Automatische variabelen: automatische variabelen slaan de status van Power shell op.</span><span class="sxs-lookup"><span data-stu-id="affcd-121">Automatic variables: Automatic variables store the state of PowerShell.</span></span> <span data-ttu-id="affcd-122">Deze variabelen worden gemaakt door Power shell en Power shell wijzigt hun waarden naar behoefte om hun nauw keurigheid te behouden.</span><span class="sxs-lookup"><span data-stu-id="affcd-122">These variables are created by PowerShell, and PowerShell changes their values as required to maintain their accuracy.</span></span> <span data-ttu-id="affcd-123">Gebruikers kunnen de waarde van deze variabelen niet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="affcd-123">Users can't change the value of these variables.</span></span> <span data-ttu-id="affcd-124">De `$PSHOME` variabele slaat bijvoorbeeld het pad op naar de installatie directory van Power shell.</span><span class="sxs-lookup"><span data-stu-id="affcd-124">For example, the `$PSHOME` variable stores the path to the PowerShell installation directory.</span></span>

  <span data-ttu-id="affcd-125">Zie [about_Automatic_Variables](about_Automatic_Variables.md)voor meer informatie, een lijst en een beschrijving van de automatische variabelen.</span><span class="sxs-lookup"><span data-stu-id="affcd-125">For more information, a list, and a description of the automatic variables, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

- <span data-ttu-id="affcd-126">Voorkeurs variabelen: voorkeurs variabelen slaan gebruikers voorkeuren op voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="affcd-126">Preference variables: Preference variables store user preferences for PowerShell.</span></span> <span data-ttu-id="affcd-127">Deze variabelen worden gemaakt door Power shell en worden gevuld met standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="affcd-127">These variables are created by PowerShell and are populated with default values.</span></span> <span data-ttu-id="affcd-128">Gebruikers kunnen de waarden van deze variabelen wijzigen.</span><span class="sxs-lookup"><span data-stu-id="affcd-128">Users can change the values of these variables.</span></span> <span data-ttu-id="affcd-129">De `$MaximumHistoryCount` variabele bepaalt bijvoorbeeld het maximum aantal vermeldingen in de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="affcd-129">For example, the `$MaximumHistoryCount` variable determines the maximum number of entries in the session history.</span></span>

  <span data-ttu-id="affcd-130">Zie [about_Preference_Variables](about_Preference_Variables.md)voor meer informatie, een lijst en een beschrijving van de voorkeurs variabelen.</span><span class="sxs-lookup"><span data-stu-id="affcd-130">For more information, a list, and a description of the preference variables, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

## <a name="working-with-variables"></a><span data-ttu-id="affcd-131">Werken met variabelen</span><span class="sxs-lookup"><span data-stu-id="affcd-131">Working with variables</span></span>

<span data-ttu-id="affcd-132">Als u een nieuwe variabele wilt maken, gebruikt u een toewijzings instructie om een waarde toe te wijzen aan de variabele.</span><span class="sxs-lookup"><span data-stu-id="affcd-132">To create a new variable, use an assignment statement to assign a value to the variable.</span></span> <span data-ttu-id="affcd-133">U hoeft de variabele niet te declareren voordat u deze gebruikt.</span><span class="sxs-lookup"><span data-stu-id="affcd-133">You don't have to declare the variable before using it.</span></span> <span data-ttu-id="affcd-134">De standaard waarde van alle variabelen is `$null` .</span><span class="sxs-lookup"><span data-stu-id="affcd-134">The default value of all variables is `$null`.</span></span>

<span data-ttu-id="affcd-135">Als u een lijst wilt weer geven met alle variabelen in uw Power shell-sessie, typt u `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="affcd-135">To get a list of all the variables in your PowerShell session, type `Get-Variable`.</span></span> <span data-ttu-id="affcd-136">De namen van variabelen worden weer gegeven zonder het voor gaande dollar `$` teken () dat wordt gebruikt om te verwijzen naar variabelen.</span><span class="sxs-lookup"><span data-stu-id="affcd-136">The variable names are displayed without the preceding dollar (`$`) sign that is used to reference variables.</span></span>

<span data-ttu-id="affcd-137">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="affcd-137">For example:</span></span>

```powershell
$MyVariable = 1, 2, 3

$Path = "C:\Windows\System32"
```

<span data-ttu-id="affcd-138">Variabelen zijn handig om de resultaten van opdrachten op te slaan.</span><span class="sxs-lookup"><span data-stu-id="affcd-138">Variables are useful for storing the results of commands.</span></span>

<span data-ttu-id="affcd-139">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="affcd-139">For example:</span></span>

```powershell
$Processes = Get-Process

$Today = (Get-Date).DateTime
```

<span data-ttu-id="affcd-140">Als u de waarde van een variabele wilt weer geven, typt u de naam van de variabele, voorafgegaan door een dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="affcd-140">To display the value of a variable, type the variable name, preceded by a dollar sign (`$`).</span></span>

<span data-ttu-id="affcd-141">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="affcd-141">For example:</span></span>

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

<span data-ttu-id="affcd-142">Als u de waarde van een variabele wilt wijzigen, wijst u een nieuwe waarde toe aan de variabele.</span><span class="sxs-lookup"><span data-stu-id="affcd-142">To change the value of a variable, assign a new value to the variable.</span></span>

<span data-ttu-id="affcd-143">In de volgende voor beelden wordt de waarde van de variabele weer gegeven `$MyVariable` , wordt de waarde van de variabele gewijzigd, waarna de nieuwe waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="affcd-143">The following examples display the value of the `$MyVariable` variable, changes the value of the variable, and then displays the new value.</span></span>

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

<span data-ttu-id="affcd-144">Als u de waarde van een variabele wilt verwijderen, gebruikt u de `Clear-Variable` cmdlet of wijzigt u de waarde in `$null` .</span><span class="sxs-lookup"><span data-stu-id="affcd-144">To delete the value of a variable, use the `Clear-Variable` cmdlet or change the value to `$null`.</span></span>

```powershell
Clear-Variable -Name MyVariable
```

```powershell
$MyVariable = $null
```

<span data-ttu-id="affcd-145">Als u de variabele wilt verwijderen, gebruikt u [Remove-variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) of [Remove-item](xref:Microsoft.PowerShell.Management.Remove-Item).</span><span class="sxs-lookup"><span data-stu-id="affcd-145">To delete the variable, use [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) or [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item).</span></span>

```powershell
Remove-Variable -Name MyVariable
```

```powershell
Remove-Item -Path Variable:\MyVariable
```

## <a name="types-of-variables"></a><span data-ttu-id="affcd-146">Typen variabelen</span><span class="sxs-lookup"><span data-stu-id="affcd-146">Types of variables</span></span>

<span data-ttu-id="affcd-147">U kunt elk type object in een variabele opslaan, met inbegrip van gehele getallen, teken reeksen, matrices en hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="affcd-147">You can store any type of object in a variable, including integers, strings, arrays, and hash tables.</span></span> <span data-ttu-id="affcd-148">En, objecten die processen, services, gebeurtenis logboeken en computers vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="affcd-148">And, objects that represent processes, services, event logs, and computers.</span></span>

<span data-ttu-id="affcd-149">Power shell-variabelen worden op een losse manier getypt, wat betekent dat ze niet zijn beperkt tot een bepaald type object.</span><span class="sxs-lookup"><span data-stu-id="affcd-149">PowerShell variables are loosely typed, which means that they aren't limited to a particular type of object.</span></span> <span data-ttu-id="affcd-150">Eén variabele kan zelfs een verzameling, of matrix, van verschillende typen objecten tegelijk bevatten.</span><span class="sxs-lookup"><span data-stu-id="affcd-150">A single variable can even contain a collection, or array, of different types of objects at the same time.</span></span>

<span data-ttu-id="affcd-151">Het gegevens type van een variabele wordt bepaald door de .NET-typen van de waarden van de variabele.</span><span class="sxs-lookup"><span data-stu-id="affcd-151">The data type of a variable is determined by the .NET types of the values of the variable.</span></span> <span data-ttu-id="affcd-152">Als u het object type van een variabele wilt weer geven, gebruikt u [Get-member](xref:Microsoft.PowerShell.Utility.Get-Member).</span><span class="sxs-lookup"><span data-stu-id="affcd-152">To view a variable's object type, use [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member).</span></span>

<span data-ttu-id="affcd-153">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="affcd-153">For example:</span></span>

```powershell
$a = 12                         # System.Int32
$a = "Word"                     # System.String
$a = 12, "Word"                 # array of System.Int32, System.String
$a = Get-ChildItem C:\Windows   # FileInfo and DirectoryInfo types
```

<span data-ttu-id="affcd-154">U kunt een type kenmerk en een cast-notatie gebruiken om ervoor te zorgen dat een variabele alleen specifieke object typen of objecten kan bevatten die kunnen worden geconverteerd naar dat type.</span><span class="sxs-lookup"><span data-stu-id="affcd-154">You can use a type attribute and cast notation to ensure that a variable can contain only specific object types or objects that can be converted to that type.</span></span> <span data-ttu-id="affcd-155">Als u een waarde van een ander type wilt toewijzen, probeert Power shell de waarde naar het type te converteren.</span><span class="sxs-lookup"><span data-stu-id="affcd-155">If you try to assign a value of another type, PowerShell tries to convert the value to its type.</span></span> <span data-ttu-id="affcd-156">Als het type niet kan worden geconverteerd, mislukt de toewijzings instructie.</span><span class="sxs-lookup"><span data-stu-id="affcd-156">If the type can't be converted, the assignment statement fails.</span></span>

<span data-ttu-id="affcd-157">Als u de cast-notatie wilt gebruiken, voert u een type naam tussen vier Kante haken in, vóór de naam van de variabele (aan de linkerkant van de toewijzings instructie).</span><span class="sxs-lookup"><span data-stu-id="affcd-157">To use cast notation, enter a type name, enclosed in brackets, before the variable name (on the left side of the assignment statement).</span></span> <span data-ttu-id="affcd-158">In het volgende voor beeld wordt een `$number` variabele gemaakt die alleen gehele getallen kan bevatten, een `$words` variabele die alleen teken reeksen kan bevatten en een `$dates` variabele die alleen **DateTime** -objecten kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="affcd-158">The following example creates a `$number` variable that can contain only integers, a `$words` variable that can contain only strings, and a `$dates` variable that can contain only **DateTime** objects.</span></span>

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

## <a name="using-variables-in-commands-and-expressions"></a><span data-ttu-id="affcd-159">Variabelen gebruiken in opdrachten en expressies</span><span class="sxs-lookup"><span data-stu-id="affcd-159">Using variables in commands and expressions</span></span>

<span data-ttu-id="affcd-160">Als u een variabele wilt gebruiken in een opdracht of expressie, typt u de naam van de variabele, voorafgegaan door het dollar `$` teken ().</span><span class="sxs-lookup"><span data-stu-id="affcd-160">To use a variable in a command or expression, type the variable name, preceded by the dollar (`$`) sign.</span></span>

<span data-ttu-id="affcd-161">Als de naam van de variabele en het dollar teken niet tussen aanhalings tekens staan, of als deze tussen dubbele aanhalings `"` tekens () zijn geplaatst, wordt de waarde van de variabele in de opdracht of expressie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="affcd-161">If the variable name and dollar sign aren't enclosed in quotation marks, or if they're enclosed in double quotation (`"`) marks, the value of the variable is used in the command or expression.</span></span>

<span data-ttu-id="affcd-162">Als de naam van de variabele en het dollar teken tussen enkele aanhalings `'` tekens () worden geplaatst, wordt de naam van de variabele in de expressie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="affcd-162">If the variable name and dollar sign are enclosed in single quotation (`'`) marks, the variable name is used in the expression.</span></span>

<span data-ttu-id="affcd-163">Zie [about_Quoting_Rules](about_Quoting_Rules.md)voor meer informatie over het gebruik van aanhalings tekens in Power shell.</span><span class="sxs-lookup"><span data-stu-id="affcd-163">For more information about using quotation marks in PowerShell, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

<span data-ttu-id="affcd-164">In dit voor beeld wordt de waarde van de `$PROFILE` variabele opgehaald, het pad naar het Power shell-gebruikers profiel bestand in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="affcd-164">This example gets the value of the `$PROFILE` variable, which is the path to the PowerShell user profile file in the PowerShell console.</span></span>

```powershell
$PROFILE
```

```Output
C:\Users\User01\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
```

<span data-ttu-id="affcd-165">In dit voor beeld worden twee opdrachten weer gegeven waarmee het Power shell-profiel in **notepad.exe** kan worden geopend.</span><span class="sxs-lookup"><span data-stu-id="affcd-165">In this example, two commands are shown that can open the PowerShell profile in **notepad.exe**.</span></span> <span data-ttu-id="affcd-166">Het voor beeld met dubbele aanhalings `"` tekens () maakt gebruik van de waarde van de variabele.</span><span class="sxs-lookup"><span data-stu-id="affcd-166">The example with double-quote (`"`) marks uses the variable's value.</span></span>

```powershell
notepad $PROFILE

notepad "$PROFILE"
```

<span data-ttu-id="affcd-167">In de volgende voor beelden worden enkele aanhalings `'` tekens () gebruikt die de variabele behandelen als letterlijke tekst.</span><span class="sxs-lookup"><span data-stu-id="affcd-167">The following examples use single-quote (`'`) marks that treat the variable as literal text.</span></span>

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

## <a name="variable-names-that-include-special-characters"></a><span data-ttu-id="affcd-168">Namen van variabelen die speciale tekens bevatten</span><span class="sxs-lookup"><span data-stu-id="affcd-168">Variable names that include special characters</span></span>

<span data-ttu-id="affcd-169">Namen van variabelen beginnen met een dollar ( `$` ) teken en kunnen alfanumerieke tekens en speciale tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="affcd-169">Variable names begin with a dollar (`$`) sign and can include alphanumeric characters and special characters.</span></span> <span data-ttu-id="affcd-170">De lengte van de variabele naam wordt alleen beperkt door het beschik bare geheugen.</span><span class="sxs-lookup"><span data-stu-id="affcd-170">The variable name length is limited only by available memory.</span></span>

<span data-ttu-id="affcd-171">De best practice is dat namen van variabelen alleen alfanumerieke tekens en het onderstrepings `_` teken () bevatten.</span><span class="sxs-lookup"><span data-stu-id="affcd-171">The best practice is that variable names include only alphanumeric characters and the underscore (`_`) character.</span></span> <span data-ttu-id="affcd-172">Namen van variabelen die spaties en andere speciale tekens bevatten, zijn lastig te gebruiken en moeten worden vermeden.</span><span class="sxs-lookup"><span data-stu-id="affcd-172">Variable names that include spaces and other special characters, are difficult to use and should be avoided.</span></span>

<span data-ttu-id="affcd-173">Alfanumerieke namen van variabelen kunnen de volgende tekens bevatten:</span><span class="sxs-lookup"><span data-stu-id="affcd-173">Alphanumeric variable names can contain these characters:</span></span>

- <span data-ttu-id="affcd-174">Unicode-tekens uit deze categorieën: **Lu** , **ll** , **lt** , **LM** , **lo** of **ND**.</span><span class="sxs-lookup"><span data-stu-id="affcd-174">Unicode characters from these categories: **Lu** , **Ll** , **Lt** , **Lm** , **Lo** , or **Nd**.</span></span>
- <span data-ttu-id="affcd-175">Onderstrepings `_` teken ().</span><span class="sxs-lookup"><span data-stu-id="affcd-175">Underscore (`_`) character.</span></span>
- <span data-ttu-id="affcd-176">Vraag teken ( `?` )-teken.</span><span class="sxs-lookup"><span data-stu-id="affcd-176">Question mark (`?`) character.</span></span>

<span data-ttu-id="affcd-177">De volgende lijst bevat de beschrijvingen van de Unicode-categorie.</span><span class="sxs-lookup"><span data-stu-id="affcd-177">The following list contains the Unicode category descriptions.</span></span> <span data-ttu-id="affcd-178">Zie [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="affcd-178">For more information, see [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory).</span></span>

- <span data-ttu-id="affcd-179">**Lu** -UppercaseLetter</span><span class="sxs-lookup"><span data-stu-id="affcd-179">**Lu** - UppercaseLetter</span></span>
- <span data-ttu-id="affcd-180">**Ll** -LowercaseLetter</span><span class="sxs-lookup"><span data-stu-id="affcd-180">**Ll** - LowercaseLetter</span></span>
- <span data-ttu-id="affcd-181">**Lt** -TitlecaseLetter</span><span class="sxs-lookup"><span data-stu-id="affcd-181">**Lt** - TitlecaseLetter</span></span>
- <span data-ttu-id="affcd-182">**LM** -ModifierLetter</span><span class="sxs-lookup"><span data-stu-id="affcd-182">**Lm** - ModifierLetter</span></span>
- <span data-ttu-id="affcd-183">**Lo** -OtherLetter</span><span class="sxs-lookup"><span data-stu-id="affcd-183">**Lo** - OtherLetter</span></span>
- <span data-ttu-id="affcd-184">**ND** -DecimalDigitNumber</span><span class="sxs-lookup"><span data-stu-id="affcd-184">**Nd** - DecimalDigitNumber</span></span>

<span data-ttu-id="affcd-185">Als u een naam van een variabele wilt maken of weer geven die spaties of speciale tekens bevat, moet u de naam van de variabele tussen accolades ( `{}` ) plaatsen.</span><span class="sxs-lookup"><span data-stu-id="affcd-185">To create or display a variable name that includes spaces or special characters, enclose the variable name with the curly braces (`{}`) characters.</span></span>
<span data-ttu-id="affcd-186">De accolades direct Power shell om de tekens van de naam van de variabele te interpreteren als letterlijke waarden.</span><span class="sxs-lookup"><span data-stu-id="affcd-186">The curly braces direct PowerShell to interpret the variable name's characters as literals.</span></span>

<span data-ttu-id="affcd-187">Namen van speciale teken variabelen kunnen de volgende tekens bevatten:</span><span class="sxs-lookup"><span data-stu-id="affcd-187">Special character variable names can contain these characters:</span></span>

- <span data-ttu-id="affcd-188">Elk Unicode-teken, met de volgende uitzonde ringen:</span><span class="sxs-lookup"><span data-stu-id="affcd-188">Any Unicode character, with the following exceptions:</span></span>
  - <span data-ttu-id="affcd-189">Het accolade `}` teken () sluiten (U + 007D).</span><span class="sxs-lookup"><span data-stu-id="affcd-189">The closing curly brace (`}`) character (U+007D).</span></span>
  - <span data-ttu-id="affcd-190">Het apostroffen ( `` ` `` )-teken (U + 0060).</span><span class="sxs-lookup"><span data-stu-id="affcd-190">The backtick (`` ` ``) character (U+0060).</span></span> <span data-ttu-id="affcd-191">De apostroffen wordt gebruikt om Unicode-tekens te escapen zodat ze als letterlijke waarden worden behandeld.</span><span class="sxs-lookup"><span data-stu-id="affcd-191">The backtick is used to escape Unicode characters so they're treated as literals.</span></span>

<span data-ttu-id="affcd-192">Power Shell heeft gereserveerde variabelen `$$` , zoals,, `$?` `$^` en `$_` die alfanumerieke en speciale tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="affcd-192">PowerShell has reserved variables such as `$$`, `$?`, `$^`, and `$_` that contain alphanumeric and special characters.</span></span> <span data-ttu-id="affcd-193">Zie [about_Automatic_Variables](about_automatic_variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="affcd-193">For more information, see [about_Automatic_Variables](about_automatic_variables.md).</span></span>

<span data-ttu-id="affcd-194">Met de volgende opdracht wordt bijvoorbeeld de variabele met de naam gemaakt `save-items` .</span><span class="sxs-lookup"><span data-stu-id="affcd-194">For example, the following command creates the variable named `save-items`.</span></span> <span data-ttu-id="affcd-195">De accolades ( `{}` ) zijn nodig omdat de naam van de variabele een afbreek streepje () met een `-` speciaal teken bevat.</span><span class="sxs-lookup"><span data-stu-id="affcd-195">The curly braces (`{}`) are needed because variable name includes a hyphen (`-`) special character.</span></span>

```powershell
${save-items} = "a", "b", "c"
${save-items}
```

```Output
a
b
c
```

<span data-ttu-id="affcd-196">Met de volgende opdracht worden de onderliggende items in de map opgehaald die wordt vertegenwoordigd door de `ProgramFiles(x86)` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="affcd-196">The following command gets the child items in the directory that is represented by the `ProgramFiles(x86)` environment variable.</span></span>

```powershell
Get-ChildItem ${env:ProgramFiles(x86)}
```

<span data-ttu-id="affcd-197">Als u wilt verwijzen naar een naam van een variabele die accolades bevat, plaatst u de naam van de variabele tussen accolades en gebruikt u het apostroffen-teken om de accolades te escapen.</span><span class="sxs-lookup"><span data-stu-id="affcd-197">To reference a variable name that includes braces, enclose the variable name in braces, and use the backtick character to escape the braces.</span></span> <span data-ttu-id="affcd-198">Als u bijvoorbeeld een variabele met de naam `this{value}is` type wilt maken:</span><span class="sxs-lookup"><span data-stu-id="affcd-198">For example, to create a variable named `this{value}is` type:</span></span>

```powershell
${this`{value`}is} = "This variable name uses braces and backticks."
${this`{value`}is}
```

```Output
This variable name uses braces and backticks.
```

## <a name="variables-and-scope"></a><span data-ttu-id="affcd-199">Variabelen en bereik</span><span class="sxs-lookup"><span data-stu-id="affcd-199">Variables and scope</span></span>

<span data-ttu-id="affcd-200">Variabelen zijn standaard alleen beschikbaar in het bereik waarin ze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="affcd-200">By default, variables are only available in the scope in which they're created.</span></span>

<span data-ttu-id="affcd-201">Een variabele die u in een functie hebt gemaakt, is bijvoorbeeld alleen beschikbaar in de functie.</span><span class="sxs-lookup"><span data-stu-id="affcd-201">For example, a variable that you create in a function is available only within the function.</span></span> <span data-ttu-id="affcd-202">Een variabele die u in een script maakt, is alleen beschikbaar in het script.</span><span class="sxs-lookup"><span data-stu-id="affcd-202">A variable that you create in a script is available only within the script.</span></span> <span data-ttu-id="affcd-203">Als u het script met de punt-bron, wordt de variabele toegevoegd aan het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="affcd-203">If you dot-source the script, the variable is added to the current scope.</span></span> <span data-ttu-id="affcd-204">Zie [about_Scopes](about_Scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="affcd-204">For more information, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="affcd-205">U kunt een bereik wijzigings functie gebruiken om het standaard bereik van de variabele te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="affcd-205">You can use a scope modifier to change the default scope of the variable.</span></span> <span data-ttu-id="affcd-206">Met de volgende expressie maakt u een variabele met de naam `Computers` .</span><span class="sxs-lookup"><span data-stu-id="affcd-206">The following expression creates a variable named `Computers`.</span></span> <span data-ttu-id="affcd-207">De variabele heeft een globaal bereik, zelfs wanneer deze in een script of functie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="affcd-207">The variable has a global scope, even when it's created in a script or function.</span></span>

```powershell
$Global:Computers = "Server01"
```

<span data-ttu-id="affcd-208">Voor elk script of elke opdracht die uit de sessie wordt uitgevoerd, hebt u de `Using` bereik wijzigings functie nodig om variabele waarden van het aanroepende sessie bereik in te sluiten, zodat out of Session-code er toegang toe heeft.</span><span class="sxs-lookup"><span data-stu-id="affcd-208">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span>

<span data-ttu-id="affcd-209">Zie [about_Remote_Variables](about_Remote_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="affcd-209">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="saving-variables"></a><span data-ttu-id="affcd-210">Variabelen opslaan</span><span class="sxs-lookup"><span data-stu-id="affcd-210">Saving variables</span></span>

<span data-ttu-id="affcd-211">Variabelen die u maakt, zijn alleen beschikbaar in de sessie waarin u ze maakt.</span><span class="sxs-lookup"><span data-stu-id="affcd-211">Variables that you create are available only in the session in which you create them.</span></span> <span data-ttu-id="affcd-212">Ze gaan verloren wanneer u uw sessie sluit.</span><span class="sxs-lookup"><span data-stu-id="affcd-212">They're lost when you close your session.</span></span>

<span data-ttu-id="affcd-213">Als u de variabele wilt maken in elke Power shell-sessie die u start, voegt u de variabele toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="affcd-213">To create the variable in every PowerShell session that you start, add the variable to your PowerShell profile.</span></span>

<span data-ttu-id="affcd-214">Als u bijvoorbeeld de waarde van de `$VerbosePreference` variabele in elke Power shell-sessie wilt wijzigen, voegt u de volgende opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="affcd-214">For example, to change the value of the `$VerbosePreference` variable in every PowerShell session, add the following command to your PowerShell profile.</span></span>

```powershell
$VerbosePreference = "Continue"
```

<span data-ttu-id="affcd-215">U kunt deze opdracht toevoegen aan uw Power shell-profiel door het bestand te openen `$PROFILE` in een tekst editor, zoals **notepad.exe**.</span><span class="sxs-lookup"><span data-stu-id="affcd-215">You can add this command to your PowerShell profile by opening the `$PROFILE` file in a text editor, such as **notepad.exe**.</span></span> <span data-ttu-id="affcd-216">Zie [about_Profiles](about_Profiles.md)voor meer informatie over Power shell-profielen.</span><span class="sxs-lookup"><span data-stu-id="affcd-216">For more information about PowerShell profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="the-variable-drive"></a><span data-ttu-id="affcd-217">De variabele: station</span><span class="sxs-lookup"><span data-stu-id="affcd-217">The Variable: drive</span></span>

<span data-ttu-id="affcd-218">De provider van de Power shell-variabele maakt een `Variable:` station dat eruitziet en fungeert als een bestandssysteem station, maar bevat de variabelen in uw sessie en hun waarden.</span><span class="sxs-lookup"><span data-stu-id="affcd-218">The PowerShell Variable provider creates a `Variable:` drive that looks and acts like a file system drive, but it contains the variables in your session and their values.</span></span>

<span data-ttu-id="affcd-219">Als u het station wilt wijzigen `Variable:` , gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="affcd-219">To change to the `Variable:` drive, use the following command:</span></span>

```powershell
Set-Location Variable:
```

<span data-ttu-id="affcd-220">`Variable:`Gebruik de `Get-Item` cmdlets of om de items en variabelen in het station weer te geven `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="affcd-220">To list the items and variables in the `Variable:` drive, use the `Get-Item` or `Get-ChildItem` cmdlets.</span></span>

```powershell
Get-ChildItem Variable:
```

<span data-ttu-id="affcd-221">Als u de waarde van een bepaalde variabele wilt ophalen, gebruikt u de notatie File System om de naam van het station en de naam van de variabele op te geven.</span><span class="sxs-lookup"><span data-stu-id="affcd-221">To get the value of a particular variable, use file system notation to specify the name of the drive and the name of the variable.</span></span> <span data-ttu-id="affcd-222">`$PSCulture`Gebruik bijvoorbeeld de volgende opdracht om de automatische variabele op te halen.</span><span class="sxs-lookup"><span data-stu-id="affcd-222">For example, to get the `$PSCulture` automatic variable, use the following command.</span></span>

```powershell
Get-Item Variable:\PSCulture
```

```Output
Name                           Value
----                           -----
PSCulture                      en-US
```

<span data-ttu-id="affcd-223">Als u meer informatie over het `Variable:` station en de Power shell-variabele provider wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="affcd-223">To display more information about the `Variable:` drive and the PowerShell Variable provider, type:</span></span>

```powershell
Get-Help Variable
```

## <a name="variable-syntax-with-provider-paths"></a><span data-ttu-id="affcd-224">Variabele syntaxis met provider paden</span><span class="sxs-lookup"><span data-stu-id="affcd-224">Variable syntax with provider paths</span></span>

<span data-ttu-id="affcd-225">U kunt een pad naar een provider voor voegsel met het dollar ( `$` )-teken en toegang krijgen tot de inhoud van elke provider die de [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) -interface implementeert.</span><span class="sxs-lookup"><span data-stu-id="affcd-225">You can prefix a provider path with the dollar (`$`) sign, and access the content of any provider that implements the [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span></span>

<span data-ttu-id="affcd-226">De volgende ingebouwde Power shell-providers ondersteunen deze notatie:</span><span class="sxs-lookup"><span data-stu-id="affcd-226">The following built-in PowerShell providers support this notation:</span></span>

- [<span data-ttu-id="affcd-227">about_Environment_Provider</span><span class="sxs-lookup"><span data-stu-id="affcd-227">about_Environment_Provider</span></span>](about_Environment_Provider.md)
- [<span data-ttu-id="affcd-228">about_Variable_Provider</span><span class="sxs-lookup"><span data-stu-id="affcd-228">about_Variable_Provider</span></span>](about_Variable_Provider.md)
- [<span data-ttu-id="affcd-229">about_Function_Provider</span><span class="sxs-lookup"><span data-stu-id="affcd-229">about_Function_Provider</span></span>](about_Function_Provider.md)
- [<span data-ttu-id="affcd-230">about_Alias_Provider</span><span class="sxs-lookup"><span data-stu-id="affcd-230">about_Alias_Provider</span></span>](about_Alias_Provider.md)

## <a name="the-variable-cmdlets"></a><span data-ttu-id="affcd-231">De variabele-cmdlets</span><span class="sxs-lookup"><span data-stu-id="affcd-231">The variable cmdlets</span></span>

<span data-ttu-id="affcd-232">Power shell bevat een set cmdlets die zijn ontworpen voor het beheren van variabelen.</span><span class="sxs-lookup"><span data-stu-id="affcd-232">PowerShell includes a set of cmdlets that are designed to manage variables.</span></span>

<span data-ttu-id="affcd-233">Als u de cmdlets wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="affcd-233">To list the cmdlets, type:</span></span>

```powershell
Get-Command -Noun Variable
```

<span data-ttu-id="affcd-234">Als u hulp wilt krijgen voor een specifieke cmdlet, typt u:</span><span class="sxs-lookup"><span data-stu-id="affcd-234">To get help for a specific cmdlet, type:</span></span>

```powershell
Get-Help <cmdlet-name>
```

| <span data-ttu-id="affcd-235">Naam van cmdlet</span><span class="sxs-lookup"><span data-stu-id="affcd-235">Cmdlet Name</span></span>       | <span data-ttu-id="affcd-236">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="affcd-236">Description</span></span>                                |
| ---------------   | ------------------------------------------ |
| `Clear-Variable`  | <span data-ttu-id="affcd-237">Hiermee verwijdert u de waarde van een variabele.</span><span class="sxs-lookup"><span data-stu-id="affcd-237">Deletes the value of a variable.</span></span>           |
| `Get-Variable`    | <span data-ttu-id="affcd-238">Hiermee worden de variabelen in de huidige console opgehaald.</span><span class="sxs-lookup"><span data-stu-id="affcd-238">Gets the variables in the current console.</span></span> |
| `New-Variable`    | <span data-ttu-id="affcd-239">Hiermee maakt u een nieuwe variabele.</span><span class="sxs-lookup"><span data-stu-id="affcd-239">Creates a new variable.</span></span>                    |
| `Remove-Variable` | <span data-ttu-id="affcd-240">Hiermee verwijdert u een variabele en de bijbehorende waarde.</span><span class="sxs-lookup"><span data-stu-id="affcd-240">Deletes a variable and its value.</span></span>          |
| `Set-Variable`    | <span data-ttu-id="affcd-241">Wijzigt de waarde van een variabele.</span><span class="sxs-lookup"><span data-stu-id="affcd-241">Changes the value of a variable.</span></span>           |

## <a name="see-also"></a><span data-ttu-id="affcd-242">Zie ook</span><span class="sxs-lookup"><span data-stu-id="affcd-242">See also</span></span>

[<span data-ttu-id="affcd-243">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="affcd-243">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="affcd-244">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="affcd-244">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="affcd-245">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="affcd-245">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="affcd-246">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="affcd-246">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="affcd-247">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="affcd-247">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="affcd-248">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="affcd-248">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="affcd-249">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="affcd-249">about_Remote_Variables</span></span>](about_Remote_Variables.md)
