---
description: Hierin worden de Opera tors beschreven die met Microsoft .NET typen werken.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Operators
ms.openlocfilehash: 829dfbbf2cd02c1bf4f1616b49f01f8f079d7d0e
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93253036"
---
# <a name="about-type-operators"></a><span data-ttu-id="e13d7-104">Over type operators</span><span class="sxs-lookup"><span data-stu-id="e13d7-104">About Type Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="e13d7-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e13d7-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="e13d7-106">Hierin worden de Opera tors beschreven die met Microsoft .NET typen werken.</span><span class="sxs-lookup"><span data-stu-id="e13d7-106">Describes the operators that work with Microsoft .NET types.</span></span>

## <a name="long-description"></a><span data-ttu-id="e13d7-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e13d7-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="e13d7-108">De Boole-operator ( `-is` en `-isNot` ) geven aan of een object een exemplaar van een opgegeven .net-type is.</span><span class="sxs-lookup"><span data-stu-id="e13d7-108">The Boolean type operators (`-is` and `-isNot`) tell whether an object is an instance of a specified .NET type.</span></span> <span data-ttu-id="e13d7-109">De `-is` operator retourneert de waarde **True** als het type overeenkomt met en de waarde **False** .</span><span class="sxs-lookup"><span data-stu-id="e13d7-109">The `-is` operator returns a value of **TRUE** if the type matches and a value of **FALSE** otherwise.</span></span> <span data-ttu-id="e13d7-110">De `-isNot` operator retourneert de waarde **False** als het type overeenkomt met en de waarde **True** .</span><span class="sxs-lookup"><span data-stu-id="e13d7-110">The `-isNot` operator returns a value of **FALSE** if the type matches and a value of **TRUE** otherwise.</span></span>

<span data-ttu-id="e13d7-111">De `-as` operator probeert het invoer object te converteren naar het opgegeven .net-type.</span><span class="sxs-lookup"><span data-stu-id="e13d7-111">The `-as` operator tries to convert the input object to the specified .NET type.</span></span> <span data-ttu-id="e13d7-112">Als dit lukt, wordt het geconverteerde object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e13d7-112">If it succeeds, it returns the converted object.</span></span> <span data-ttu-id="e13d7-113">Als dit mislukt, wordt geretourneerd `$null` .</span><span class="sxs-lookup"><span data-stu-id="e13d7-113">If it fails, it returns `$null`.</span></span> <span data-ttu-id="e13d7-114">Er wordt geen fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e13d7-114">It does not return an error.</span></span>

<span data-ttu-id="e13d7-115">De volgende tabel bevat de type operators in Power shell.</span><span class="sxs-lookup"><span data-stu-id="e13d7-115">The following table lists the type operators in PowerShell.</span></span>

|<span data-ttu-id="e13d7-116">Operator</span><span class="sxs-lookup"><span data-stu-id="e13d7-116">Operator</span></span>|<span data-ttu-id="e13d7-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e13d7-117">Description</span></span>                |<span data-ttu-id="e13d7-118">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e13d7-118">Example</span></span>                          |
|--------|---------------------------|---------------------------------|
|`-is`   |<span data-ttu-id="e13d7-119">Retourneert waar wanneer de invoer</span><span class="sxs-lookup"><span data-stu-id="e13d7-119">Returns TRUE when the input</span></span>|`(get-date) -is [DateTime]`      |
|        |<span data-ttu-id="e13d7-120">is een exemplaar van de</span><span class="sxs-lookup"><span data-stu-id="e13d7-120">is an instance of the</span></span>      |`True`                           |
|        |<span data-ttu-id="e13d7-121">opgegeven .NET-type.</span><span class="sxs-lookup"><span data-stu-id="e13d7-121">specified .NET type.</span></span>       |                                 |
|`-isNot`|<span data-ttu-id="e13d7-122">Retourneert waar wanneer de invoer</span><span class="sxs-lookup"><span data-stu-id="e13d7-122">Returns TRUE when the input</span></span>|`(get-date) -isNot [DateTime]`   |
|        |<span data-ttu-id="e13d7-123">geen exemplaar van de</span><span class="sxs-lookup"><span data-stu-id="e13d7-123">not an instance of the</span></span>     |`False`                          |
|        |<span data-ttu-id="e13d7-124">type specified.NET.</span><span class="sxs-lookup"><span data-stu-id="e13d7-124">specified.NET type.</span></span>        |                                 |
|`-as`   |<span data-ttu-id="e13d7-125">Hiermee wordt de invoer geconverteerd naar de</span><span class="sxs-lookup"><span data-stu-id="e13d7-125">Converts the input to the</span></span>  |`"5/7/07" -as [DateTime]`        |
|        |<span data-ttu-id="e13d7-126">opgegeven .NET-type.</span><span class="sxs-lookup"><span data-stu-id="e13d7-126">specified .NET type.</span></span>       |`Monday, May 7, 2007 12:00:00 AM`|

