---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/start-trace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Trace
ms.openlocfilehash: cbdb40edf85dd4645552f6e096a99384532b4443
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250326"
---
# <span data-ttu-id="fb129-103">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="fb129-103">Start-Trace</span></span>

## <span data-ttu-id="fb129-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="fb129-104">SYNOPSIS</span></span>
<span data-ttu-id="fb129-105">Start een logboek registratie sessie voor gebeurtenis tracering.</span><span class="sxs-lookup"><span data-stu-id="fb129-105">Start an Event Trace logging session.</span></span>

## <span data-ttu-id="fb129-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="fb129-106">SYNTAX</span></span>

```
Start-Trace [-SessionName] <String> [[-OutputFilePath] <String>] [[-ProviderFilePath] <String>]
 [-ETS] [-Format <String>] [-MinBuffers <Int32>] [-MaxBuffers <Int32>]
 [-BufferSizeInKB <Int32>] [-MaxLogFileSizeInMB <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="fb129-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fb129-107">DESCRIPTION</span></span>
<span data-ttu-id="fb129-108">Met deze cmdlet wordt een Windows-sessie voor logboek registratie van gebeurtenissen gestart.</span><span class="sxs-lookup"><span data-stu-id="fb129-108">This cmdlet starts a Windows Event Trace logging session.</span></span>

<span data-ttu-id="fb129-109">Deze cmdlet wordt gebruikt door de volgende cmdlets:</span><span class="sxs-lookup"><span data-stu-id="fb129-109">This cmdlet is used by the following cmdlets:</span></span>

- `Enable-PSWSManCombinedTrace`
- `Enable-WSManTrace`

<span data-ttu-id="fb129-110">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="fb129-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="fb129-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="fb129-111">EXAMPLES</span></span>

### <span data-ttu-id="fb129-112">Voor beeld 1: een sessie met WSMan-traceer logboek registratie starten</span><span class="sxs-lookup"><span data-stu-id="fb129-112">Example 1: Start a WSMan Trace logging session</span></span>

```powershell
Start-Trace -SessionName 'wsmlog' -ETS -OutputFilePath "$env:windir\system32\wsmtraces.log" -Format 'bincirc' -MinBuffers 16 -MaxBuffers 256 -BufferSizeInKb 64 -MaxLogFileSizeInMB 256 -ProviderFilePath "$env:windir\system32\wsmtraceproviders.txt"
```

## <span data-ttu-id="fb129-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fb129-113">PARAMETERS</span></span>

### <span data-ttu-id="fb129-114">-BufferSizeInKB</span><span class="sxs-lookup"><span data-stu-id="fb129-114">-BufferSizeInKB</span></span>
<span data-ttu-id="fb129-115">Buffer grootte voor de gebeurtenis tracerings sessie in kilo bytes (KB).</span><span class="sxs-lookup"><span data-stu-id="fb129-115">Event Trace Session buffer size in kilobytes (KB).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb129-116">-ETS</span><span class="sxs-lookup"><span data-stu-id="fb129-116">-ETS</span></span>
<span data-ttu-id="fb129-117">Opdrachten zonder opslaan of plannen rechtstreeks naar Gebeurtenissessies Trace kunnen verzenden.</span><span class="sxs-lookup"><span data-stu-id="fb129-117">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

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

### <span data-ttu-id="fb129-118">-Indeling</span><span class="sxs-lookup"><span data-stu-id="fb129-118">-Format</span></span>
<span data-ttu-id="fb129-119">Hiermee geeft u de indeling voor de gegevensverzamelaar.</span><span class="sxs-lookup"><span data-stu-id="fb129-119">Specifies the log format for the data collector.</span></span> <span data-ttu-id="fb129-120">Voor SQL database indeling moet u de optie **OutputFilePath** in de opdracht regel gebruiken met de `dsn!log` waarde.</span><span class="sxs-lookup"><span data-stu-id="fb129-120">For SQL database format, you must use the **OutputFilePath** option in the command line with the `dsn!log` value.</span></span> <span data-ttu-id="fb129-121">De standaard waarde is binary (bin).</span><span class="sxs-lookup"><span data-stu-id="fb129-121">The default is binary (bin).</span></span> <span data-ttu-id="fb129-122">De mogelijke waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="fb129-122">The possible values are:</span></span>

- <span data-ttu-id="fb129-123">bin-binary</span><span class="sxs-lookup"><span data-stu-id="fb129-123">bin - binary</span></span>
- <span data-ttu-id="fb129-124">bincirc-binary met circulaire logboek registratie</span><span class="sxs-lookup"><span data-stu-id="fb129-124">bincirc - binary with circular logging</span></span>
- <span data-ttu-id="fb129-125">CSV-door Komma's gescheiden waarden</span><span class="sxs-lookup"><span data-stu-id="fb129-125">csv - Comma-separated values</span></span>
- <span data-ttu-id="fb129-126">TSV-door tabs gescheiden waarden</span><span class="sxs-lookup"><span data-stu-id="fb129-126">tsv - Tab-separated values</span></span>
- <span data-ttu-id="fb129-127">SQL-SQL database</span><span class="sxs-lookup"><span data-stu-id="fb129-127">sql - SQL database</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:
Accepted values: bin, bincirc, csv, tsv, sql

Required: False
Position: Named
Default value: bin
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb129-128">-MaxBuffers</span><span class="sxs-lookup"><span data-stu-id="fb129-128">-MaxBuffers</span></span>
<span data-ttu-id="fb129-129">Hiermee stelt u het maximum aantal buffers voor gebeurtenis tracerings sessies.</span><span class="sxs-lookup"><span data-stu-id="fb129-129">Sets the maximum number of Event Trace Session buffers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 256
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb129-130">-MaxLogFileSizeInMB</span><span class="sxs-lookup"><span data-stu-id="fb129-130">-MaxLogFileSizeInMB</span></span>
<span data-ttu-id="fb129-131">Hiermee stelt u de maximale grootte van het logboek bestand in mega bytes (MB) of het aantal records voor SQL-logboeken.</span><span class="sxs-lookup"><span data-stu-id="fb129-131">Sets the maximum log file size in megabytes (MB) or number of records for SQL logs.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0 (no limit)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb129-132">-MinBuffers</span><span class="sxs-lookup"><span data-stu-id="fb129-132">-MinBuffers</span></span>
<span data-ttu-id="fb129-133">Hiermee stelt u het minimum aantal buffers voor gebeurtenis tracerings sessies.</span><span class="sxs-lookup"><span data-stu-id="fb129-133">Sets the minimum number of Event Trace Session buffers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb129-134">-OutputFilePath</span><span class="sxs-lookup"><span data-stu-id="fb129-134">-OutputFilePath</span></span>
<span data-ttu-id="fb129-135">Pad van het uitvoer logboek bestand of de naam van de DSN en logboekset in een SQL database.</span><span class="sxs-lookup"><span data-stu-id="fb129-135">Path of the output log file or the DSN and log set name in a SQL database.</span></span> <span data-ttu-id="fb129-136">Het standaardpad is `$env:systemdrive\PerfLogs\Admin` .</span><span class="sxs-lookup"><span data-stu-id="fb129-136">The default path is `$env:systemdrive\PerfLogs\Admin`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: $env:systemdrive\PerfLogs\Admin
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb129-137">-ProviderFilePath</span><span class="sxs-lookup"><span data-stu-id="fb129-137">-ProviderFilePath</span></span>
<span data-ttu-id="fb129-138">Bestand waarin meerdere gebeurtenistraceerproviders worden weer gegeven om in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="fb129-138">File listing multiple Event Trace providers to enable.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb129-139">-Sessie naam</span><span class="sxs-lookup"><span data-stu-id="fb129-139">-SessionName</span></span>
<span data-ttu-id="fb129-140">De naam van de gebeurtenistraceersessie.</span><span class="sxs-lookup"><span data-stu-id="fb129-140">The name of the Event Trace session.</span></span> <span data-ttu-id="fb129-141">Als u een tracerings sessie wilt stoppen, moet u de sessie naam weten.</span><span class="sxs-lookup"><span data-stu-id="fb129-141">To stop a trace session you must know the session name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb129-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fb129-142">CommonParameters</span></span>

<span data-ttu-id="fb129-143">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fb129-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fb129-144">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fb129-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fb129-145">INVOER</span><span class="sxs-lookup"><span data-stu-id="fb129-145">INPUTS</span></span>

### <span data-ttu-id="fb129-146">Geen</span><span class="sxs-lookup"><span data-stu-id="fb129-146">None</span></span>

## <span data-ttu-id="fb129-147">UITVOER</span><span class="sxs-lookup"><span data-stu-id="fb129-147">OUTPUTS</span></span>

### <span data-ttu-id="fb129-148">System. object</span><span class="sxs-lookup"><span data-stu-id="fb129-148">System.Object</span></span>

## <span data-ttu-id="fb129-149">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="fb129-149">NOTES</span></span>

## <span data-ttu-id="fb129-150">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="fb129-150">RELATED LINKS</span></span>

[<span data-ttu-id="fb129-151">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="fb129-151">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="fb129-152">Stoppen-traceren</span><span class="sxs-lookup"><span data-stu-id="fb129-152">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="fb129-153">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="fb129-153">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="fb129-154">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="fb129-154">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="fb129-155">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="fb129-155">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="fb129-156">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="fb129-156">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
