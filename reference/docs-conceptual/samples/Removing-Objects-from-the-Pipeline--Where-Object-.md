---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Objecten verwijderen uit de pijp lijn waarbij het object
description: Met de cmdlet Where-Object kunt u objecten filteren die worden door gegeven in de pijp lijn.
ms.openlocfilehash: e744dc671303711f1cbe8cc724a97c3327c1da85
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500110"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="068e4-104">Objecten uit de pijplijn verwijderen (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="068e4-104">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="068e4-105">In Power shell genereert u vaak meerdere objecten naar een pijp lijn dan u wilt.</span><span class="sxs-lookup"><span data-stu-id="068e4-105">In PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="068e4-106">U kunt de eigenschappen van bepaalde objecten opgeven die moeten worden weer gegeven met behulp van de `Format-*` -cmdlets, maar dit biedt geen ondersteuning voor het probleem van het verwijderen van volledige objecten uit de weer gave.</span><span class="sxs-lookup"><span data-stu-id="068e4-106">You can specify the properties of particular objects to display by using the `Format-*` cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="068e4-107">Misschien wilt u objecten filteren vóór het einde van een pijp lijn, zodat u alleen acties kunt uitvoeren op een subset van de eerste gegenereerde objecten.</span><span class="sxs-lookup"><span data-stu-id="068e4-107">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="068e4-108">Power shell bevat een `Where-Object` cmdlet waarmee u elk object in de pijp lijn kunt testen en alleen door geven aan de pijp lijn als het voldoet aan een bepaalde test voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="068e4-108">PowerShell includes a `Where-Object` cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="068e4-109">Objecten die de test niet door lopen, worden uit de pijp lijn verwijderd.</span><span class="sxs-lookup"><span data-stu-id="068e4-109">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="068e4-110">U geeft de test voorwaarde op als de waarde van de para meter **FilterScript** .</span><span class="sxs-lookup"><span data-stu-id="068e4-110">You supply the test condition as the value of the **FilterScript** parameter.</span></span>

## <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="068e4-111">Eenvoudige tests uitvoeren met Where-Object</span><span class="sxs-lookup"><span data-stu-id="068e4-111">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="068e4-112">De waarde van **FilterScript** is een *script blok* : een of meer Power shell-opdrachten omgeven door accolades ( `{}` ), die als waar of ONWAAR worden geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="068e4-112">The value of **FilterScript** is a *script block* - one or more PowerShell commands surrounded by braces (`{}`) - that evaluates to true or false.</span></span> <span data-ttu-id="068e4-113">Deze script blokken kunnen zeer eenvoudig zijn, maar het maken ervan vereist dat u weet wat een ander Power shell-concept, vergelijkings operators is.</span><span class="sxs-lookup"><span data-stu-id="068e4-113">These script blocks can be very simple, but creating them requires knowing about another PowerShell concept, comparison operators.</span></span> <span data-ttu-id="068e4-114">Een vergelijkings operator vergelijkt de items die aan elkaar worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="068e4-114">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="068e4-115">Vergelijkings operatoren beginnen met een koppel teken ( `-` ) en worden gevolgd door een naam.</span><span class="sxs-lookup"><span data-stu-id="068e4-115">Comparison operators begin with a hyphen character (`-`) and are followed by a name.</span></span> <span data-ttu-id="068e4-116">Eenvoudige vergelijkings operators werken aan bijna elk soort object.</span><span class="sxs-lookup"><span data-stu-id="068e4-116">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="068e4-117">De geavanceerde vergelijkings operators kunnen alleen werken met tekst of matrices.</span><span class="sxs-lookup"><span data-stu-id="068e4-117">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="068e4-118">Wanneer u werkt met tekst, zijn de Power shell-vergelijkings operatoren standaard niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="068e4-118">By default, when working with text, PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="068e4-119">Als gevolg van het parseren van overwegingen, symbolen zoals `<` , `>` , en `=` worden niet gebruikt als vergelijkings operators.</span><span class="sxs-lookup"><span data-stu-id="068e4-119">Due to parsing considerations, symbols such as `<`,`>`, and `=` are not used as comparison operators.</span></span> <span data-ttu-id="068e4-120">In plaats daarvan bestaan vergelijkings operatoren uit letters.</span><span class="sxs-lookup"><span data-stu-id="068e4-120">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="068e4-121">De basis-vergelijkings operatoren worden weer gegeven in de volgende tabel.</span><span class="sxs-lookup"><span data-stu-id="068e4-121">The basic comparison operators are listed in the following table.</span></span>

