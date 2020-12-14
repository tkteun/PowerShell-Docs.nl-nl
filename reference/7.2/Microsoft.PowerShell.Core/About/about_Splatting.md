---
description: Hierin wordt beschreven hoe u splatting gebruikt om para meters door te geven aan opdrachten in Power shell.
Locale: en-US
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_splatting?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Splatting
ms.openlocfilehash: e028f43828afd69d645591ab20795689cb115e12
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706203"
---
# <a name="about-splatting"></a><span data-ttu-id="78587-103">Over splatting</span><span class="sxs-lookup"><span data-stu-id="78587-103">About Splatting</span></span>

## <a name="short-description"></a><span data-ttu-id="78587-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="78587-104">Short description</span></span>

<span data-ttu-id="78587-105">Hierin wordt beschreven hoe u splatting gebruikt om para meters door te geven aan opdrachten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="78587-105">Describes how to use splatting to pass parameters to commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="78587-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="78587-106">Long description</span></span>

<span data-ttu-id="78587-107">Splatting is een methode voor het door geven van een verzameling parameter waarden aan een opdracht als een eenheid.</span><span class="sxs-lookup"><span data-stu-id="78587-107">Splatting is a method of passing a collection of parameter values to a command as a unit.</span></span> <span data-ttu-id="78587-108">Power shell koppelt elke waarde in de verzameling met een opdracht parameter.</span><span class="sxs-lookup"><span data-stu-id="78587-108">PowerShell associates each value in the collection with a command parameter.</span></span> <span data-ttu-id="78587-109">Splatted parameter waarden worden opgeslagen in benoemde splatting-variabelen, die eruitzien als standaard variabelen, maar beginnen met een at `@` -symbool () in plaats van een dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="78587-109">Splatted parameter values are stored in named splatting variables, which look like standard variables, but begin with an At symbol (`@`) instead of a dollar sign (`$`).</span></span> <span data-ttu-id="78587-110">Het at-symbool vertelt Power shell dat u een verzameling waarden, in plaats van één waarde, door gegeven.</span><span class="sxs-lookup"><span data-stu-id="78587-110">The At symbol tells PowerShell that you are passing a collection of values, instead of a single value.</span></span>

<span data-ttu-id="78587-111">Splatting maakt uw opdrachten korter en eenvoudiger te lezen.</span><span class="sxs-lookup"><span data-stu-id="78587-111">Splatting makes your commands shorter and easier to read.</span></span> <span data-ttu-id="78587-112">U kunt de splatting-waarden in verschillende opdracht aanroepen opnieuw gebruiken en splatting gebruiken om parameter waarden van de `$PSBoundParameters` Automatische variabele door te geven aan andere scripts en functies.</span><span class="sxs-lookup"><span data-stu-id="78587-112">You can reuse the splatting values in different command calls and use splatting to pass parameter values from the `$PSBoundParameters` automatic variable to other scripts and functions.</span></span>

<span data-ttu-id="78587-113">Vanaf Windows Power Shell 3,0 kunt u ook splatting gebruiken om alle para meters van een opdracht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="78587-113">Beginning in Windows PowerShell 3.0, you can also use splatting to represent all parameters of a command.</span></span>

## <a name="syntax"></a><span data-ttu-id="78587-114">Syntax</span><span class="sxs-lookup"><span data-stu-id="78587-114">Syntax</span></span>

```
<CommandName> <optional parameters> @<HashTable> <optional parameters>
<CommandName> <optional parameters> @<Array> <optional parameters>
```

<span data-ttu-id="78587-115">Gebruik de matrix syntaxis om parameter waarden op te geven voor positionele para meters, waarbij geen parameter namen zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="78587-115">To provide parameter values for positional parameters, in which parameter names are not required, use the array syntax.</span></span> <span data-ttu-id="78587-116">Als u parameter naam-en-waardeparen wilt opgeven, gebruikt u de syntaxis van de hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="78587-116">To provide parameter name and value pairs, use the hash table syntax.</span></span> <span data-ttu-id="78587-117">De splatted-waarde kan ergens in de parameter lijst worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="78587-117">The splatted value can appear anywhere in the parameter list.</span></span>

