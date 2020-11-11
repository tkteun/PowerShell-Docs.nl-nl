---
description: Hierin wordt beschreven hoe variabelen waarden opslaan die kunnen worden gebruikt in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variables?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Variables
ms.openlocfilehash: 2a6daa33cc671bd287b395aa4e1dd6f871c26bf9
ms.sourcegitcommit: 768816a5c05cc2d07ffd84bed95b0499f4b49f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483159"
---
# <a name="about-variables"></a><span data-ttu-id="307e0-104">Over variabelen</span><span class="sxs-lookup"><span data-stu-id="307e0-104">About Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="307e0-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="307e0-105">Short description</span></span>

<span data-ttu-id="307e0-106">Hierin wordt beschreven hoe variabelen waarden opslaan die kunnen worden gebruikt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="307e0-106">Describes how variables store values that can be used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="307e0-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="307e0-107">Long description</span></span>

<span data-ttu-id="307e0-108">U kunt alle typen waarden opslaan in Power shell-variabelen.</span><span class="sxs-lookup"><span data-stu-id="307e0-108">You can store all types of values in PowerShell variables.</span></span> <span data-ttu-id="307e0-109">U kunt bijvoorbeeld de resultaten van opdrachten opslaan en elementen opslaan die in opdrachten en expressies worden gebruikt, zoals namen, paden, instellingen en waarden.</span><span class="sxs-lookup"><span data-stu-id="307e0-109">For example, store the results of commands, and store elements that are used in commands and expressions, such as names, paths, settings, and values.</span></span>

<span data-ttu-id="307e0-110">Een variabele is een geheugen eenheid waarin waarden worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="307e0-110">A variable is a unit of memory in which values are stored.</span></span> <span data-ttu-id="307e0-111">In Power shell worden variabelen vertegenwoordigd door teken reeksen die beginnen met een dollar teken ( `$` ), zoals `$a` , `$process` of `$my_var` .</span><span class="sxs-lookup"><span data-stu-id="307e0-111">In PowerShell, variables are represented by text strings that begin with a dollar sign (`$`), such as `$a`, `$process`, or `$my_var`.</span></span>

<span data-ttu-id="307e0-112">Namen van variabelen zijn niet hoofdletter gevoelig en kunnen spaties en speciale tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="307e0-112">Variable names aren't case-sensitive, and can include spaces and special characters.</span></span> <span data-ttu-id="307e0-113">Namen van variabelen met speciale tekens en spaties zijn echter lastig te gebruiken en moeten worden vermeden.</span><span class="sxs-lookup"><span data-stu-id="307e0-113">But, variable names that include special characters and spaces are difficult to use and should be avoided.</span></span> <span data-ttu-id="307e0-114">Zie [namen van variabelen die speciale tekens bevatten](#variable-names-that-include-special-characters)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="307e0-114">For more information, see [Variable names that include special characters](#variable-names-that-include-special-characters).</span></span>

<span data-ttu-id="307e0-115">Er zijn verschillende typen variabelen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="307e0-115">There are several different types of variables in PowerShell.</span></span>

- <span data-ttu-id="307e0-116">Door gebruiker gemaakte variabelen: door de gebruiker gemaakte variabelen worden gemaakt en onderhouden door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="307e0-116">User-created variables: User-created variables are created and maintained by the user.</span></span> <span data-ttu-id="307e0-117">De variabelen die u in de Power shell-opdracht regel maakt, bestaan standaard alleen wanneer het Power shell-venster is geopend.</span><span class="sxs-lookup"><span data-stu-id="307e0-117">By default, the variables that you create at the PowerShell command line exist only while the PowerShell window is open.</span></span> <span data-ttu-id="307e0-118">Wanneer het Power shell-venster wordt gesloten, worden de variabelen verwijderd.</span><span class="sxs-lookup"><span data-stu-id="307e0-118">When the PowerShell windows is closed, the variables are deleted.</span></span> <span data-ttu-id="307e0-119">Als u een variabele wilt opslaan, voegt u deze toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="307e0-119">To save a variable, add it to your PowerShell profile.</span></span> <span data-ttu-id="307e0-120">U kunt ook variabelen maken in scripts met globaal, script of lokaal bereik.</span><span class="sxs-lookup"><span data-stu-id="307e0-120">You can also create variables in scripts with global, script, or local scope.</span></span>