| <span data-ttu-id="068e4-122">Vergelijkingsoperator</span><span class="sxs-lookup"><span data-stu-id="068e4-122">Comparison Operator</span></span> |                  <span data-ttu-id="068e4-123">Betekenis</span><span class="sxs-lookup"><span data-stu-id="068e4-123">Meaning</span></span>                   |    <span data-ttu-id="068e4-124">Voor beeld (retourneert waar)</span><span class="sxs-lookup"><span data-stu-id="068e4-124">Example (returns true)</span></span>    |
| ------------------- | ------------------------------------------ | ---------------------------- |
| <span data-ttu-id="068e4-125">-eq</span><span class="sxs-lookup"><span data-stu-id="068e4-125">-eq</span></span>                 | <span data-ttu-id="068e4-126">is gelijk aan</span><span class="sxs-lookup"><span data-stu-id="068e4-126">is equal to</span></span>                                | <span data-ttu-id="068e4-127">1-EQ 1</span><span class="sxs-lookup"><span data-stu-id="068e4-127">1 -eq 1</span></span>                      |
| <span data-ttu-id="068e4-128">-ne</span><span class="sxs-lookup"><span data-stu-id="068e4-128">-ne</span></span>                 | <span data-ttu-id="068e4-129">Is niet gelijk aan</span><span class="sxs-lookup"><span data-stu-id="068e4-129">Is not equal to</span></span>                            | <span data-ttu-id="068e4-130">1-ne 2</span><span class="sxs-lookup"><span data-stu-id="068e4-130">1 -ne 2</span></span>                      |
| <span data-ttu-id="068e4-131">-lt</span><span class="sxs-lookup"><span data-stu-id="068e4-131">-lt</span></span>                 | <span data-ttu-id="068e4-132">Is kleiner dan</span><span class="sxs-lookup"><span data-stu-id="068e4-132">Is less than</span></span>                               | <span data-ttu-id="068e4-133">1-lt 2</span><span class="sxs-lookup"><span data-stu-id="068e4-133">1 -lt 2</span></span>                      |
| <span data-ttu-id="068e4-134">-Le</span><span class="sxs-lookup"><span data-stu-id="068e4-134">-le</span></span>                 | <span data-ttu-id="068e4-135">Is kleiner dan of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="068e4-135">Is less than or equal to</span></span>                   | <span data-ttu-id="068e4-136">1-Le 2</span><span class="sxs-lookup"><span data-stu-id="068e4-136">1 -le 2</span></span>                      |
| <span data-ttu-id="068e4-137">-gt</span><span class="sxs-lookup"><span data-stu-id="068e4-137">-gt</span></span>                 | <span data-ttu-id="068e4-138">Is groter dan</span><span class="sxs-lookup"><span data-stu-id="068e4-138">Is greater than</span></span>                            | <span data-ttu-id="068e4-139">2-gt 1</span><span class="sxs-lookup"><span data-stu-id="068e4-139">2 -gt 1</span></span>                      |
| <span data-ttu-id="068e4-140">-ge</span><span class="sxs-lookup"><span data-stu-id="068e4-140">-ge</span></span>                 | <span data-ttu-id="068e4-141">Is groter dan of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="068e4-141">Is greater than or equal to</span></span>                | <span data-ttu-id="068e4-142">2-ge 1</span><span class="sxs-lookup"><span data-stu-id="068e4-142">2 -ge 1</span></span>                      |
| <span data-ttu-id="068e4-143">-like</span><span class="sxs-lookup"><span data-stu-id="068e4-143">-like</span></span>               | <span data-ttu-id="068e4-144">Is vergelijkbaar (vergelijking van joker tekens voor tekst)</span><span class="sxs-lookup"><span data-stu-id="068e4-144">Is like (wildcard comparison for text)</span></span>     | <span data-ttu-id="068e4-145">"file.doc"-like "f \*. do?"</span><span class="sxs-lookup"><span data-stu-id="068e4-145">"file.doc" -like "f\*.do?"</span></span>    |
| <span data-ttu-id="068e4-146">-notlike</span><span class="sxs-lookup"><span data-stu-id="068e4-146">-notlike</span></span>            | <span data-ttu-id="068e4-147">Is niet hetzelfde (vergelijking van joker tekens voor tekst)</span><span class="sxs-lookup"><span data-stu-id="068e4-147">Is not like (wildcard comparison for text)</span></span> | <span data-ttu-id="068e4-148">"file.doc"-notlike "p\*. doc"</span><span class="sxs-lookup"><span data-stu-id="068e4-148">"file.doc" -notlike "p\*.doc"</span></span> |
| <span data-ttu-id="068e4-149">-contains</span><span class="sxs-lookup"><span data-stu-id="068e4-149">-contains</span></span>           | <span data-ttu-id="068e4-150">Contains</span><span class="sxs-lookup"><span data-stu-id="068e4-150">Contains</span></span>                                   | <span data-ttu-id="068e4-151">1, 2, 3-bevat 1</span><span class="sxs-lookup"><span data-stu-id="068e4-151">1,2,3 -contains 1</span></span>            |
| <span data-ttu-id="068e4-152">-notcontains</span><span class="sxs-lookup"><span data-stu-id="068e4-152">-notcontains</span></span>        | <span data-ttu-id="068e4-153">Bevat niet</span><span class="sxs-lookup"><span data-stu-id="068e4-153">Does not contain</span></span>                           | <span data-ttu-id="068e4-154">1, 2, 3-notcontains 4</span><span class="sxs-lookup"><span data-stu-id="068e4-154">1,2,3 -notcontains 4</span></span>         |

