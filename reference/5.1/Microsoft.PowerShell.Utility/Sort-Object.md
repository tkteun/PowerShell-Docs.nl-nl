---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Sort-Object
ms.openlocfilehash: 1d27641f94d82b85bab694b392c0f09bb3265517
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251742"
---
# <span data-ttu-id="71b24-103">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="71b24-103">Sort-Object</span></span>

## <span data-ttu-id="71b24-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="71b24-104">SYNOPSIS</span></span>
<span data-ttu-id="71b24-105">Objecten sorteren op eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="71b24-105">Sorts objects by property values.</span></span>

## <span data-ttu-id="71b24-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="71b24-106">SYNTAX</span></span>

### <span data-ttu-id="71b24-107">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="71b24-107">Default (Default)</span></span>

```
Sort-Object [[-Property] <Object[]>] [-Descending] [-Unique] [-InputObject <psobject>]
 [-Culture <string>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="71b24-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="71b24-108">DESCRIPTION</span></span>

<span data-ttu-id="71b24-109">`Sort-Object`Met de cmdlet worden objecten in oplopende of aflopende volg orde gesorteerd op basis van de object eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="71b24-109">The `Sort-Object` cmdlet sorts objects in ascending or descending order based on object property values.</span></span> <span data-ttu-id="71b24-110">Als Sorteer eigenschappen niet zijn opgenomen in een opdracht, gebruikt Power Shell standaard sorteer eigenschappen van het eerste invoer object.</span><span class="sxs-lookup"><span data-stu-id="71b24-110">If sort properties are not included in a command, PowerShell uses default sort properties of the first input object.</span></span> <span data-ttu-id="71b24-111">Als het type van het invoer object geen standaard sorteer eigenschappen heeft, probeert Power shell de objecten zelf te vergelijken.</span><span class="sxs-lookup"><span data-stu-id="71b24-111">If the type of the input object has no default sort properties, PowerShell attempts to compare the objects themselves.</span></span> <span data-ttu-id="71b24-112">Zie de sectie [opmerkingen](#notes) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="71b24-112">For more information, see the [Notes](#notes) section.</span></span>

<span data-ttu-id="71b24-113">U kunt objecten sorteren op één eigenschap of meerdere eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="71b24-113">You can sort objects by a single property or multiple properties.</span></span> <span data-ttu-id="71b24-114">Meerdere eigenschappen gebruiken hash-tabellen om in oplopende volg orde, aflopende volg orde of een combi natie van sorteer volgorden te sorteren.</span><span class="sxs-lookup"><span data-stu-id="71b24-114">Multiple properties use hash tables to sort in ascending order, descending order, or a combination of sort orders.</span></span> <span data-ttu-id="71b24-115">Eigenschappen worden gesorteerd als hoofdletter gevoelig of niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="71b24-115">Properties are sorted as case-sensitive or case-insensitive.</span></span> <span data-ttu-id="71b24-116">Gebruik de **unieke** para meter voor het verwijderen van dubbele waarden uit de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="71b24-116">Use the **Unique** parameter to eliminate duplicates from the output.</span></span>

## <span data-ttu-id="71b24-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="71b24-117">EXAMPLES</span></span>

### <span data-ttu-id="71b24-118">Voor beeld 1: de huidige map sorteren op naam</span><span class="sxs-lookup"><span data-stu-id="71b24-118">Example 1: Sort the current directory by name</span></span>

<span data-ttu-id="71b24-119">Met deze opdracht worden de bestanden en submappen in een map gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="71b24-119">This command sorts the files and subdirectories in a directory.</span></span>

```
PS> Get-ChildItem -Path C:\Test | Sort-Object

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
d-----        2/25/2019     18:25                Files
d-----        2/25/2019     18:24                Logs
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
```

<span data-ttu-id="71b24-120">`Get-ChildItem`Met de cmdlet worden de bestanden en submappen opgehaald uit de map die is opgegeven door de para meter **Path** , **C:\Test**.</span><span class="sxs-lookup"><span data-stu-id="71b24-120">The `Get-ChildItem` cmdlet gets the files and subdirectories from the directory specified by the **Path** parameter, **C:\Test**.</span></span> <span data-ttu-id="71b24-121">De objecten worden naar de-cmdlet verzonden via de pijp lijn `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="71b24-121">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="71b24-122">`Sort-Object` geeft geen eigenschap op waardoor de uitvoer wordt gesorteerd op basis van de standaard sorteer eigenschap, **naam**.</span><span class="sxs-lookup"><span data-stu-id="71b24-122">`Sort-Object` does not specify a property so the output is sorted by the default sort property, **Name**.</span></span>

### <span data-ttu-id="71b24-123">Voor beeld 2: de huidige map sorteren op bestands lengte</span><span class="sxs-lookup"><span data-stu-id="71b24-123">Example 2: Sort the current directory by file length</span></span>

<span data-ttu-id="71b24-124">Met deze opdracht worden de bestanden in de huidige map op basis van de lengte in oplopende volg orde weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="71b24-124">This command displays the files in the current directory by length in ascending order.</span></span>

