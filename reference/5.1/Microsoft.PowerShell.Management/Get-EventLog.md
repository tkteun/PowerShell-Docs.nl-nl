---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 3/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventLog
ms.openlocfilehash: ab1a97dc3c78bbfdcc239fd573ef3b1f839e2b21
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250808"
---
# <span data-ttu-id="2dc7b-103">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="2dc7b-103">Get-EventLog</span></span>

## <span data-ttu-id="2dc7b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2dc7b-104">SYNOPSIS</span></span>
<span data-ttu-id="2dc7b-105">Hiermee haalt u de gebeurtenissen in een gebeurtenis logboek of een lijst met de gebeurtenis logboeken op de lokale computer of externe computers op.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-105">Gets the events in an event log, or a list of the event logs, on the local computer or remote computers.</span></span>

## <span data-ttu-id="2dc7b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2dc7b-106">SYNTAX</span></span>

### <span data-ttu-id="2dc7b-107">LogName (standaard)</span><span class="sxs-lookup"><span data-stu-id="2dc7b-107">LogName (Default)</span></span>

```
Get-EventLog [-LogName] <String> [-ComputerName <String[]>] [-Newest <Int32>] [-After <DateTime>]
 [-Before <DateTime>] [-UserName <String[]>] [[-InstanceId] <Int64[]>] [-Index <Int32[]>]
 [-EntryType <String[]>] [-Source <String[]>] [-Message <String>] [-AsBaseObject]
 [<CommonParameters>]
```

### <span data-ttu-id="2dc7b-108">Lijst</span><span class="sxs-lookup"><span data-stu-id="2dc7b-108">List</span></span>

```
Get-EventLog [-ComputerName <String[]>] [-List] [-AsString] [<CommonParameters>]
```

## <span data-ttu-id="2dc7b-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2dc7b-109">DESCRIPTION</span></span>

<span data-ttu-id="2dc7b-110">De `Get-EventLog` cmdlet haalt gebeurtenissen en gebeurtenis logboeken op van lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-110">The `Get-EventLog` cmdlet gets events and event logs from local and remote computers.</span></span> <span data-ttu-id="2dc7b-111">Standaard `Get-EventLog` haalt logboeken van de lokale computer op.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-111">By default, `Get-EventLog` gets logs from the local computer.</span></span> <span data-ttu-id="2dc7b-112">Als u logboeken van externe computers wilt ontvangen, gebruikt u de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="2dc7b-112">To get logs from remote computers, use the **ComputerName** parameter.</span></span>

<span data-ttu-id="2dc7b-113">U kunt de `Get-EventLog` para meters en eigenschaps waarden gebruiken om te zoeken naar gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-113">You can use the `Get-EventLog` parameters and property values to search for events.</span></span> <span data-ttu-id="2dc7b-114">De cmdlet haalt gebeurtenissen op die overeenkomen met de opgegeven eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-114">The cmdlet gets events that match the specified property values.</span></span>

<span data-ttu-id="2dc7b-115">Power shell-cmdlets die het `EventLog` zelfstandig naam woord bevatten, werken alleen in klassieke Windows-gebeurtenis logboeken, zoals toepassing, systeem of beveiliging.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-115">PowerShell cmdlets that contain the `EventLog` noun work only on Windows classic event logs such as Application, System, or Security.</span></span> <span data-ttu-id="2dc7b-116">Als u logboeken wilt ophalen die gebruikmaken van de Windows-gebeurtenis logboek technologie in Windows Vista en latere versies van Windows, gebruikt u `Get-WinEvent` .</span><span class="sxs-lookup"><span data-stu-id="2dc7b-116">To get logs that use the Windows Event Log technology in Windows Vista and later Windows versions, use `Get-WinEvent`.</span></span>

> [!NOTE]
> <span data-ttu-id="2dc7b-117">`Get-EventLog` maakt gebruik van een Win32 API die is afgeschaft.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-117">`Get-EventLog` uses a Win32 API that is deprecated.</span></span> <span data-ttu-id="2dc7b-118">De resultaten zijn mogelijk niet nauw keurig.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-118">The results may not be accurate.</span></span> <span data-ttu-id="2dc7b-119">Gebruik `Get-WinEvent` in plaats daarvan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-119">Use the `Get-WinEvent` cmdlet instead.</span></span>

## <span data-ttu-id="2dc7b-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2dc7b-120">EXAMPLES</span></span>

### <span data-ttu-id="2dc7b-121">Voor beeld 1: gebeurtenis logboeken op de lokale computer ophalen</span><span class="sxs-lookup"><span data-stu-id="2dc7b-121">Example 1: Get event logs on the local computer</span></span>

