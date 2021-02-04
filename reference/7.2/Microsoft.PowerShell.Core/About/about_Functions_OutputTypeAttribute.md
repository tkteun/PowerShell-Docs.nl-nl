---
description: Beschrijft een kenmerk dat het type object rapporteert dat door de functie wordt geretourneerd.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_OutputTypeAttribute
ms.openlocfilehash: 82f1615c4a2fe2a24f104d8e5637103dea6e5a0a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706099"
---
# <a name="about-functions-outputtypeattribute"></a><span data-ttu-id="dbc00-103">Over functies OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="dbc00-103">About Functions OutputTypeAttribute</span></span>

## <a name="short-description"></a><span data-ttu-id="dbc00-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="dbc00-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="dbc00-105">Beschrijft een kenmerk dat het type object rapporteert dat door de functie wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="dbc00-105">Describes an attribute that reports the type of object that the function returns.</span></span>

## <a name="long-description"></a><span data-ttu-id="dbc00-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="dbc00-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="dbc00-107">Het kenmerk output type geeft de .NET-typen objecten weer die door de functies worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="dbc00-107">The OutputType attribute lists the .NET types of objects that the functions returns.</span></span> <span data-ttu-id="dbc00-108">U kunt de optionele ParameterSetName-para meter gebruiken om verschillende uitvoer typen voor elke parameterset weer te geven.</span><span class="sxs-lookup"><span data-stu-id="dbc00-108">You can use its optional ParameterSetName parameter to list different output types for each parameter set.</span></span>

<span data-ttu-id="dbc00-109">Het kenmerk output type wordt ondersteund voor eenvoudige en geavanceerde functies.</span><span class="sxs-lookup"><span data-stu-id="dbc00-109">The OutputType attribute is supported on simple and advanced functions.</span></span> <span data-ttu-id="dbc00-110">Het is onafhankelijk van het kenmerk CmdletBinding.</span><span class="sxs-lookup"><span data-stu-id="dbc00-110">It is independent of the CmdletBinding attribute.</span></span>

<span data-ttu-id="dbc00-111">Het kenmerk output type levert de waarde van de eigenschap output type van het object **System. Management. Automation. FunctionInfo** dat door de `Get-Command` cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="dbc00-111">The OutputType attribute provides the value of the OutputType property of the **System.Management.Automation.FunctionInfo** object that the `Get-Command` cmdlet returns.</span></span>

<span data-ttu-id="dbc00-112">De waarde van het kenmerk output type is alleen een documentatie opmerking.</span><span class="sxs-lookup"><span data-stu-id="dbc00-112">The OutputType attribute value is only a documentation note.</span></span> <span data-ttu-id="dbc00-113">Het is niet afgeleid van de functie code of vergeleken met de daad werkelijke functie-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="dbc00-113">It is not derived from the function code or compared to the actual function output.</span></span> <span data-ttu-id="dbc00-114">De waarde kan als zodanig onjuist zijn.</span><span class="sxs-lookup"><span data-stu-id="dbc00-114">As such, the value might be inaccurate.</span></span>

## <a name="syntax"></a><span data-ttu-id="dbc00-115">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="dbc00-115">SYNTAX</span></span>

<span data-ttu-id="dbc00-116">Het kenmerk output type van functions heeft de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="dbc00-116">The OutputType attribute of functions has the following syntax:</span></span>

```
[OutputType([<TypeLiteral>], ParameterSetName="<Name>")]
[OutputType("<TypeNameString>", ParameterSetName="<Name>")]
```

<span data-ttu-id="dbc00-117">De para meter **ParameterSetName** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="dbc00-117">The **ParameterSetName** parameter is optional.</span></span>

<span data-ttu-id="dbc00-118">U kunt meerdere typen in het kenmerk output type vermelden.</span><span class="sxs-lookup"><span data-stu-id="dbc00-118">You can list multiple types in the OutputType attribute.</span></span>

```
[OutputType([<Type1>],[<Type2>],[<Type3>])]
```

<span data-ttu-id="dbc00-119">U kunt de para meter **ParameterSetName** gebruiken om aan te geven dat verschillende parameter sets verschillende typen retour neren.</span><span class="sxs-lookup"><span data-stu-id="dbc00-119">You can use the **ParameterSetName** parameter to indicate that different parameter sets return different types.</span></span>