```
PS> Get-ChildItem -Path C:\Test -File | Sort-Object -Property Length

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
-a----        2/13/2019     08:55             26 anotherfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-a----        2/12/2019     15:40         118014 Command.txt
```

<span data-ttu-id="71b24-125">De `Get-ChildItem` cmdlet haalt de bestanden op uit de map die is opgegeven door de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="71b24-125">The `Get-ChildItem` cmdlet gets the files from the directory specified by the **Path** parameter.</span></span>
<span data-ttu-id="71b24-126">De **File** -para meter geeft aan dat `Get-ChildItem` alleen bestands objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="71b24-126">The **File** parameter specifies that `Get-ChildItem` only gets file objects.</span></span> <span data-ttu-id="71b24-127">De objecten worden naar de-cmdlet verzonden via de pijp lijn `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="71b24-127">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="71b24-128">`Sort-Object` gebruikt de **lengte** parameter om de bestanden te sorteren op lengte in oplopende volg orde.</span><span class="sxs-lookup"><span data-stu-id="71b24-128">`Sort-Object` uses the **Length** parameter to sort the files by length in ascending order.</span></span>

### <span data-ttu-id="71b24-129">Voor beeld 3: processen sorteren op geheugen gebruik</span><span class="sxs-lookup"><span data-stu-id="71b24-129">Example 3: Sort processes by memory usage</span></span>

<span data-ttu-id="71b24-130">In dit voor beeld worden processen met het hoogste geheugen gebruik weer gegeven op basis van de grootte van de werkset (WS).</span><span class="sxs-lookup"><span data-stu-id="71b24-130">This example displays processes with the highest memory usage based on their working set (WS) size.</span></span>

```
PS> Get-Process | Sort-Object -Property WS | Select-Object -Last 5

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    136   193.92     217.11     889.16   87492   8 OUTLOOK
    112   347.73     297.02      95.19  106908   8 Teams
    206   266.54     323.71      37.17   60620   8 MicrosoftEdgeCP
     35   552.19     549.94     131.66    6552   8 Code
      0     1.43     595.12       0.00    2780   0 Memory Compression
```

<span data-ttu-id="71b24-131">De `Get-Process` cmdlet haalt de lijst op met processen die op de computer worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="71b24-131">The `Get-Process` cmdlet gets the list of processes running on the computer.</span></span> <span data-ttu-id="71b24-132">De proces objecten worden in de pijp lijn naar de `Sort-Object` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="71b24-132">The process objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="71b24-133">`Sort-Object` gebruikt de para meter **Property** om de objecten te sorteren op **WS**.</span><span class="sxs-lookup"><span data-stu-id="71b24-133">`Sort-Object` uses the **Property** parameter to sort the objects by **WS**.</span></span> <span data-ttu-id="71b24-134">De objecten worden naar de-cmdlet verzonden via de pijp lijn `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="71b24-134">The objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span>
<span data-ttu-id="71b24-135">`Select-Object` gebruikt de **laatste** para meter om de laatste vijf objecten op te geven. Dit zijn de objecten met het hoogste **WS** -gebruik.</span><span class="sxs-lookup"><span data-stu-id="71b24-135">`Select-Object` uses the **Last** parameter to specify the last five objects, which are the objects with the highest **WS** usage.</span></span>

### <span data-ttu-id="71b24-136">Voor beeld 4: HistoryInfo-objecten sorteren op id</span><span class="sxs-lookup"><span data-stu-id="71b24-136">Example 4: Sort HistoryInfo objects by Id</span></span>

<span data-ttu-id="71b24-137">Met deze opdracht worden de **HistoryInfo** -objecten van de Power shell **-** sessie gesorteerd met de eigenschap ID.</span><span class="sxs-lookup"><span data-stu-id="71b24-137">This command sorts the PowerShell session's **HistoryInfo** objects using the **Id** property.</span></span> <span data-ttu-id="71b24-138">Elke Power shell-sessie heeft een eigen opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="71b24-138">Each PowerShell session has its own command history.</span></span>

```
PS> Get-History | Sort-Object -Property Id -Descending

  Id CommandLine
  -- -----------
  10 Get-Command Sort-Object -Syntax
   9 $PSVersionTable
   8 Get-Command Sort-Object -Syntax
   7 Get-Command Sort-Object -ShowCommandInfo
   6 Get-ChildItem -Path C:\Test | Sort-Object -Property Length
   5 Get-Help Clear-History -online
   4 Get-Help Clear-History -full
   3 Get-ChildItem | Get-Member
   2 Get-Command Sort-Object -Syntax
   1 Set-Location C:\Test\
```