<span data-ttu-id="2dc7b-122">In dit voor beeld wordt de lijst weer gegeven met gebeurtenis logboeken die beschikbaar zijn op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-122">This example displays the list of event logs that are available on the local computer.</span></span> <span data-ttu-id="2dc7b-123">De namen in de logboek kolom worden gebruikt in combi natie met de para meter **LogName** om op te geven welk logboek moet worden doorzocht op gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-123">The names in the Log column are used with the **LogName** parameter to specify which log is searched for events.</span></span>

```powershell
Get-EventLog -List
```

```Output
Max(K)   Retain   OverflowAction      Entries  Log
------   ------   --------------      -------  ---
15,168        0   OverwriteAsNeeded   20,792   Application
15,168        0   OverwriteAsNeeded   12,559   System
15,360        0   OverwriteAsNeeded   11,173   Windows PowerShell
```

<span data-ttu-id="2dc7b-124">De `Get-EventLog` cmdlet gebruikt de **List** -para meter om de beschik bare logboeken weer te geven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-124">The `Get-EventLog` cmdlet uses the **List** parameter to display the available logs.</span></span>

### <span data-ttu-id="2dc7b-125">Voor beeld 2: recente vermeldingen ophalen uit een gebeurtenis logboek op de lokale computer</span><span class="sxs-lookup"><span data-stu-id="2dc7b-125">Example 2: Get recent entries from an event log on the local computer</span></span>

<span data-ttu-id="2dc7b-126">In dit voor beeld worden recente vermeldingen opgehaald uit het logboek voor systeem gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-126">This example gets recent entries from the System event log.</span></span>

```powershell
Get-EventLog -LogName System -Newest 5
```

```Output
Index   Time          EntryType    Source              InstanceID   Message
-----   ----          ---------    ------              ----------   -------
13820   Jan 17 19:16  Error        DCOM                     10016   The description for Event...
13819   Jan 17 19:08  Error        DCOM                     10016   The description for Event...
13818   Jan 17 19:06  Information  Service Control...  1073748864   The start type of the Back...
13817   Jan 17 19:05  Error        DCOM                     10016   The description for Event...
13815   Jan 17 19:03  Information  Microsoft-Windows...        35   The time service is now sync...
```

<span data-ttu-id="2dc7b-127">De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem gebeurtenis logboek op te geven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-127">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System event log.</span></span> <span data-ttu-id="2dc7b-128">De **nieuwste** para meter retourneert de vijf meest recente gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-128">The **Newest** parameter returns the five most recent events.</span></span>

### <span data-ttu-id="2dc7b-129">Voor beeld 3: alle bronnen zoeken voor een specifiek aantal vermeldingen in een gebeurtenis logboek</span><span class="sxs-lookup"><span data-stu-id="2dc7b-129">Example 3: Find all sources for a specific number of entries in an event log</span></span>

<span data-ttu-id="2dc7b-130">In dit voor beeld ziet u hoe u alle bronnen vindt die zijn opgenomen in de 1000 meest recente vermeldingen in het systeem gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-130">This example shows how to find all of the sources that are included in the 1000 most recent entries in the System event log.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$Events | Group-Object -Property Source -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count   Name
-----   ----
  110   DCOM
   65   Service Control Manager
   51   Microsoft-Windows-Kern...
   14   EventLog
   14   BTHUSB
   13   Win32k
