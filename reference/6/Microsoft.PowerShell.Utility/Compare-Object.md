---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/compare-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compare-Object
ms.openlocfilehash: c72cde8e626993726ae1a52206c88e20c3a7c588
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "93253225"
---
# <span data-ttu-id="e8512-103">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="e8512-103">Compare-Object</span></span>

## <span data-ttu-id="e8512-104">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="e8512-104">Synopsis</span></span>
<span data-ttu-id="e8512-105">Vergelijkt twee sets met objecten.</span><span class="sxs-lookup"><span data-stu-id="e8512-105">Compares two sets of objects.</span></span>

## <span data-ttu-id="e8512-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e8512-106">Syntax</span></span>

```
Compare-Object [-ReferenceObject] <PSObject[]> [-DifferenceObject] <PSObject[]>
 [-SyncWindow <Int32>] [-Property <Object[]>] [-ExcludeDifferent] [-IncludeEqual] [-PassThru]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="e8512-107">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e8512-107">Description</span></span>

<span data-ttu-id="e8512-108">De `Compare-Object` cmdlet vergelijkt twee sets met objecten.</span><span class="sxs-lookup"><span data-stu-id="e8512-108">The `Compare-Object` cmdlet compares two sets of objects.</span></span> <span data-ttu-id="e8512-109">Een set van objecten is de **verwijzing** en de andere set met objecten is het **verschil**.</span><span class="sxs-lookup"><span data-stu-id="e8512-109">One set of objects is the **reference** , and the other set of objects is the **difference**.</span></span>

<span data-ttu-id="e8512-110">`Compare-Object` Hiermee wordt gecontroleerd op beschik bare methoden voor het vergelijken van een geheel object.</span><span class="sxs-lookup"><span data-stu-id="e8512-110">`Compare-Object` checks for available methods of comparing a whole object.</span></span> <span data-ttu-id="e8512-111">Als er geen geschikte methode kan worden gevonden, worden de **toString ()** -methoden van de invoer objecten aangeroepen en worden de teken reeks resultaten vergeleken.</span><span class="sxs-lookup"><span data-stu-id="e8512-111">If it can't find a suitable method, it calls the **ToString()** methods of the input objects and compares the string results.</span></span> <span data-ttu-id="e8512-112">U kunt een of meer eigenschappen opgeven die moeten worden gebruikt voor de vergelijking.</span><span class="sxs-lookup"><span data-stu-id="e8512-112">You can provide one or more properties to be used for comparison.</span></span> <span data-ttu-id="e8512-113">Wanneer eigenschappen worden gegeven, vergelijkt de cmdlet alleen de waarden van die eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="e8512-113">When properties are provided, the cmdlet compares the values of those properties only.</span></span>

<span data-ttu-id="e8512-114">Het resultaat van de vergelijking geeft aan of een eigenschaps waarde alleen voor komt in het **verwijzings** object ( `<=` ) of alleen in het object **diff** ( `=>` ).</span><span class="sxs-lookup"><span data-stu-id="e8512-114">The result of the comparison indicates whether a property value appeared only in the **reference** object (`<=`) or only in the **difference** object (`=>`).</span></span> <span data-ttu-id="e8512-115">Als de para meter **IncludeEqual** wordt gebruikt, ( `==` ) geeft aan dat de waarde in beide objecten is.</span><span class="sxs-lookup"><span data-stu-id="e8512-115">If the **IncludeEqual** parameter is used, (`==`) indicates the value is in both objects.</span></span>

<span data-ttu-id="e8512-116">Als de **verwijzings** -of de **verschillen** objecten Null ( `$null` ) zijn, wordt `Compare-Object` een afsluit fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="e8512-116">If the **reference** or the **difference** objects are null (`$null`), `Compare-Object` generates a terminating error.</span></span>

<span data-ttu-id="e8512-117">Enkele voor beelden gebruiken splatting om de regel lengte van de code voorbeelden te reduceren.</span><span class="sxs-lookup"><span data-stu-id="e8512-117">Some examples use splatting to reduce the line length of the code samples.</span></span> <span data-ttu-id="e8512-118">Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e8512-118">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="e8512-119">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="e8512-119">Examples</span></span>

### <span data-ttu-id="e8512-120">Voor beeld 1: de inhoud van twee tekst bestanden vergelijken</span><span class="sxs-lookup"><span data-stu-id="e8512-120">Example 1 - Compare the content of two text files</span></span>

<span data-ttu-id="e8512-121">In dit voor beeld wordt de inhoud van twee tekst bestanden vergeleken.</span><span class="sxs-lookup"><span data-stu-id="e8512-121">This example compares the contents of two text files.</span></span> <span data-ttu-id="e8512-122">In het voor beeld worden de volgende twee tekst bestanden gebruikt, met elke waarde op een afzonderlijke regel.</span><span class="sxs-lookup"><span data-stu-id="e8512-122">The example uses the following two text files, with each value on a separate line.</span></span>

- <span data-ttu-id="e8512-123">`Testfile1.txt` bevat de waarden: hond, Squirrel en vogel.</span><span class="sxs-lookup"><span data-stu-id="e8512-123">`Testfile1.txt` contains the values: dog, squirrel, and bird.</span></span>
- <span data-ttu-id="e8512-124">`Testfile2.txt` bevat de waarden: kat, vogel en racoon.</span><span class="sxs-lookup"><span data-stu-id="e8512-124">`Testfile2.txt` contains the values: cat, bird, and racoon.</span></span>

<span data-ttu-id="e8512-125">In de uitvoer worden alleen de lijnen weer gegeven die verschillen tussen de bestanden.</span><span class="sxs-lookup"><span data-stu-id="e8512-125">The output displays only the lines that are different between the files.</span></span> <span data-ttu-id="e8512-126">`Testfile1.txt` is het **referentie** object ( `<=` ) en `Testfile2.txt` is het object **diff** ( `=>` ).</span><span class="sxs-lookup"><span data-stu-id="e8512-126">`Testfile1.txt` is the **reference** object (`<=`) and `Testfile2.txt`is the **difference** object (`=>`).</span></span> <span data-ttu-id="e8512-127">Regels met inhoud die worden weer gegeven in beide bestanden, worden niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e8512-127">Lines with content that appear in both files aren't displayed.</span></span>

```powershell
Compare-Object -ReferenceObject (Get-Content -Path C:\Test\Testfile1.txt) -DifferenceObject (Get-Content -Path C:\Test\Testfile2.txt)
```

```Output
InputObject SideIndicator
----------- -------------
cat         =>
racoon      =>
dog         <=
squirrel    <=
```

### <span data-ttu-id="e8512-128">Voor beeld 2: elke regel met inhoud vergelijken en de verschillen uitsluiten</span><span class="sxs-lookup"><span data-stu-id="e8512-128">Example 2 - Compare each line of content and exclude the differences</span></span>

<span data-ttu-id="e8512-129">In dit voor beeld worden de para meters **IncludeEqual** en **ExcludeDifferent** gebruikt voor het vergelijken van elke regel met inhoud in twee tekst bestanden.</span><span class="sxs-lookup"><span data-stu-id="e8512-129">This example uses the **IncludeEqual** and **ExcludeDifferent** parameters to compare each line of content in two text files.</span></span>

<span data-ttu-id="e8512-130">Omdat de opdracht de para meter **ExcludeDifferent** gebruikt, bevat de uitvoer alleen regels die in beide bestanden zijn opgenomen, zoals wordt weer gegeven door de **SideIndicator** ( `==` ).</span><span class="sxs-lookup"><span data-stu-id="e8512-130">Because the command uses the **ExcludeDifferent** parameter, the output only contains lines contained in both files, as shown by the **SideIndicator** (`==`).</span></span>

```powershell
$objects = @{
  ReferenceObject = (Get-Content -Path C:\Test\Testfile1.txt)
  DifferenceObject = (Get-Content -Path C:\Test\Testfile2.txt)
}
Compare-Object @objects -IncludeEqual -ExcludeDifferent
```

```Output
InputObject SideIndicator
----------- -------------
bird        ==
```

<a id="ex3" />

### <span data-ttu-id="e8512-131">Voor beeld 3: het verschil weer geven bij gebruik van de para meter PassThru</span><span class="sxs-lookup"><span data-stu-id="e8512-131">Example 3 - Show the difference when using the PassThru parameter</span></span>

<span data-ttu-id="e8512-132">Normaal gesp roken `Compare-Object` retourneert een **PSCustomObject** -type met de volgende eigenschappen:</span><span class="sxs-lookup"><span data-stu-id="e8512-132">Normally, `Compare-Object` returns a **PSCustomObject** type with the following properties:</span></span>

- <span data-ttu-id="e8512-133">De **input object** die wordt vergeleken</span><span class="sxs-lookup"><span data-stu-id="e8512-133">The **InputObject** being compared</span></span>
- <span data-ttu-id="e8512-134">De eigenschap **SideIndicator** geeft aan met welk invoer object de uitvoer hoort</span><span class="sxs-lookup"><span data-stu-id="e8512-134">The **SideIndicator** property showing which input object the output belongs to</span></span>

<span data-ttu-id="e8512-135">Wanneer u de para meter **PassThru** gebruikt, wordt het **type** van het object niet gewijzigd, maar het exemplaar van het geretourneerde object heeft een toegevoegd **NoteProperty** met de naam **SideIndicator**.</span><span class="sxs-lookup"><span data-stu-id="e8512-135">When you use the **PassThru** parameter, the **Type** of the object is not changed but the instance of the object returned has an added **NoteProperty** named **SideIndicator**.</span></span> <span data-ttu-id="e8512-136">**SideIndicator** laat zien met welk invoer object de uitvoer behoort.</span><span class="sxs-lookup"><span data-stu-id="e8512-136">**SideIndicator** shows which input object the output belongs to.</span></span>

<span data-ttu-id="e8512-137">In de volgende voor beelden ziet u de verschillende uitvoer typen.</span><span class="sxs-lookup"><span data-stu-id="e8512-137">The following examples shows the different output types.</span></span>

```powershell
$a = $True
Compare-Object -IncludeEqual $a $a
(Compare-Object -IncludeEqual $a $a) | Get-Member
```

```Output
InputObject SideIndicator
----------- -------------
       True ==

   TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