<span data-ttu-id="71b24-139">De `Get-History` cmdlet haalt de geschiedenis objecten op uit de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="71b24-139">The `Get-History` cmdlet gets the history objects from the current PowerShell session.</span></span> <span data-ttu-id="71b24-140">De objecten worden naar de-cmdlet verzonden via de pijp lijn `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="71b24-140">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="71b24-141">`Sort-Object` gebruikt de para meter **Property** om de objecten op **id** te sorteren. De **aflopende** para meter sorteert de opdracht geschiedenis van nieuwste naar oudste.</span><span class="sxs-lookup"><span data-stu-id="71b24-141">`Sort-Object` uses the **Property** parameter to sort the objects by **Id**. The **Descending** parameter sorts the command history from newest to oldest.</span></span>

### <span data-ttu-id="71b24-142">Voor beeld 5: een hash-tabel gebruiken om eigenschappen in oplopende en aflopende volg orde te sorteren</span><span class="sxs-lookup"><span data-stu-id="71b24-142">Example 5: Use a hash table to sort properties in ascending and descending order</span></span>

<span data-ttu-id="71b24-143">Met deze opdracht worden twee eigenschappen gebruikt om de objecten, **status** en **DisplayName** te sorteren.</span><span class="sxs-lookup"><span data-stu-id="71b24-143">This command uses two properties to sort the objects, **Status** and **DisplayName**.</span></span> <span data-ttu-id="71b24-144">De **status** wordt gesorteerd in aflopende volg orde en **DisplayName** wordt in oplopende volg orde gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="71b24-144">**Status** is sorted in descending order and **DisplayName** is sorted in ascending order.</span></span>

<span data-ttu-id="71b24-145">Een hash-tabel wordt gebruikt om de waarde van de **eigenschap** para meter op te geven.</span><span class="sxs-lookup"><span data-stu-id="71b24-145">A hash table is used to specify the **Property** parameter's value.</span></span> <span data-ttu-id="71b24-146">De hash-tabel gebruikt een expressie om de namen van eigenschappen en sorteer volgorden op te geven.</span><span class="sxs-lookup"><span data-stu-id="71b24-146">The hash table uses an expression to specify the property names and sort orders.</span></span> <span data-ttu-id="71b24-147">Zie [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)voor meer informatie over hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="71b24-147">For more information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

<span data-ttu-id="71b24-148">De eigenschap **status** die in de hash-tabel wordt gebruikt, is een opgesomde eigenschap.</span><span class="sxs-lookup"><span data-stu-id="71b24-148">The **Status** property used in the hash table is an enumerated property.</span></span>
<span data-ttu-id="71b24-149">Zie [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="71b24-149">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

```
PS C:\> Get-Service | Sort-Object -Property @{Expression = "Status"; Descending = $True}, @{Expression = "DisplayName"; Descending = $False}

Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  BthAvctpSvc        AVCTP service
Running  BrokerInfrastru... Background Tasks Infrastructure Ser...
Running  BDESVC             BitLocker Drive Encryption Service
Running  CoreMessagingRe... CoreMessaging
Running  VaultSvc           Credential Manager
Running  DsSvc              Data Sharing Service
Running  Dhcp               DHCP Client
...
Stopped  ALG                Application Layer Gateway Service
Stopped  AppMgmt            Application Management
Stopped  BITS               Background Intelligent Transfer Ser...
Stopped  wbengine           Block Level Backup Engine Service
Stopped  BluetoothUserSe... Bluetooth User Support Service_14fb...
Stopped  COMSysApp          COM+ System Application
Stopped  smstsmgr           ConfigMgr Task Sequence Agent
Stopped  DeviceInstall      Device Install Service
Stopped  MSDTC              Distributed Transaction Coordinator
```

<span data-ttu-id="71b24-150">De `Get-Service` cmdlet haalt de lijst met Services op de computer op.</span><span class="sxs-lookup"><span data-stu-id="71b24-150">The `Get-Service` cmdlet gets the list of services on the computer.</span></span> <span data-ttu-id="71b24-151">De service objecten worden naar de-cmdlet verzonden via de pijp lijn `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="71b24-151">The service objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="71b24-152">`Sort-Object` gebruikt de **eigenschaps** parameter met een hash-tabel om de namen van eigenschappen en sorteer volgorden op te geven.</span><span class="sxs-lookup"><span data-stu-id="71b24-152">`Sort-Object` uses the **Property** parameter with a hash table to specify the property names and sort orders.</span></span> <span data-ttu-id="71b24-153">De **eigenschaps** parameter is gesorteerd op twee eigenschappen, **status** in aflopende volg orde en **DisplayName** in oplopende volg orde.</span><span class="sxs-lookup"><span data-stu-id="71b24-153">The **Property** parameter is sorted by two properties, **Status** in descending order and **DisplayName** in ascending order.</span></span>

