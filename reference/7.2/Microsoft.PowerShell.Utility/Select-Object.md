---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Object
ms.openlocfilehash: 80882d27c9c8fa2d7f9e1c8ca00a02cf73ae94e6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704751"
---
# <span data-ttu-id="8cb4c-102">Select-Object</span><span class="sxs-lookup"><span data-stu-id="8cb4c-102">Select-Object</span></span>

## <span data-ttu-id="8cb4c-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="8cb4c-103">SYNOPSIS</span></span>
<span data-ttu-id="8cb4c-104">Objecten of object eigenschappen selecteren.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-104">Selects objects or object properties.</span></span>

## <span data-ttu-id="8cb4c-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="8cb4c-105">SYNTAX</span></span>

### <span data-ttu-id="8cb4c-106">DefaultParameter (standaard)</span><span class="sxs-lookup"><span data-stu-id="8cb4c-106">DefaultParameter (Default)</span></span>

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-Last <Int32>] [-First <Int32>] [-Skip <Int32>] [-Wait]
 [<CommonParameters>]
```

### <span data-ttu-id="8cb4c-107">SkipLastParameter</span><span class="sxs-lookup"><span data-stu-id="8cb4c-107">SkipLastParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-SkipLast <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="8cb4c-108">IndexParameter</span><span class="sxs-lookup"><span data-stu-id="8cb4c-108">IndexParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [-Unique] [-Wait] [-Index <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="8cb4c-109">SkipIndexParameter</span><span class="sxs-lookup"><span data-stu-id="8cb4c-109">SkipIndexParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [-Unique] [-SkipIndex <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="8cb4c-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8cb4c-110">DESCRIPTION</span></span>

<span data-ttu-id="8cb4c-111">De `Select-Object` cmdlet selecteert opgegeven eigenschappen van een object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-111">The `Select-Object` cmdlet selects specified properties of an object or set of objects.</span></span> <span data-ttu-id="8cb4c-112">Het kan ook unieke objecten, een opgegeven aantal objecten of objecten in een opgegeven positie in een matrix selecteren.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-112">It can also select unique objects, a specified number of objects, or objects in a specified position in an array.</span></span>

<span data-ttu-id="8cb4c-113">Als u objecten uit een verzameling wilt selecteren, gebruikt u de para meters **eerste**, **laatste**, **uniek**, **overs Laan** en **index** .</span><span class="sxs-lookup"><span data-stu-id="8cb4c-113">To select objects from a collection, use the **First**, **Last**, **Unique**, **Skip**, and **Index** parameters.</span></span> <span data-ttu-id="8cb4c-114">Als u object eigenschappen wilt selecteren, gebruikt u de para meter **Property** .</span><span class="sxs-lookup"><span data-stu-id="8cb4c-114">To select object properties, use the **Property** parameter.</span></span> <span data-ttu-id="8cb4c-115">Wanneer u eigenschappen selecteert, `Select-Object` retourneert nieuwe objecten die alleen de opgegeven eigenschappen hebben.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-115">When you select properties, `Select-Object` returns new objects that have only the specified properties.</span></span>

<span data-ttu-id="8cb4c-116">Vanaf Windows Power Shell 3,0 `Select-Object` bevat een optimalisatie functie waarmee wordt voor komen dat opdrachten objecten maken en verwerken die niet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-116">Beginning in Windows PowerShell 3.0, `Select-Object` includes an optimization feature that prevents commands from creating and processing objects that are not used.</span></span>

<span data-ttu-id="8cb4c-117">Wanneer u een opdracht opneemt `Select-Object` met de **eerste** of **index** parameters in een opdracht pijplijn, stopt Power shell de opdracht waarmee de objecten worden gegenereerd zodra het geselecteerde aantal objecten wordt gegenereerd, zelfs wanneer de opdracht die de objecten genereert, wordt weer gegeven voor de `Select-Object` opdracht in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-117">When you include a `Select-Object` command with the **First** or **Index** parameters in a command pipeline, PowerShell stops the command that generates the objects as soon as the selected number of objects is generated, even when the command that generates the objects appears before the `Select-Object` command in the pipeline.</span></span> <span data-ttu-id="8cb4c-118">Als u dit optimalisatie gedrag wilt uitschakelen, gebruikt u de para meter **wait** .</span><span class="sxs-lookup"><span data-stu-id="8cb4c-118">To turn off this optimizing behavior, use the **Wait** parameter.</span></span>

## <span data-ttu-id="8cb4c-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8cb4c-119">EXAMPLES</span></span>

### <span data-ttu-id="8cb4c-120">Voor beeld 1: objecten op eigenschap selecteren</span><span class="sxs-lookup"><span data-stu-id="8cb4c-120">Example 1: Select objects by property</span></span>

<span data-ttu-id="8cb4c-121">In dit voor beeld worden objecten gemaakt met de eigenschappen **name**, **id** en Working set (**WS**) van Process-objecten.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-121">This example creates objects that have the **Name**, **ID**, and working set (**WS**) properties of process objects.</span></span>

```powershell
Get-Process | Select-Object -Property ProcessName, Id, WS
```

### <span data-ttu-id="8cb4c-122">Voor beeld 2: objecten selecteren op eigenschap en de resultaten opmaken</span><span class="sxs-lookup"><span data-stu-id="8cb4c-122">Example 2: Select objects by property and format the results</span></span>

<span data-ttu-id="8cb4c-123">In dit voor beeld wordt informatie opgehaald over de modules die worden gebruikt door de processen op de computer.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-123">This example gets information about the modules used by the processes on the computer.</span></span> <span data-ttu-id="8cb4c-124">De functie `Get-Process` cmdlet wordt gebruikt om het proces op de computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-124">It uses `Get-Process` cmdlet to get the process on the computer.</span></span>

<span data-ttu-id="8cb4c-125">De cmdlet wordt gebruikt `Select-Object` om een matrix van exemplaren uit te voeren `[System.Diagnostics.ProcessModule]` , zoals opgenomen in de eigenschap **modules** van elk exemplaar dat `System.Diagnostics.Process` door wordt uitgevoerd `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="8cb4c-125">It uses the `Select-Object` cmdlet to output an array of `[System.Diagnostics.ProcessModule]` instances as contained in the **Modules** property of each `System.Diagnostics.Process` instance output by `Get-Process`.</span></span>