<span data-ttu-id="068e4-155">`Where-Object` script blokken gebruiken de speciale variabele `$_` om te verwijzen naar het huidige object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="068e4-155">`Where-Object` script blocks use the special variable `$_` to refer to the current object in the pipeline.</span></span> <span data-ttu-id="068e4-156">Hier volgt een voor beeld van hoe het werkt.</span><span class="sxs-lookup"><span data-stu-id="068e4-156">Here is an example of how it works.</span></span> <span data-ttu-id="068e4-157">Als u een lijst met getallen hebt en alleen deze wilt retour neren die kleiner zijn dan 3, kunt u gebruiken `Where-Object` om de getallen te filteren door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="068e4-157">If you have a list of numbers, and only want to return the ones that are less than 3, you can use `Where-Object` to filter the numbers by typing:</span></span>

```
1,2,3,4 | Where-Object {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a><span data-ttu-id="068e4-158">Filteren op basis van object eigenschappen</span><span class="sxs-lookup"><span data-stu-id="068e4-158">Filtering Based on Object Properties</span></span>

<span data-ttu-id="068e4-159">Omdat `$_` verwijst naar het huidige pijplijn object, hebben we toegang tot de eigenschappen van de tests.</span><span class="sxs-lookup"><span data-stu-id="068e4-159">Since `$_` refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="068e4-160">U kunt bijvoorbeeld de klasse **Win32_SystemDriver** in WMI bekijken.</span><span class="sxs-lookup"><span data-stu-id="068e4-160">As an example, we can look at the **Win32_SystemDriver** class in WMI.</span></span> <span data-ttu-id="068e4-161">Er zijn mogelijk honderden systeem Stuur Programma's op een bepaald systeem, maar u bent mogelijk alleen geïnteresseerd in een bepaalde set van de systeem Stuur Programma's, zoals die op dit moment worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="068e4-161">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="068e4-162">De relevante eigenschap is **status**voor de **Win32_SystemDriver** klasse.</span><span class="sxs-lookup"><span data-stu-id="068e4-162">For the **Win32_SystemDriver** class the relevant property is **State**.</span></span> <span data-ttu-id="068e4-163">U kunt de systeem Stuur Programma's filteren en alleen de actieve items selecteren door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="068e4-163">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq 'Running'}
```

<span data-ttu-id="068e4-164">Er wordt nog steeds een lange lijst gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="068e4-164">This still produces a long list.</span></span> <span data-ttu-id="068e4-165">U kunt filteren op alleen de ingestelde Stuur Programma's selecteren om automatisch te starten door de **Start** modus-waarde te testen:</span><span class="sxs-lookup"><span data-stu-id="068e4-165">You may want to filter to only select the drivers set to start automatically by testing the **StartMode** value as well:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Auto"}
```

```Output
DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
...
```

<span data-ttu-id="068e4-166">Dit biedt ons veel informatie die we niet meer nodig hebben omdat we weten dat de Stuur Programma's worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="068e4-166">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span>
<span data-ttu-id="068e4-167">De enige informatie die we waarschijnlijk op dit moment nodig hebben, zijn de naam en de weergave naam.</span><span class="sxs-lookup"><span data-stu-id="068e4-167">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="068e4-168">De volgende opdracht bevat alleen die twee eigenschappen, wat resulteert in veel eenvoudiger uitvoer:</span><span class="sxs-lookup"><span data-stu-id="068e4-168">The following command includes only those two properties, resulting in much simpler output:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Manual"} |
      Format-Table -Property Name,DisplayName
```