<span data-ttu-id="71b24-154">**Status** is een opgesomde eigenschap.</span><span class="sxs-lookup"><span data-stu-id="71b24-154">**Status** is an enumerated property.</span></span> <span data-ttu-id="71b24-155">**Gestopt** heeft de waarde **1** en **wordt uitgevoerd** met de waarde **4**.</span><span class="sxs-lookup"><span data-stu-id="71b24-155">**Stopped** has a value of **1** and **Running** has a value of **4**.</span></span> <span data-ttu-id="71b24-156">De **aflopende** para meter is ingesteld op `$True` zodat **actieve** processen worden weer gegeven voordat processen worden **gestopt** .</span><span class="sxs-lookup"><span data-stu-id="71b24-156">The **Descending** parameter is set to `$True` so that **Running** processes are displayed before **Stopped** processes.</span></span> <span data-ttu-id="71b24-157">**DisplayName** stelt de **aflopende** para meter in om `$False` de weergave namen in alfabetische volg orde te sorteren.</span><span class="sxs-lookup"><span data-stu-id="71b24-157">**DisplayName** sets the **Descending** parameter to `$False` to sort the display names in alphabetical order.</span></span>

### <span data-ttu-id="71b24-158">Voor beeld 6: tekst bestanden sorteren op tijds Panne</span><span class="sxs-lookup"><span data-stu-id="71b24-158">Example 6: Sort text files by time span</span></span>

<span data-ttu-id="71b24-159">Met deze opdracht worden tekst bestanden in aflopende volg orde gesorteerd op basis van de tijds duur tussen **CreationTime** en **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="71b24-159">This command sorts text files in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

```
PS> Get-ChildItem -Path C:\Test\*.txt | Sort-Object -Property @{Expression = {$_.CreationTime - $_.LastWriteTime}; Descending = $False} | Format-Table CreationTime, LastWriteTime, FullName

CreationTime          LastWriteTime        FullName
------------          -------------        --------
11/21/2018 12:39:01   2/26/2019 08:59:36   C:\Test\test2.txt
12/4/2018 08:29:41    2/26/2019 08:57:05   C:\Test\powershell_list.txt
2/20/2019 08:15:59    2/26/2019 12:09:43   C:\Test\CreateTestFile.txt
2/20/2019 08:15:59    2/26/2019 12:07:41   C:\Test\Command.txt
2/20/2019 08:15:59    2/26/2019 08:57:52   C:\Test\ReadOnlyFile.txt
11/29/2018 15:16:50   12/4/2018 16:16:24   C:\Test\LogData.txt
2/25/2019 18:25:11    2/26/2019 12:08:47   C:\Test\Zsystemlog.txt
2/25/2019 18:25:11    2/26/2019 08:55:33   C:\Test\Bfile.txt
2/26/2019 08:46:59    2/26/2019 12:12:19   C:\Test\LogFile3.txt

```

<span data-ttu-id="71b24-160">De `Get-ChildItem` cmdlet gebruikt de para meter **Path** om de map **C:\Test** en alle bestanden op te geven `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="71b24-160">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory **C:\Test** and all of the `*.txt` files.</span></span> <span data-ttu-id="71b24-161">De objecten worden naar de-cmdlet verzonden via de pijp lijn `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="71b24-161">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="71b24-162">`Sort-Object` gebruikt de **eigenschaps** parameter met een hash-tabel om te bepalen hoeveel bestanden de tijd tussen **CreationTime** en **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="71b24-162">`Sort-Object` uses the **Property** parameter with a hash table to determine each files time span between **CreationTime** and **LastWriteTime**.</span></span> <span data-ttu-id="71b24-163">De **aflopende** para meter is ingesteld op `$False` om te sorteren in de volg orde van voor de kortste periode.</span><span class="sxs-lookup"><span data-stu-id="71b24-163">The **Descending** parameter is set to `$False` to sort in the order of longest to shortest time span.</span></span>

### <span data-ttu-id="71b24-164">Voor beeld 7: namen in een tekst bestand sorteren</span><span class="sxs-lookup"><span data-stu-id="71b24-164">Example 7: Sort names in a text file</span></span>

<span data-ttu-id="71b24-165">In dit voor beeld ziet u hoe u een lijst kunt sorteren op basis van een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="71b24-165">This example shows how to sort a list from a text file.</span></span> <span data-ttu-id="71b24-166">Het oorspronkelijke bestand wordt weer gegeven als een niet-gesorteerde lijst.</span><span class="sxs-lookup"><span data-stu-id="71b24-166">The original file is displayed as an unsorted list.</span></span> <span data-ttu-id="71b24-167">`Sort-Object` Hiermee wordt de inhoud gesorteerd en wordt de inhoud gesorteerd met de **unieke** para meter waarmee dubbele waarden worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="71b24-167">`Sort-Object` sorts the contents and then sorts the contents with the **Unique** parameter that removes duplicates.</span></span>

```
PS> Get-Content -Path C:\Test\ServerNames.txt
localhost
server01
server25
LOCALHOST
Server19
server3
localhost

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object
localhost
LOCALHOST
localhost
server01
Server19
server25
server3

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object -Unique
localhost
server01
Server19
server25
server3
```

<span data-ttu-id="71b24-168">De `Get-Content` cmdlet gebruikt de para meter **Path** om de map en de bestands naam op te geven.</span><span class="sxs-lookup"><span data-stu-id="71b24-168">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="71b24-169">Het bestand **ServerNames.txt** bevat een niet-gesorteerde lijst met computer namen.</span><span class="sxs-lookup"><span data-stu-id="71b24-169">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span>