<span data-ttu-id="8cb4c-126">De **eigenschap** para meter van de `Select-Object` cmdlet selecteert de proces namen.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-126">The **Property** parameter of the `Select-Object` cmdlet selects the process names.</span></span> <span data-ttu-id="8cb4c-127">Hiermee wordt een `ProcessName` **NoteProperty** toegevoegd aan elk `[System.Diagnostics.ProcessModule]` exemplaar en gevuld met de waarde van de eigenschap **proces** naam van het huidige proces.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-127">This adds a `ProcessName` **NoteProperty** to every `[System.Diagnostics.ProcessModule]` instance and populates it with the value of current process's **ProcessName** property.</span></span>

<span data-ttu-id="8cb4c-128">Ten slotte `Format-List` wordt de cmdlet gebruikt om de naam en modules van elk proces in een lijst weer te geven.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-128">Finally, `Format-List` cmdlet is used to display the name and modules of each process in a list.</span></span>

```powershell
Get-Process Explorer | Select-Object -Property ProcessName -ExpandProperty Modules | Format-List
```

```Output
ProcessName       : explorer
ModuleName        : explorer.exe
FileName          : C:\WINDOWS\explorer.exe
BaseAddress       : 140697278152704
ModuleMemorySize  : 3919872
EntryPointAddress : 140697278841168
FileVersionInfo   : File:             C:\WINDOWS\explorer.exe
                    InternalName:     explorer
                    OriginalFilename: EXPLORER.EXE.MUI
                    FileVersion:      10.0.17134.1 (WinBuild.160101.0800)
                    FileDescription:  Windows Explorer
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.17134.1
...
```

### <span data-ttu-id="8cb4c-129">Voor beeld 3: processen selecteren met het meeste geheugen</span><span class="sxs-lookup"><span data-stu-id="8cb4c-129">Example 3: Select processes using the most memory</span></span>

<span data-ttu-id="8cb4c-130">In dit voor beeld worden de vijf processen opgehaald die het meeste geheugen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-130">This example gets the five processes that are using the most memory.</span></span> <span data-ttu-id="8cb4c-131">De `Get-Process` cmdlet haalt de processen op de computer op.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-131">The `Get-Process` cmdlet gets the processes on the computer.</span></span> <span data-ttu-id="8cb4c-132">Met de `Sort-Object` cmdlet worden de processen gesorteerd op basis van het gebruik van geheugen (werkset) en de `Select-Object` cmdlet selecteert alleen de laatste vijf leden van de resulterende matrix met objecten.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-132">The `Sort-Object` cmdlet sorts the processes according to memory (working set) usage, and the `Select-Object` cmdlet selects only the last five members of the resulting array of objects.</span></span>