- <span data-ttu-id="307e0-121">Automatische variabelen: automatische variabelen slaan de status van Power shell op.</span><span class="sxs-lookup"><span data-stu-id="307e0-121">Automatic variables: Automatic variables store the state of PowerShell.</span></span> <span data-ttu-id="307e0-122">Deze variabelen worden gemaakt door Power shell en Power shell wijzigt hun waarden naar behoefte om hun nauw keurigheid te behouden.</span><span class="sxs-lookup"><span data-stu-id="307e0-122">These variables are created by PowerShell, and PowerShell changes their values as required to maintain their accuracy.</span></span> <span data-ttu-id="307e0-123">Gebruikers kunnen de waarde van deze variabelen niet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="307e0-123">Users can't change the value of these variables.</span></span> <span data-ttu-id="307e0-124">De `$PSHOME` variabele slaat bijvoorbeeld het pad op naar de installatie directory van Power shell.</span><span class="sxs-lookup"><span data-stu-id="307e0-124">For example, the `$PSHOME` variable stores the path to the PowerShell installation directory.</span></span>

  <span data-ttu-id="307e0-125">Zie [about_Automatic_Variables](about_Automatic_Variables.md)voor meer informatie, een lijst en een beschrijving van de automatische variabelen.</span><span class="sxs-lookup"><span data-stu-id="307e0-125">For more information, a list, and a description of the automatic variables, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

- <span data-ttu-id="307e0-126">Voorkeurs variabelen: voorkeurs variabelen slaan gebruikers voorkeuren op voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="307e0-126">Preference variables: Preference variables store user preferences for PowerShell.</span></span> <span data-ttu-id="307e0-127">Deze variabelen worden gemaakt door Power shell en worden gevuld met standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="307e0-127">These variables are created by PowerShell and are populated with default values.</span></span> <span data-ttu-id="307e0-128">Gebruikers kunnen de waarden van deze variabelen wijzigen.</span><span class="sxs-lookup"><span data-stu-id="307e0-128">Users can change the values of these variables.</span></span> <span data-ttu-id="307e0-129">De `$MaximumHistoryCount` variabele bepaalt bijvoorbeeld het maximum aantal vermeldingen in de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="307e0-129">For example, the `$MaximumHistoryCount` variable determines the maximum number of entries in the session history.</span></span>

  <span data-ttu-id="307e0-130">Zie [about_Preference_Variables](about_Preference_Variables.md)voor meer informatie, een lijst en een beschrijving van de voorkeurs variabelen.</span><span class="sxs-lookup"><span data-stu-id="307e0-130">For more information, a list, and a description of the preference variables, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

## <a name="working-with-variables"></a><span data-ttu-id="307e0-131">Werken met variabelen</span><span class="sxs-lookup"><span data-stu-id="307e0-131">Working with variables</span></span>

<span data-ttu-id="307e0-132">Als u een nieuwe variabele wilt maken, gebruikt u een toewijzings instructie om een waarde toe te wijzen aan de variabele.</span><span class="sxs-lookup"><span data-stu-id="307e0-132">To create a new variable, use an assignment statement to assign a value to the variable.</span></span> <span data-ttu-id="307e0-133">U hoeft de variabele niet te declareren voordat u deze gebruikt.</span><span class="sxs-lookup"><span data-stu-id="307e0-133">You don't have to declare the variable before using it.</span></span> <span data-ttu-id="307e0-134">De standaard waarde van alle variabelen is `$null` .</span><span class="sxs-lookup"><span data-stu-id="307e0-134">The default value of all variables is `$null`.</span></span>

<span data-ttu-id="307e0-135">Als u een lijst wilt weer geven met alle variabelen in uw Power shell-sessie, typt u `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="307e0-135">To get a list of all the variables in your PowerShell session, type `Get-Variable`.</span></span> <span data-ttu-id="307e0-136">De namen van variabelen worden weer gegeven zonder het voor gaande dollar `$` teken () dat wordt gebruikt om te verwijzen naar variabelen.</span><span class="sxs-lookup"><span data-stu-id="307e0-136">The variable names are displayed without the preceding dollar (`$`) sign that is used to reference variables.</span></span>

<span data-ttu-id="307e0-137">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="307e0-137">For example:</span></span>

```powershell
$MyVariable = 1, 2, 3

$Path = "C:\Windows\System32"
```

<span data-ttu-id="307e0-138">Variabelen zijn handig om de resultaten van opdrachten op te slaan.</span><span class="sxs-lookup"><span data-stu-id="307e0-138">Variables are useful for storing the results of commands.</span></span>

<span data-ttu-id="307e0-139">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="307e0-139">For example:</span></span>

```powershell
$Processes = Get-Process