<span data-ttu-id="71b24-170">De `Get-Content` cmdlet gebruikt de para meter **Path** om de map en de bestands naam op te geven.</span><span class="sxs-lookup"><span data-stu-id="71b24-170">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="71b24-171">Het bestand **ServerNames.txt** bevat een niet-gesorteerde lijst met computer namen.</span><span class="sxs-lookup"><span data-stu-id="71b24-171">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span> <span data-ttu-id="71b24-172">De objecten worden naar de-cmdlet verzonden via de pijp lijn `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="71b24-172">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="71b24-173">`Sort-Object` sorteert de lijst in de standaard volgorde, oplopend.</span><span class="sxs-lookup"><span data-stu-id="71b24-173">`Sort-Object` sorts the list in the default order, ascending.</span></span>

<span data-ttu-id="71b24-174">De `Get-Content` cmdlet gebruikt de para meter **Path** om de map en de bestands naam op te geven.</span><span class="sxs-lookup"><span data-stu-id="71b24-174">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="71b24-175">Het bestand **ServerNames.txt** bevat een niet-gesorteerde lijst met computer namen.</span><span class="sxs-lookup"><span data-stu-id="71b24-175">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span> <span data-ttu-id="71b24-176">De objecten worden naar de-cmdlet verzonden via de pijp lijn `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="71b24-176">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="71b24-177">`Sort-Object` gebruikt de **unieke** para meter voor het verwijderen van dubbele computer namen.</span><span class="sxs-lookup"><span data-stu-id="71b24-177">`Sort-Object` uses the **Unique** parameter to remove duplicate computer names.</span></span> <span data-ttu-id="71b24-178">De lijst wordt gesorteerd in de standaard volgorde, oplopend.</span><span class="sxs-lookup"><span data-stu-id="71b24-178">The list is sorted in the default order, ascending.</span></span>

### <span data-ttu-id="71b24-179">Voor beeld 8: een teken reeks sorteren als een geheel getal</span><span class="sxs-lookup"><span data-stu-id="71b24-179">Example 8: Sort a string as an integer</span></span>

<span data-ttu-id="71b24-180">In dit voor beeld ziet u hoe u een tekst bestand met teken reeks objecten kunt sorteren als gehele getallen.</span><span class="sxs-lookup"><span data-stu-id="71b24-180">This example shows how to sort a text file that contains string objects as integers.</span></span> <span data-ttu-id="71b24-181">U kunt elke opdracht naar de pijp lijn verzenden om te `Get-Member` controleren of de objecten teken reeksen zijn in plaats van gehele getallen.</span><span class="sxs-lookup"><span data-stu-id="71b24-181">You can send each command down the pipeline to `Get-Member` and verify that the objects are strings instead of integers.</span></span> <span data-ttu-id="71b24-182">In deze voor beelden `ProductId.txt` bevat het bestand een niet-gesorteerde lijst met product nummers.</span><span class="sxs-lookup"><span data-stu-id="71b24-182">For these examples, the `ProductId.txt` file contains an unsorted list of product numbers.</span></span>

<span data-ttu-id="71b24-183">In het eerste voor beeld `Get-Content` wordt de inhoud van het bestand en pijp lijnen naar de `Sort-Object` cmdlet opgehaald.</span><span class="sxs-lookup"><span data-stu-id="71b24-183">In the first example, `Get-Content` gets the contents of the file and pipes lines to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="71b24-184">`Sort-Object` Hiermee worden de teken reeks objecten in oplopende volg orde gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="71b24-184">`Sort-Object` sorts the string objects in ascending order.</span></span>

```
PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object
0
1
12345
1500
2
2800
3500
4100
500
6200
77
88
99999

PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object {[int]$_}
0
1
2
77
88
500
1500
2800
3500
4100
6200
12345
99999
```

<span data-ttu-id="71b24-185">In het tweede voor beeld `Get-Content` wordt de inhoud van het bestand en pijp lijnen naar de `Sort-Object` cmdlet opgehaald.</span><span class="sxs-lookup"><span data-stu-id="71b24-185">In the second example, `Get-Content` gets the contents of the file and pipes lines to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="71b24-186">`Sort-Object` maakt gebruik van een script blok om de teken reeksen te converteren naar gehele getallen.</span><span class="sxs-lookup"><span data-stu-id="71b24-186">`Sort-Object` uses a script block to convert the strings to integers.</span></span> <span data-ttu-id="71b24-187">In de voorbeeld code wordt `[int]` de teken reeks geconverteerd naar een geheel getal en `$_` wordt elke teken reeks aangeduid als de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="71b24-187">In the sample code, `[int]` converts the string to an integer and `$_` represents each string as it comes down the pipeline.</span></span> <span data-ttu-id="71b24-188">De objecten met gehele getallen worden via de pijp lijn naar de `Sort-Object` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="71b24-188">The integer objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="71b24-189">`Sort-Object` de objecten van het gehele getal worden in numerieke volg orde gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="71b24-189">`Sort-Object` sorts the integer objects in numeric order.</span></span>