<span data-ttu-id="8cb4c-133">De **wait** -para meter is niet vereist in opdrachten die de `Sort-Object` cmdlet bevatten `Sort-Object` , omdat alle objecten worden verwerkt en vervolgens een verzameling wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-133">The **Wait** parameter is not required in commands that include the `Sort-Object` cmdlet because `Sort-Object` processes all objects and then returns a collection.</span></span> <span data-ttu-id="8cb4c-134">De `Select-Object` optimalisatie is alleen beschikbaar voor opdrachten die objecten afzonderlijk retour neren wanneer ze worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-134">The `Select-Object` optimization is available only for commands that return objects individually as they are processed.</span></span>

```powershell
Get-Process | Sort-Object -Property WS | Select-Object -Last 5
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VS(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
2866     320       33432      45764   203   222.41   1292 svchost
577      17        23676      50516   265    50.58   4388 WINWORD
826      11        75448      76712   188    19.77   3780 Ps
1367     14        73152      88736   216    61.69    676 Ps
1612     44        66080      92780   380   900.59   6132 INFOPATH
```

### <span data-ttu-id="8cb4c-135">Voor beeld 4: unieke tekens uit een matrix selecteren</span><span class="sxs-lookup"><span data-stu-id="8cb4c-135">Example 4: Select unique characters from an array</span></span>

<span data-ttu-id="8cb4c-136">In dit voor beeld wordt de **unieke** para meter van gebruikt `Select-Object` om unieke tekens uit een matrix met tekens op te halen.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-136">This example uses the **Unique** parameter of `Select-Object` to get unique characters from an array of characters.</span></span>

```powershell
"a","b","c","a","a","a" | Select-Object -Unique
```

```Output
a
b
c
```

### <span data-ttu-id="8cb4c-137">Voor beeld 5: de nieuwste en oudste gebeurtenissen in het gebeurtenis logboek selecteren</span><span class="sxs-lookup"><span data-stu-id="8cb4c-137">Example 5: Select newest and oldest events in the event log</span></span>

<span data-ttu-id="8cb4c-138">In dit voor beeld worden de eerste (nieuwste) en laatste (oudste) gebeurtenissen in het Windows Power shell-gebeurtenis logboek opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-138">This example gets the first (newest) and last (oldest) events in the Windows PowerShell event log.</span></span>

<span data-ttu-id="8cb4c-139">`Get-EventLog` Hiermee worden alle gebeurtenissen in het Windows Power shell-logboek opgehaald en opgeslagen in de `$a` variabele.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-139">`Get-EventLog` gets all events in the Windows PowerShell log and saves them in the `$a` variable.</span></span>
<span data-ttu-id="8cb4c-140">Vervolgens wordt door gegeven `$a` aan de `Select-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-140">Then, `$a` is piped to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="8cb4c-141">De `Select-Object` opdracht gebruikt de para meter **index** om gebeurtenissen te selecteren uit de matrix met gebeurtenissen in de `$a` variabele.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-141">The `Select-Object` command uses the **Index** parameter to select events from the array of events in the `$a` variable.</span></span> <span data-ttu-id="8cb4c-142">De index van de eerste gebeurtenis is 0.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-142">The index of the first event is 0.</span></span> <span data-ttu-id="8cb4c-143">De index van de laatste gebeurtenis is het aantal items in `$a` min 1.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-143">The index of the last event is the number of items in `$a` minus 1.</span></span>

```powershell
$a = Get-EventLog -LogName "Windows PowerShell"
$a | Select-Object -Index 0, ($A.count - 1)
```

### <span data-ttu-id="8cb4c-144">Voor beeld 6: Alles selecteren, behalve het eerste object</span><span class="sxs-lookup"><span data-stu-id="8cb4c-144">Example 6: Select all but the first object</span></span>

<span data-ttu-id="8cb4c-145">In dit voor beeld wordt een nieuwe PSSession gemaakt op elke computer die wordt vermeld in de Servers.txt-bestanden, met uitzonde ring van de eerste.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-145">This example creates a new PSSession on each of the computers listed in the Servers.txt files, except for the first one.</span></span>

<span data-ttu-id="8cb4c-146">`Select-Object` selecteert alle computers behalve de eerste computer in een lijst met computer namen.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-146">`Select-Object` selects all but the first computer in a list of computer names.</span></span> <span data-ttu-id="8cb4c-147">De resulterende lijst met computers wordt ingesteld als de waarde van de para meter **ComputerName** van de `New-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-147">The resulting list of computers is set as the value of the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span>

```powershell
New-PSSession -ComputerName (Get-Content Servers.txt | Select-Object -Skip 1)
```

### <span data-ttu-id="8cb4c-148">Voor beeld 7: bestanden een andere naam geven en meerdere selecteren om weer te geven</span><span class="sxs-lookup"><span data-stu-id="8cb4c-148">Example 7: Rename files and select several to review</span></span>