<span data-ttu-id="78587-118">Wanneer splatting, hoeft u geen hash-tabel of matrix te gebruiken om alle para meters door te geven.</span><span class="sxs-lookup"><span data-stu-id="78587-118">When splatting, you do not need to use a hash table or an array to pass all parameters.</span></span> <span data-ttu-id="78587-119">U kunt bepaalde para meters door geven door splatting te gebruiken en anderen door te geven op positie of op parameter naam.</span><span class="sxs-lookup"><span data-stu-id="78587-119">You may pass some parameters by using splatting and pass others by position or by parameter name.</span></span> <span data-ttu-id="78587-120">U kunt ook meerdere objecten in één opdracht splat, zodat u niet meer dan één waarde voor elke para meter hoeft door te geven.</span><span class="sxs-lookup"><span data-stu-id="78587-120">Also, you can splat multiple objects in a single command so you don't pass more than one value for each parameter.</span></span>

<span data-ttu-id="78587-121">Vanaf Power shell 7,1 kunt u een splatted-para meter onderdrukken door expliciet een para meter in een opdracht te definiëren.</span><span class="sxs-lookup"><span data-stu-id="78587-121">As of PowerShell 7.1, you can override a splatted parameter by explicitly defining a parameter in a command.</span></span>

## <a name="splatting-with-hash-tables"></a><span data-ttu-id="78587-122">Splatting met hash-tabellen</span><span class="sxs-lookup"><span data-stu-id="78587-122">Splatting with hash tables</span></span>

<span data-ttu-id="78587-123">Gebruik een hash-tabel om parameter naam-en-waardeparen te splat.</span><span class="sxs-lookup"><span data-stu-id="78587-123">Use a hash table to splat parameter name and value pairs.</span></span> <span data-ttu-id="78587-124">U kunt deze indeling gebruiken voor alle parameter typen, waaronder positionele para meters en switch parameters.</span><span class="sxs-lookup"><span data-stu-id="78587-124">You can use this format for all parameter types, including positional and switch parameters.</span></span>
<span data-ttu-id="78587-125">Positionele para meters moeten worden toegewezen op naam.</span><span class="sxs-lookup"><span data-stu-id="78587-125">Positional parameters must be assigned by name.</span></span>

<span data-ttu-id="78587-126">In de volgende voor beelden `Copy-Item` worden twee opdrachten vergeleken waarmee het Test.txt-bestand wordt gekopieerd naar het Test2.txt-bestand in dezelfde map.</span><span class="sxs-lookup"><span data-stu-id="78587-126">The following examples compare two `Copy-Item` commands that copy the Test.txt file to the Test2.txt file in the same directory.</span></span>

<span data-ttu-id="78587-127">In het eerste voor beeld wordt gebruikgemaakt van de traditionele notatie waarin parameter namen worden opgenomen.</span><span class="sxs-lookup"><span data-stu-id="78587-127">The first example uses the traditional format in which parameter names are included.</span></span>

```powershell
Copy-Item -Path "test.txt" -Destination "test2.txt" -WhatIf
```

<span data-ttu-id="78587-128">In het tweede voor beeld wordt gebruikgemaakt van hash-tabel splatting.</span><span class="sxs-lookup"><span data-stu-id="78587-128">The second example uses hash table splatting.</span></span> <span data-ttu-id="78587-129">Met de eerste opdracht maakt u een hash-tabel met de para meter-naam en parameter-waardeparen en slaat u deze op in de `$HashArguments` variabele.</span><span class="sxs-lookup"><span data-stu-id="78587-129">The first command creates a hash table of parameter-name and parameter-value pairs and stores it in the `$HashArguments` variable.</span></span> <span data-ttu-id="78587-130">Met de tweede opdracht wordt de `$HashArguments` variabele gebruikt in een opdracht met splatting.</span><span class="sxs-lookup"><span data-stu-id="78587-130">The second command uses the `$HashArguments` variable in a command with splatting.</span></span> <span data-ttu-id="78587-131">Het symbool at ( `@HashArguments` ) vervangt het dollar teken ( `$HashArguments` ) in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="78587-131">The At symbol (`@HashArguments`) replaces the dollar sign (`$HashArguments`) in the command.</span></span>

<span data-ttu-id="78587-132">Als u een waarde wilt opgeven voor de switch parameter **WhatIf** , gebruikt u `$True` of `$False` .</span><span class="sxs-lookup"><span data-stu-id="78587-132">To provide a value for the **WhatIf** switch parameter, use `$True` or `$False`.</span></span>