```

<span data-ttu-id="2dc7b-131">De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem logboek op te geven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-131">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="2dc7b-132">De **nieuwste** para meter selecteert de meest recente gebeurtenissen van 1000.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-132">The **Newest** parameter selects the 1000 most recent events.</span></span> <span data-ttu-id="2dc7b-133">De gebeurtenis objecten worden opgeslagen in de `$Events` variabele.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-133">The event objects are stored in the `$Events` variable.</span></span> <span data-ttu-id="2dc7b-134">De `$Events` objecten worden naar de-cmdlet verzonden via de pijp lijn `Group-Object` .</span><span class="sxs-lookup"><span data-stu-id="2dc7b-134">The `$Events` objects are sent down the pipeline to the `Group-Object` cmdlet.</span></span>
<span data-ttu-id="2dc7b-135">`Group-Object` gebruikt de **eigenschaps** parameter om de objecten op bron te groeperen en telt het aantal objecten voor elke bron.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-135">`Group-Object` uses the **Property** parameter to group the objects by source and counts the number of objects for each source.</span></span> <span data-ttu-id="2dc7b-136">De para meter **microelement** verwijdert de groeps leden uit de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-136">The **NoElement** parameter removes the group members from the output.</span></span>
<span data-ttu-id="2dc7b-137">De `Sort-Object` cmdlet gebruikt de para meter **Property** om te sorteren op het aantal van elke bron naam.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-137">The `Sort-Object` cmdlet uses the **Property** parameter to sort by the count of each source name.</span></span>
<span data-ttu-id="2dc7b-138">De **aflopende** para meter sorteert de lijst in order by aantal van hoogste naar laagste.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-138">The **Descending** parameter sorts the list in order by count from highest to lowest.</span></span>

### <span data-ttu-id="2dc7b-139">Voor beeld 4: fout gebeurtenissen van een specifiek gebeurtenis logboek ophalen</span><span class="sxs-lookup"><span data-stu-id="2dc7b-139">Example 4: Get error events from a specific event log</span></span>

<span data-ttu-id="2dc7b-140">In dit voor beeld worden fout gebeurtenissen van het systeem gebeurtenis logboek opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-140">This example gets error events from the System event log.</span></span>

```powershell
Get-EventLog -LogName System -EntryType Error
```

```Output
Index Time          EntryType   Source  InstanceID Message
----- ----          ---------   ------  ---------- -------
13296 Jan 16 13:53  Error       DCOM    10016 The description for Event ID '10016' in Source...
13291 Jan 16 13:51  Error       DCOM    10016 The description for Event ID '10016' in Source...
13245 Jan 16 11:45  Error       DCOM    10016 The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error       DCOM    10016 The description for Event ID '10016' in Source...
```

<span data-ttu-id="2dc7b-141">De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem logboek op te geven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-141">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="2dc7b-142">Met de para meter **entry type is** worden de gebeurtenissen gefilterd om alleen fout gebeurtenissen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-142">The **EntryType** parameter filters the events to show only Error events.</span></span>

### <span data-ttu-id="2dc7b-143">Voor beeld 5: gebeurtenissen ophalen uit een gebeurtenis logboek met een InstanceId en een bron waarde</span><span class="sxs-lookup"><span data-stu-id="2dc7b-143">Example 5: Get events from an event log with an InstanceId and Source value</span></span>

<span data-ttu-id="2dc7b-144">In dit voor beeld worden gebeurtenissen uit het systeem logboek voor een specifieke InstanceId en bron opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-144">This example gets events from the System log for a specific InstanceId and Source.</span></span>

```powershell
Get-EventLog -LogName System -InstanceId 10016 -Source DCOM
```

```Output
Index Time          EntryType  Source  InstanceID  Message
----- ----          ---------  ------  ----------  -------
13245 Jan 16 11:45  Error      DCOM         10016  The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error      DCOM         10016  The description for Event ID '10016' in Source...
13219 Jan 16 10:00  Error      DCOM         10016  The description for Event ID '10016' in Source...
```

<span data-ttu-id="2dc7b-145">De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem logboek op te geven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-145">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="2dc7b-146">De para meter **InstanceId** selecteert de gebeurtenissen met de opgegeven exemplaar-id.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-146">The **InstanceID** parameter selects the events with the specified Instance ID.</span></span> <span data-ttu-id="2dc7b-147">De para meter **Source** geeft u de gebeurtenis eigenschap op.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-147">The **Source** parameter specifies the event property.</span></span>

### <span data-ttu-id="2dc7b-148">Voor beeld 6: gebeurtenissen van meerdere computers ophalen</span><span class="sxs-lookup"><span data-stu-id="2dc7b-148">Example 6: Get events from multiple computers</span></span>

<span data-ttu-id="2dc7b-149">Met deze opdracht worden de gebeurtenissen uit het systeem gebeurtenis logboek op drie computers opgehaald: Server01, Server02 en Server03.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-149">This command gets the events from the System event log on three computers: Server01, Server02, and Server03.</span></span>

```powershell
Get-EventLog -LogName System -ComputerName Server01, Server02, Server03
```

<span data-ttu-id="2dc7b-150">De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem logboek op te geven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-150">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="2dc7b-151">De para meter **ComputerName** maakt gebruik van een door komma's gescheiden teken reeks voor het weer geven van de computers waarvan u de gebeurtenis logboeken wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-151">The **ComputerName** parameter uses a comma-separated string to list the computers from which you want to get the event logs.</span></span>

### <span data-ttu-id="2dc7b-152">Voor beeld 7: alle gebeurtenissen ophalen die een specifiek woord in het bericht bevatten</span><span class="sxs-lookup"><span data-stu-id="2dc7b-152">Example 7: Get all events that include a specific word in the message</span></span>

<span data-ttu-id="2dc7b-153">Met deze opdracht worden alle gebeurtenissen in het systeem gebeurtenis logboek opgehaald die een specifiek woord in het bericht van de gebeurtenis bevatten.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-153">This command gets all the events in the System event log that contain a specific word in the event's message.</span></span> <span data-ttu-id="2dc7b-154">Het is mogelijk dat de waarde van uw opgegeven **bericht** parameter is opgenomen in de inhoud van het bericht, maar niet wordt weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-154">It's possible that your specified **Message** parameter's value is included in the message's content but isn't displayed on the PowerShell console.</span></span>

```powershell
Get-EventLog -LogName System -Message *description*
```

```Output
Index Time          EntryType   Source       InstanceID   Message
----- ----          ---------   ------       ----------   -------
13821 Jan 17 19:17  Error       DCOM              10016   The description for Event ID '10016'...
13820 Jan 17 19:16  Error       DCOM              10016   The description for Event ID '10016'...
13819 Jan 17 19:08  Error       DCOM              10016   The description for Event ID '10016'...
```

<span data-ttu-id="2dc7b-155">De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem gebeurtenis logboek op te geven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-155">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System event log.</span></span> <span data-ttu-id="2dc7b-156">De para meter **bericht** geeft een woord op waarnaar moet worden gezocht in het veld bericht van elke gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-156">The **Message** parameter specifies a word to search for in the message field of each event.</span></span>

### <span data-ttu-id="2dc7b-157">Voor beeld 8: de eigenschaps waarden van een gebeurtenis weer geven</span><span class="sxs-lookup"><span data-stu-id="2dc7b-157">Example 8: Display the property values of an event</span></span>

<span data-ttu-id="2dc7b-158">In dit voor beeld ziet u hoe alle eigenschappen en waarden van een gebeurtenis worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-158">This example shows how to display all of an event's properties and values.</span></span>

```powershell
$A = Get-EventLog -LogName System -Newest 1
$A | Select-Object -Property *
```

```Output
EventID            : 10016
MachineName        : localhost
Data               : {}
Index              : 13821
Category           : (0)
CategoryNumber     : 0
EntryType          : Error
Message            : The description for Event ID '10016' in Source 'DCOM'...
Source             : DCOM
ReplacementStrings : {Local,...}
InstanceId         : 10016
TimeGenerated      : 1/17/2019 19:17:23
TimeWritten        : 1/17/2019 19:17:23
UserName           : username
Site               :
Container          :
```

<span data-ttu-id="2dc7b-159">De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem gebeurtenis logboek op te geven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-159">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System event log.</span></span> <span data-ttu-id="2dc7b-160">Met de **nieuwste** para meter selecteert u het meest recente gebeurtenis object.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-160">The **Newest** parameter selects the most recent event object.</span></span> <span data-ttu-id="2dc7b-161">Het object wordt opgeslagen in de `$A` variabele.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-161">The object is stored in the `$A` variable.</span></span> <span data-ttu-id="2dc7b-162">Het object in de `$A` variabele wordt via de pijp lijn naar de `Select-Object` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-162">The object in the `$A` variable is sent down the pipeline to the `Select-Object` cmdlet.</span></span>
<span data-ttu-id="2dc7b-163">`Select-Object` gebruikt de **eigenschaps** parameter met een asterisk ( `*` ) om alle eigenschappen van het object te selecteren.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-163">`Select-Object` uses the **Property** parameter with an asterisk (`*`) to select all of the object's properties.</span></span>

### <span data-ttu-id="2dc7b-164">Voor beeld 9: gebeurtenissen uit een gebeurtenis logboek ophalen met behulp van een bron-en gebeurtenis-ID</span><span class="sxs-lookup"><span data-stu-id="2dc7b-164">Example 9: Get events from an event log using a source and event ID</span></span>

<span data-ttu-id="2dc7b-165">In dit voor beeld worden gebeurtenissen voor een opgegeven bron en gebeurtenis-ID opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-165">This example gets events for a specified Source and Event ID.</span></span>

```powershell
Get-EventLog -LogName Application -Source Outlook | Where-Object {$_.EventID -eq 63} |
              Select-Object -Property Source, EventID, InstanceId, Message