<span data-ttu-id="8cb4c-149">In dit voor beeld wordt een "-ro"-achtervoegsel toegevoegd aan de basis namen van tekst bestanden met het kenmerk alleen-lezen en worden de eerste vijf bestanden weer gegeven, zodat de gebruiker een voor beeld van het effect kan zien.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-149">This example adds a "-ro" suffix to the base names of text files that have the read-only attribute and then displays the first five files so the user can see a sample of the effect.</span></span>

<span data-ttu-id="8cb4c-150">`Get-ChildItem` maakt gebruik **van de alleen** -lezen dynamische para meter voor het ophalen van bestanden met het kenmerk alleen-laden</span><span class="sxs-lookup"><span data-stu-id="8cb4c-150">`Get-ChildItem` uses the **ReadOnly** dynamic parameter to get read-only files.</span></span> <span data-ttu-id="8cb4c-151">De resulterende bestanden worden door gegeven aan de `Rename-Item` cmdlet, waarmee de naam van het bestand wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-151">The resulting files are piped to the `Rename-Item` cmdlet, which renames the file.</span></span> <span data-ttu-id="8cb4c-152">Hiermee wordt de para meter **PassThru** van verzonden voor het `Rename-Item` verzenden van de hernoemde bestanden naar de `Select-Object` cmdlet, waarmee de eerste 5 wordt geselecteerd voor weer gave.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-152">It uses the **Passthru** parameter of `Rename-Item` to send the renamed files to the `Select-Object` cmdlet, which selects the first 5 for display.</span></span>

<span data-ttu-id="8cb4c-153">De **wait** -para meter van `Select-Object` voor komt dat Power shell de `Get-ChildItem` cmdlet stopt nadat de eerste vijf tekst bestanden met het kenmerk alleen-lezen worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-153">The **Wait** parameter of `Select-Object` prevents PowerShell from stopping the `Get-ChildItem` cmdlet after it gets the first five read-only text files.</span></span> <span data-ttu-id="8cb4c-154">Zonder deze para meter worden alleen de eerste vijf alleen-lezen bestanden hernoemd.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-154">Without this parameter, only the first five read-only files would be renamed.</span></span>

```powershell
Get-ChildItem *.txt -ReadOnly |
    Rename-Item -NewName {$_.BaseName + "-ro.txt"} -PassThru |
    Select-Object -First 5 -Wait
```

### <span data-ttu-id="8cb4c-155">Voor beeld 8: Demonstreer de complexiteit van de para meter-ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="8cb4c-155">Example 8: Demonstrate the intricacies of the -ExpandProperty parameter</span></span>

<span data-ttu-id="8cb4c-156">In dit voor beeld wordt de complexiteit van de para meter **ExpandProperty** gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-156">This example demonstrates the intricacies of the **ExpandProperty** parameter.</span></span>

<span data-ttu-id="8cb4c-157">Houd er rekening mee dat de gegenereerde uitvoer een matrix van `[System.Int32]` exemplaren is.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-157">Note that the output generated was an array of `[System.Int32]` instances.</span></span> <span data-ttu-id="8cb4c-158">De exemplaren voldoen aan de standaard regels voor opmaak van de **uitvoer weergave**.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-158">The instances conform to standard formatting rules of the **Output View**.</span></span> <span data-ttu-id="8cb4c-159">Dit geldt voor alle *uitgevouwen* eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-159">This is true for any *Expanded* properties.</span></span> <span data-ttu-id="8cb4c-160">Als de outputtende objecten een specifieke standaard indeling hebben, is de uitgebreide eigenschap mogelijk niet zichtbaar.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-160">If the outputted objects have a specific standard format, the expanded property might not be visible.</span></span>

```powershell
# Create a custom object to use for the Select-Object example.
$object = [pscustomobject]@{Name="CustomObject";Expand=@(1,2,3,4,5)}
# Use the ExpandProperty parameter to Expand the property.
$object | Select-Object -ExpandProperty Expand -Property Name
```

```Output
1
2
3
4
5
```

```powershell
# The output did not contain the Name property, but it was added successfully.
# Use Get-Member to confirm the Name property was added and populated.
$object | Select-Object -ExpandProperty Expand -Property Name | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType   Definition
----        ----------   ----------
CompareTo   Method       int CompareTo(System.Object value), int CompareTo(int value), int IComparable.CompareTo(System.Object obj)...
Equals      Method       bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int].Equals(int other)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
GetTypeCode Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar      Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime  Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal   Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble    Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16     Method       int16 IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32     Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64     Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte     Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle    Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString    Method       string ToString(), string ToString(string format), string ToString(System.IFormatProvider provider)...
ToType      Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16    Method       uint16 IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32    Method       uint32 IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64    Method       uint64 IConvertible.ToUInt64(System.IFormatProvider provider)
Name        NoteProperty string Name=CustomObject
```