```powershell
$HashArguments = @{
  Path = "test.txt"
  Destination = "test2.txt"
  WhatIf = $true
}
Copy-Item @HashArguments
```

> [!NOTE]
> <span data-ttu-id="78587-133">In de eerste opdracht geeft het at-symbool ( `@` ) een hash-tabel aan, geen splatted-waarde.</span><span class="sxs-lookup"><span data-stu-id="78587-133">In the first command, the At symbol (`@`) indicates a hash table, not a splatted value.</span></span> <span data-ttu-id="78587-134">De syntaxis voor hash-tabellen in Power shell is: `@{<name>=<value>; <name>=<value>; ...}`</span><span class="sxs-lookup"><span data-stu-id="78587-134">The syntax for hash tables in PowerShell is: `@{<name>=<value>; <name>=<value>; ...}`</span></span>

## <a name="splatting-with-arrays"></a><span data-ttu-id="78587-135">Splatting met matrices</span><span class="sxs-lookup"><span data-stu-id="78587-135">Splatting with arrays</span></span>

<span data-ttu-id="78587-136">Gebruik een matrix om waarden te splat voor positionele para meters, waarvoor geen parameter namen zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="78587-136">Use an array to splat values for positional parameters, which do not require parameter names.</span></span> <span data-ttu-id="78587-137">De waarden moeten op positie nummer in de matrix staan.</span><span class="sxs-lookup"><span data-stu-id="78587-137">The values must be in position-number order in the array.</span></span>

<span data-ttu-id="78587-138">In de volgende voor beelden `Copy-Item` worden twee opdrachten vergeleken waarmee het Test.txt-bestand wordt gekopieerd naar het Test2.txt-bestand in dezelfde map.</span><span class="sxs-lookup"><span data-stu-id="78587-138">The following examples compare two `Copy-Item` commands that copy the Test.txt file to the Test2.txt file in the same directory.</span></span>

<span data-ttu-id="78587-139">In het eerste voor beeld wordt gebruikgemaakt van de traditionele notatie waarin parameter namen worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="78587-139">The first example uses the traditional format in which parameter names are omitted.</span></span> <span data-ttu-id="78587-140">De parameter waarden worden weer gegeven in positie volgorde in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="78587-140">The parameter values appear in position order in the command.</span></span>

```powershell
Copy-Item "test.txt" "test2.txt" -WhatIf
```

<span data-ttu-id="78587-141">In het tweede voor beeld wordt gebruikgemaakt van matrix splatting.</span><span class="sxs-lookup"><span data-stu-id="78587-141">The second example uses array splatting.</span></span> <span data-ttu-id="78587-142">Met de eerste opdracht maakt u een matrix van de parameter waarden en slaat u deze op in de `$ArrayArguments` variabele.</span><span class="sxs-lookup"><span data-stu-id="78587-142">The first command creates an array of the parameter values and stores it in the `$ArrayArguments` variable.</span></span> <span data-ttu-id="78587-143">De waarden bevinden zich in positie volgorde in de matrix.</span><span class="sxs-lookup"><span data-stu-id="78587-143">The values are in position order in the array.</span></span> <span data-ttu-id="78587-144">Met de tweede opdracht wordt de `$ArrayArguments` variabele gebruikt in een opdracht in splatting.</span><span class="sxs-lookup"><span data-stu-id="78587-144">The second command uses the `$ArrayArguments` variable in a command in splatting.</span></span> <span data-ttu-id="78587-145">Het symbool at ( `@ArrayArguments` ) vervangt het dollar teken ( `$ArrayArguments` ) in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="78587-145">The At symbol (`@ArrayArguments`) replaces the dollar sign (`$ArrayArguments`) in the command.</span></span>

```powershell
$ArrayArguments = "test.txt", "test2.txt"
Copy-Item @ArrayArguments -WhatIf
```

### <a name="using-the-argumentlist-parameter"></a><span data-ttu-id="78587-146">De para meter argument list gebruiken</span><span class="sxs-lookup"><span data-stu-id="78587-146">Using the ArgumentList parameter</span></span>