<span data-ttu-id="71b24-190">De `Get-Content` cmdlet gebruikt de para meter **Path** om de map en de bestands naam op te geven.</span><span class="sxs-lookup"><span data-stu-id="71b24-190">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="71b24-191">Het bestand **ProductId.txt** bevat een niet-gesorteerde lijst met product nummers.</span><span class="sxs-lookup"><span data-stu-id="71b24-191">The file **ProductId.txt** contains an unsorted list of product numbers.</span></span> <span data-ttu-id="71b24-192">De teken reeks objecten worden naar de-cmdlet verzonden via de pijp lijn `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="71b24-192">The string objects are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="71b24-193">`ForEach-Object` maakt gebruik van een script blok om de teken reeksen te converteren naar gehele getallen.</span><span class="sxs-lookup"><span data-stu-id="71b24-193">`ForEach-Object` uses a script block to convert the strings to integers.</span></span> <span data-ttu-id="71b24-194">In de voorbeeld code wordt `[int]` de teken reeks geconverteerd naar een geheel getal en `$_` wordt elke teken reeks aangeduid als de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="71b24-194">In the sample code, `[int]` converts the string to an integer and `$_` represents each string as it comes down the pipeline.</span></span> <span data-ttu-id="71b24-195">De objecten met gehele getallen worden via de pijp lijn naar de `Sort-Object` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="71b24-195">The integer objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="71b24-196">`Sort-Object` de objecten van het gehele getal worden in numerieke volg orde gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="71b24-196">`Sort-Object` sorts the integer objects in numeric order.</span></span>
## <span data-ttu-id="71b24-197">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="71b24-197">PARAMETERS</span></span>

### <span data-ttu-id="71b24-198">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="71b24-198">-CaseSensitive</span></span>

<span data-ttu-id="71b24-199">Hiermee wordt aangegeven dat de sortering hoofdletter gevoelig is.</span><span class="sxs-lookup"><span data-stu-id="71b24-199">Indicates that the sort is case-sensitive.</span></span> <span data-ttu-id="71b24-200">Sorteren is standaard niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="71b24-200">By default, sorts are not case-sensitive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Case-insensitive
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="71b24-201">-Cultuur</span><span class="sxs-lookup"><span data-stu-id="71b24-201">-Culture</span></span>

<span data-ttu-id="71b24-202">Hiermee geeft u de cultuur configuratie op die moet worden gebruikt voor het sorteren.</span><span class="sxs-lookup"><span data-stu-id="71b24-202">Specifies the cultural configuration to use for sorts.</span></span> <span data-ttu-id="71b24-203">Gebruiken `Get-Culture` om de configuratie van de systeem cultuur weer te geven.</span><span class="sxs-lookup"><span data-stu-id="71b24-203">Use `Get-Culture` to display the system's culture configuration.</span></span>

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

### <span data-ttu-id="71b24-204">-Aflopend</span><span class="sxs-lookup"><span data-stu-id="71b24-204">-Descending</span></span>

<span data-ttu-id="71b24-205">Hiermee wordt aangegeven dat `Sort-Object` de objecten in aflopende volg orde worden gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="71b24-205">Indicates that `Sort-Object` sorts the objects in descending order.</span></span> <span data-ttu-id="71b24-206">De standaard instelling is oplopende volg orde.</span><span class="sxs-lookup"><span data-stu-id="71b24-206">The default is ascending order.</span></span>

<span data-ttu-id="71b24-207">Als u meerdere eigenschappen met verschillende sorteer volgorden wilt sorteren, gebruikt u een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="71b24-207">To sort multiple properties with different sort orders, use a hash table.</span></span> <span data-ttu-id="71b24-208">Met een hash-tabel kunt u bijvoorbeeld één eigenschap in oplopende volg orde sorteren en een andere eigenschap in aflopende volg orde.</span><span class="sxs-lookup"><span data-stu-id="71b24-208">For example, with a hash table you can sort one property in ascending order and another property in descending order.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Ascending
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="71b24-209">-Input object</span><span class="sxs-lookup"><span data-stu-id="71b24-209">-InputObject</span></span>

<span data-ttu-id="71b24-210">Als u objecten wilt sorteren, stuurt u ze omlaag in de pijp lijn `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="71b24-210">To sort objects, send them down the pipeline to `Sort-Object`.</span></span> <span data-ttu-id="71b24-211">Als u de para meter **input object** gebruikt voor het verzenden van een verzameling items, `Sort-Object` ontvangt u één object dat de verzameling vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="71b24-211">If you use the **InputObject** parameter to submit a collection of items, `Sort-Object` receives one object that represents the collection.</span></span> <span data-ttu-id="71b24-212">Omdat één object niet kan worden gesorteerd, `Sort-Object` retourneert de hele verzameling ongewijzigd.</span><span class="sxs-lookup"><span data-stu-id="71b24-212">Because one object cannot be sorted, `Sort-Object` returns the entire collection unchanged.</span></span>

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

### <span data-ttu-id="71b24-213">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="71b24-213">-Property</span></span>

