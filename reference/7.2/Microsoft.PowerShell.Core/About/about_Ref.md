---
description: Hierin wordt beschreven hoe u een verwijzings type variabele maakt en gebruikt. U kunt verwijzings type variabelen gebruiken om een functie toe te staan de waarde te wijzigen van een variabele die wordt door gegeven.
Locale: en-US
ms.date: 08/24/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_ref?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Ref
ms.openlocfilehash: 5b966816c8ac1ef91e03c78378f57fa20b5697de
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705783"
---
# <a name="about-ref"></a><span data-ttu-id="5f700-104">Over Ref</span><span class="sxs-lookup"><span data-stu-id="5f700-104">About Ref</span></span>

## <a name="short-description"></a><span data-ttu-id="5f700-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="5f700-105">Short description</span></span>
<span data-ttu-id="5f700-106">Hierin wordt beschreven hoe u een verwijzings type variabele maakt en gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5f700-106">Describes how to create and use a reference type variable.</span></span> <span data-ttu-id="5f700-107">U kunt verwijzings type variabelen gebruiken om een functie toe te staan de waarde te wijzigen van een variabele die wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f700-107">You can use reference type variables to permit a function to change the value of a variable that is passed to it.</span></span>

## <a name="long-description"></a><span data-ttu-id="5f700-108">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="5f700-108">Long description</span></span>

<span data-ttu-id="5f700-109">U kunt variabelen door geven aan functies op *basis van verwijzing* of *op waarde*.</span><span class="sxs-lookup"><span data-stu-id="5f700-109">You can pass variables to functions *by reference* or *by value*.</span></span>

<span data-ttu-id="5f700-110">Wanneer u een variabele door geeft aan de hand van een *waarde*, wordt een kopie van de gegevens door gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f700-110">When you pass a variable *by value*, you are passing a copy of the data.</span></span>

<span data-ttu-id="5f700-111">In het volgende voor beeld wijzigt de functie de waarde van de variabele die hieraan wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f700-111">In the following example, the function changes the value of the variable passed to it.</span></span> <span data-ttu-id="5f700-112">In Power shell zijn integers waardetypen zodat ze door een waarde worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f700-112">In PowerShell, integers are value types so they are passed by value.</span></span>
<span data-ttu-id="5f700-113">Daarom is de waarde van `$var` ongewijzigd buiten het bereik van de functie.</span><span class="sxs-lookup"><span data-stu-id="5f700-113">Therefore, the value of `$var` is unchanged outside the scope of the function.</span></span>

```powershell
Function Test($data)
{
    $data = 3
}

$var = 10
Test -data $var
$var
```

```output
10
```

<span data-ttu-id="5f700-114">In het volgende voor beeld wordt een variabele met een `Hashtable` wordt door gegeven aan een functie.</span><span class="sxs-lookup"><span data-stu-id="5f700-114">In the following example, a variable containing a `Hashtable` is passed to a function.</span></span> <span data-ttu-id="5f700-115">`Hashtable` is een object type dat standaard wordt door gegeven aan de functie *door verwijzing*.</span><span class="sxs-lookup"><span data-stu-id="5f700-115">`Hashtable` is an object type so by default it is passed to the function *by reference*.</span></span>

<span data-ttu-id="5f700-116">Wanneer een variabele *door wordt door* gegeven, kan de functie de gegevens wijzigen en de wijziging blijft behouden nadat de functie is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5f700-116">When passing a variable *by reference*, the function can change the data and that change persists after the function executes.</span></span>

```powershell
Function Test($data)
{
    $data.Test = "New Text"
}

$var = @{}
Test -data $var
$var
```

```output
Name                           Value
----                           -----
Test                           New Text
```

<span data-ttu-id="5f700-117">De functie voegt een nieuw sleutel/waarde-paar toe dat zich buiten het bereik van de functie bevindt.</span><span class="sxs-lookup"><span data-stu-id="5f700-117">The function adds a new key-value pair that persists outside of the function's scope.</span></span>

### <a name="writing-functions-to-accept-reference-parameters"></a><span data-ttu-id="5f700-118">Functies schrijven om referentie parameters te accepteren</span><span class="sxs-lookup"><span data-stu-id="5f700-118">Writing functions to accept reference parameters</span></span>

<span data-ttu-id="5f700-119">U kunt uw functies coderen om een para meter als referentie te maken, ongeacht het type gegevens dat is door gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f700-119">You can code your functions to take a parameter as a reference, regardless of the type of data passed.</span></span> <span data-ttu-id="5f700-120">Hiervoor moet u het type para meters opgeven als `System.Management.Automation.PSReference` , of `[ref]` .</span><span class="sxs-lookup"><span data-stu-id="5f700-120">This requires that you specify the parameters type as `System.Management.Automation.PSReference`, or `[ref]`.</span></span>