<span data-ttu-id="78587-147">Verschillende cmdlets hebben een **argument List** -para meter die wordt gebruikt om parameter waarden door te geven aan een script blok dat door de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="78587-147">Several cmdlets have an **ArgumentList** parameter that is used to pass parameter values to a script block that is executed by the cmdlet.</span></span> <span data-ttu-id="78587-148">De para meter **argument List** gebruikt een matrix van waarden die worden door gegeven aan het script blok.</span><span class="sxs-lookup"><span data-stu-id="78587-148">The **ArgumentList** parameter takes an array of values that is passed to the script block.</span></span> <span data-ttu-id="78587-149">Power Shell maakt effectief gebruik van matrix splatting om de waarden te binden aan de para meters van het-script blok.</span><span class="sxs-lookup"><span data-stu-id="78587-149">PowerShell is effectively using array splatting to bind the values to the parameters of the script block.</span></span> <span data-ttu-id="78587-150">Wanneer u **argument List** gebruikt en u een matrix wilt door geven als één object dat aan één para meter is gebonden, moet u de matrix als het enige element van een andere matrix laten teruglopen.</span><span class="sxs-lookup"><span data-stu-id="78587-150">When using **ArgumentList**, if you need to pass an array as a single object bound to a single parameter, you must wrap the array as the only element of another array.</span></span>

<span data-ttu-id="78587-151">Het volgende voor beeld heeft een script blok dat één para meter gebruikt die een matrix met teken reeksen is.</span><span class="sxs-lookup"><span data-stu-id="78587-151">The following example has a script block that takes a single parameter that is an array of strings.</span></span>

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList $array
```
<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->
<span data-ttu-id="78587-152">In dit voor beeld wordt alleen het eerste item in `$array` door gegeven aan het script blok.</span><span class="sxs-lookup"><span data-stu-id="78587-152">In this example, only the first item in `$array` is passed to the script block.</span></span>

```Output
Hello
```

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
} -ArgumentList (,$array)
```

<span data-ttu-id="78587-153">In dit voor beeld `$array` wordt verpakt in een matrix, zodat de gehele matrix als één object wordt door gegeven aan het script blok.</span><span class="sxs-lookup"><span data-stu-id="78587-153">In this example, `$array` is wrapped in an array so that the entire array is passed to the script block as a single object.</span></span>

```Output
Hello World!
```

## <a name="examples"></a><span data-ttu-id="78587-154">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="78587-154">Examples</span></span>

### <a name="example-1-reuse-splatted-parameters-in-different-commands"></a><span data-ttu-id="78587-155">Voor beeld 1: splatted-para meters opnieuw gebruiken in verschillende opdrachten</span><span class="sxs-lookup"><span data-stu-id="78587-155">Example 1: Reuse splatted parameters in different commands</span></span>

<span data-ttu-id="78587-156">In dit voor beeld ziet u hoe u splatted waarden in verschillende opdrachten opnieuw kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="78587-156">This example shows how to reuse splatted values in different commands.</span></span> <span data-ttu-id="78587-157">Met de opdrachten in dit voor beeld wordt de `Write-Host` cmdlet gebruikt voor het schrijven van berichten naar de console van de host.</span><span class="sxs-lookup"><span data-stu-id="78587-157">The commands in this example use the `Write-Host` cmdlet to write messages to the host program console.</span></span> <span data-ttu-id="78587-158">Splatting wordt gebruikt om de voorgrond-en achtergrond kleuren op te geven.</span><span class="sxs-lookup"><span data-stu-id="78587-158">It uses splatting to specify the foreground and background colors.</span></span>

<span data-ttu-id="78587-159">Als u de kleuren van alle opdrachten wilt wijzigen, wijzigt u alleen de waarde van de `$Colors` variabele.</span><span class="sxs-lookup"><span data-stu-id="78587-159">To change the colors of all commands, just change the value of the `$Colors` variable.</span></span>

<span data-ttu-id="78587-160">Met de eerste opdracht maakt u een hash-tabel met parameter namen en-waarden en slaat u de hash-tabel op in de `$Colors` variabele.</span><span class="sxs-lookup"><span data-stu-id="78587-160">The first command creates a hash table of parameter names and values and stores the hash table in the `$Colors` variable.</span></span>

```powershell
$Colors = @{ForegroundColor = "black"; BackgroundColor = "white"}
```