<span data-ttu-id="71b24-214">Hiermee geeft u de eigenschapnamen `Sort-Object` op waarmee de objecten worden gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="71b24-214">Specifies the property names that `Sort-Object` uses to sort the objects.</span></span> <span data-ttu-id="71b24-215">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="71b24-215">Wildcards are permitted.</span></span>
<span data-ttu-id="71b24-216">Objecten worden gesorteerd op basis van de eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="71b24-216">Objects are sorted based on the property values.</span></span> <span data-ttu-id="71b24-217">Als u geen eigenschap opgeeft, `Sort-Object` sorteert u op basis van de standaard eigenschappen voor het object type of de objecten zelf.</span><span class="sxs-lookup"><span data-stu-id="71b24-217">If you do not specify a property, `Sort-Object` sorts based on default properties for the object type or the objects themselves.</span></span>

<span data-ttu-id="71b24-218">Meerdere eigenschappen kunnen in oplopende volg orde, aflopende volg orde of een combi natie van sorteer volgorden worden gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="71b24-218">Multiple properties can be sorted in ascending order, descending order, or a combination of sort orders.</span></span> <span data-ttu-id="71b24-219">Wanneer u meerdere eigenschappen opgeeft, worden de objecten gesorteerd op de eerste eigenschap.</span><span class="sxs-lookup"><span data-stu-id="71b24-219">When you specify multiple properties, the objects are sorted by the first property.</span></span> <span data-ttu-id="71b24-220">Als meerdere objecten dezelfde waarde hebben voor de eerste eigenschap, worden deze objecten gesorteerd op de tweede eigenschap.</span><span class="sxs-lookup"><span data-stu-id="71b24-220">If multiple objects have the same value for the first property, those objects are sorted by the second property.</span></span> <span data-ttu-id="71b24-221">Dit proces wordt voortgezet totdat er geen specifieke eigenschappen of groepen van objecten zijn.</span><span class="sxs-lookup"><span data-stu-id="71b24-221">This process continues until there are no more specified properties or no groups of objects.</span></span>

<span data-ttu-id="71b24-222">De waarde van de **eigenschaps** parameter kan een berekende eigenschap zijn.</span><span class="sxs-lookup"><span data-stu-id="71b24-222">The **Property** parameter's value can be a calculated property.</span></span> <span data-ttu-id="71b24-223">Als u een berekende eigenschap wilt maken, gebruikt u een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="71b24-223">To create a calculated property, use a hash table.</span></span>

<span data-ttu-id="71b24-224">Geldige sleutels voor een hash-tabel zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="71b24-224">Valid keys for a hash table are as follows:</span></span>

- <span data-ttu-id="71b24-225">`expression` - `<string>` of `<script block>`</span><span class="sxs-lookup"><span data-stu-id="71b24-225">`expression` - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="71b24-226">`ascending` of `descending` - `<boolean>`</span><span class="sxs-lookup"><span data-stu-id="71b24-226">`ascending` or `descending` - `<boolean>`</span></span>

<span data-ttu-id="71b24-227">Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="71b24-227">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: Default properties
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="71b24-228">-Uniek</span><span class="sxs-lookup"><span data-stu-id="71b24-228">-Unique</span></span>

<span data-ttu-id="71b24-229">Hiermee wordt aangegeven dat `Sort-Object` dubbele waarden worden geëlimineerd en alleen de unieke leden van de verzameling worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="71b24-229">Indicates that `Sort-Object` eliminates duplicates and returns only the unique members of the collection.</span></span> <span data-ttu-id="71b24-230">Het eerste exemplaar van een unieke waarde is opgenomen in de gesorteerde uitvoer.</span><span class="sxs-lookup"><span data-stu-id="71b24-230">The first instance of a unique value is included in the sorted output.</span></span>

<span data-ttu-id="71b24-231">**Uniek** is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="71b24-231">**Unique** is case-insensitive.</span></span> <span data-ttu-id="71b24-232">Teken reeksen die alleen verschillen per teken, worden als hetzelfde beschouwd.</span><span class="sxs-lookup"><span data-stu-id="71b24-232">Strings that only differ by character case are considered the same.</span></span>
<span data-ttu-id="71b24-233">Bijvoorbeeld teken en teken.</span><span class="sxs-lookup"><span data-stu-id="71b24-233">For example, character and CHARACTER.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="71b24-234">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="71b24-234">CommonParameters</span></span>

<span data-ttu-id="71b24-235">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="71b24-235">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="71b24-236">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="71b24-236">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="71b24-237">INVOER</span><span class="sxs-lookup"><span data-stu-id="71b24-237">INPUTS</span></span>

### <span data-ttu-id="71b24-238">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="71b24-238">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="71b24-239">U kunt de objecten waarop moet worden gesorteerd, door sluizen `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="71b24-239">You can pipe the objects to be sorted to `Sort-Object`.</span></span>

## <span data-ttu-id="71b24-240">UITVOER</span><span class="sxs-lookup"><span data-stu-id="71b24-240">OUTPUTS</span></span>