```

```Output
Source   EventID   InstanceId   Message
------   -------   ----------   -------
Outlook       63   1073741887   The Exchange web service request succeeded.
Outlook       63   1073741887   Outlook detected a change notification.
Outlook       63   1073741887   The Exchange web service request succeeded.
```

<span data-ttu-id="2dc7b-166">De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het gebeurtenis logboek van de toepassing op te geven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-166">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the Application event log.</span></span> <span data-ttu-id="2dc7b-167">De para meter **Source** specificeert de naam van de toepassing, Outlook.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-167">The **Source** parameter specifies the application name, Outlook.</span></span> <span data-ttu-id="2dc7b-168">De objecten worden naar de-cmdlet verzonden via de pijp lijn `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="2dc7b-168">The objects are sent down the pipeline to the `Where-Object` cmdlet.</span></span> <span data-ttu-id="2dc7b-169">Voor elk object in de pijp lijn gebruikt de- `Where-Object` cmdlet de variabele `$_.EventID` om de eigenschap gebeurtenis-id te vergelijken met de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-169">For each object in the pipeline, the `Where-Object` cmdlet uses the variable `$_.EventID` to compare the Event ID property to the specified value.</span></span> <span data-ttu-id="2dc7b-170">De objecten worden naar de-cmdlet verzonden via de pijp lijn `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="2dc7b-170">The objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="2dc7b-171">`Select-Object` gebruikt de para meter **Property** om de eigenschappen te selecteren die u wilt weer geven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-171">`Select-Object` uses the **Property** parameter to select the properties to display in the PowerShell console.</span></span>