<span data-ttu-id="e13d7-127">De syntaxis van de type operators is als volgt:</span><span class="sxs-lookup"><span data-stu-id="e13d7-127">The syntax of the type operators is as follows:</span></span>

```powershell
<input> <operator> [.NET type]
```

<span data-ttu-id="e13d7-128">U kunt ook de volgende syntaxis gebruiken:</span><span class="sxs-lookup"><span data-stu-id="e13d7-128">You can also use the following syntax:</span></span>

```powershell
<input> <operator> ".NET type"
```

<span data-ttu-id="e13d7-129">Het .NET-type kan worden geschreven als een type naam tussen vier Kante haken of een teken reeks, zoals `[DateTime]` of `"DateTime"` voor **System. datetime**.</span><span class="sxs-lookup"><span data-stu-id="e13d7-129">The .NET type can be written as a type name in brackets or a string, such as `[DateTime]` or `"DateTime"` for **System.DateTime**.</span></span> <span data-ttu-id="e13d7-130">Als het type zich niet in de hoofdmap van de naam ruimte van het systeem bevindt, geeft u de volledige naam van het object type op.</span><span class="sxs-lookup"><span data-stu-id="e13d7-130">If the type is not at the root of the system namespace, specify the full name of the object type.</span></span> <span data-ttu-id="e13d7-131">U kunt ' System. ' weglaten.</span><span class="sxs-lookup"><span data-stu-id="e13d7-131">You can omit "System.".</span></span> <span data-ttu-id="e13d7-132">U kunt bijvoorbeeld **System. Diagnostics. process** opgeven, invoeren `[System.Diagnostics.Process]` , `[Diagnostics.Process]` of `"Diagnostics.Process"` .</span><span class="sxs-lookup"><span data-stu-id="e13d7-132">For example, to specify **System.Diagnostics.Process** , enter `[System.Diagnostics.Process]`, `[Diagnostics.Process]`, or `"Diagnostics.Process"`.</span></span>

<span data-ttu-id="e13d7-133">De type operators worden altijd als geheel op het invoer object toegepast.</span><span class="sxs-lookup"><span data-stu-id="e13d7-133">The type operators always operate on the input object as a whole.</span></span> <span data-ttu-id="e13d7-134">Dat wil zeggen, als het invoer object een verzameling is, het het type _verzameling_ dat wordt getest, niet de typen van de _elementen_ van de verzameling.</span><span class="sxs-lookup"><span data-stu-id="e13d7-134">That is, if the input object is a collection, it is the _collection_ type that is tested, not the types of the collection's _elements_.</span></span>

### <a name="-isisnot-operators"></a><span data-ttu-id="e13d7-135">-is/isNot Opera tors</span><span class="sxs-lookup"><span data-stu-id="e13d7-135">-is/isNot operators</span></span>

<span data-ttu-id="e13d7-136">De **Boole** -operator ( `-is` en `-isNot` ) retour neren altijd een **Booleaanse** waarde, zelfs als de invoer een verzameling van objecten is.</span><span class="sxs-lookup"><span data-stu-id="e13d7-136">The **Boolean** type operators (`-is` and `-isNot`) always return a **Boolean** value, even if the input is a collection of objects.</span></span>

<span data-ttu-id="e13d7-137">Als `<input>` is een type dat gelijk is aan of is _afgeleid_ van het .net-type, `-is` retourneert de operator `$True` .</span><span class="sxs-lookup"><span data-stu-id="e13d7-137">If `<input>` is a type that is the same as or is _derived_ from the .NET Type, the `-is` operator returns `$True`.</span></span>

<span data-ttu-id="e13d7-138">Het type **DirectoryInfo** wordt bijvoorbeeld afgeleid van het type **FileSystemInfo** .</span><span class="sxs-lookup"><span data-stu-id="e13d7-138">For example, the **DirectoryInfo** type is derived from the **FileSystemInfo** type.</span></span> <span data-ttu-id="e13d7-139">Beide voor beelden geven daarom de **waarde True**.</span><span class="sxs-lookup"><span data-stu-id="e13d7-139">Therefore, both of these examples return **True**.</span></span>