### <span data-ttu-id="8cb4c-161">Voor beeld 9: aangepaste eigenschappen maken voor objecten</span><span class="sxs-lookup"><span data-stu-id="8cb4c-161">Example 9: Create custom properties on objects</span></span>

<span data-ttu-id="8cb4c-162">In het volgende voor beeld ziet u hoe u `Select-Object` een aangepaste eigenschap aan een object kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-162">The following example demonstrates using `Select-Object` to add a custom property to any object.</span></span>
<span data-ttu-id="8cb4c-163">Wanneer u een eigenschaps naam opgeeft die niet bestaat, `Select-Object` maakt deze eigenschap als een **NoteProperty** voor elk object dat wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-163">When you specify a property name that does not exist, `Select-Object` creates that property as a **NoteProperty** on each object passed.</span></span>

```powershell
$customObject = 1 | Select-Object -Property MyCustomProperty
$customObject.MyCustomProperty = "New Custom Property"
$customObject
```

```Output
MyCustomProperty
----------------
New Custom Property
```

### <span data-ttu-id="8cb4c-164">Voor beeld 10: berekende eigenschappen maken voor elke input object</span><span class="sxs-lookup"><span data-stu-id="8cb4c-164">Example 10: Create calculated properties for each InputObject</span></span>

<span data-ttu-id="8cb4c-165">Dit voor beeld laat zien hoe u met behulp van `Select-Object` berekende eigenschappen aan uw invoer kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-165">This example demonstrates using `Select-Object` to add calculated properties to your input.</span></span> <span data-ttu-id="8cb4c-166">Door een **script Block** door te geven aan de **eigenschaps parameter,** wordt `Select-Object` de expressie geëvalueerd op elk object dat is door gegeven en worden de resultaten aan de uitvoer toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-166">Passing a **ScriptBlock** to the **Property** parameter causes `Select-Object` to evaluate the expression on each object passed and add the results to the output.</span></span> <span data-ttu-id="8cb4c-167">Binnen de **script Block** kunt u de variabele gebruiken `$_` om te verwijzen naar het huidige object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-167">Within the **ScriptBlock**, you can use the `$_` variable to reference the current object in the pipeline.</span></span>