$Today = (Get-Date).DateTime
```

<span data-ttu-id="307e0-140">Als u de waarde van een variabele wilt weer geven, typt u de naam van de variabele, voorafgegaan door een dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="307e0-140">To display the value of a variable, type the variable name, preceded by a dollar sign (`$`).</span></span>

<span data-ttu-id="307e0-141">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="307e0-141">For example:</span></span>

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

<span data-ttu-id="307e0-142">Als u de waarde van een variabele wilt wijzigen, wijst u een nieuwe waarde toe aan de variabele.</span><span class="sxs-lookup"><span data-stu-id="307e0-142">To change the value of a variable, assign a new value to the variable.</span></span>

<span data-ttu-id="307e0-143">In de volgende voor beelden wordt de waarde van de variabele weer gegeven `$MyVariable` , wordt de waarde van de variabele gewijzigd, waarna de nieuwe waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="307e0-143">The following examples display the value of the `$MyVariable` variable, changes the value of the variable, and then displays the new value.</span></span>

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

<span data-ttu-id="307e0-144">Als u de waarde van een variabele wilt verwijderen, gebruikt u de `Clear-Variable` cmdlet of wijzigt u de waarde in `$null` .</span><span class="sxs-lookup"><span data-stu-id="307e0-144">To delete the value of a variable, use the `Clear-Variable` cmdlet or change the value to `$null`.</span></span>

```powershell
Clear-Variable -Name MyVariable
```

```powershell
$MyVariable = $null
```

<span data-ttu-id="307e0-145">Als u de variabele wilt verwijderen, gebruikt u [Remove-variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) of [Remove-item](xref:Microsoft.PowerShell.Management.Remove-Item).</span><span class="sxs-lookup"><span data-stu-id="307e0-145">To delete the variable, use [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) or [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item).</span></span>

```powershell
Remove-Variable -Name MyVariable
```

```powershell
Remove-Item -Path Variable:\MyVariable
```

## <a name="types-of-variables"></a><span data-ttu-id="307e0-146">Typen variabelen</span><span class="sxs-lookup"><span data-stu-id="307e0-146">Types of variables</span></span>

<span data-ttu-id="307e0-147">U kunt elk type object in een variabele opslaan, met inbegrip van gehele getallen, teken reeksen, matrices en hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="307e0-147">You can store any type of object in a variable, including integers, strings, arrays, and hash tables.</span></span> <span data-ttu-id="307e0-148">En, objecten die processen, services, gebeurtenis logboeken en computers vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="307e0-148">And, objects that represent processes, services, event logs, and computers.</span></span>

<span data-ttu-id="307e0-149">Power shell-variabelen worden op een losse manier getypt, wat betekent dat ze niet zijn beperkt tot een bepaald type object.</span><span class="sxs-lookup"><span data-stu-id="307e0-149">PowerShell variables are loosely typed, which means that they aren't limited to a particular type of object.</span></span> <span data-ttu-id="307e0-150">Eén variabele kan zelfs een verzameling, of matrix, van verschillende typen objecten tegelijk bevatten.</span><span class="sxs-lookup"><span data-stu-id="307e0-150">A single variable can even contain a collection, or array, of different types of objects at the same time.</span></span>

<span data-ttu-id="307e0-151">Het gegevens type van een variabele wordt bepaald door de .NET-typen van de waarden van de variabele.</span><span class="sxs-lookup"><span data-stu-id="307e0-151">The data type of a variable is determined by the .NET types of the values of the variable.</span></span> <span data-ttu-id="307e0-152">Als u het object type van een variabele wilt weer geven, gebruikt u [Get-member](xref:Microsoft.PowerShell.Utility.Get-Member).</span><span class="sxs-lookup"><span data-stu-id="307e0-152">To view a variable's object type, use [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member).</span></span>

<span data-ttu-id="307e0-153">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="307e0-153">For example:</span></span>

```powershell
$a = 12                         # System.Int32
$a = "Word"                     # System.String
$a = 12, "Word"                 # array of System.Int32, System.String
$a = Get-ChildItem C:\Windows   # FileInfo and DirectoryInfo types
```

<span data-ttu-id="307e0-154">U kunt een type kenmerk en een cast-notatie gebruiken om ervoor te zorgen dat een variabele alleen specifieke object typen of objecten kan bevatten die kunnen worden geconverteerd naar dat type.</span><span class="sxs-lookup"><span data-stu-id="307e0-154">You can use a type attribute and cast notation to ensure that a variable can contain only specific object types or objects that can be converted to that type.</span></span> <span data-ttu-id="307e0-155">Als u een waarde van een ander type wilt toewijzen, probeert Power shell de waarde naar het type te converteren.</span><span class="sxs-lookup"><span data-stu-id="307e0-155">If you try to assign a value of another type, PowerShell tries to convert the value to its type.</span></span> <span data-ttu-id="307e0-156">Als het type niet kan worden geconverteerd, mislukt de toewijzings instructie.</span><span class="sxs-lookup"><span data-stu-id="307e0-156">If the type can't be converted, the assignment statement fails.</span></span>

<span data-ttu-id="307e0-157">Als u de cast-notatie wilt gebruiken, voert u een type naam tussen vier Kante haken in, vóór de naam van de variabele (aan de linkerkant van de toewijzings instructie).</span><span class="sxs-lookup"><span data-stu-id="307e0-157">To use cast notation, enter a type name, enclosed in brackets, before the variable name (on the left side of the assignment statement).</span></span> <span data-ttu-id="307e0-158">In het volgende voor beeld wordt een `$number` variabele gemaakt die alleen gehele getallen kan bevatten, een `$words` variabele die alleen teken reeksen kan bevatten en een `$dates` variabele die alleen **DateTime** -objecten kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="307e0-158">The following example creates a `$number` variable that can contain only integers, a `$words` variable that can contain only strings, and a `$dates` variable that can contain only **DateTime** objects.</span></span>

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

## <a name="using-variables-in-commands-and-expressions"></a><span data-ttu-id="307e0-159">Variabelen gebruiken in opdrachten en expressies</span><span class="sxs-lookup"><span data-stu-id="307e0-159">Using variables in commands and expressions</span></span>

<span data-ttu-id="307e0-160">Als u een variabele wilt gebruiken in een opdracht of expressie, typt u de naam van de variabele, voorafgegaan door het dollar `$` teken ().</span><span class="sxs-lookup"><span data-stu-id="307e0-160">To use a variable in a command or expression, type the variable name, preceded by the dollar (`$`) sign.</span></span>

<span data-ttu-id="307e0-161">Als de naam van de variabele en het dollar teken niet tussen aanhalings tekens staan, of als deze tussen dubbele aanhalings `"` tekens () zijn geplaatst, wordt de waarde van de variabele in de opdracht of expressie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="307e0-161">If the variable name and dollar sign aren't enclosed in quotation marks, or if they're enclosed in double quotation (`"`) marks, the value of the variable is used in the command or expression.</span></span>

<span data-ttu-id="307e0-162">Als de naam van de variabele en het dollar teken tussen enkele aanhalings `'` tekens () worden geplaatst, wordt de naam van de variabele in de expressie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="307e0-162">If the variable name and dollar sign are enclosed in single quotation (`'`) marks, the variable name is used in the expression.</span></span>

<span data-ttu-id="307e0-163">Zie [about_Quoting_Rules](about_Quoting_Rules.md)voor meer informatie over het gebruik van aanhalings tekens in Power shell.</span><span class="sxs-lookup"><span data-stu-id="307e0-163">For more information about using quotation marks in PowerShell, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

<span data-ttu-id="307e0-164">In dit voor beeld wordt de waarde van de `$PROFILE` variabele opgehaald, het pad naar het Power shell-gebruikers profiel bestand in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="307e0-164">This example gets the value of the `$PROFILE` variable, which is the path to the PowerShell user profile file in the PowerShell console.</span></span>

```powershell
$PROFILE
```

```Output
C:\Users\User01\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
```

<span data-ttu-id="307e0-165">In dit voor beeld worden twee opdrachten weer gegeven waarmee het Power shell-profiel in **notepad.exe** kan worden geopend.</span><span class="sxs-lookup"><span data-stu-id="307e0-165">In this example, two commands are shown that can open the PowerShell profile in **notepad.exe**.</span></span> <span data-ttu-id="307e0-166">Het voor beeld met dubbele aanhalings `"` tekens () maakt gebruik van de waarde van de variabele.</span><span class="sxs-lookup"><span data-stu-id="307e0-166">The example with double-quote (`"`) marks uses the variable's value.</span></span>

```powershell
notepad $PROFILE