### <span data-ttu-id="2dc7b-172">Voor beeld 10: gebeurtenissen en groepen op basis van een eigenschap ophalen</span><span class="sxs-lookup"><span data-stu-id="2dc7b-172">Example 10: Get events and group by a property</span></span>

```powershell
Get-EventLog -LogName System -UserName NT* | Group-Object -Property UserName -NoElement |
              Select-Object -Property Count, Name
```

```Output
Count  Name
-----  ----
6031   NT AUTHORITY\SYSTEM
  42   NT AUTHORITY\LOCAL SERVICE
   4   NT AUTHORITY\NETWORK SERVICE
```

<span data-ttu-id="2dc7b-173">De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem logboek op te geven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-173">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="2dc7b-174">De para meter **username** bevat het `*` Joker teken sterretje () om een deel van de gebruikers naam op te geven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-174">The **UserName** parameter includes the asterisk (`*`) wildcard to specify a portion of the user name.</span></span> <span data-ttu-id="2dc7b-175">De gebeurtenis objecten worden in de pijp lijn naar de `Group-Object` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-175">The event objects are sent down the pipeline to the `Group-Object` cmdlet.</span></span> <span data-ttu-id="2dc7b-176">`Group-Object` maakt gebruik van de **eigenschap** para meter om op te geven dat de eigenschap **username** wordt gebruikt om de objecten te groeperen en het aantal objecten voor elke gebruikers naam te tellen.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-176">`Group-Object` uses the **Property** parameter to specify that the **UserName** property is used to group the objects and count the number of objects for each user name.</span></span> <span data-ttu-id="2dc7b-177">De para meter **microelement** verwijdert de groeps leden uit de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-177">The **NoElement** parameter removes the group members from the output.</span></span> <span data-ttu-id="2dc7b-178">De objecten worden naar de-cmdlet verzonden via de pijp lijn `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="2dc7b-178">The objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span>
<span data-ttu-id="2dc7b-179">`Select-Object` gebruikt de para meter **Property** om de eigenschappen te selecteren die u wilt weer geven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-179">`Select-Object` uses the **Property** parameter to select the properties to display in the PowerShell console.</span></span>

### <span data-ttu-id="2dc7b-180">Voor beeld 11: gebeurtenissen ophalen die zijn opgetreden tijdens een bepaald datum-en tijds bereik</span><span class="sxs-lookup"><span data-stu-id="2dc7b-180">Example 11: Get events that occurred during a specific date and time range</span></span>

<span data-ttu-id="2dc7b-181">In dit voor beeld worden fout gebeurtenissen van het logboek voor systeem gebeurtenissen opgehaald voor een opgegeven datum-en tijds bereik.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-181">This example gets Error events from the System event log for a specified date and time range.</span></span> <span data-ttu-id="2dc7b-182">De para meters **before** en **After** hebben de datum en het tijds bereik ingesteld, maar worden uitgesloten van de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-182">The **Before** and **After** parameters set the date and time range but are excluded from the output.</span></span>

```powershell
$Begin = Get-Date -Date '1/17/2019 08:00:00'
$End = Get-Date -Date '1/17/2019 17:00:00'
Get-EventLog -LogName System -EntryType Error -After $Begin -Before $End
```

```Output
Index Time          EntryType   Source   InstanceID  Message
----- ----          ---------   ------   ----------  -------
13821 Jan 17 13:40  Error       DCOM          10016  The description for Event ID...
13820 Jan 17 13:11  Error       DCOM          10016  The description for Event ID...
...
12372 Jan 17 10:08  Error       DCOM          10016  The description for Event ID...
12371 Jan 17 09:04  Error       DCOM          10016  The description for Event ID...
```

<span data-ttu-id="2dc7b-183">De `Get-Date` cmdlet gebruikt de para meter **date** om een datum en tijd op te geven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-183">The `Get-Date` cmdlet uses the **Date** parameter to specify a date and time.</span></span> <span data-ttu-id="2dc7b-184">De **DateTime** -objecten worden opgeslagen in `$Begin` de `$End` variabelen en.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-184">The **DateTime** objects are stored in the `$Begin` and `$End` variables.</span></span> <span data-ttu-id="2dc7b-185">De `Get-EventLog` cmdlet gebruikt de para meter **LogName** om het systeem logboek op te geven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-185">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="2dc7b-186">De **entry type is** para meter geeft u het type fout gebeurtenis op.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-186">The **EntryType** parameter specifies the Error event type.</span></span> <span data-ttu-id="2dc7b-187">Het datum-en tijds bereik wordt ingesteld met de para meter en de variabele **After** `$Begin` en de **before** -para meter en de `$End` variabele.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-187">The date and time range is set by the **After** parameter and `$Begin` variable and the **Before** parameter and `$End` variable.</span></span>