InputObject   NoteProperty System.Boolean InputObject=True
SideIndicator NoteProperty string SideIndicator===
```

```powershell
Compare-Object -IncludeEqual $a $a -PassThru
(Compare-Object -IncludeEqual $a $a -PassThru) | Get-Member
```

```Output
True

   TypeName: System.Boolean
Name          MemberType   Definition
----          ----------   ----------
CompareTo     Method       int CompareTo(System.Object obj), int CompareTo(bool value), int IComparable.CompareTo(Syst
Equals        Method       bool Equals(System.Object obj), bool Equals(bool obj), bool IEquatable[bool].Equals(bool ot
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
GetTypeCode   Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean     Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte        Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar        Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime    Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal     Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble      Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16       Method       short IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32       Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64       Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte       Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle      Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString      Method       string ToString(), string ToString(System.IFormatProvider provider), string IConvertible.To
ToType        Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16      Method       ushort IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32      Method       uint IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64      Method       ulong IConvertible.ToUInt64(System.IFormatProvider provider)
TryFormat     Method       bool TryFormat(System.Span[char] destination, [ref] int charsWritten)
SideIndicator NoteProperty string SideIndicator===
```

<span data-ttu-id="e8512-138">Wanneer u **PassThru** gebruikt, wordt het oorspronkelijke object type ( **System. Boolean** ) geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e8512-138">When using **PassThru** , the original object type ( **System.Boolean** ) is returned.</span></span> <span data-ttu-id="e8512-139">U ziet hoe de uitvoer die wordt weer gegeven door de standaard indeling voor **System. Boolean** -objecten, de eigenschap **SideIndicator** niet weergeeft.</span><span class="sxs-lookup"><span data-stu-id="e8512-139">Note how the output displayed by the default format for **System.Boolean** objects didn't display the **SideIndicator** property.</span></span> <span data-ttu-id="e8512-140">Het geretourneerde **System. Boolean** -object heeft echter het toegevoegde **NoteProperty**.</span><span class="sxs-lookup"><span data-stu-id="e8512-140">However, the returned **System.Boolean** object has the added **NoteProperty**.</span></span>

### <span data-ttu-id="e8512-141">Voor beeld 4: twee eenvoudige objecten vergelijken met eigenschappen</span><span class="sxs-lookup"><span data-stu-id="e8512-141">Example 4 - Compare two simple objects using properties</span></span>

<span data-ttu-id="e8512-142">In dit voor beeld vergelijken we twee verschillende teken reeksen die dezelfde lengte hebben.</span><span class="sxs-lookup"><span data-stu-id="e8512-142">In this example, we compare two different string that have the same length.</span></span>

```powershell
Compare-Object -ReferenceObject 'abc' -DifferenceObject 'xyz' -Property Length -IncludeEqual
```

```Output
Length SideIndicator
------ -------------
     3 ==
```

### <span data-ttu-id="e8512-143">Voor beeld 5: complexe objecten vergelijken met eigenschappen</span><span class="sxs-lookup"><span data-stu-id="e8512-143">Example 5 - Comparing complex objects using properties</span></span>

<span data-ttu-id="e8512-144">In dit voor beeld ziet u het gedrag bij het vergelijken van complexe objecten.</span><span class="sxs-lookup"><span data-stu-id="e8512-144">This example shows the behavior when comparing complex objects.</span></span> <span data-ttu-id="e8512-145">In dit voor beeld slaan we twee verschillende proces objecten op voor verschillende instanties van Power shell.</span><span class="sxs-lookup"><span data-stu-id="e8512-145">In this example we store two different process objects for different instances of PowerShell.</span></span> <span data-ttu-id="e8512-146">Beide variabelen bevatten proces objecten met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="e8512-146">Both variables contain process objects with the same name.</span></span> <span data-ttu-id="e8512-147">Wanneer de objecten worden vergeleken zonder de para meter **Property** op te geven, beschouwt de cmdlet dat de objecten gelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="e8512-147">When the objects are compared without specifying the **Property** parameter, the cmdlet considers the objects to be equal.</span></span> <span data-ttu-id="e8512-148">U ziet dat de waarde van **input object** gelijk is aan het resultaat van de methode **toString ()** .</span><span class="sxs-lookup"><span data-stu-id="e8512-148">Notice that the value of the **InputObject** is the same as the result of the **ToString()** method.</span></span> <span data-ttu-id="e8512-149">Omdat de klasse **System. Diagnostics. process** niet de interface **IComparable** heeft, converteert de cmdlet de objecten naar teken reeksen en vergelijkt de resultaten.</span><span class="sxs-lookup"><span data-stu-id="e8512-149">Since the **System.Diagnostics.Process** class does not have the **IComparable** interface, the cmdlet converts the objects to strings then compares the results.</span></span>

```powershell
PS> Get-Process pwsh

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    101   123.32     139.10      35.81   11168   1 pwsh
     89   107.55      66.97      11.44   17600   1 pwsh

PS> $a = Get-Process -Id 11168
PS> $b = Get-Process -Id 17600
PS> $a.ToString()
System.Diagnostics.Process (pwsh)
PS> $b.ToString()
System.Diagnostics.Process (pwsh)
PS> Compare-Object $a $b -IncludeEqual

InputObject                       SideIndicator
-----------                       -------------
System.Diagnostics.Process (pwsh) ==

PS> Compare-Object $a $b -Property ProcessName, Id, CPU

ProcessName    Id       CPU SideIndicator
-----------    --       --- -------------
pwsh        17600   11.4375 =>
pwsh        11168 36.203125 <=
```

<span data-ttu-id="e8512-150">Wanneer u de eigenschappen opgeeft die moeten worden vergeleken, worden de verschillen in de cmdlet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e8512-150">When you specify properties to be compared, the cmdlet shows the differences.</span></span>

### <span data-ttu-id="e8512-151">Voor beeld 6: complexe objecten vergelijken die IComparable implementeren</span><span class="sxs-lookup"><span data-stu-id="e8512-151">Example 6 - Comparing complex objects that implement IComparable</span></span>

<span data-ttu-id="e8512-152">Als het object **icomparable** implementeert, zoekt de cmdlet naar manieren om de objecten te vergelijken. Als de objecten verschillend zijn, wordt het object **verschil** geconverteerd naar het type van de **ReferenceObject** en vervolgens vergeleken.</span><span class="sxs-lookup"><span data-stu-id="e8512-152">If the object implements **IComparable** , the cmdlet searches for ways to compare the objects.If the objects are different types, the **Difference** object is converted to the type of the **ReferenceObject** then compared.</span></span>

<span data-ttu-id="e8512-153">In dit voor beeld vergelijkt u een teken reeks naar een **time span** -object.</span><span class="sxs-lookup"><span data-stu-id="e8512-153">In this example, we are comparing a string to a **TimeSpan** object.</span></span> <span data-ttu-id="e8512-154">In het eerste geval wordt de teken reeks geconverteerd naar een **time span** zodat de objecten gelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="e8512-154">In the first case, the string is converted to a **TimeSpan** so the objects are equal.</span></span>

```powershell
Compare-Object ([TimeSpan]"0:0:1") "0:0:1" -IncludeEqual
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    ==
```

```powershell
Compare-Object "0:0:1" ([TimeSpan]"0:0:1")
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    =>
0:0:1       <=
```

<span data-ttu-id="e8512-155">In het tweede geval wordt de **time span** geconverteerd naar een teken reeks zodat het object verschillend is.</span><span class="sxs-lookup"><span data-stu-id="e8512-155">In the second case, the **TimeSpan** is converted to a string so the object are different.</span></span>

## <span data-ttu-id="e8512-156">Parameters</span><span class="sxs-lookup"><span data-stu-id="e8512-156">Parameters</span></span>

### <span data-ttu-id="e8512-157">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="e8512-157">-CaseSensitive</span></span>

<span data-ttu-id="e8512-158">Geeft aan dat vergelijkingen hoofdletter gevoelig moeten zijn.</span><span class="sxs-lookup"><span data-stu-id="e8512-158">Indicates that comparisons should be case-sensitive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8512-159">-Cultuur</span><span class="sxs-lookup"><span data-stu-id="e8512-159">-Culture</span></span>

<span data-ttu-id="e8512-160">Hiermee geeft u de cultuur op die moet worden gebruikt voor vergelijkingen.</span><span class="sxs-lookup"><span data-stu-id="e8512-160">Specifies the culture to use for comparisons.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8512-161">-DifferenceObject</span><span class="sxs-lookup"><span data-stu-id="e8512-161">-DifferenceObject</span></span>

<span data-ttu-id="e8512-162">Hiermee geeft u de objecten die worden vergeleken met de **referentie** objecten.</span><span class="sxs-lookup"><span data-stu-id="e8512-162">Specifies the objects that are compared to the **reference** objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e8512-163">-ExcludeDifferent</span><span class="sxs-lookup"><span data-stu-id="e8512-163">-ExcludeDifferent</span></span>

<span data-ttu-id="e8512-164">Geeft aan dat met deze cmdlet alleen de kenmerken van vergeleken objecten worden weer gegeven die gelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="e8512-164">Indicates that this cmdlet displays only the characteristics of compared objects that are equal.</span></span> <span data-ttu-id="e8512-165">De verschillen tussen de objecten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="e8512-165">The differences between the objects are discarded.</span></span>

<span data-ttu-id="e8512-166">Gebruik **ExcludeDifferent** met **IncludeEqual** om alleen de lijnen weer te geven die overeenkomen met de objecten **Reference** en **diff** .</span><span class="sxs-lookup"><span data-stu-id="e8512-166">Use **ExcludeDifferent** with **IncludeEqual** to display only the lines that match between the **reference** and **difference** objects.</span></span>

<span data-ttu-id="e8512-167">Als **ExcludeDifferent** is opgegeven zonder **IncludeEqual** , is er geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="e8512-167">If **ExcludeDifferent** is specified without **IncludeEqual** , there's no output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8512-168">-IncludeEqual</span><span class="sxs-lookup"><span data-stu-id="e8512-168">-IncludeEqual</span></span>

<span data-ttu-id="e8512-169">**IncludeEqual** geeft de overeenkomsten tussen de objecten **verwijzing** en **verschil** weer.</span><span class="sxs-lookup"><span data-stu-id="e8512-169">**IncludeEqual** displays the matches between the **reference** and **difference** objects.</span></span>

<span data-ttu-id="e8512-170">De uitvoer bevat standaard ook de verschillen tussen de objecten **verwijzing** en **verschil** .</span><span class="sxs-lookup"><span data-stu-id="e8512-170">By default, the output also includes the differences between the **reference** and **difference** objects.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8512-171">-PassThru</span><span class="sxs-lookup"><span data-stu-id="e8512-171">-PassThru</span></span>

<span data-ttu-id="e8512-172">Wanneer u de para meter **PassThru** gebruikt, `Compare-Object` wordt de **PSCustomObject** -wrapper rond de vergeleken objecten wegge laten en worden de verschillende objecten ongewijzigd geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e8512-172">When you use the **PassThru** parameter, `Compare-Object` omits the **PSCustomObject** wrapper around the compared objects and returns the differing objects, unchanged.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8512-173">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="e8512-173">-Property</span></span>

<span data-ttu-id="e8512-174">Hiermee geeft u een matrix met eigenschappen van de objecten **Reference** en **diff** op die u wilt vergelijken.</span><span class="sxs-lookup"><span data-stu-id="e8512-174">Specifies an array of properties of the **reference** and **difference** objects to compare.</span></span>

<span data-ttu-id="e8512-175">De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="e8512-175">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="e8512-176">De berekende eigenschap kan een script blok of een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="e8512-176">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="e8512-177">Geldige sleutel-waardeparen zijn:</span><span class="sxs-lookup"><span data-stu-id="e8512-177">Valid key-value pairs are:</span></span>

- <span data-ttu-id="e8512-178">Expressie- `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="e8512-178">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="e8512-179">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e8512-179">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8512-180">-ReferenceObject</span><span class="sxs-lookup"><span data-stu-id="e8512-180">-ReferenceObject</span></span>

<span data-ttu-id="e8512-181">Hiermee wordt een matrix met objecten opgegeven die worden gebruikt als verwijzing voor de vergelijking.</span><span class="sxs-lookup"><span data-stu-id="e8512-181">Specifies an array of objects used as a reference for comparison.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8512-182">-SyncWindow</span><span class="sxs-lookup"><span data-stu-id="e8512-182">-SyncWindow</span></span>

<span data-ttu-id="e8512-183">Hiermee geeft u het aantal aangrenzende objecten op dat `Compare-Object` inspecteert terwijl er wordt gezocht naar een overeenkomst in een verzameling objecten.</span><span class="sxs-lookup"><span data-stu-id="e8512-183">Specifies the number of adjacent objects that `Compare-Object` inspects while looking for a match in a collection of objects.</span></span> <span data-ttu-id="e8512-184">`Compare-Object` Hiermee worden aangrenzende objecten onderzocht wanneer het object niet op dezelfde positie in een verzameling wordt gevonden.</span><span class="sxs-lookup"><span data-stu-id="e8512-184">`Compare-Object` examines adjacent objects when it doesn't find the object in the same position in a collection.</span></span> <span data-ttu-id="e8512-185">De standaard waarde is `[Int32]::MaxValue` , wat betekent dat `Compare-Object` de volledige object verzameling onderzoekt.</span><span class="sxs-lookup"><span data-stu-id="e8512-185">The default value is `[Int32]::MaxValue`, which means that `Compare-Object` examines the entire object collection.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: [Int32]::MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8512-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e8512-186">CommonParameters</span></span>

<span data-ttu-id="e8512-187">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e8512-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e8512-188">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e8512-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e8512-189">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="e8512-189">Inputs</span></span>

### <span data-ttu-id="e8512-190">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="e8512-190">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="e8512-191">U kunt een object naar de **DifferenceObject** -para meter verzenden via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="e8512-191">You can send an object down the pipeline to the **DifferenceObject** parameter.</span></span>

## <span data-ttu-id="e8512-192">Uitvoer</span><span class="sxs-lookup"><span data-stu-id="e8512-192">Outputs</span></span>

### <span data-ttu-id="e8512-193">Geen</span><span class="sxs-lookup"><span data-stu-id="e8512-193">None</span></span>

<span data-ttu-id="e8512-194">Als het **referentie** object en het **verschil** object hetzelfde zijn, is er geen uitvoer, tenzij u de para meter **IncludeEqual** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e8512-194">If the **reference** object and the **difference** object are the same, there's no output, unless you use the **IncludeEqual** parameter.</span></span>

### <span data-ttu-id="e8512-195">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="e8512-195">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="e8512-196">Als de objecten verschillend zijn, worden `Compare-Object` de objecten in een `PSCustomObject` wrapper vervangen door de **SideIndicator** -eigenschap om te verwijzen naar de verschillen.</span><span class="sxs-lookup"><span data-stu-id="e8512-196">If the objects are different, `Compare-Object` wraps the differing objects in a `PSCustomObject` wrapper with a **SideIndicator** property to reference the differences.</span></span>

<span data-ttu-id="e8512-197">Wanneer u de para meter **PassThru** gebruikt, wordt het **type** van het object niet gewijzigd, maar het exemplaar van het geretourneerde object heeft een toegevoegd **NoteProperty** met de naam **SideIndicator**.</span><span class="sxs-lookup"><span data-stu-id="e8512-197">When you use the **PassThru** parameter, the **Type** of the object is not changed but the instance of the object returned has an added **NoteProperty** named **SideIndicator**.</span></span> <span data-ttu-id="e8512-198">**SideIndicator** laat zien met welk invoer object de uitvoer behoort.</span><span class="sxs-lookup"><span data-stu-id="e8512-198">**SideIndicator** shows which input object the output belongs to.</span></span>

## <span data-ttu-id="e8512-199">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e8512-199">Notes</span></span>

<span data-ttu-id="e8512-200">Wanneer u de para meter **PassThru** gebruikt, bevat de uitvoer die in de-console wordt weer gegeven, mogelijk niet de eigenschap **SideIndicator** .</span><span class="sxs-lookup"><span data-stu-id="e8512-200">When using the **PassThru** parameter, the output displayed in the console may not include the **SideIndicator** property.</span></span> <span data-ttu-id="e8512-201">De standaard indelings weergave van de voor het object type uitvoer met `Compare-Object` bevat niet de eigenschap **SideIndicator** .</span><span class="sxs-lookup"><span data-stu-id="e8512-201">The default format view of the for the object type output by `Compare-Object` does not include the **SideIndicator** property.</span></span> <span data-ttu-id="e8512-202">Zie [voor beeld 3](#ex3) in dit artikel voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e8512-202">For more information see [Example 3](#ex3) in this article.</span></span>

## <span data-ttu-id="e8512-203">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="e8512-203">Related links</span></span>

[<span data-ttu-id="e8512-204">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="e8512-204">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="e8512-205">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="e8512-205">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="e8512-206">Groep-object</span><span class="sxs-lookup"><span data-stu-id="e8512-206">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="e8512-207">Meting object</span><span class="sxs-lookup"><span data-stu-id="e8512-207">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="e8512-208">New-Object</span><span class="sxs-lookup"><span data-stu-id="e8512-208">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="e8512-209">Select-Object</span><span class="sxs-lookup"><span data-stu-id="e8512-209">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="e8512-210">Sorteer object</span><span class="sxs-lookup"><span data-stu-id="e8512-210">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="e8512-211">T-object</span><span class="sxs-lookup"><span data-stu-id="e8512-211">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="e8512-212">Where-object</span><span class="sxs-lookup"><span data-stu-id="e8512-212">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

[<span data-ttu-id="e8512-213">Get-Process</span><span class="sxs-lookup"><span data-stu-id="e8512-213">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)