```
[OutputType([<Type1>], ParameterSetName=("<Set1>","<Set2>"))]
[OutputType([<Type2>], ParameterSetName="<Set3>")]
```

<span data-ttu-id="dbc00-120">Plaats de instructies output type-kenmerk in de lijst met kenmerken die voorafgaat aan de `Param` instructie.</span><span class="sxs-lookup"><span data-stu-id="dbc00-120">Place the OutputType attribute statements in the attributes list that precedes the `Param` statement.</span></span>

<span data-ttu-id="dbc00-121">In het volgende voor beeld wordt de plaatsing van het kenmerk output type in een eenvoudige functie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="dbc00-121">The following example shows the placement of the OutputType attribute in a simple function.</span></span>

```powershell
function SimpleFunction2
{
  [OutputType([<Type>])]
  Param ($Parameter1)

  <function body>
}
```

<span data-ttu-id="dbc00-122">In het volgende voor beeld wordt de plaatsing van het kenmerk output type in geavanceerde functies weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="dbc00-122">The following example shows the placement of the OutputType attribute in advanced functions.</span></span>

```powershell
function AdvancedFunction1
{
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}

function AdvancedFunction2
{
  [CmdletBinding(SupportsShouldProcess=<Boolean>)]
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}
```

## <a name="examples"></a><span data-ttu-id="dbc00-123">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="dbc00-123">EXAMPLES</span></span>

### <a name="example-1-create-a-function-that-has-the-outputtype-of-string"></a><span data-ttu-id="dbc00-124">Voor beeld 1: een functie maken die het output type van de teken reeks bevat</span><span class="sxs-lookup"><span data-stu-id="dbc00-124">Example 1: Create a function that has the OutputType of String</span></span>

```powershell
function Send-Greeting
{
  [OutputType([String])]
  Param ($Name)

  "Hello, $Name"
}
```