notepad "$PROFILE"
```

<span data-ttu-id="307e0-167">In de volgende voor beelden worden enkele aanhalings `'` tekens () gebruikt die de variabele behandelen als letterlijke tekst.</span><span class="sxs-lookup"><span data-stu-id="307e0-167">The following examples use single-quote (`'`) marks that treat the variable as literal text.</span></span>

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

## <a name="variable-names-that-include-special-characters"></a><span data-ttu-id="307e0-168">Namen van variabelen die speciale tekens bevatten</span><span class="sxs-lookup"><span data-stu-id="307e0-168">Variable names that include special characters</span></span>

<span data-ttu-id="307e0-169">Namen van variabelen beginnen met een dollar ( `$` ) teken en kunnen alfanumerieke tekens en speciale tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="307e0-169">Variable names begin with a dollar (`$`) sign and can include alphanumeric characters and special characters.</span></span> <span data-ttu-id="307e0-170">De lengte van de variabele naam wordt alleen beperkt door het beschik bare geheugen.</span><span class="sxs-lookup"><span data-stu-id="307e0-170">The variable name length is limited only by available memory.</span></span>

<span data-ttu-id="307e0-171">De best practice is dat namen van variabelen alleen alfanumerieke tekens en het onderstrepings `_` teken () bevatten.</span><span class="sxs-lookup"><span data-stu-id="307e0-171">The best practice is that variable names include only alphanumeric characters and the underscore (`_`) character.</span></span> <span data-ttu-id="307e0-172">Namen van variabelen die spaties en andere speciale tekens bevatten, zijn lastig te gebruiken en moeten worden vermeden.</span><span class="sxs-lookup"><span data-stu-id="307e0-172">Variable names that include spaces and other special characters, are difficult to use and should be avoided.</span></span>

<span data-ttu-id="307e0-173">Alfanumerieke namen van variabelen kunnen de volgende tekens bevatten:</span><span class="sxs-lookup"><span data-stu-id="307e0-173">Alphanumeric variable names can contain these characters:</span></span>

- <span data-ttu-id="307e0-174">Unicode-tekens uit deze categorieën: **Lu** , **ll** , **lt** , **LM** , **lo** of **ND**.</span><span class="sxs-lookup"><span data-stu-id="307e0-174">Unicode characters from these categories: **Lu** , **Ll** , **Lt** , **Lm** , **Lo** , or **Nd**.</span></span>
- <span data-ttu-id="307e0-175">Onderstrepings `_` teken ().</span><span class="sxs-lookup"><span data-stu-id="307e0-175">Underscore (`_`) character.</span></span>
- <span data-ttu-id="307e0-176">Vraag teken ( `?` )-teken.</span><span class="sxs-lookup"><span data-stu-id="307e0-176">Question mark (`?`) character.</span></span>

<span data-ttu-id="307e0-177">De volgende lijst bevat de beschrijvingen van de Unicode-categorie.</span><span class="sxs-lookup"><span data-stu-id="307e0-177">The following list contains the Unicode category descriptions.</span></span> <span data-ttu-id="307e0-178">Zie [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="307e0-178">For more information, see [UnicodeCategory](/dotnet/api/system.globalization.unicodecategory).</span></span>

- <span data-ttu-id="307e0-179">**Lu** -UppercaseLetter</span><span class="sxs-lookup"><span data-stu-id="307e0-179">**Lu** - UppercaseLetter</span></span>
- <span data-ttu-id="307e0-180">**Ll** -LowercaseLetter</span><span class="sxs-lookup"><span data-stu-id="307e0-180">**Ll** - LowercaseLetter</span></span>
- <span data-ttu-id="307e0-181">**Lt** -TitlecaseLetter</span><span class="sxs-lookup"><span data-stu-id="307e0-181">**Lt** - TitlecaseLetter</span></span>
- <span data-ttu-id="307e0-182">**LM** -ModifierLetter</span><span class="sxs-lookup"><span data-stu-id="307e0-182">**Lm** - ModifierLetter</span></span>
- <span data-ttu-id="307e0-183">**Lo** -OtherLetter</span><span class="sxs-lookup"><span data-stu-id="307e0-183">**Lo** - OtherLetter</span></span>
- <span data-ttu-id="307e0-184">**ND** -DecimalDigitNumber</span><span class="sxs-lookup"><span data-stu-id="307e0-184">**Nd** - DecimalDigitNumber</span></span>

<span data-ttu-id="307e0-185">Als u een naam van een variabele wilt maken of weer geven die spaties of speciale tekens bevat, moet u de naam van de variabele tussen accolades ( `{}` ) plaatsen.</span><span class="sxs-lookup"><span data-stu-id="307e0-185">To create or display a variable name that includes spaces or special characters, enclose the variable name with the curly braces (`{}`) characters.</span></span>
<span data-ttu-id="307e0-186">De accolades direct Power shell om de tekens van de naam van de variabele te interpreteren als letterlijke waarden.</span><span class="sxs-lookup"><span data-stu-id="307e0-186">The curly braces direct PowerShell to interpret the variable name's characters as literals.</span></span>

<span data-ttu-id="307e0-187">Namen van speciale teken variabelen kunnen de volgende tekens bevatten:</span><span class="sxs-lookup"><span data-stu-id="307e0-187">Special character variable names can contain these characters:</span></span>

- <span data-ttu-id="307e0-188">Elk Unicode-teken, met de volgende uitzonde ringen:</span><span class="sxs-lookup"><span data-stu-id="307e0-188">Any Unicode character, with the following exceptions:</span></span>
  - <span data-ttu-id="307e0-189">Het accolade `}` teken () sluiten (U + 007D).</span><span class="sxs-lookup"><span data-stu-id="307e0-189">The closing curly brace (`}`) character (U+007D).</span></span>
  - <span data-ttu-id="307e0-190">Het apostroffen ( `` ` `` )-teken (U + 0060).</span><span class="sxs-lookup"><span data-stu-id="307e0-190">The backtick (`` ` ``) character (U+0060).</span></span> <span data-ttu-id="307e0-191">De apostroffen wordt gebruikt om Unicode-tekens te escapen zodat ze als letterlijke waarden worden behandeld.</span><span class="sxs-lookup"><span data-stu-id="307e0-191">The backtick is used to escape Unicode characters so they're treated as literals.</span></span>

<span data-ttu-id="307e0-192">Power Shell heeft gereserveerde variabelen `$$` , zoals,, `$?` `$^` en `$_` die alfanumerieke en speciale tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="307e0-192">PowerShell has reserved variables such as `$$`, `$?`, `$^`, and `$_` that contain alphanumeric and special characters.</span></span> <span data-ttu-id="307e0-193">Zie [about_Automatic_Variables](about_automatic_variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="307e0-193">For more information, see [about_Automatic_Variables](about_automatic_variables.md).</span></span>

<span data-ttu-id="307e0-194">Met de volgende opdracht wordt bijvoorbeeld de variabele met de naam gemaakt `save-items` .</span><span class="sxs-lookup"><span data-stu-id="307e0-194">For example, the following command creates the variable named `save-items`.</span></span> <span data-ttu-id="307e0-195">De accolades ( `{}` ) zijn nodig omdat de naam van de variabele een afbreek streepje () met een `-` speciaal teken bevat.</span><span class="sxs-lookup"><span data-stu-id="307e0-195">The curly braces (`{}`) are needed because variable name includes a hyphen (`-`) special character.</span></span>

```powershell
${save-items} = "a", "b", "c"
${save-items}
```

```Output
a
b
c
```

<span data-ttu-id="307e0-196">Met de volgende opdracht worden de onderliggende items in de map opgehaald die wordt vertegenwoordigd door de `ProgramFiles(x86)` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="307e0-196">The following command gets the child items in the directory that is represented by the `ProgramFiles(x86)` environment variable.</span></span>

```powershell
Get-ChildItem ${env:ProgramFiles(x86)}
```

<span data-ttu-id="307e0-197">Als u wilt verwijzen naar een naam van een variabele die accolades bevat, plaatst u de naam van de variabele tussen accolades en gebruikt u het apostroffen-teken om de accolades te escapen.</span><span class="sxs-lookup"><span data-stu-id="307e0-197">To reference a variable name that includes braces, enclose the variable name in braces, and use the backtick character to escape the braces.</span></span> <span data-ttu-id="307e0-198">Als u bijvoorbeeld een variabele met de naam `this{value}is` type wilt maken:</span><span class="sxs-lookup"><span data-stu-id="307e0-198">For example, to create a variable named `this{value}is` type:</span></span>

```powershell
${this`{value`}is} = "This variable name uses braces and backticks."
${this`{value`}is}
```

```Output
This variable name uses braces and backticks.
```

## <a name="variables-and-scope"></a><span data-ttu-id="307e0-199">Variabelen en bereik</span><span class="sxs-lookup"><span data-stu-id="307e0-199">Variables and scope</span></span>

<span data-ttu-id="307e0-200">Variabelen zijn standaard alleen beschikbaar in het bereik waarin ze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="307e0-200">By default, variables are only available in the scope in which they're created.</span></span>

<span data-ttu-id="307e0-201">Een variabele die u in een functie hebt gemaakt, is bijvoorbeeld alleen beschikbaar in de functie.</span><span class="sxs-lookup"><span data-stu-id="307e0-201">For example, a variable that you create in a function is available only within the function.</span></span> <span data-ttu-id="307e0-202">Een variabele die u in een script maakt, is alleen beschikbaar in het script.</span><span class="sxs-lookup"><span data-stu-id="307e0-202">A variable that you create in a script is available only within the script.</span></span> <span data-ttu-id="307e0-203">Als u het script met de punt-bron, wordt de variabele toegevoegd aan het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="307e0-203">If you dot-source the script, the variable is added to the current scope.</span></span> <span data-ttu-id="307e0-204">Zie [about_Scopes](about_Scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="307e0-204">For more information, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="307e0-205">U kunt een bereik wijzigings functie gebruiken om het standaard bereik van de variabele te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="307e0-205">You can use a scope modifier to change the default scope of the variable.</span></span> <span data-ttu-id="307e0-206">Met de volgende expressie maakt u een variabele met de naam `Computers` .</span><span class="sxs-lookup"><span data-stu-id="307e0-206">The following expression creates a variable named `Computers`.</span></span> <span data-ttu-id="307e0-207">De variabele heeft een globaal bereik, zelfs wanneer deze in een script of functie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="307e0-207">The variable has a global scope, even when it's created in a script or function.</span></span>

```powershell
$Global:Computers = "Server01"
```

<span data-ttu-id="307e0-208">Voor elk script of elke opdracht die uit de sessie wordt uitgevoerd, hebt u de `Using` bereik wijzigings functie nodig om variabele waarden van het aanroepende sessie bereik in te sluiten, zodat out of Session-code er toegang toe heeft.</span><span class="sxs-lookup"><span data-stu-id="307e0-208">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span>

<span data-ttu-id="307e0-209">Zie [about_Remote_Variables](about_Remote_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="307e0-209">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="saving-variables"></a><span data-ttu-id="307e0-210">Variabelen opslaan</span><span class="sxs-lookup"><span data-stu-id="307e0-210">Saving variables</span></span>

<span data-ttu-id="307e0-211">Variabelen die u maakt, zijn alleen beschikbaar in de sessie waarin u ze maakt.</span><span class="sxs-lookup"><span data-stu-id="307e0-211">Variables that you create are available only in the session in which you create them.</span></span> <span data-ttu-id="307e0-212">Ze gaan verloren wanneer u uw sessie sluit.</span><span class="sxs-lookup"><span data-stu-id="307e0-212">They're lost when you close your session.</span></span>

<span data-ttu-id="307e0-213">Als u de variabele wilt maken in elke Power shell-sessie die u start, voegt u de variabele toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="307e0-213">To create the variable in every PowerShell session that you start, add the variable to your PowerShell profile.</span></span>

<span data-ttu-id="307e0-214">Als u bijvoorbeeld de waarde van de `$VerbosePreference` variabele in elke Power shell-sessie wilt wijzigen, voegt u de volgende opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="307e0-214">For example, to change the value of the `$VerbosePreference` variable in every PowerShell session, add the following command to your PowerShell profile.</span></span>

```powershell
$VerbosePreference = "Continue"
```

<span data-ttu-id="307e0-215">U kunt deze opdracht toevoegen aan uw Power shell-profiel door het bestand te openen `$PROFILE` in een tekst editor, zoals **notepad.exe**.</span><span class="sxs-lookup"><span data-stu-id="307e0-215">You can add this command to your PowerShell profile by opening the `$PROFILE` file in a text editor, such as **notepad.exe**.</span></span> <span data-ttu-id="307e0-216">Zie [about_Profiles](about_Profiles.md)voor meer informatie over Power shell-profielen.</span><span class="sxs-lookup"><span data-stu-id="307e0-216">For more information about PowerShell profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="the-variable-drive"></a><span data-ttu-id="307e0-217">De variabele: station</span><span class="sxs-lookup"><span data-stu-id="307e0-217">The Variable: drive</span></span>

<span data-ttu-id="307e0-218">De provider van de Power shell-variabele maakt een `Variable:` station dat eruitziet en fungeert als een bestandssysteem station, maar bevat de variabelen in uw sessie en hun waarden.</span><span class="sxs-lookup"><span data-stu-id="307e0-218">The PowerShell Variable provider creates a `Variable:` drive that looks and acts like a file system drive, but it contains the variables in your session and their values.</span></span>

<span data-ttu-id="307e0-219">Als u het station wilt wijzigen `Variable:` , gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="307e0-219">To change to the `Variable:` drive, use the following command:</span></span>

```powershell
Set-Location Variable:
```

<span data-ttu-id="307e0-220">`Variable:`Gebruik de `Get-Item` cmdlets of om de items en variabelen in het station weer te geven `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="307e0-220">To list the items and variables in the `Variable:` drive, use the `Get-Item` or `Get-ChildItem` cmdlets.</span></span>