<span data-ttu-id="78587-161">De tweede en derde opdracht gebruiken de `$Colors` variabele voor splatting in een `Write-Host` opdracht.</span><span class="sxs-lookup"><span data-stu-id="78587-161">The second and third commands use the `$Colors` variable for splatting in a `Write-Host` command.</span></span> <span data-ttu-id="78587-162">Als u de wilt gebruiken `$Colors variable` , vervangt u het dollar teken ( `$Colors` ) door een at-symbool ( `@Colors` ).</span><span class="sxs-lookup"><span data-stu-id="78587-162">To use the `$Colors variable`, replace the dollar sign (`$Colors`) with an At symbol (`@Colors`).</span></span>

```powershell
#Write a message with the colors in $Colors
Write-Host "This is a test." @Colors

#Write second message with same colors. The position of splatted
#hash table does not matter.
Write-Host @Colors "This is another test."
```

### <a name="example-2-forward-parameters-using-psboundparameters"></a><span data-ttu-id="78587-163">Voor beeld 2: para meters door sturen met $PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="78587-163">Example 2: Forward parameters using $PSBoundParameters</span></span>

<span data-ttu-id="78587-164">In dit voor beeld ziet u hoe u de para meters kunt door sturen naar andere opdrachten met behulp van splatting en de `$PSBoundParameters` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="78587-164">This example shows how to forward their parameters to other commands by using splatting and the `$PSBoundParameters` automatic variable.</span></span>

<span data-ttu-id="78587-165">De `$PSBoundParameters` Automatische variabele is een Dictionary-object (System. Collections. generic. Dictionary) met daarin alle parameter namen en-waarden die worden gebruikt wanneer een script of functie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="78587-165">The `$PSBoundParameters` automatic variable is a dictionary object (System.Collections.Generic.Dictionary) that contains all the parameter names and values that are used when a script or function is run.</span></span>

<span data-ttu-id="78587-166">In het volgende voor beeld gebruiken we de `$PSBoundParameters` variabele voor het door sturen van de parameter waarden die zijn door gegeven aan een script of functie van `Test2` de functie naar de `Test1` functie.</span><span class="sxs-lookup"><span data-stu-id="78587-166">In the following example, we use the `$PSBoundParameters` variable to forward the parameters values passed to a script or function from `Test2` function to the `Test1` function.</span></span> <span data-ttu-id="78587-167">Beide aanroepen naar de `Test1` functie vanuit het `Test2` gebruik van splatting.</span><span class="sxs-lookup"><span data-stu-id="78587-167">Both calls to the `Test1` function from `Test2` use splatting.</span></span>

```powershell
function Test1
{
    param($a, $b, $c)

    $a
    $b
    $c
}

function Test2
{
    param($a, $b, $c)

    #Call the Test1 function with $a, $b, and $c.
    Test1 @PsBoundParameters

    #Call the Test1 function with $b and $c, but not with $a
    $LimitedParameters = $PSBoundParameters
    $LimitedParameters.Remove("a") | Out-Null
    Test1 @LimitedParameters
}
```

```Output
Test2 -a 1 -b 2 -c 3
1
2
3
2
3
```

### <a name="example-3-override-splatted-parameters-with-explicitly-defined-parameters"></a><span data-ttu-id="78587-168">Voor beeld 3: splatted-para meters negeren met expliciet gedefinieerde para meters</span><span class="sxs-lookup"><span data-stu-id="78587-168">Example 3: Override splatted parameters with explicitly defined parameters</span></span>

<span data-ttu-id="78587-169">In dit voor beeld ziet u hoe u een splatted-para meter overschrijft met expliciet gedefinieerde para meters.</span><span class="sxs-lookup"><span data-stu-id="78587-169">This example shows how to override a splatted parameter using explicitly defined parameters.</span></span> <span data-ttu-id="78587-170">Dit is handig als u geen nieuwe hashtabel wilt maken of als u een waarde in de hashtabel wilt wijzigen die u gebruikt voor splat.</span><span class="sxs-lookup"><span data-stu-id="78587-170">This is useful when you don't want to build a new hashtable or change a value in the hashtable you are using to splat.</span></span>