## <span data-ttu-id="2dc7b-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2dc7b-188">PARAMETERS</span></span>

### <span data-ttu-id="2dc7b-189">-Na</span><span class="sxs-lookup"><span data-stu-id="2dc7b-189">-After</span></span>

<span data-ttu-id="2dc7b-190">Hiermee worden gebeurtenissen opgehaald die zijn opgetreden na een opgegeven datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-190">Gets events that occurred after a specified date and time.</span></span> <span data-ttu-id="2dc7b-191">De datum en tijd van de para meter **After** worden uitgesloten van de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-191">The **After** parameter date and time are excluded from the output.</span></span> <span data-ttu-id="2dc7b-192">Voer een **DateTime** -object in, zoals de waarde die door de cmdlet wordt geretourneerd `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="2dc7b-192">Enter a **DateTime** object, such as the value returned by the `Get-Date` cmdlet.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dc7b-193">-AsBaseObject</span><span class="sxs-lookup"><span data-stu-id="2dc7b-193">-AsBaseObject</span></span>

<span data-ttu-id="2dc7b-194">Geeft aan dat met deze cmdlet een standaard **System. Diagnostics. EventLogEntry** -object wordt geretourneerd voor elke gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-194">Indicates that this cmdlet returns a standard **System.Diagnostics.EventLogEntry** object for each event.</span></span> <span data-ttu-id="2dc7b-195">Zonder deze para meter `Get-EventLog` retourneert een Extended **PSObject** -object met aanvullende eigenschappen voor **Eventlog** , **Source** en **InstanceId** .</span><span class="sxs-lookup"><span data-stu-id="2dc7b-195">Without this parameter, `Get-EventLog` returns an extended **PSObject** object with additional **EventLogName** , **Source** , and **InstanceId** properties.</span></span>

<span data-ttu-id="2dc7b-196">Als u het effect van deze para meter wilt zien, pipet u de gebeurtenissen naar de `Get-Member` cmdlet en bekijkt u de waarde **TypeName** in het resultaat.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-196">To see the effect of this parameter, pipe the events to the `Get-Member` cmdlet and examine the **TypeName** value in the result.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dc7b-197">-AsString</span><span class="sxs-lookup"><span data-stu-id="2dc7b-197">-AsString</span></span>

<span data-ttu-id="2dc7b-198">Geeft aan dat deze cmdlet de uitvoer als teken reeksen retourneert in plaats van objecten.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-198">Indicates that this cmdlet returns the output as strings, instead of objects.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dc7b-199">-Vóór</span><span class="sxs-lookup"><span data-stu-id="2dc7b-199">-Before</span></span>

<span data-ttu-id="2dc7b-200">Hiermee worden gebeurtenissen opgehaald die zijn opgetreden vóór een opgegeven datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-200">Gets events that occurred before a specified date and time.</span></span> <span data-ttu-id="2dc7b-201">De datum en tijd van de para meter **before** worden uitgesloten van de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-201">The **Before** parameter date and time are excluded from the output.</span></span> <span data-ttu-id="2dc7b-202">Voer een **DateTime** -object in, zoals de waarde die door de cmdlet wordt geretourneerd `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="2dc7b-202">Enter a **DateTime** object, such as the value returned by the `Get-Date` cmdlet.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dc7b-203">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="2dc7b-203">-ComputerName</span></span>

<span data-ttu-id="2dc7b-204">Met deze para meter wordt de NetBIOS-naam, het Internet Protocol (IP)-adres of een Fully Qualified Domain Name (FQDN) van de externe computer opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-204">This parameter specifies a remote computer's NetBIOS name, Internet Protocol (IP) address, or a fully qualified domain name (FQDN).</span></span>

<span data-ttu-id="2dc7b-205">Als de para meter **ComputerName** niet is opgegeven, wordt `Get-EventLog` standaard de lokale computer gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-205">If the **ComputerName** parameter isn't specified, `Get-EventLog` defaults to the local computer.</span></span> <span data-ttu-id="2dc7b-206">De para meter accepteert ook een punt ( `.` ) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-206">The parameter also accepts a dot (`.`) to specify the local computer.</span></span>