```powershell
Get-ChildItem Variable:
```

<span data-ttu-id="307e0-221">Als u de waarde van een bepaalde variabele wilt ophalen, gebruikt u de notatie File System om de naam van het station en de naam van de variabele op te geven.</span><span class="sxs-lookup"><span data-stu-id="307e0-221">To get the value of a particular variable, use file system notation to specify the name of the drive and the name of the variable.</span></span> <span data-ttu-id="307e0-222">`$PSCulture`Gebruik bijvoorbeeld de volgende opdracht om de automatische variabele op te halen.</span><span class="sxs-lookup"><span data-stu-id="307e0-222">For example, to get the `$PSCulture` automatic variable, use the following command.</span></span>

```powershell
Get-Item Variable:\PSCulture
```

```Output
Name                           Value
----                           -----
PSCulture                      en-US
```

<span data-ttu-id="307e0-223">Als u meer informatie over het `Variable:` station en de Power shell-variabele provider wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="307e0-223">To display more information about the `Variable:` drive and the PowerShell Variable provider, type:</span></span>

```powershell
Get-Help Variable
```

## <a name="variable-syntax-with-provider-paths"></a><span data-ttu-id="307e0-224">Variabele syntaxis met provider paden</span><span class="sxs-lookup"><span data-stu-id="307e0-224">Variable syntax with provider paths</span></span>