<span data-ttu-id="8cb4c-168">`Select-Object`De **script Block** -teken reeks wordt standaard gebruikt als de naam van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-168">By default, `Select-Object` will use the **ScriptBlock** string as the name of the property.</span></span> <span data-ttu-id="8cb4c-169">Met behulp van een **hashtabel** kunt u de uitvoer van uw **script Block** labelen als een aangepaste eigenschap die aan elk object is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-169">Using a **Hashtable**, you can label the output of your **ScriptBlock** as a custom property added to each object.</span></span> <span data-ttu-id="8cb4c-170">U kunt meerdere berekende eigenschappen toevoegen aan elk object dat wordt door gegeven aan `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="8cb4c-170">You can add multiple calculated properties to each object passed to `Select-Object`.</span></span>

```powershell
# Create a calculated property called $_.StartTime.DayOfWeek
Get-Process | Select-Object -Property ProcessName,{$_.StartTime.DayOfWeek}
```

```Output
ProcessName  $_.StartTime.DayOfWeek
----         ----------------------
alg                       Wednesday
ati2evxx                  Wednesday
ati2evxx                   Thursday
...
```

```powershell
# Add a custom property to calculate the size in KiloBytes of each FileInfo object you pass in.
# Use the pipeline variable to divide each file's length by 1 KiloBytes
$size = @{label="Size(KB)";expression={$_.length/1KB}}
# Create an additional calculated property with the number of Days since the file was last accessed.
# You can also shorten the key names to be 'l', and 'e', or use Name instead of Label.
$days = @{l="Days";e={((Get-Date) - $_.LastAccessTime).Days}}
# You can also shorten the name of your label key to 'l' and your expression key to 'e'.
Get-ChildItem $PSHOME -File | Select-Object Name, $size, $days
```

```Output
Name                        Size(KB)        Days
----                        --------        ----
Certificate.format.ps1xml   12.5244140625   223
Diagnostics.Format.ps1xml   4.955078125     223
DotNetTypes.format.ps1xml   134.9833984375  223
```

## <span data-ttu-id="8cb4c-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8cb4c-171">PARAMETERS</span></span>

### <span data-ttu-id="8cb4c-172">-ExcludeProperty</span><span class="sxs-lookup"><span data-stu-id="8cb4c-172">-ExcludeProperty</span></span>

<span data-ttu-id="8cb4c-173">Hiermee geeft u de eigenschappen op die met deze cmdlet worden uitgesloten van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-173">Specifies the properties that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="8cb4c-174">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-174">Wildcards are permitted.</span></span>

<span data-ttu-id="8cb4c-175">Vanaf Power shell 6 is het niet meer nodig om de para meter **Property** voor **ExcludeProperty** te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-175">Beginning in PowerShell 6, it is no longer required to include the **Property** parameter for **ExcludeProperty** to work.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8cb4c-176">-ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="8cb4c-176">-ExpandProperty</span></span>

<span data-ttu-id="8cb4c-177">Geeft een eigenschap aan die moet worden geselecteerd en geeft aan dat er een poging moet worden gedaan om die eigenschap uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-177">Specifies a property to select, and indicates that an attempt should be made to expand that property.</span></span>

- <span data-ttu-id="8cb4c-178">Als de opgegeven eigenschap een matrix is, wordt elke waarde van de matrix opgenomen in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-178">If the specified property is an array, each value of the array is included in the output.</span></span>
- <span data-ttu-id="8cb4c-179">Als de opgegeven eigenschap een object is, worden de eigenschappen van de objecten uitgebreid voor elke **input object**</span><span class="sxs-lookup"><span data-stu-id="8cb4c-179">If the specified property is an object, the objects properties are expanded for every **InputObject**</span></span>

<span data-ttu-id="8cb4c-180">In beide gevallen komt het **type** objecten uitvoer overeen met het **type** van de uitgevouwen eigenschap.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-180">In either case, the **Type** of objects output will match the **Type** of the expanded property.</span></span>

<span data-ttu-id="8cb4c-181">Als de **eigenschaps** parameter is opgegeven, `Select-Object` probeert elke geselecteerde eigenschap als een **NoteProperty** toe te voegen aan elk object dat wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-181">If the **Property** parameter is specified, `Select-Object` will attempt to add each selected property as a **NoteProperty** to every outputted object.</span></span>

> [!WARNING]
> <span data-ttu-id="8cb4c-182">Als u de fout melding: Select: de eigenschap kan niet worden verwerkt omdat er al een eigenschap `<PropertyName>` bestaat, kunt u het volgende overwegen.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-182">If you receive the error: Select : Property cannot be processed because property `<PropertyName>` already exists, consider the following.</span></span>
> <span data-ttu-id="8cb4c-183">Houd er rekening mee dat bij `-ExpandProperty` `Select-Object` het gebruik geen bestaande eigenschap kan worden vervangen.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-183">Note that when using `-ExpandProperty`, `Select-Object` can not replace an existing property.</span></span>
> <span data-ttu-id="8cb4c-184">Dit betekent:</span><span class="sxs-lookup"><span data-stu-id="8cb4c-184">This means:</span></span>
>
> - <span data-ttu-id="8cb4c-185">Als het uitgevouwen object een eigenschap met dezelfde naam heeft, treedt er een fout op.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-185">If the expanded object has a property of the same name, an error will occur.</span></span>
> - <span data-ttu-id="8cb4c-186">Als het *geselecteerde* object een eigenschap heeft die dezelfde naam heeft als een *uitgebreide* objecten eigenschap, treedt er een fout op.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-186">If the *Selected* object has a property of the same name as an *Expanded* objects property, an error will occur.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cb4c-187">-Eerste</span><span class="sxs-lookup"><span data-stu-id="8cb4c-187">-First</span></span>

<span data-ttu-id="8cb4c-188">Hiermee wordt het aantal objecten aangegeven dat moet worden geselecteerd vanaf het begin van een matrix met invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-188">Specifies the number of objects to select from the beginning of an array of input objects.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cb4c-189">-Index</span><span class="sxs-lookup"><span data-stu-id="8cb4c-189">-Index</span></span>

<span data-ttu-id="8cb4c-190">Objecten uit een matrix selecteren op basis van de index waarden.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-190">Selects objects from an array based on their index values.</span></span> <span data-ttu-id="8cb4c-191">Voer de indexen in een lijst met door komma's gescheiden waarden in.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-191">Enter the indexes in a comma-separated list.</span></span> <span data-ttu-id="8cb4c-192">Indexen in een matrix beginnen met 0, waarbij 0 staat voor de eerste waarde en (n-1) de laatste waarde.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-192">Indexes in an array begin with 0, where 0 represents the first value and (n-1) represents the last value.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cb4c-193">-Input object</span><span class="sxs-lookup"><span data-stu-id="8cb4c-193">-InputObject</span></span>

<span data-ttu-id="8cb4c-194">Geeft objecten aan die via de pijp lijn naar de cmdlet worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-194">Specifies objects to send to the cmdlet through the pipeline.</span></span> <span data-ttu-id="8cb4c-195">Met deze para meter kunt u objecten pipet naar `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="8cb4c-195">This parameter enables you to pipe objects to `Select-Object`.</span></span>