<span data-ttu-id="2dc7b-207">De para meter **ComputerName** is niet gebaseerd op externe communicatie met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-207">The **ComputerName** parameter doesn't rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="2dc7b-208">U kunt `Get-EventLog` met de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-208">You can use `Get-EventLog` with the **ComputerName** parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dc7b-209">-Entry type is</span><span class="sxs-lookup"><span data-stu-id="2dc7b-209">-EntryType</span></span>

<span data-ttu-id="2dc7b-210">Geeft als een teken reeks matrix het type vermelding van de gebeurtenissen die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-210">Specifies, as a string array, the entry type of the events that this cmdlet gets.</span></span>

<span data-ttu-id="2dc7b-211">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="2dc7b-211">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="2dc7b-212">Fout</span><span class="sxs-lookup"><span data-stu-id="2dc7b-212">Error</span></span>
- <span data-ttu-id="2dc7b-213">Informatie</span><span class="sxs-lookup"><span data-stu-id="2dc7b-213">Information</span></span>
- <span data-ttu-id="2dc7b-214">FailureAudit</span><span class="sxs-lookup"><span data-stu-id="2dc7b-214">FailureAudit</span></span>
- <span data-ttu-id="2dc7b-215">SuccessAudit</span><span class="sxs-lookup"><span data-stu-id="2dc7b-215">SuccessAudit</span></span>
- <span data-ttu-id="2dc7b-216">Waarschuwing</span><span class="sxs-lookup"><span data-stu-id="2dc7b-216">Warning</span></span>

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dc7b-217">-Index</span><span class="sxs-lookup"><span data-stu-id="2dc7b-217">-Index</span></span>

<span data-ttu-id="2dc7b-218">Hiermee geeft u de index waarden op die moeten worden opgehaald uit het gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-218">Specifies the index values to get from the event log.</span></span> <span data-ttu-id="2dc7b-219">De para meter accepteert een door komma's gescheiden teken reeks met waarden.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-219">The parameter accepts a comma-separated string of values.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dc7b-220">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="2dc7b-220">-InstanceId</span></span>

<span data-ttu-id="2dc7b-221">Hiermee geeft u de exemplaar-Id's op die moeten worden opgehaald uit het gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-221">Specifies the Instance IDs to get from the event log.</span></span> <span data-ttu-id="2dc7b-222">De para meter accepteert een door komma's gescheiden teken reeks met waarden.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-222">The parameter accepts a comma-separated string of values.</span></span>

```yaml
Type: System.Int64[]
Parameter Sets: LogName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dc7b-223">-Lijst</span><span class="sxs-lookup"><span data-stu-id="2dc7b-223">-List</span></span>

<span data-ttu-id="2dc7b-224">Hiermee wordt de lijst met gebeurtenis logboeken op de computer weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-224">Displays the list of event logs on the computer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dc7b-225">-LogName</span><span class="sxs-lookup"><span data-stu-id="2dc7b-225">-LogName</span></span>

<span data-ttu-id="2dc7b-226">Hiermee geeft u de naam van één gebeurtenis logboek op.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-226">Specifies the name of one event log.</span></span> <span data-ttu-id="2dc7b-227">Als u de logboek namen wilt vinden `Get-EventLog -List` .</span><span class="sxs-lookup"><span data-stu-id="2dc7b-227">To find the log names use `Get-EventLog -List`.</span></span> <span data-ttu-id="2dc7b-228">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-228">Wildcard characters are permitted.</span></span> <span data-ttu-id="2dc7b-229">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-229">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2dc7b-230">-Bericht</span><span class="sxs-lookup"><span data-stu-id="2dc7b-230">-Message</span></span>

<span data-ttu-id="2dc7b-231">Hiermee wordt een teken reeks in het gebeurtenis bericht opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-231">Specifies a string in the event message.</span></span> <span data-ttu-id="2dc7b-232">U kunt deze para meter gebruiken om te zoeken naar berichten die bepaalde woorden of zinsdelen bevatten.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-232">You can use this parameter to search for messages that contain certain words or phrases.</span></span> <span data-ttu-id="2dc7b-233">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-233">Wildcards are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: MSG

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2dc7b-234">-Nieuwste</span><span class="sxs-lookup"><span data-stu-id="2dc7b-234">-Newest</span></span>

<span data-ttu-id="2dc7b-235">Begint met de nieuwste gebeurtenissen en haalt het opgegeven aantal gebeurtenissen op.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-235">Begins with the newest events and gets the specified number of events.</span></span> <span data-ttu-id="2dc7b-236">Het aantal gebeurtenissen is bijvoorbeeld vereist `-Newest 100` .</span><span class="sxs-lookup"><span data-stu-id="2dc7b-236">The number of events is required, for example `-Newest 100`.</span></span> <span data-ttu-id="2dc7b-237">Hiermee geeft u het maximum aantal gebeurtenissen op dat wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-237">Specifies the maximum number of events that are returned.</span></span>

```yaml
Type: System.Int32
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2dc7b-238">-Source</span><span class="sxs-lookup"><span data-stu-id="2dc7b-238">-Source</span></span>

