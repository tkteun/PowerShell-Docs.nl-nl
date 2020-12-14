---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/group-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Group-Object
ms.openlocfilehash: 6198964f01a4c0dc70584cdb3e5c0e13f3965934
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705707"
---
# <span data-ttu-id="f9fb3-102">Group-Object</span><span class="sxs-lookup"><span data-stu-id="f9fb3-102">Group-Object</span></span>

## <span data-ttu-id="f9fb3-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f9fb3-103">SYNOPSIS</span></span>
<span data-ttu-id="f9fb3-104">Groeps objecten die dezelfde waarde voor opgegeven eigenschappen bevatten.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-104">Groups objects that contain the same value for specified properties.</span></span>

## <span data-ttu-id="f9fb3-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f9fb3-105">SYNTAX</span></span>

### <span data-ttu-id="f9fb3-106">Hashtabel</span><span class="sxs-lookup"><span data-stu-id="f9fb3-106">HashTable</span></span>

```
Group-Object [-NoElement] [-AsHashTable] [-AsString] [-InputObject <PSObject>]
 [[-Property] <Object[]>] [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="f9fb3-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f9fb3-107">DESCRIPTION</span></span>

<span data-ttu-id="f9fb3-108">De `Group-Object` cmdlet geeft objecten weer in groepen op basis van de waarde van een opgegeven eigenschap.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-108">The `Group-Object` cmdlet displays objects in groups based on the value of a specified property.</span></span>
<span data-ttu-id="f9fb3-109">`Group-Object` retourneert een tabel met één rij voor elke eigenschaps waarde en een kolom waarin het aantal items met die waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-109">`Group-Object` returns a table with one row for each property value and a column that displays the number of items with that value.</span></span>

<span data-ttu-id="f9fb3-110">Als u meer dan één eigenschap opgeeft, worden `Group-Object` deze eerst gegroepeerd op de waarden van de eerste eigenschap en vervolgens in elke eigenschappen groep, die wordt gegroepeerd op de waarde van de volgende eigenschap.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-110">If you specify more than one property, `Group-Object` first groups them by the values of the first property, and then, within each property group, it groups by the value of the next property.</span></span>

<span data-ttu-id="f9fb3-111">Vanaf Power shell 7 `Group-Object` kunnen de para meters **CaseSensitive** en **AsHashtable** combi neren om een hoofdletter gevoelige hash-tabel te maken.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-111">Beginning in PowerShell 7, `Group-Object` can combine the **CaseSensitive** and **AsHashtable** parameters to create a case-sensitive hash table.</span></span> <span data-ttu-id="f9fb3-112">De hash-tabel sleutels gebruiken hoofdletter gevoelige vergelijkingen en voeren een **System. Collections. Hashtable** -object uit.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-112">The hash table keys use case-sensitive comparisons and output a **System.Collections.Hashtable** object.</span></span>

## <span data-ttu-id="f9fb3-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f9fb3-113">EXAMPLES</span></span>

### <span data-ttu-id="f9fb3-114">Voor beeld 1: bestanden groeperen op extensie</span><span class="sxs-lookup"><span data-stu-id="f9fb3-114">Example 1: Group files by extension</span></span>

<span data-ttu-id="f9fb3-115">In dit voor beeld worden de bestanden op basis `$PSHOME` van de bestandsnaam extensie recursief opgehaald en gegroepeerd.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-115">This example recursively gets the files under `$PSHOME` and groups them by file name extension.</span></span> <span data-ttu-id="f9fb3-116">De uitvoer wordt verzonden naar de `Sort-Object` cmdlet, die deze sorteert op het aantal bestanden dat is gevonden voor de opgegeven extensie.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-116">The output is sent to the `Sort-Object` cmdlet, which sorts them by the count files found for the given extension.</span></span> <span data-ttu-id="f9fb3-117">De lege **naam** vertegenwoordigt directory's.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-117">The empty **Name** represents directories.</span></span>

<span data-ttu-id="f9fb3-118">In dit voor beeld wordt de para meter **element** niet gebruikt om de leden van de groep weg te laten.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-118">This example uses the **NoElement** parameter to omit the members of the group.</span></span>

```powershell
$files = Get-ChildItem -Path $PSHOME -Recurse
$files | Group-Object -Property extension -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  365 .xml
  231 .cdxml
  197
  169 .ps1xml
  142 .txt
  114 .psd1
   63 .psm1
   49 .xsd
   36 .dll
   15 .mfl
   15 .mof