<span data-ttu-id="78587-171">De `$commonParams` variabele slaat de para meters op voor het maken van virtuele machines op de `East US` locatie.</span><span class="sxs-lookup"><span data-stu-id="78587-171">The `$commonParams` variable stores the parameters to create virtual machines in the `East US` location.</span></span> <span data-ttu-id="78587-172">De `$allVms` variabele is een lijst met virtuele machines die moeten worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="78587-172">The `$allVms` variable is a list of virtual machines to create.</span></span> <span data-ttu-id="78587-173">De lijst wordt door lopen en gebruikt `$commonParams` om de para meters te splat voor het maken van elke virtuele machine.</span><span class="sxs-lookup"><span data-stu-id="78587-173">We loop through the list and use `$commonParams` to splat the parameters to create each virtual machine.</span></span> <span data-ttu-id="78587-174">We willen echter `myVM2` in een andere regio dan de andere virtuele machines worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="78587-174">However, we want `myVM2` to be created in a different region than the other virtual machines.</span></span> <span data-ttu-id="78587-175">In plaats van de `$commonParams` hashtabel aan te passen, kunt u expliciet de **locatie** parameter in `New-AzVm` vervangen door de waarde van de `Location` sleutel in `$commonParams` .</span><span class="sxs-lookup"><span data-stu-id="78587-175">Instead of adjusting the `$commonParams` hashtable, you can explicitly define the **Location** parameter in `New-AzVm` to supersede the value of the `Location` key in `$commonParams`.</span></span>

```powershell
$commonParams = @{
    ResourceGroupName = "myResourceGroup"
    Location = "East US"
    VirtualNetworkName = "myVnet"
    SubnetName = "mySubnet"
    SecurityGroupName = "myNetworkSecurityGroup"
    PublicIpAddressName = "myPublicIpAddress"
}

$allVms = @('myVM1','myVM2','myVM3',)

foreach ($vm in $allVms)
{
    if ($vm -eq 'myVM2')
    {
        New-AzVm @commonParams -Name $vm -Location "West US"
    }
    else
    {
        New-AzVm @commonParams -Name $vm
    }
}
```

## <a name="splatting-command-parameters"></a><span data-ttu-id="78587-176">Splatting-opdracht parameters</span><span class="sxs-lookup"><span data-stu-id="78587-176">Splatting command parameters</span></span>

<span data-ttu-id="78587-177">U kunt splatting gebruiken om de para meters van een opdracht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="78587-177">You can use splatting to represent the parameters of a command.</span></span> <span data-ttu-id="78587-178">Deze techniek is handig wanneer u een proxy functie maakt, dat wil zeggen een functie die een andere opdracht aanroept.</span><span class="sxs-lookup"><span data-stu-id="78587-178">This technique is useful when you are creating a proxy function, that is, a function that calls another command.</span></span> <span data-ttu-id="78587-179">Deze functie is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="78587-179">This feature is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="78587-180">Als u de para meters van een opdracht wilt splat, gebruikt `@Args` u om de opdracht parameters weer te geven.</span><span class="sxs-lookup"><span data-stu-id="78587-180">To splat the parameters of a command, use `@Args` to represent the command parameters.</span></span> <span data-ttu-id="78587-181">Deze techniek is eenvoudiger dan het inventariseren van opdracht parameters en werkt zonder revisie, zelfs niet als de para meters van de aangeroepen opdracht veranderen.</span><span class="sxs-lookup"><span data-stu-id="78587-181">This technique is easier than enumerating command parameters and it works without revision even if the parameters of the called command change.</span></span>

<span data-ttu-id="78587-182">De functie maakt gebruik van de `$Args` Automatische variabele, die alle niet-toegewezen parameter waarden bevat.</span><span class="sxs-lookup"><span data-stu-id="78587-182">The feature uses the `$Args` automatic variable, which contains all unassigned parameter values.</span></span>