<span data-ttu-id="307e0-225">U kunt een pad naar een provider voor voegsel met het dollar ( `$` )-teken en toegang krijgen tot de inhoud van elke provider die de [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) -interface implementeert.</span><span class="sxs-lookup"><span data-stu-id="307e0-225">You can prefix a provider path with the dollar (`$`) sign, and access the content of any provider that implements the [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span></span>

<span data-ttu-id="307e0-226">De volgende ingebouwde Power shell-providers ondersteunen deze notatie:</span><span class="sxs-lookup"><span data-stu-id="307e0-226">The following built-in PowerShell providers support this notation:</span></span>

- [<span data-ttu-id="307e0-227">about_Environment_Provider</span><span class="sxs-lookup"><span data-stu-id="307e0-227">about_Environment_Provider</span></span>](about_Environment_Provider.md)
- [<span data-ttu-id="307e0-228">about_Variable_Provider</span><span class="sxs-lookup"><span data-stu-id="307e0-228">about_Variable_Provider</span></span>](about_Variable_Provider.md)
- [<span data-ttu-id="307e0-229">about_Function_Provider</span><span class="sxs-lookup"><span data-stu-id="307e0-229">about_Function_Provider</span></span>](about_Function_Provider.md)
- [<span data-ttu-id="307e0-230">about_Alias_Provider</span><span class="sxs-lookup"><span data-stu-id="307e0-230">about_Alias_Provider</span></span>](about_Alias_Provider.md)

## <a name="the-variable-cmdlets"></a><span data-ttu-id="307e0-231">De variabele-cmdlets</span><span class="sxs-lookup"><span data-stu-id="307e0-231">The variable cmdlets</span></span>

<span data-ttu-id="307e0-232">Power shell bevat een set cmdlets die zijn ontworpen voor het beheren van variabelen.</span><span class="sxs-lookup"><span data-stu-id="307e0-232">PowerShell includes a set of cmdlets that are designed to manage variables.</span></span>

<span data-ttu-id="307e0-233">Als u de cmdlets wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="307e0-233">To list the cmdlets, type:</span></span>

```powershell
Get-Command -Noun Variable
```

<span data-ttu-id="307e0-234">Als u hulp wilt krijgen voor een specifieke cmdlet, typt u:</span><span class="sxs-lookup"><span data-stu-id="307e0-234">To get help for a specific cmdlet, type:</span></span>

```powershell
Get-Help <cmdlet-name>
```

| <span data-ttu-id="307e0-235">Naam van cmdlet</span><span class="sxs-lookup"><span data-stu-id="307e0-235">Cmdlet Name</span></span>       | <span data-ttu-id="307e0-236">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="307e0-236">Description</span></span>                                |
| ---------------   | ------------------------------------------ |
| `Clear-Variable`  | <span data-ttu-id="307e0-237">Hiermee verwijdert u de waarde van een variabele.</span><span class="sxs-lookup"><span data-stu-id="307e0-237">Deletes the value of a variable.</span></span>           |
| `Get-Variable`    | <span data-ttu-id="307e0-238">Hiermee worden de variabelen in de huidige console opgehaald.</span><span class="sxs-lookup"><span data-stu-id="307e0-238">Gets the variables in the current console.</span></span> |
| `New-Variable`    | <span data-ttu-id="307e0-239">Hiermee maakt u een nieuwe variabele.</span><span class="sxs-lookup"><span data-stu-id="307e0-239">Creates a new variable.</span></span>                    |
| `Remove-Variable` | <span data-ttu-id="307e0-240">Hiermee verwijdert u een variabele en de bijbehorende waarde.</span><span class="sxs-lookup"><span data-stu-id="307e0-240">Deletes a variable and its value.</span></span>          |
| `Set-Variable`    | <span data-ttu-id="307e0-241">Wijzigt de waarde van een variabele.</span><span class="sxs-lookup"><span data-stu-id="307e0-241">Changes the value of a variable.</span></span>           |

## <a name="see-also"></a><span data-ttu-id="307e0-242">Zie ook</span><span class="sxs-lookup"><span data-stu-id="307e0-242">See also</span></span>

[<span data-ttu-id="307e0-243">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="307e0-243">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="307e0-244">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="307e0-244">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="307e0-245">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="307e0-245">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="307e0-246">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="307e0-246">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="307e0-247">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="307e0-247">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="307e0-248">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="307e0-248">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="307e0-249">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="307e0-249">about_Remote_Variables</span></span>](about_Remote_Variables.md)