...
```

### <span data-ttu-id="f9fb3-119">Voor beeld 2: gehele getallen groeperen op conflicteert en zelfs</span><span class="sxs-lookup"><span data-stu-id="f9fb3-119">Example 2: Group integers by odds and evens</span></span>

<span data-ttu-id="f9fb3-120">In dit voor beeld ziet u hoe u script blokken gebruikt als de waarde van de **eigenschaps** parameter.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-120">This example shows how to use script blocks as the value of the **Property** parameter.</span></span> <span data-ttu-id="f9fb3-121">Met deze opdracht worden de gehele getallen van 1 tot en met 20, gegroepeerd op conflicteert en zelfs weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-121">This command displays the integers from 1 to 20, grouped by odds and even.</span></span>

```powershell
1..20 | Group-Object -Property {$_ % 2}
```

```Output
Count Name                      Group
----- ----                      -----
   10 0                         {2, 4, 6, 8...}
   10 1                         {1, 3, 5, 7...}
```

### <span data-ttu-id="f9fb3-122">Voor beeld 3: gebeurtenissen in gebeurtenis logboeken groeperen op entry type is</span><span class="sxs-lookup"><span data-stu-id="f9fb3-122">Example 3: Group event log events by EntryType</span></span>

<span data-ttu-id="f9fb3-123">In dit voor beeld worden de 1.000 meest recente vermeldingen in het systeem gebeurtenis logboek weer gegeven, gegroepeerd op **entry type is**.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-123">This example displays the 1,000 most recent entries in the System event log, grouped by **EntryType**.</span></span>

<span data-ttu-id="f9fb3-124">In de uitvoer staat de kolom **aantal** voor het aantal items in elke groep.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-124">In the output, the **Count** column represents the number of entries in each group.</span></span> <span data-ttu-id="f9fb3-125">De kolom **naam** vertegenwoordigt de waarden van het type **Event** waarmee een groep wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-125">The **Name** column represents the **EventType** values that define a group.</span></span> <span data-ttu-id="f9fb3-126">De kolom **groep** vertegenwoordigt de objecten in elke groep.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-126">The **Group** column represents the objects in each group.</span></span>

```powershell
Get-WinEvent -LogName System -MaxEvents 1000 | Group-Object -Property LevelDisplayName
```

```Output
Count Name          Group
----- ----          -----
  153 Error         {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  722 Information   {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  125 Warning       {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
```

### <span data-ttu-id="f9fb3-127">Voor beeld 4: groeps processen op prioriteits klasse</span><span class="sxs-lookup"><span data-stu-id="f9fb3-127">Example 4: Group processes by priority class</span></span>

<span data-ttu-id="f9fb3-128">In dit voor beeld ziet u het effect van de para meter **element** .</span><span class="sxs-lookup"><span data-stu-id="f9fb3-128">This example demonstrates the effect of the **NoElement** parameter.</span></span> <span data-ttu-id="f9fb3-129">Met deze opdrachten worden de processen op de computer gegroepeerd op prioriteits klasse.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-129">These commands group the processes on the computer by priority class.</span></span>

<span data-ttu-id="f9fb3-130">Met de eerste opdracht wordt de- `Get-Process` cmdlet gebruikt om de processen op de computer op te halen en de objecten naar de pijp lijn te verzenden.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-130">The first command uses the `Get-Process` cmdlet to get the processes on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="f9fb3-131">`Group-Object`groepeert de objecten op de waarde van de eigenschap **PriorityClass** van het proces.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-131">`Group-Object`groups the objects by the value of the **PriorityClass** property of the process.</span></span>

<span data-ttu-id="f9fb3-132">In het tweede voor beeld wordt de para meter **element** niet gebruikt om de leden van de groep uit de uitvoer te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-132">The second example uses the **NoElement** parameter to eliminate the members of the group from the output.</span></span> <span data-ttu-id="f9fb3-133">Het resultaat is een tabel met alleen de waarde van de eigenschap **Count** en **name** .</span><span class="sxs-lookup"><span data-stu-id="f9fb3-133">The result is a table with only the **Count** and **Name** property value.</span></span>

<span data-ttu-id="f9fb3-134">De resultaten worden weer gegeven in de volgende voorbeeld uitvoer.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-134">The results are shown in the following sample output.</span></span>

```powershell
Get-Process | Group-Object -Property PriorityClass
```

```Output
Count Name         Group
----- ----         -----
   55 Normal       {System.Diagnostics.Process (AdtAgent), System.Diagnosti...
    1              {System.Diagnostics.Process (Idle)}
    3 High         {System.Diagnostics.Process (Newproc), System.Diagnostic...
    2 BelowNormal  {System.Diagnostics.Process (winperf),
```

```powershell
Get-Process | Group-Object -Property PriorityClass -NoElement
```

```Output
Count Name
----- ----
   55 Normal
    1
    3 High
    2 BelowNormal
```

### <span data-ttu-id="f9fb3-135">Voor beeld 5: processen groeperen op naam</span><span class="sxs-lookup"><span data-stu-id="f9fb3-135">Example 5: Group processes by name</span></span>

<span data-ttu-id="f9fb3-136">In het volgende voor beeld wordt gebruikgemaakt `Group-Object` van het groeperen van meerdere exemplaren van processen die op de lokale computer worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-136">The following example uses `Group-Object` to group multiple instances of processes running on the local computer.</span></span> <span data-ttu-id="f9fb3-137">`Where-Object` Hiermee worden processen met meer dan één exemplaar weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-137">`Where-Object` displays processes with more than one instance.</span></span>

```powershell
Get-Process | Group-Object -Property Name -NoElement | Where-Object {$_.Count -gt 1}
```

```Output
Count Name
----- ----
2     csrss
5     svchost
2     winlogon
2     wmiprvse
```

### <span data-ttu-id="f9fb3-138">Voor beeld 6: objecten groeperen in een hash-tabel</span><span class="sxs-lookup"><span data-stu-id="f9fb3-138">Example 6: Group objects in a hash table</span></span>

<span data-ttu-id="f9fb3-139">In dit voor beeld worden de para meters **AsHashTable** en **AsString** gebruikt voor het retour neren van de groepen in een hash-tabel, als een verzameling sleutel-waardeparen.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-139">This example uses the **AsHashTable** and **AsString** parameters to return the groups in a hash table, as a collection of key-value pairs.</span></span>

<span data-ttu-id="f9fb3-140">In de resulterende hash-tabel is elke eigenschaps waarde een sleutel en de groeps elementen zijn de waarden.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-140">In the resulting hash table, each property value is a key, and the group elements are the values.</span></span>
<span data-ttu-id="f9fb3-141">Omdat elke sleutel een eigenschap van het object van een hash-tabel is, kunt u de teken punt notatie gebruiken om de waarden weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-141">Because each key is a property of the hash table object, you can use dot notation to display the values.</span></span>

<span data-ttu-id="f9fb3-142">Met de eerste opdracht `Get` worden de `Set` -en-cmdlets in de sessie opgehaald, gegroepeerd op werk woord, worden de groepen geretourneerd als een hash-tabel en wordt de hash-tabel in de `$A` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-142">The first command gets the `Get` and `Set` cmdlets in the session, groups them by verb, returns the groups as a hash table, and saves the hash table in the `$A` variable.</span></span>

<span data-ttu-id="f9fb3-143">Met de tweede opdracht wordt de hash-tabel in weer gegeven `$A` .</span><span class="sxs-lookup"><span data-stu-id="f9fb3-143">The second command displays the hash table in `$A`.</span></span> <span data-ttu-id="f9fb3-144">Er zijn twee sleutel-waardeparen, een voor de `Get` cmdlets en één voor de `Set` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-144">There are two key-value pairs, one for the `Get` cmdlets and one for the `Set` cmdlets.</span></span>

<span data-ttu-id="f9fb3-145">De derde opdracht maakt gebruik van punt notatie `$A.Get` om de waarden van de **Get** -toets in weer te geven `$A` .</span><span class="sxs-lookup"><span data-stu-id="f9fb3-145">The third command uses dot notation, `$A.Get` to display the values of the **Get** key in `$A`.</span></span> <span data-ttu-id="f9fb3-146">De waarden zijn **CmdletInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-146">The values are **CmdletInfo** object.</span></span> <span data-ttu-id="f9fb3-147">Met de para meter **AsString** worden de objecten in de groepen niet geconverteerd naar teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-147">The **AsString** parameter doesn't convert the objects in the groups to strings.</span></span>

```powershell
$A = Get-Command Get-*, Set-* -CommandType cmdlet | Group-Object -Property Verb -AsHashTable -AsString
$A
```

```Output
Name     Value
----     -----
Get      {Get-Acl, Get-Alias, Get-AppLockerFileInformation, Get-AppLockerPolicy...}
Set      {Set-Acl, Set-Alias, Set-AppBackgroundTaskResourcePolicy, Set-AppLockerPolicy...}
```

```powershell
$A.Get
```

```Output
CommandType     Name                                Version    Source
-----------     ----                                -------    ------
Cmdlet          Get-Acl                             7.0.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-Alias                           7.0.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-AppLockerFileInformation        2.0.0.0    AppLocker
Cmdlet          Get-AppLockerPolicy                 2.0.0.0    AppLocker
...
```

### <span data-ttu-id="f9fb3-148">Voor beeld 7: een hoofdletter gevoelige hash-tabel maken</span><span class="sxs-lookup"><span data-stu-id="f9fb3-148">Example 7: Create a case-sensitive hash table</span></span>

<span data-ttu-id="f9fb3-149">In dit voor beeld worden de para meters **CaseSensitive** en **AsHashTable** gecombineerd om een hoofdletter gevoelige hash-tabel te maken.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-149">This example combines the **CaseSensitive** and **AsHashTable** parameters to create a case-sensitive hash table.</span></span> <span data-ttu-id="f9fb3-150">De bestanden in het voor beeld hebben uitbrei dingen van `.txt` en `.TXT` .</span><span class="sxs-lookup"><span data-stu-id="f9fb3-150">The files in the example have extensions of `.txt` and `.TXT`.</span></span>

```powershell
$hash = Get-ChildItem -Path C:\Files | Group-Object -Property Extension -CaseSensitive -AsHashTable
$hash
```

```Output
Name           Value
----           -----
.TXT           {C:\Files\File7.TXT, C:\Files\File8.TXT, C:\Files\File9.TXT}
.txt           {C:\Files\file1.txt, C:\Files\file2.txt, C:\Files\file3.txt}
```

<span data-ttu-id="f9fb3-151">De `$hash` variabele slaat het object **System. Collections. hashtabel** op.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-151">The `$hash` variable stores the **System.Collections.Hashtable** object.</span></span> <span data-ttu-id="f9fb3-152">`Get-ChildItem` Hiermee worden de bestands namen opgehaald uit de `C:\Files` Directory en worden de **System. io. file info** -objecten omlaag in de pijp lijn verzonden.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-152">`Get-ChildItem` gets the file names from the `C:\Files` directory and sends the **System.IO.FileInfo** objects down the pipeline.</span></span> <span data-ttu-id="f9fb3-153">`Group-Object`de objecten worden gegroepeerd met de **extensie** van de **eigenschaps** waarde.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-153">`Group-Object` groups the objects using the **Property** value **Extension**.</span></span> <span data-ttu-id="f9fb3-154">De para meters **CaseSensitive** en **AsHashTable** maken de tabel hash en de sleutels worden gegroepeerd met behulp van hoofdletter gevoelige sleutels `.txt` en `.TXT` .</span><span class="sxs-lookup"><span data-stu-id="f9fb3-154">The **CaseSensitive** and **AsHashTable** parameters create the hash table and the keys are grouped using the case-sensitive keys `.txt` and `.TXT`.</span></span>

## <span data-ttu-id="f9fb3-155">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f9fb3-155">PARAMETERS</span></span>

### <span data-ttu-id="f9fb3-156">-AsHashTable</span><span class="sxs-lookup"><span data-stu-id="f9fb3-156">-AsHashTable</span></span>

<span data-ttu-id="f9fb3-157">Geeft aan dat deze cmdlet de groep als een hash-tabel retourneert.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-157">Indicates that this cmdlet returns the group as a hash table.</span></span> <span data-ttu-id="f9fb3-158">De sleutels van de hash-tabel zijn de eigenschapwaarden waarmee de objecten worden gegroepeerd.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-158">The keys of the hash table are the property values by which the objects are grouped.</span></span> <span data-ttu-id="f9fb3-159">De waarden van de hash-tabel zijn de objecten met die eigenschaps waarde.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-159">The values of the hash table are the objects that have that property value.</span></span>

<span data-ttu-id="f9fb3-160">De **AsHashTable** -para meter retourneert elke hash-tabel waarin elke sleutel een exemplaar van het gegroepeerde object is.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-160">By itself, the **AsHashTable** parameter returns each hash table in which each key is an instance of the grouped object.</span></span> <span data-ttu-id="f9fb3-161">In combi natie met de para meter **AsString** zijn de sleutels in de hash-tabel teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-161">When used with the **AsString** parameter, the keys in the hash table are strings.</span></span>

<span data-ttu-id="f9fb3-162">Vanaf Power shell 7, voor het maken van hoofdletter gevoelige hash-tabellen, neemt u **CaseSensitive** en **AsHashtable** op in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-162">Beginning in PowerShell 7, to create case-sensitive hash tables, include **CaseSensitive** and **AsHashtable** in your command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: AHT

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9fb3-163">-AsString</span><span class="sxs-lookup"><span data-stu-id="f9fb3-163">-AsString</span></span>

<span data-ttu-id="f9fb3-164">Geeft aan dat met deze cmdlet de hash-tabel sleutels naar teken reeksen worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-164">Indicates that this cmdlet converts the hash table keys to strings.</span></span> <span data-ttu-id="f9fb3-165">De hash-tabel sleutels zijn standaard instanties van het gegroepeerde object.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-165">By default, the hash table keys are instances of the grouped object.</span></span> <span data-ttu-id="f9fb3-166">Deze para meter is alleen geldig in combi natie met de para meter **AsHashTable** .</span><span class="sxs-lookup"><span data-stu-id="f9fb3-166">This parameter is valid only when used with the **AsHashTable** parameter.</span></span>

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

### <span data-ttu-id="f9fb3-167">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="f9fb3-167">-CaseSensitive</span></span>

<span data-ttu-id="f9fb3-168">Geeft aan dat met deze cmdlet de groepering hoofdletter gevoelig wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-168">Indicates that this cmdlet makes the grouping case-sensitive.</span></span> <span data-ttu-id="f9fb3-169">Zonder deze para meter kunnen de eigenschaps waarden van objecten in een groep verschillende cases hebben.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-169">Without this parameter, the property values of objects in a group might have different cases.</span></span>

<span data-ttu-id="f9fb3-170">Vanaf Power shell 7, voor het maken van hoofdletter gevoelige hash-tabellen, neemt u **CaseSensitive** en **AsHashtable** op in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-170">Beginning in PowerShell 7, to create case-sensitive hash tables, include **CaseSensitive** and **AsHashtable** in your command.</span></span>

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

### <span data-ttu-id="f9fb3-171">-Cultuur</span><span class="sxs-lookup"><span data-stu-id="f9fb3-171">-Culture</span></span>

<span data-ttu-id="f9fb3-172">Hiermee geeft u de cultuur op die moet worden gebruikt bij het vergelijken van teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-172">Specifies the culture to use when comparing strings.</span></span>

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

### <span data-ttu-id="f9fb3-173">-Input object</span><span class="sxs-lookup"><span data-stu-id="f9fb3-173">-InputObject</span></span>

<span data-ttu-id="f9fb3-174">Geeft aan welke objecten moeten worden gegroepeerd.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-174">Specifies the objects to group.</span></span> <span data-ttu-id="f9fb3-175">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-175">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="f9fb3-176">Wanneer u de para meter **input object** gebruikt voor het verzenden van een verzameling objecten naar `Group-Object` , ontvangt u `Group-Object` één object dat de verzameling vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-176">When you use the **InputObject** parameter to submit a collection of objects to `Group-Object`, `Group-Object` receives one object that represents the collection.</span></span> <span data-ttu-id="f9fb3-177">Als gevolg hiervan wordt een afzonderlijke groep met dat object gemaakt als lid.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-177">As a result, it creates a single group with that object as its member.</span></span>

<span data-ttu-id="f9fb3-178">Als u de objecten in een verzameling wilt groeperen, pipet u de objecten naar `Group-Object` .</span><span class="sxs-lookup"><span data-stu-id="f9fb3-178">To group the objects in a collection, pipe the objects to `Group-Object`.</span></span>

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

### <span data-ttu-id="f9fb3-179">-Element</span><span class="sxs-lookup"><span data-stu-id="f9fb3-179">-NoElement</span></span>

<span data-ttu-id="f9fb3-180">Geeft aan dat met deze cmdlet de leden van een groep uit de resultaten worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-180">Indicates that this cmdlet omits the members of a group from the results.</span></span>

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

### <span data-ttu-id="f9fb3-181">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="f9fb3-181">-Property</span></span>

<span data-ttu-id="f9fb3-182">Hiermee geeft u de eigenschappen voor groeperen op.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-182">Specifies the properties for grouping.</span></span> <span data-ttu-id="f9fb3-183">De objecten worden ingedeeld in groepen op basis van de waarde van de opgegeven eigenschap.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-183">The objects are arranged into groups based on the value of the specified property.</span></span>

<span data-ttu-id="f9fb3-184">De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-184">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="f9fb3-185">De berekende eigenschap kan een script blok of een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-185">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="f9fb3-186">Geldige sleutel-waardeparen zijn:</span><span class="sxs-lookup"><span data-stu-id="f9fb3-186">Valid key-value pairs are:</span></span>

- <span data-ttu-id="f9fb3-187">Expressie- `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="f9fb3-187">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="f9fb3-188">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-188">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9fb3-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f9fb3-189">CommonParameters</span></span>

<span data-ttu-id="f9fb3-190">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f9fb3-191">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f9fb3-192">INVOER</span><span class="sxs-lookup"><span data-stu-id="f9fb3-192">INPUTS</span></span>

### <span data-ttu-id="f9fb3-193">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="f9fb3-193">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="f9fb3-194">U kunt elk object door sluizen naar `Group-Object` .</span><span class="sxs-lookup"><span data-stu-id="f9fb3-194">You can pipe any object to `Group-Object`.</span></span>

## <span data-ttu-id="f9fb3-195">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f9fb3-195">OUTPUTS</span></span>

### <span data-ttu-id="f9fb3-196">Micro soft. Power shell. commands. GroupInfo of System. Collections. hashtabel</span><span class="sxs-lookup"><span data-stu-id="f9fb3-196">Microsoft.PowerShell.Commands.GroupInfo or System.Collections.Hashtable</span></span>

<span data-ttu-id="f9fb3-197">Wanneer u de para meter **AsHashTable** gebruikt, `Group-Object` wordt een **Hashtable** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-197">When you use the **AsHashTable** parameter, `Group-Object` returns a **Hashtable** object.</span></span>
<span data-ttu-id="f9fb3-198">Anders wordt een **GroupInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-198">Otherwise, it returns a **GroupInfo** object.</span></span>

## <span data-ttu-id="f9fb3-199">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f9fb3-199">NOTES</span></span>

<span data-ttu-id="f9fb3-200">U kunt de para meter **GroupBy** van de Format-cmdlets, zoals `Format-Table` en `Format-List` , gebruiken voor het groeperen van objecten.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-200">You can use the **GroupBy** parameter of the formatting cmdlets, such as `Format-Table` and `Format-List`, to group objects.</span></span> <span data-ttu-id="f9fb3-201">In tegens telling tot `Group-Object` , waarmee een enkele tabel wordt gemaakt met een rij voor elke eigenschaps waarde, maken de para meter **GroupBy** een tabel voor elke eigenschaps waarde met een rij voor elk item met de waarde van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-201">Unlike `Group-Object`, which creates a single table with a row for each property value, the **GroupBy** parameters create a table for each property value with a row for each item that has the property value.</span></span>

<span data-ttu-id="f9fb3-202">`Group-Object` vereist niet dat de objecten die worden gegroepeerd hetzelfde Microsoft .NET-kern type hebben.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-202">`Group-Object` doesn't require that the objects being grouped are of the same Microsoft .NET Core type.</span></span> <span data-ttu-id="f9fb3-203">Bij het groeperen van objecten van verschillende .NET-kern typen, `Group-Object` worden de volgende regels gebruikt:</span><span class="sxs-lookup"><span data-stu-id="f9fb3-203">When grouping objects of different .NET Core types, `Group-Object` uses the following rules:</span></span>

- <span data-ttu-id="f9fb3-204">Dezelfde eigenschapnamen en typen.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-204">Same Property Names and Types.</span></span>

  <span data-ttu-id="f9fb3-205">Als de objecten een eigenschap hebben met de opgegeven naam en de eigenschaps waarden hetzelfde .NET core-type hebben, worden de eigenschaps waarden gegroepeerd met dezelfde regels die zouden worden gebruikt voor objecten van hetzelfde type.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-205">If the objects have a property with the specified name, and the property values have the same .NET Core type, the property values are grouped by using the same rules that would be used for objects of the same type.</span></span>

- <span data-ttu-id="f9fb3-206">Dezelfde eigenschapnamen, verschillende typen.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-206">Same Property Names, Different Types.</span></span>

  <span data-ttu-id="f9fb3-207">Als de objecten een eigenschap hebben met de opgegeven naam, maar de eigenschaps waarden een ander .NET-kern type hebben in verschillende objecten, `Group-Object` gebruikt het .net-kern type van het eerste exemplaar van de eigenschap als .net-kern type voor die eigenschaps groep.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-207">If the objects have a property with the specified name, but the property values have a different .NET Core type in different objects, `Group-Object` uses the .NET Core type of the first occurrence of the property as the .NET Core type for that property group.</span></span> <span data-ttu-id="f9fb3-208">Wanneer een object een eigenschap heeft met een ander type, wordt de waarde van de eigenschap geconverteerd naar het type voor die groep.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-208">When an object has a property with a different type, the property value is converted to the type for that group.</span></span> <span data-ttu-id="f9fb3-209">Als het type conversie mislukt, is het object niet opgenomen in de groep.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-209">If the type conversion fails, the object isn't included in the group.</span></span>

- <span data-ttu-id="f9fb3-210">Eigenschappen ontbreken.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-210">Missing Properties.</span></span>

  <span data-ttu-id="f9fb3-211">Objecten waarvoor geen eigenschap is opgegeven, kunnen niet worden gegroepeerd.</span><span class="sxs-lookup"><span data-stu-id="f9fb3-211">Objects that don't have a specified property can't be grouped.</span></span> <span data-ttu-id="f9fb3-212">Objecten die niet zijn gegroepeerd, worden weer gegeven in de uiteindelijke uitvoer van de **GroupInfo** -objecten in een groep met de naam `AutomationNull.Value` .</span><span class="sxs-lookup"><span data-stu-id="f9fb3-212">Objects that aren't grouped appear in the final **GroupInfo** object output in a group named `AutomationNull.Value`.</span></span>

## <span data-ttu-id="f9fb3-213">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f9fb3-213">RELATED LINKS</span></span>

[<span data-ttu-id="f9fb3-214">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="f9fb3-214">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="f9fb3-215">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="f9fb3-215">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="f9fb3-216">Compare-object</span><span class="sxs-lookup"><span data-stu-id="f9fb3-216">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="f9fb3-217">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="f9fb3-217">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="f9fb3-218">Meting object</span><span class="sxs-lookup"><span data-stu-id="f9fb3-218">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="f9fb3-219">New-Object</span><span class="sxs-lookup"><span data-stu-id="f9fb3-219">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="f9fb3-220">Select-Object</span><span class="sxs-lookup"><span data-stu-id="f9fb3-220">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="f9fb3-221">Sorteer object</span><span class="sxs-lookup"><span data-stu-id="f9fb3-221">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="f9fb3-222">T-object</span><span class="sxs-lookup"><span data-stu-id="f9fb3-222">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="f9fb3-223">Where-object</span><span class="sxs-lookup"><span data-stu-id="f9fb3-223">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