```Output
Name              DisplayName
----              -----------
AsyncMac               RAS Asynchronous Media Driver
bindflt                Windows Bind Filter Driver
bowser                 Browser
CompositeBus           Composite Bus Enumerator Driver
condrv                 Console Driver
HdAudAddService        Microsoft 1.1 UAA Function Driver for High Definition Audio Service
HDAudBus               Microsoft UAA Bus Driver for High Definition Audio
HidUsb                 Microsoft HID Class Driver
HTTP                   HTTP Service
igfx                   igfx
IntcDAud               Intel(R) Display Audio
intelppm               Intel Processor Driver
...
```

<span data-ttu-id="068e4-169">`Where-Object`De bovenstaande opdracht bevat twee elementen, maar deze kunnen worden uitgedrukt in één `Where-Object` element met behulp van de `-and` logische operator, zoals:</span><span class="sxs-lookup"><span data-stu-id="068e4-169">There are two `Where-Object` elements in the above command, but they can be expressed in a single `Where-Object` element by using the `-and` logical operator, like this:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual')} |
    Format-Table -Property Name,DisplayName
```

<span data-ttu-id="068e4-170">De standaard logische Opera tors worden weer gegeven in de volgende tabel.</span><span class="sxs-lookup"><span data-stu-id="068e4-170">The standard logical operators are listed in the following table.</span></span>

| <span data-ttu-id="068e4-171">Logische operator</span><span class="sxs-lookup"><span data-stu-id="068e4-171">Logical Operator</span></span> |                 <span data-ttu-id="068e4-172">Betekenis</span><span class="sxs-lookup"><span data-stu-id="068e4-172">Meaning</span></span>                  |  <span data-ttu-id="068e4-173">Voor beeld (retourneert waar)</span><span class="sxs-lookup"><span data-stu-id="068e4-173">Example (returns true)</span></span>  |
| ---------------- | ---------------------------------------- | ------------------------ |
| <span data-ttu-id="068e4-174">-en</span><span class="sxs-lookup"><span data-stu-id="068e4-174">-and</span></span>             | <span data-ttu-id="068e4-175">Logische en; waar als beide zijden waar zijn</span><span class="sxs-lookup"><span data-stu-id="068e4-175">Logical and; true if both sides are true</span></span> | <span data-ttu-id="068e4-176">(1-EQ 1)-en (2-EQ 2)</span><span class="sxs-lookup"><span data-stu-id="068e4-176">(1 -eq 1) -and (2 -eq 2)</span></span> |
| <span data-ttu-id="068e4-177">-of</span><span class="sxs-lookup"><span data-stu-id="068e4-177">-or</span></span>              | <span data-ttu-id="068e4-178">Logische of; waar als een van beide zijden waar is</span><span class="sxs-lookup"><span data-stu-id="068e4-178">Logical or; true if either side is true</span></span>  | <span data-ttu-id="068e4-179">(1-EQ 1)-of (1-EQ 2)</span><span class="sxs-lookup"><span data-stu-id="068e4-179">(1 -eq 1) -or (1 -eq 2)</span></span>  |
| <span data-ttu-id="068e4-180">-niet</span><span class="sxs-lookup"><span data-stu-id="068e4-180">-not</span></span>             | <span data-ttu-id="068e4-181">Logische niet; keert waar en ONWAAR om</span><span class="sxs-lookup"><span data-stu-id="068e4-181">Logical not; reverses true and false</span></span>     | <span data-ttu-id="068e4-182">-niet (1-EQ 2)</span><span class="sxs-lookup"><span data-stu-id="068e4-182">-not (1 -eq 2)</span></span>           |
| \!               | <span data-ttu-id="068e4-183">Logische niet; keert waar en ONWAAR om</span><span class="sxs-lookup"><span data-stu-id="068e4-183">Logical not; reverses true and false</span></span>     | <span data-ttu-id="068e4-184">\!(1-EQ 2)</span><span class="sxs-lookup"><span data-stu-id="068e4-184">\!(1 -eq 2)</span></span>              |