```powershell
PS> (Get-Item /) -is [System.IO.DirectoryInfo]
True
PS> (Get-Item /) -is [System.IO.FileSystemInfo]
True
```

<span data-ttu-id="e13d7-140">De `-is` operator kan ook interfaces overeenkomen als de `<input>` interface in de vergelijking wordt geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="e13d7-140">The `-is` operator can also match interfaces if the `<input>` implements the interface in the comparison.</span></span> <span data-ttu-id="e13d7-141">In dit voor beeld is de invoer een matrix.</span><span class="sxs-lookup"><span data-stu-id="e13d7-141">In this example, the input is an array.</span></span> <span data-ttu-id="e13d7-142">Matrices implementeren de interface **System. Collections. IList** .</span><span class="sxs-lookup"><span data-stu-id="e13d7-142">Arrays implement the **System.Collections.IList** interface.</span></span>

```powershell
PS> 1, 2 -is [System.Collections.IList]
True
```

### <a name="-as-operator"></a><span data-ttu-id="e13d7-143">-as-operator</span><span class="sxs-lookup"><span data-stu-id="e13d7-143">-as operator</span></span>

<span data-ttu-id="e13d7-144">De `-as` operator probeert het invoer object te converteren naar het opgegeven .net-type.</span><span class="sxs-lookup"><span data-stu-id="e13d7-144">The `-as` operator tries to convert the input object to the specified .NET type.</span></span> <span data-ttu-id="e13d7-145">Als dit lukt, wordt het geconverteerde object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e13d7-145">If it succeeds, it returns the converted object.</span></span> <span data-ttu-id="e13d7-146">Als dit mislukt, wordt geretourneerd `$null` .</span><span class="sxs-lookup"><span data-stu-id="e13d7-146">It if fails, it returns `$null`.</span></span> <span data-ttu-id="e13d7-147">Er wordt geen fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e13d7-147">It does not return an error.</span></span>

<span data-ttu-id="e13d7-148">Als het `<input>` is een type dat is _afgeleid_ van het .net-type door gegeven, `-as` _passes through_ wordt het ingevoerde invoer object ongewijzigd.</span><span class="sxs-lookup"><span data-stu-id="e13d7-148">If the `<input>` is a type that is _derived_ from the .NET Type `-as` _passes through_ returns input object unchanged.</span></span> <span data-ttu-id="e13d7-149">Het type **DirectoryInfo** wordt bijvoorbeeld afgeleid van het type **FileSystemInfo** .</span><span class="sxs-lookup"><span data-stu-id="e13d7-149">For example, the **DirectoryInfo** type is derived from the **FileSystemInfo** type.</span></span> <span data-ttu-id="e13d7-150">Daarom is het object type ongewijzigd in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="e13d7-150">Therefore, the object type is unchanged in the following example:</span></span>

```powershell
PS> $fsroot = (Get-Item /) -as [System.IO.FileSystemInfo]
PS> $fsroot.GetType().FullName
System.IO.DirectoryInfo
```

#### <a name="converting-the-datetime-type-is-culture-sensitive"></a><span data-ttu-id="e13d7-151">Conversie van het type DateTime is cultuur gevoelig</span><span class="sxs-lookup"><span data-stu-id="e13d7-151">Converting the DateTime type is culture-sensitive</span></span>

<span data-ttu-id="e13d7-152">Conversie naar `[DateTime]` type met behulp `-as` van de operator werkt alleen met teken reeksen die zijn opgemaakt op basis van de regels van de huidige cultuur, in tegens telling tot type cast.</span><span class="sxs-lookup"><span data-stu-id="e13d7-152">Unlike type casting, converting to `[DateTime]` type using the `-as` operator only works with strings that are formatted according to the rules of the current culture.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr-FR'
PS> '13/5/20' -as [datetime]

mercredi 13 mai 2020 00:00:00

PS> '05/13/20' -as [datetime]
PS> [datetime]'05/13/20'

mercredi 13 mai 2020 00:00:00