<span data-ttu-id="5f700-121">Wanneer u verwijzingen gebruikt, moet u de `Value` eigenschap van het `System.Management.Automation.PSReference` type gebruiken om toegang te krijgen tot uw gegevens.</span><span class="sxs-lookup"><span data-stu-id="5f700-121">When using references, you must use the `Value` property of the `System.Management.Automation.PSReference` type to access your data.</span></span>

```powershell
Function Test([ref]$data)
{
    $data.Value = 3
}
```

<span data-ttu-id="5f700-122">Als u een variabele wilt door geven aan een para meter die een verwijzing verwacht, moet u uw variabele als referentie typen.</span><span class="sxs-lookup"><span data-stu-id="5f700-122">To pass a variable to a parameter that expects a reference, you must type cast your variable as a reference.</span></span>

> [!NOTE]
> <span data-ttu-id="5f700-123">De haken en haakjes zijn beide verplicht.</span><span class="sxs-lookup"><span data-stu-id="5f700-123">The brackets and parenthesis are BOTH required.</span></span>

```powershell
$var = 10
Test -data ([ref]$var)
$var
```

```output
3
```

### <a name="passing-references-to-net-methods"></a><span data-ttu-id="5f700-124">Verwijzingen naar .NET-methoden door geven</span><span class="sxs-lookup"><span data-stu-id="5f700-124">Passing references to .NET methods</span></span>

<span data-ttu-id="5f700-125">Voor sommige .NET-methoden moet u mogelijk een variabele door geven als referentie.</span><span class="sxs-lookup"><span data-stu-id="5f700-125">Some .NET methods may require you to pass a variable as a reference.</span></span> <span data-ttu-id="5f700-126">Wanneer de definitie van de methode gebruikmaakt van de tref woorden `in` , `out` of `ref` op basis van een para meter, wordt een verwijzing verwacht.</span><span class="sxs-lookup"><span data-stu-id="5f700-126">When the method's definition uses the keywords `in`, `out`, or `ref` on a parameter, it expects a reference.</span></span>

```powershell
[int] | Get-Member -Static -Name TryParse
```

```output
Name     MemberType Definition
----     ---------- ----------
TryParse Method     static bool TryParse(string s, [ref] int result)
```

<span data-ttu-id="5f700-127">De `TryParse` methode probeert een teken reeks te parseren als een geheel getal.</span><span class="sxs-lookup"><span data-stu-id="5f700-127">The `TryParse` method attempts to parse a string as an integer.</span></span> <span data-ttu-id="5f700-128">Als de methode is geslaagd, wordt geretourneerd `$true` en wordt het resultaat opgeslagen in de variabele die u hebt door gegeven als **verwijzing**.</span><span class="sxs-lookup"><span data-stu-id="5f700-128">If the method succeeds, it returns `$true`, and the result is stored in the variable you passed **by reference**.</span></span>

```
PS> $number = 0
PS> [int]::TryParse("15", ([ref]$number))
True
PS> $number
15
```

### <a name="references-and-scopes"></a><span data-ttu-id="5f700-129">Verwijzingen en bereiken</span><span class="sxs-lookup"><span data-stu-id="5f700-129">References and scopes</span></span>

<span data-ttu-id="5f700-130">Met verwijzingen kan de waarde van een variabele in het bovenliggende bereik worden gewijzigd binnen een onderliggend bereik.</span><span class="sxs-lookup"><span data-stu-id="5f700-130">References allow the value of a variable in the parent scope to be changed within a child scope.</span></span>

```powershell
# Create a value type variable.
$i = 0
# Create a reference type variable.
$iRef = [ref]0
# Invoke a scriptblock to attempt to change both values.
&{$i++;$iRef.Value++}
# Output the results.
"`$i = $i;`$iRef = $($iRef.Value)"
```

```output
$i = 0;$iRef = 1
```

<span data-ttu-id="5f700-131">Alleen de variabele van het verwijzings type is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="5f700-131">Only the reference type's variable was changed.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f700-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5f700-132">See also</span></span>

[<span data-ttu-id="5f700-133">about_Variables</span><span class="sxs-lookup"><span data-stu-id="5f700-133">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="5f700-134">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="5f700-134">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="5f700-135">about_Functions</span><span class="sxs-lookup"><span data-stu-id="5f700-135">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="5f700-136">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="5f700-136">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="5f700-137">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="5f700-137">about_Scopes</span></span>](about_scopes.md)