### <span data-ttu-id="71b24-241">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="71b24-241">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="71b24-242">`Sort-Object` Hiermee worden de gesorteerde objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="71b24-242">`Sort-Object` returns the sorted objects.</span></span>

## <span data-ttu-id="71b24-243">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="71b24-243">NOTES</span></span>

<span data-ttu-id="71b24-244">`Sort-Object`Met de cmdlet worden objecten gesorteerd op basis van eigenschappen die zijn opgegeven in de opdracht of de standaard sorteer eigenschappen voor het object type.</span><span class="sxs-lookup"><span data-stu-id="71b24-244">The `Sort-Object` cmdlet sorts objects based on properties specified in the command or the default sort properties for the object type.</span></span> <span data-ttu-id="71b24-245">Standaard sorteer eigenschappen worden gedefinieerd met behulp `PropertySet` van de naam `DefaultKeyPropertySet` in een `types.ps1xml` bestand.</span><span class="sxs-lookup"><span data-stu-id="71b24-245">Default sort properties are defined using the `PropertySet` named `DefaultKeyPropertySet` in a `types.ps1xml` file.</span></span> <span data-ttu-id="71b24-246">Zie [about_Types.ps1XML](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="71b24-246">For more information, see [about_Types.ps1xml](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml).</span></span>

<span data-ttu-id="71b24-247">Als een object niet over een van de opgegeven eigenschappen beschikt, wordt de eigenschaps waarde voor dat object geïnterpreteerd `Sort-Object` als **Null** en aan het einde van de sorteer volgorde geplaatst.</span><span class="sxs-lookup"><span data-stu-id="71b24-247">If an object does not have one of the specified properties, the property value for that object is interpreted by `Sort-Object` as **Null** and placed at the end of the sort order.</span></span>

<span data-ttu-id="71b24-248">Als er geen sorteer eigenschappen beschikbaar zijn, probeert Power shell de objecten zelf te vergelijken.</span><span class="sxs-lookup"><span data-stu-id="71b24-248">When no sort properties are available, PowerShell attempts to compare the objects themselves.</span></span>
<span data-ttu-id="71b24-249">`Sort-Object` maakt gebruik van de **vergelijkings** methode voor elke eigenschap.</span><span class="sxs-lookup"><span data-stu-id="71b24-249">`Sort-Object` uses the **Compare** method for each property.</span></span> <span data-ttu-id="71b24-250">Als een eigenschap niet wordt geïmplementeerd **IComparable** , wordt de waarde van de eigenschap door de cmdlet geconverteerd naar een teken reeks en wordt de **vergelijkings** methode voor **System. String** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="71b24-250">If a property does not implement **IComparable** , the cmdlet converts the property value to a string and uses the **Compare** method for **System.String**.</span></span> <span data-ttu-id="71b24-251">Zie de [methode PSObject. CompareTo (object)](/dotnet/api/system.management.automation.psobject.compareto)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="71b24-251">For more information, see [PSObject.CompareTo(Object) Method](/dotnet/api/system.management.automation.psobject.compareto).</span></span>

<span data-ttu-id="71b24-252">Als u sorteert op een opgesomde eigenschap zoals **status** , wordt `Sort-Object` gesorteerd op de opsommings waarden.</span><span class="sxs-lookup"><span data-stu-id="71b24-252">If you sort on an enumerated property such as **Status** , `Sort-Object` sorts by the enumeration values.</span></span> <span data-ttu-id="71b24-253">Voor Windows-Services is **gestopt** met de waarde **1** en **wordt uitgevoerd** met de waarde **4**.</span><span class="sxs-lookup"><span data-stu-id="71b24-253">For Windows services, **Stopped** has a value of **1** and **Running** has a value of **4**.</span></span>
<span data-ttu-id="71b24-254">**Gestopt** wordt gesorteerd voordat deze **wordt uitgevoerd** vanwege de opgesomde waarden.</span><span class="sxs-lookup"><span data-stu-id="71b24-254">**Stopped** is sorted before **Running** because of the enumerated values.</span></span> <span data-ttu-id="71b24-255">Zie [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="71b24-255">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

## <span data-ttu-id="71b24-256">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="71b24-256">RELATED LINKS</span></span>

[<span data-ttu-id="71b24-257">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="71b24-257">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="71b24-258">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="71b24-258">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="71b24-259">about_Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="71b24-259">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="71b24-260">Compare-object</span><span class="sxs-lookup"><span data-stu-id="71b24-260">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="71b24-261">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="71b24-261">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="71b24-262">Groep-object</span><span class="sxs-lookup"><span data-stu-id="71b24-262">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="71b24-263">Meting object</span><span class="sxs-lookup"><span data-stu-id="71b24-263">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="71b24-264">New-Object</span><span class="sxs-lookup"><span data-stu-id="71b24-264">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="71b24-265">Select-Object</span><span class="sxs-lookup"><span data-stu-id="71b24-265">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="71b24-266">T-object</span><span class="sxs-lookup"><span data-stu-id="71b24-266">Tee-Object</span></span>](Tee-Object.md)
