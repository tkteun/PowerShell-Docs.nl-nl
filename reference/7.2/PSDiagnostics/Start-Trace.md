---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/start-trace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Trace
ms.openlocfilehash: b1c6a596f3dc35028b928c3a6b5459a805bc2512
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705583"
---
# <span data-ttu-id="36bd8-102">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="36bd8-102">Start-Trace</span></span>

## <span data-ttu-id="36bd8-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="36bd8-103">SYNOPSIS</span></span>
<span data-ttu-id="36bd8-104">Start een logboek registratie sessie voor gebeurtenis tracering.</span><span class="sxs-lookup"><span data-stu-id="36bd8-104">Start an Event Trace logging session.</span></span>

## <span data-ttu-id="36bd8-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="36bd8-105">SYNTAX</span></span>

```
Start-Trace [-SessionName] <String> [[-OutputFilePath] <String>] [[-ProviderFilePath] <String>]
 [-ETS] [-Format <String>] [-MinBuffers <Int32>] [-MaxBuffers <Int32>]
 [-BufferSizeInKB <Int32>] [-MaxLogFileSizeInMB <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="36bd8-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="36bd8-106">DESCRIPTION</span></span>
<span data-ttu-id="36bd8-107">Met deze cmdlet wordt een Windows-sessie voor logboek registratie van gebeurtenissen gestart.</span><span class="sxs-lookup"><span data-stu-id="36bd8-107">This cmdlet starts a Windows Event Trace logging session.</span></span>

<span data-ttu-id="36bd8-108">Deze cmdlet wordt gebruikt door de volgende cmdlets:</span><span class="sxs-lookup"><span data-stu-id="36bd8-108">This cmdlet is used by the following cmdlets:</span></span>

- `Enable-PSWSManCombinedTrace`
- `Enable-WSManTrace`

<span data-ttu-id="36bd8-109">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="36bd8-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="36bd8-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="36bd8-110">EXAMPLES</span></span>

### <span data-ttu-id="36bd8-111">Voor beeld 1: een sessie met WSMan-traceer logboek registratie starten</span><span class="sxs-lookup"><span data-stu-id="36bd8-111">Example 1: Start a WSMan Trace logging session</span></span>

```powershell
Start-Trace -SessionName 'wsmlog' -ETS -OutputFilePath "$env:windir\system32\wsmtraces.log" -Format 'bincirc' -MinBuffers 16 -MaxBuffers 256 -BufferSizeInKb 64 -MaxLogFileSizeInMB 256 -ProviderFilePath "$env:windir\system32\wsmtraceproviders.txt"
```

## <span data-ttu-id="36bd8-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="36bd8-112">PARAMETERS</span></span>

### <span data-ttu-id="36bd8-113">-BufferSizeInKB</span><span class="sxs-lookup"><span data-stu-id="36bd8-113">-BufferSizeInKB</span></span>
<span data-ttu-id="36bd8-114">Buffer grootte voor de gebeurtenis tracerings sessie in kilo bytes (KB).</span><span class="sxs-lookup"><span data-stu-id="36bd8-114">Event Trace Session buffer size in kilobytes (KB).</span></span>

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

### <span data-ttu-id="36bd8-115">-ETS</span><span class="sxs-lookup"><span data-stu-id="36bd8-115">-ETS</span></span>
<span data-ttu-id="36bd8-116">Opdrachten zonder opslaan of plannen rechtstreeks naar Gebeurtenissessies Trace kunnen verzenden.</span><span class="sxs-lookup"><span data-stu-id="36bd8-116">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

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

### <span data-ttu-id="36bd8-117">-Indeling</span><span class="sxs-lookup"><span data-stu-id="36bd8-117">-Format</span></span>
<span data-ttu-id="36bd8-118">Hiermee geeft u de indeling voor de gegevensverzamelaar.</span><span class="sxs-lookup"><span data-stu-id="36bd8-118">Specifies the log format for the data collector.</span></span> <span data-ttu-id="36bd8-119">Voor SQL database indeling moet u de optie **OutputFilePath** in de opdracht regel gebruiken met de `dsn!log` waarde.</span><span class="sxs-lookup"><span data-stu-id="36bd8-119">For SQL database format, you must use the **OutputFilePath** option in the command line with the `dsn!log` value.</span></span> <span data-ttu-id="36bd8-120">De standaard waarde is binary (bin).</span><span class="sxs-lookup"><span data-stu-id="36bd8-120">The default is binary (bin).</span></span> <span data-ttu-id="36bd8-121">De mogelijke waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="36bd8-121">The possible values are:</span></span>

- <span data-ttu-id="36bd8-122">bin-binary</span><span class="sxs-lookup"><span data-stu-id="36bd8-122">bin - binary</span></span>
- <span data-ttu-id="36bd8-123">bincirc-binary met circulaire logboek registratie</span><span class="sxs-lookup"><span data-stu-id="36bd8-123">bincirc - binary with circular logging</span></span>
- <span data-ttu-id="36bd8-124">CSV-door Komma's gescheiden waarden</span><span class="sxs-lookup"><span data-stu-id="36bd8-124">csv - Comma-separated values</span></span>
- <span data-ttu-id="36bd8-125">TSV-door tabs gescheiden waarden</span><span class="sxs-lookup"><span data-stu-id="36bd8-125">tsv - Tab-separated values</span></span>
- <span data-ttu-id="36bd8-126">SQL-SQL database</span><span class="sxs-lookup"><span data-stu-id="36bd8-126">sql - SQL database</span></span>

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

### <span data-ttu-id="36bd8-127">-MaxBuffers</span><span class="sxs-lookup"><span data-stu-id="36bd8-127">-MaxBuffers</span></span>
<span data-ttu-id="36bd8-128">Hiermee stelt u het maximum aantal buffers voor gebeurtenis tracerings sessies.</span><span class="sxs-lookup"><span data-stu-id="36bd8-128">Sets the maximum number of Event Trace Session buffers.</span></span>

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

### <span data-ttu-id="36bd8-129">-MaxLogFileSizeInMB</span><span class="sxs-lookup"><span data-stu-id="36bd8-129">-MaxLogFileSizeInMB</span></span>
<span data-ttu-id="36bd8-130">Hiermee stelt u de maximale grootte van het logboek bestand in mega bytes (MB) of het aantal records voor SQL-logboeken.</span><span class="sxs-lookup"><span data-stu-id="36bd8-130">Sets the maximum log file size in megabytes (MB) or number of records for SQL logs.</span></span>

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

### <span data-ttu-id="36bd8-131">-MinBuffers</span><span class="sxs-lookup"><span data-stu-id="36bd8-131">-MinBuffers</span></span>
<span data-ttu-id="36bd8-132">Hiermee stelt u het minimum aantal buffers voor gebeurtenis tracerings sessies.</span><span class="sxs-lookup"><span data-stu-id="36bd8-132">Sets the minimum number of Event Trace Session buffers.</span></span>

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

### <span data-ttu-id="36bd8-133">-OutputFilePath</span><span class="sxs-lookup"><span data-stu-id="36bd8-133">-OutputFilePath</span></span>
<span data-ttu-id="36bd8-134">Pad van het uitvoer logboek bestand of de naam van de DSN en logboekset in een SQL database.</span><span class="sxs-lookup"><span data-stu-id="36bd8-134">Path of the output log file or the DSN and log set name in a SQL database.</span></span> <span data-ttu-id="36bd8-135">Het standaardpad is `$env:systemdrive\PerfLogs\Admin` .</span><span class="sxs-lookup"><span data-stu-id="36bd8-135">The default path is `$env:systemdrive\PerfLogs\Admin`.</span></span>

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

### <span data-ttu-id="36bd8-136">-ProviderFilePath</span><span class="sxs-lookup"><span data-stu-id="36bd8-136">-ProviderFilePath</span></span>
<span data-ttu-id="36bd8-137">Bestand waarin meerdere gebeurtenistraceerproviders worden weer gegeven om in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="36bd8-137">File listing multiple Event Trace providers to enable.</span></span>

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

### <span data-ttu-id="36bd8-138">-Sessie naam</span><span class="sxs-lookup"><span data-stu-id="36bd8-138">-SessionName</span></span>
<span data-ttu-id="36bd8-139">De naam van de gebeurtenistraceersessie.</span><span class="sxs-lookup"><span data-stu-id="36bd8-139">The name of the Event Trace session.</span></span> <span data-ttu-id="36bd8-140">Als u een tracerings sessie wilt stoppen, moet u de sessie naam weten.</span><span class="sxs-lookup"><span data-stu-id="36bd8-140">To stop a trace session you must know the session name.</span></span>

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

### <span data-ttu-id="36bd8-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36bd8-141">CommonParameters</span></span>

<span data-ttu-id="36bd8-142">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="36bd8-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36bd8-143">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="36bd8-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="36bd8-144">INVOER</span><span class="sxs-lookup"><span data-stu-id="36bd8-144">INPUTS</span></span>

### <span data-ttu-id="36bd8-145">Geen</span><span class="sxs-lookup"><span data-stu-id="36bd8-145">None</span></span>

## <span data-ttu-id="36bd8-146">UITVOER</span><span class="sxs-lookup"><span data-stu-id="36bd8-146">OUTPUTS</span></span>

### <span data-ttu-id="36bd8-147">Geen</span><span class="sxs-lookup"><span data-stu-id="36bd8-147">None</span></span>

## <span data-ttu-id="36bd8-148">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="36bd8-148">NOTES</span></span>

## <span data-ttu-id="36bd8-149">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="36bd8-149">RELATED LINKS</span></span>

[<span data-ttu-id="36bd8-150">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="36bd8-150">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="36bd8-151">Stoppen-traceren</span><span class="sxs-lookup"><span data-stu-id="36bd8-151">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="36bd8-152">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="36bd8-152">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="36bd8-153">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="36bd8-153">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="36bd8-154">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="36bd8-154">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="36bd8-155">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="36bd8-155">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)