PS> [datetime]'13/05/20'
InvalidArgument: Cannot convert value "13/05/20" to type "System.DateTime".
Error: "String '13/05/20' was not recognized as a valid DateTime."
```

<span data-ttu-id="e13d7-153">Als u het .NET-type van een object wilt zoeken, gebruikt u de `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e13d7-153">To find the .NET type of an object, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="e13d7-154">Of gebruik de **gettype** -methode van alle objecten in combi natie met de eigenschap **FullName** van deze methode.</span><span class="sxs-lookup"><span data-stu-id="e13d7-154">Or, use the **GetType** method of all the objects together with the **FullName** property of this method.</span></span> <span data-ttu-id="e13d7-155">De volgende instructie haalt bijvoorbeeld het type van de retour waarde van een opdracht op `Get-Culture` :</span><span class="sxs-lookup"><span data-stu-id="e13d7-155">For example, the following statement gets the type of the return value of a `Get-Culture` command:</span></span>

```powershell
PS> (Get-Culture).GetType().FullName
System.Globalization.CultureInfo
```

## <a name="examples"></a><span data-ttu-id="e13d7-156">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e13d7-156">EXAMPLES</span></span>

<span data-ttu-id="e13d7-157">In de volgende voor beelden ziet u enkele gebruik van de type operators:</span><span class="sxs-lookup"><span data-stu-id="e13d7-157">The following examples show some uses of the Type operators:</span></span>

```powershell
PS> 32 -is [Float]
False

PS> 32 -is "int"
True

PS> (get-date) -is [DateTime]
True

PS> "12/31/2007" -is [DateTime]
False

PS> "12/31/2007" -is [String]
True

PS> (get-process PowerShell)[0] -is [System.Diagnostics.Process]
True

PS> (get-command get-member) -is [System.Management.Automation.CmdletInfo]
True
```

<span data-ttu-id="e13d7-158">In het volgende voor beeld ziet u dat wanneer de invoer een verzameling objecten is, het overeenkomende type het .NET-type van de verzameling is, niet het type van de afzonderlijke objecten in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="e13d7-158">The following example shows that when the input is a collection of objects, the matching type is the .NET type of the collection, not the type of the individual objects in the collection.</span></span>

<span data-ttu-id="e13d7-159">In dit voor beeld, hoewel zowel `Get-Culture` de `Get-UICulture` cmdlets als **System. Globalization. Culture info** -objecten retour neren, is een verzameling van deze objecten een System. object-matrix.</span><span class="sxs-lookup"><span data-stu-id="e13d7-159">In this example, although both the `Get-Culture` and `Get-UICulture` cmdlets return **System.Globalization.CultureInfo** objects, a collection of these objects is a System.Object array.</span></span>

```powershell
PS> (get-culture) -is [System.Globalization.CultureInfo]
True

PS> (get-uiculture) -is [System.Globalization.CultureInfo]
True

PS> (get-culture), (get-uiculture) -is [System.Globalization.CultureInfo]
False

PS> (get-culture), (get-uiculture) -is [Array]
True

PS> (get-culture), (get-uiculture) | foreach {
  $_ -is [System.Globalization.CultureInfo])
}
True
True

PS> (get-culture), (get-uiculture) -is [Object]
True
```

<span data-ttu-id="e13d7-160">In de volgende voor beelden ziet u hoe u de `-as` operator gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e13d7-160">The following examples show how to use the `-as` operator.</span></span>

```powershell
PS> "12/31/07" -is [DateTime]
False

PS> "12/31/07" -as [DateTime]
Monday, December 31, 2007 12:00:00 AM

PS> $date = "12/31/07" -as [DateTime]

C:\PS>$a -is [DateTime]
True

PS> 1031 -as [System.Globalization.CultureInfo]

LCID      Name      DisplayName
----      ----      -----------
1031      de-DE     German (Germany)
```

<span data-ttu-id="e13d7-161">In het volgende voor beeld ziet u dat wanneer de `-as` operator het invoer object niet kan converteren naar het .net-type, het wordt geretourneerd `$null` .</span><span class="sxs-lookup"><span data-stu-id="e13d7-161">The following example shows that when the `-as` operator cannot convert the input object to the .NET type, it returns `$null`.</span></span>

```powershell
PS> 1031 -as [System.Diagnostics.Process]
PS>
```

## <a name="see-also"></a><span data-ttu-id="e13d7-162">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="e13d7-162">SEE ALSO</span></span>

[<span data-ttu-id="e13d7-163">about_Operators</span><span class="sxs-lookup"><span data-stu-id="e13d7-163">about_Operators</span></span>](about_Operators.md)