<span data-ttu-id="8cb4c-196">Wanneer u objecten doorgeeft aan de para meter **input object** in plaats van de pijp lijn te gebruiken, `Select-Object` behandelt de **input object** als één object, zelfs als de waarde een verzameling is.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-196">When you pass objects to the **InputObject** parameter, instead of using the pipeline, `Select-Object` treats the **InputObject** as a single object, even if the value is a collection.</span></span> <span data-ttu-id="8cb4c-197">Het is raadzaam om de pijp lijn te gebruiken bij het door geven van verzamelingen naar `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="8cb4c-197">It is recommended that you use the pipeline when passing collections to `Select-Object`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8cb4c-198">-Laatste</span><span class="sxs-lookup"><span data-stu-id="8cb4c-198">-Last</span></span>

<span data-ttu-id="8cb4c-199">Hiermee wordt het aantal objecten aangegeven dat moet worden geselecteerd vanaf het einde van een matrix met invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-199">Specifies the number of objects to select from the end of an array of input objects.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cb4c-200">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="8cb4c-200">-Property</span></span>

<span data-ttu-id="8cb4c-201">Hiermee geeft u de eigenschappen te selecteren.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-201">Specifies the properties to select.</span></span> <span data-ttu-id="8cb4c-202">Deze eigenschappen worden toegevoegd als **NoteProperty** -leden aan de uitvoer objecten.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-202">These properties are added as **NoteProperty** members to the output objects.</span></span> <span data-ttu-id="8cb4c-203">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-203">Wildcards are permitted.</span></span>

<span data-ttu-id="8cb4c-204">De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-204">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="8cb4c-205">Gebruik een hash-tabel als u een berekende eigenschap wilt maken.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-205">To create a calculated, property, use a hash table.</span></span>

<span data-ttu-id="8cb4c-206">Geldige sleutels zijn:</span><span class="sxs-lookup"><span data-stu-id="8cb4c-206">Valid keys are:</span></span>

- <span data-ttu-id="8cb4c-207">Naam (of label)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="8cb4c-207">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="8cb4c-208">Expressie- `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="8cb4c-208">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="8cb4c-209">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-209">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8cb4c-210">-Overs Laan</span><span class="sxs-lookup"><span data-stu-id="8cb4c-210">-Skip</span></span>

<span data-ttu-id="8cb4c-211">Hiermee wordt het opgegeven aantal items overgeslagen (niet geselecteerd).</span><span class="sxs-lookup"><span data-stu-id="8cb4c-211">Skips (does not select) the specified number of items.</span></span> <span data-ttu-id="8cb4c-212">Standaard telt de para meter **overs Laan** van het begin van de matrix of lijst met objecten, maar als de opdracht de **laatste** para meter gebruikt, telt deze vanaf het einde van de lijst of matrix.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-212">By default, the **Skip** parameter counts from the beginning of the array or list of objects, but if the command uses the **Last** parameter, it counts from the end of the list or array.</span></span>

<span data-ttu-id="8cb4c-213">In tegens telling tot de **index** parameter, die begint met tellen bij 0, begint de para meter **overs Laan** om 1.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-213">Unlike the **Index** parameter, which starts counting at 0, the **Skip** parameter begins at 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cb4c-214">-SkipLast</span><span class="sxs-lookup"><span data-stu-id="8cb4c-214">-SkipLast</span></span>

<span data-ttu-id="8cb4c-215">Hiermee wordt het opgegeven aantal items vanaf het einde van de lijst of matrix overgeslagen (niet geselecteerd).</span><span class="sxs-lookup"><span data-stu-id="8cb4c-215">Skips (does not select) the specified number of items from the end of the list or array.</span></span> <span data-ttu-id="8cb4c-216">Werkt op dezelfde manier als het gebruik van **overs Laan** samen met de **laatste** para meter.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-216">Works in the same way as using **Skip** together with **Last** parameter.</span></span>

<span data-ttu-id="8cb4c-217">In tegens telling tot de **index** parameter, die begint met tellen bij 0, begint de para meter **SkipLast** bij 1.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-217">Unlike the **Index** parameter, which starts counting at 0, the **SkipLast** parameter begins at 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cb4c-218">-Uniek</span><span class="sxs-lookup"><span data-stu-id="8cb4c-218">-Unique</span></span>

<span data-ttu-id="8cb4c-219">Hiermee wordt aangegeven dat als een subset van de invoer objecten identieke eigenschappen en waarden heeft, er slechts één lid van de subset wordt geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-219">Specifies that if a subset of the input objects has identical properties and values, only a single member of the subset will be selected.</span></span>

<span data-ttu-id="8cb4c-220">Deze para meter is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-220">This parameter is case-sensitive.</span></span> <span data-ttu-id="8cb4c-221">Als gevolg hiervan worden teken reeksen die alleen in Character-hoofdletter verschillen, als uniek beschouwd.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-221">As a result, strings that differ only in character casing are considered to be unique.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cb4c-222">-Wachten</span><span class="sxs-lookup"><span data-stu-id="8cb4c-222">-Wait</span></span>

<span data-ttu-id="8cb4c-223">Geeft aan dat de cmdlet optimalisatie uitschakelt.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-223">Indicates that the cmdlet turns off optimization.</span></span> <span data-ttu-id="8cb4c-224">Power Shell voert opdrachten uit in de volg orde waarin ze worden weer gegeven in de opdracht pijp lijn en maken het mogelijk om alle objecten te genereren.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-224">PowerShell runs commands in the order that they appear in the command pipeline and lets them generate all objects.</span></span> <span data-ttu-id="8cb4c-225">Als u een opdracht opneemt `Select-Object` met de **eerste** of **index** parameters in een opdracht pijplijn, stopt Power shell de opdracht die de objecten genereert zodra het geselecteerde aantal objecten wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-225">By default, if you include a `Select-Object` command with the **First** or **Index** parameters in a command pipeline, PowerShell stops the command that generates the objects as soon as the selected number of objects is generated.</span></span>

<span data-ttu-id="8cb4c-226">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-226">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultParameter, IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cb4c-227">-SkipIndex</span><span class="sxs-lookup"><span data-stu-id="8cb4c-227">-SkipIndex</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SkipIndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cb4c-228">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8cb4c-228">CommonParameters</span></span>

<span data-ttu-id="8cb4c-229">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-229">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8cb4c-230">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-230">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8cb4c-231">INVOER</span><span class="sxs-lookup"><span data-stu-id="8cb4c-231">INPUTS</span></span>

### <span data-ttu-id="8cb4c-232">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="8cb4c-232">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="8cb4c-233">U kunt elk object door sluizen naar `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="8cb4c-233">You can pipe any object to `Select-Object`.</span></span>