<span data-ttu-id="78587-183">Met de volgende functie wordt bijvoorbeeld de `Get-Process` cmdlet aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="78587-183">For example, the following function calls the `Get-Process` cmdlet.</span></span> <span data-ttu-id="78587-184">In deze functie `@Args` vertegenwoordigt alle para meters van de `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="78587-184">In this function, `@Args` represents all the parameters of the `Get-Process` cmdlet.</span></span>

```powershell
function Get-MyProcess { Get-Process @Args }
```

<span data-ttu-id="78587-185">Wanneer u de `Get-MyProcess` functie gebruikt, worden alle niet-toegewezen para meters en parameter waarden door gegeven aan `@Args` , zoals wordt weer gegeven in de volgende opdrachten.</span><span class="sxs-lookup"><span data-stu-id="78587-185">When you use the `Get-MyProcess` function, all unassigned parameters and parameter values are passed to `@Args`, as shown in the following commands.</span></span>

```powershell
Get-MyProcess -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    463      46   225484     237196   719    15.86   3228 powershell
```

```powershell
Get-MyProcess -Name PowerShell_Ise -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.2.9200.16384   6.2.9200.1638... C:\Windows\system32\WindowsPowerShell\...
```

<span data-ttu-id="78587-186">U kunt `@Args` in een functie gebruiken die expliciet para meters heeft gedeclareerd.</span><span class="sxs-lookup"><span data-stu-id="78587-186">You can use `@Args` in a function that has explicitly declared parameters.</span></span> <span data-ttu-id="78587-187">U kunt dit meer dan eens gebruiken in een functie, maar alle para meters die u invoert, worden door gegeven aan alle exemplaren van `@Args` , zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="78587-187">You can use it more than once in a function, but all parameters that you enter are passed to all instances of `@Args`, as shown in the following example.</span></span>

```powershell
function Get-MyCommand
{
    Param ([switch]$P, [switch]$C)
    if ($P) { Get-Process @Args }
    if ($C) { Get-Command @Args }
}

Get-MyCommand -P -C -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
408      28    75568      83176   620     1.33   1692 powershell

Path               : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Extension          : .exe
Definition         : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Visibility         : Public
OutputType         : {System.String}
Name               : powershell.exe
CommandType        : Application
ModuleName         :
Module             :
RemotingCapability : PowerShell
Parameters         :
ParameterSets      :
HelpUri            :
FileVersionInfo    : File:             C:\Windows\System32\WindowsPowerShell
                     \v1.0\powershell.exe
                     InternalName:     POWERSHELL
                     OriginalFilename: PowerShell.EXE.MUI
                     FileVersion:      10.0.14393.0 (rs1_release.160715-1616
                     FileDescription:  Windows PowerShell
                     Product:          Microsoft Windows Operating System
                     ProductVersion:   10.0.14393.0
                     Debug:            False
                     Patched:          False
                     PreRelease:       False
                     PrivateBuild:     False
                     SpecialBuild:     False
                     Language:         English (United States)
```

## <a name="notes"></a><span data-ttu-id="78587-188">Notities</span><span class="sxs-lookup"><span data-stu-id="78587-188">Notes</span></span>

<span data-ttu-id="78587-189">Als u een functie in een geavanceerde functie maakt met behulp van de kenmerken **CmdletBinding** of **para meter** , `$args` is de automatische variabele niet meer beschikbaar in de functie.</span><span class="sxs-lookup"><span data-stu-id="78587-189">If you make a function into an advanced function by using either the **CmdletBinding** or **Parameter** attributes, the `$args` automatic variable is no longer available in the function.</span></span> <span data-ttu-id="78587-190">Voor geavanceerde functies is expliciete parameter definitie vereist.</span><span class="sxs-lookup"><span data-stu-id="78587-190">Advanced functions require explicit parameter definition.</span></span>

<span data-ttu-id="78587-191">Power shell desired state Configuration (DSC) is niet ontworpen voor gebruik van splatting.</span><span class="sxs-lookup"><span data-stu-id="78587-191">PowerShell Desired State Configuration (DSC) was not designed to use splatting.</span></span>
<span data-ttu-id="78587-192">U kunt splatting niet gebruiken om waarden door te geven aan een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="78587-192">You cannot use splatting to pass values into a DSC resource.</span></span> <span data-ttu-id="78587-193">Zie Gael Colas ' article [pseudo-SPLATTING DSC resources (](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/)Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="78587-193">For more information, see Gael Colas' article [Pseudo-Splatting DSC Resources](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/).</span></span>

## <a name="see-also"></a><span data-ttu-id="78587-194">Zie ook</span><span class="sxs-lookup"><span data-stu-id="78587-194">See also</span></span>

[<span data-ttu-id="78587-195">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="78587-195">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="78587-196">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="78587-196">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="78587-197">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="78587-197">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="78587-198">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="78587-198">about_Parameters</span></span>](about_Parameters.md)