<span data-ttu-id="2dc7b-239">Hiermee geeft u als een teken reeks matrix de bronnen op die zijn geschreven naar het logboek dat deze cmdlet krijgt.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-239">Specifies, as a string array, sources that were written to the log that this cmdlet gets.</span></span> <span data-ttu-id="2dc7b-240">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-240">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ABO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2dc7b-241">-GebruikersNaam</span><span class="sxs-lookup"><span data-stu-id="2dc7b-241">-UserName</span></span>

<span data-ttu-id="2dc7b-242">Hiermee geeft u als een teken reeks matrix de gebruikers namen op die aan gebeurtenissen zijn gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-242">Specifies, as a string array, user names that are associated with events.</span></span> <span data-ttu-id="2dc7b-243">Voer namen of naam patronen in, zoals `User01` , `User*` of `Domain01\User*` .</span><span class="sxs-lookup"><span data-stu-id="2dc7b-243">Enter names or name patterns, such as `User01`, `User*`, or `Domain01\User*`.</span></span> <span data-ttu-id="2dc7b-244">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-244">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2dc7b-245">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2dc7b-245">CommonParameters</span></span>

<span data-ttu-id="2dc7b-246">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-246">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2dc7b-247">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-247">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2dc7b-248">INVOER</span><span class="sxs-lookup"><span data-stu-id="2dc7b-248">INPUTS</span></span>

### <span data-ttu-id="2dc7b-249">Geen</span><span class="sxs-lookup"><span data-stu-id="2dc7b-249">None</span></span>

<span data-ttu-id="2dc7b-250">U kunt geen pipe invoer naar `Get-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="2dc7b-250">You cannot pipe input to `Get-EventLog`.</span></span>

## <span data-ttu-id="2dc7b-251">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2dc7b-251">OUTPUTS</span></span>

### <span data-ttu-id="2dc7b-252">System. Diagnostics. EventLogEntry.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-252">System.Diagnostics.EventLogEntry.</span></span> <span data-ttu-id="2dc7b-253">System. Diagnostics. EventLog.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-253">System.Diagnostics.EventLog.</span></span> <span data-ttu-id="2dc7b-254">System. String</span><span class="sxs-lookup"><span data-stu-id="2dc7b-254">System.String</span></span>

<span data-ttu-id="2dc7b-255">Als de para meter **LogName** is opgegeven, is de uitvoer een verzameling **System. Diagnostics. EventLogEntry** -objecten.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-255">If the **LogName** parameter is specified, the output is a collection of **System.Diagnostics.EventLogEntry** objects.</span></span>

<span data-ttu-id="2dc7b-256">Als alleen de **lijst** parameter is opgegeven, is de uitvoer een verzameling **System. Diagnostics. Eventlog** -objecten.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-256">If only the **List** parameter is specified, the output is a collection of **System.Diagnostics.EventLog** objects.</span></span>

<span data-ttu-id="2dc7b-257">Als zowel de **lijst** -als de **AsString** -para meters zijn opgegeven, is de uitvoer een verzameling **System. String** -objecten.</span><span class="sxs-lookup"><span data-stu-id="2dc7b-257">If both the **List** and **AsString** parameters are specified, the output is a collection of **System.String** objects.</span></span>

## <span data-ttu-id="2dc7b-258">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2dc7b-258">NOTES</span></span>

<span data-ttu-id="2dc7b-259">De cmdlets `Get-EventLog` en `Get-WinEvent` worden niet ondersteund in de Windows Preinstallation Environment (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="2dc7b-259">The cmdlets `Get-EventLog` and `Get-WinEvent` are not supported in the Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="2dc7b-260">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2dc7b-260">RELATED LINKS</span></span>

[<span data-ttu-id="2dc7b-261">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="2dc7b-261">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="2dc7b-262">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="2dc7b-262">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="2dc7b-263">Groep-object</span><span class="sxs-lookup"><span data-stu-id="2dc7b-263">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="2dc7b-264">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="2dc7b-264">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="2dc7b-265">Nieuw-gebeurtenis logboek</span><span class="sxs-lookup"><span data-stu-id="2dc7b-265">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="2dc7b-266">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="2dc7b-266">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="2dc7b-267">Select-Object</span><span class="sxs-lookup"><span data-stu-id="2dc7b-267">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="2dc7b-268">Weer geven-EventLog</span><span class="sxs-lookup"><span data-stu-id="2dc7b-268">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="2dc7b-269">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="2dc7b-269">Write-EventLog</span></span>](Write-EventLog.md)