## <span data-ttu-id="8cb4c-234">UITVOER</span><span class="sxs-lookup"><span data-stu-id="8cb4c-234">OUTPUTS</span></span>

### <span data-ttu-id="8cb4c-235">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="8cb4c-235">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="8cb4c-236">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="8cb4c-236">NOTES</span></span>

- <span data-ttu-id="8cb4c-237">U kunt ook naar de `Select-Object` cmdlet verwijzen met de ingebouwde alias `select` .</span><span class="sxs-lookup"><span data-stu-id="8cb4c-237">You can also refer to the `Select-Object` cmdlet by its built-in alias, `select`.</span></span> <span data-ttu-id="8cb4c-238">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-238">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

- <span data-ttu-id="8cb4c-239">De optimalisatie functie van `Select-Object` is alleen beschikbaar voor opdrachten waarmee objecten naar de pijp lijn worden geschreven wanneer ze worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-239">The optimization feature of `Select-Object` is available only for commands that write objects to the pipeline as they are processed.</span></span> <span data-ttu-id="8cb4c-240">Dit heeft geen invloed op opdrachten die door buffer worden verwerkt en schrijf ze als een verzameling.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-240">It has no effect on commands that buffer processed objects and write them as a collection.</span></span> <span data-ttu-id="8cb4c-241">Objecten direct schrijven is een best practice voor de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8cb4c-241">Writing objects immediately is a cmdlet design best practice.</span></span> <span data-ttu-id="8cb4c-242">Zie voor meer informatie _enkelvoudige records naar de pijp lijn schrijven_ in [sterk gestimuleerde ontwikkel richtlijnen](/powershell/scripting/developer/windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="8cb4c-242">For more information, see _Write Single Records to the Pipeline_ in [Strongly Encouraged Development Guidelines](/powershell/scripting/developer/windows-powershell).</span></span>

## <span data-ttu-id="8cb4c-243">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="8cb4c-243">RELATED LINKS</span></span>

[<span data-ttu-id="8cb4c-244">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="8cb4c-244">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="8cb4c-245">Groep-object</span><span class="sxs-lookup"><span data-stu-id="8cb4c-245">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="8cb4c-246">Sorteer object</span><span class="sxs-lookup"><span data-stu-id="8cb4c-246">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="8cb4c-247">Where-object</span><span class="sxs-lookup"><span data-stu-id="8cb4c-247">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