<span data-ttu-id="dbc00-125">Als u de resulterende eigenschap van het uitvoer type wilt zien, gebruikt u de `Get-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dbc00-125">To see the resulting output type property, use the `Get-Command` cmdlet.</span></span>

```powershell
(Get-Command Send-Greeting).OutputType
```

```Output
Name                                               Type
----                                               ----
System.String                                      System.String
```

### <a name="example-2-use-the-output-attribute-to-indicate-dynamic-output-types"></a><span data-ttu-id="dbc00-126">Voor beeld 2: het uitvoer kenmerk gebruiken om dynamische uitvoer typen aan te duiden</span><span class="sxs-lookup"><span data-stu-id="dbc00-126">Example 2: Use the Output attribute to indicate dynamic output types</span></span>

<span data-ttu-id="dbc00-127">De volgende geavanceerde functie maakt gebruik van het kenmerk output type om aan te geven dat de functie verschillende typen retourneert, afhankelijk van de ingestelde para meters in de functie opdracht.</span><span class="sxs-lookup"><span data-stu-id="dbc00-127">The following advanced function uses the OutputType attribute to indicate that the function returns different types depending on the parameter set used in the function command.</span></span>

```powershell
function Get-User
{
  [CmdletBinding(DefaultParameterSetName="ID")]

  [OutputType("System.Int32", ParameterSetName="ID")]
  [OutputType([String], ParameterSetName="Name")]

  Param (
    [parameter(Mandatory=$true, ParameterSetName="ID")]
    [Int[]]
    $UserID,

    [parameter(Mandatory=$true, ParameterSetName="Name")]
    [String[]]
    $UserName
  )

  <function body>
}
```

### <a name="example-3-shows-when-an-actual-output-differs-from-the-outputtype"></a><span data-ttu-id="dbc00-128">Voor beeld 3: toont wanneer een werkelijke uitvoer afwijkt van het output type</span><span class="sxs-lookup"><span data-stu-id="dbc00-128">Example 3: Shows when an actual output differs from the OutputType</span></span>

<span data-ttu-id="dbc00-129">In het volgende voor beeld ziet u dat de waarde van de eigenschap uitvoer type de waarde van het kenmerk output item weergeeft, zelfs wanneer deze onjuist is.</span><span class="sxs-lookup"><span data-stu-id="dbc00-129">The following example demonstrates that the output type property value displays the value of the OutputType attribute, even when it is inaccurate.</span></span>

<span data-ttu-id="dbc00-130">De `Get-Time` functie retourneert een teken reeks die de korte vorm van de tijd in een datetime-object bevat.</span><span class="sxs-lookup"><span data-stu-id="dbc00-130">The `Get-Time` function returns a string that contains the short form of the time in any DateTime object.</span></span> <span data-ttu-id="dbc00-131">Met het kenmerk output type wordt echter gerapporteerd dat er een **System. datetime** -object wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="dbc00-131">However, the OutputType attribute reports that it returns a **System.DateTime** object.</span></span>

```powershell
function Get-Time
{
  [OutputType([DateTime])]
  Param (
    [parameter(Mandatory=$true)]
    [Datetime]$DateTime
  )

  $DateTime.ToShortTimeString()
}
```

<span data-ttu-id="dbc00-132">De- `GetType()` methode bevestigt dat de functie een teken reeks retourneert.</span><span class="sxs-lookup"><span data-stu-id="dbc00-132">The `GetType()` method confirms that the function returns a string.</span></span>

```powershell
(Get-Time -DateTime (Get-Date)).GetType().FullName
```

```Output
System.String
```

<span data-ttu-id="dbc00-133">De eigenschap output type, die de waarde van het kenmerk output type krijgt, rapporteert dat de functie een **DateTime** -object retourneert.</span><span class="sxs-lookup"><span data-stu-id="dbc00-133">However, the OutputType property, which gets its value from the OutputType attribute, reports that the function returns a **DateTime** object.</span></span>

```powershell
(Get-Command Get-Time).OutputType
```

```Output
Name                                      Type
----                                      ----
System.DateTime                           System.DateTime
```

### <a name="example-4-a-function--that-shouldnt-have-output"></a><span data-ttu-id="dbc00-134">Voor beeld 4: een functie die geen uitvoer mag hebben</span><span class="sxs-lookup"><span data-stu-id="dbc00-134">Example 4: A function  that shouldn't have output</span></span>

<span data-ttu-id="dbc00-135">In het volgende voor beeld ziet u een aangepaste functie die moet worden uitgevoerd, maar die geen actie retourneert.</span><span class="sxs-lookup"><span data-stu-id="dbc00-135">The following example shows a custom function that should perform and action but not return anything.</span></span>

```powershell
function Invoke-Notepad
{
  [OutputType([System.Void])]
  Param ()
  & notepad.exe | Out-Null
}
```

## <a name="notes"></a><span data-ttu-id="dbc00-136">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="dbc00-136">NOTES</span></span>

<span data-ttu-id="dbc00-137">De waarde van de eigenschap output type van een **FunctionInfo** -object is een matrix van **System. Management. Automation. PSTypeName** -objecten, die elk de eigenschappen name en type hebben.</span><span class="sxs-lookup"><span data-stu-id="dbc00-137">The value of the OutputType property of a **FunctionInfo** object is an array of **System.Management.Automation.PSTypeName** objects, each of which have Name and Type properties.</span></span>

<span data-ttu-id="dbc00-138">Als u alleen de naam van elk uitvoer type wilt ophalen, gebruikt u een opdracht met de volgende notatie.</span><span class="sxs-lookup"><span data-stu-id="dbc00-138">To get only the name of each output type, use a command with the following format.</span></span>

```powershell
(Get-Command Get-Time).OutputType | ForEach {$_.Name}
```

<span data-ttu-id="dbc00-139">De waarde van de eigenschap output type kan null zijn.</span><span class="sxs-lookup"><span data-stu-id="dbc00-139">The value of the OutputType property can be null.</span></span> <span data-ttu-id="dbc00-140">Gebruik een null-waarde wanneer de uitvoer geen .NET-type is, zoals een **WMI-** object of een opmaak weergave van een object.</span><span class="sxs-lookup"><span data-stu-id="dbc00-140">Use a null value when the output is a not a .NET type, such as a **WMI** object or a formatted view of an object.</span></span>

## <a name="see-also"></a><span data-ttu-id="dbc00-141">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="dbc00-141">SEE ALSO</span></span>

[<span data-ttu-id="dbc00-142">about_Functions</span><span class="sxs-lookup"><span data-stu-id="dbc00-142">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="dbc00-143">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="dbc00-143">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="dbc00-144">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="dbc00-144">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="dbc00-145">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="dbc00-145">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="dbc00-146">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="dbc00-146">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)
