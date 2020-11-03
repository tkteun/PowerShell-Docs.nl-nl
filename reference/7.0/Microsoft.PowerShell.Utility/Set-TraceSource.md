---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-tracesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TraceSource
ms.openlocfilehash: 7a1f7e2879b0eeefe8771a5e5a8bf763e48ff106
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249438"
---
# <span data-ttu-id="2e9ea-103">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="2e9ea-103">Set-TraceSource</span></span>

## <span data-ttu-id="2e9ea-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2e9ea-104">SYNOPSIS</span></span>
<span data-ttu-id="2e9ea-105">Hiermee configureert, start en stopt u het traceren van Power shell-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-105">Configures, starts, and stops a trace of PowerShell components.</span></span>

## <span data-ttu-id="2e9ea-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2e9ea-106">SYNTAX</span></span>

### <span data-ttu-id="2e9ea-107">optieset (standaard)</span><span class="sxs-lookup"><span data-stu-id="2e9ea-107">optionsSet (Default)</span></span>

```
Set-TraceSource [-Name] <String[]> [[-Option] <PSTraceSourceOptions>] [-ListenerOption <TraceOptions>]
 [-FilePath <String>] [-Force] [-Debugger] [-PSHost] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="2e9ea-108">removeAllListenersSet</span><span class="sxs-lookup"><span data-stu-id="2e9ea-108">removeAllListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveListener <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="2e9ea-109">removeFileListenersSet</span><span class="sxs-lookup"><span data-stu-id="2e9ea-109">removeFileListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveFileListener <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="2e9ea-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2e9ea-110">DESCRIPTION</span></span>

<span data-ttu-id="2e9ea-111">De cmdlet **set-TraceSource** configureert, start en stopt een tracering van een Power Shell-onderdeel.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-111">The **Set-TraceSource** cmdlet configures, starts, and stops a trace of a PowerShell component.</span></span>
<span data-ttu-id="2e9ea-112">U kunt deze gebruiken om op te geven welke onderdelen moeten worden getraceerd en waar de tracerings uitvoer wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-112">You can use it to specify which components will be traced and where the tracing output is sent.</span></span>

## <span data-ttu-id="2e9ea-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2e9ea-113">EXAMPLES</span></span>

### <span data-ttu-id="2e9ea-114">Voor beeld 1: het ParameterBinding-onderdeel traceren</span><span class="sxs-lookup"><span data-stu-id="2e9ea-114">Example 1: Trace the ParameterBinding component</span></span>

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -Option ExecutionFlow -PSHost -ListenerOption "ProcessId,TimeStamp"
```

<span data-ttu-id="2e9ea-115">Met deze opdracht start u het traceren van het onderdeel ParameterBinding van Power shell.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-115">This command starts tracing for the ParameterBinding component of PowerShell.</span></span>
<span data-ttu-id="2e9ea-116">Hierbij wordt de para meter *name* gebruikt voor het opgeven van de tracerings bron, de *optie* parameter voor het selecteren van de ExecutionFlow tracerings gebeurtenissen en de para meter *PSHost* om de Power shell-host-listener te selecteren, die de uitvoer naar de-console verzendt.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-116">It uses the *Name* parameter to specify the trace source, the *Option* parameter to select the ExecutionFlow trace events, and the *PSHost* parameter to select the PowerShell host listener, which sends the output to the console.</span></span>
<span data-ttu-id="2e9ea-117">Met de para meter *ListenerOption* worden de ProcessID-en time stamp-waarden toegevoegd aan het voor voegsel van het tracerings bericht.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-117">The *ListenerOption* parameter adds the ProcessID and TimeStamp values to the trace message prefix.</span></span>

### <span data-ttu-id="2e9ea-118">Voor beeld 2: een tracering stoppen</span><span class="sxs-lookup"><span data-stu-id="2e9ea-118">Example 2: Stop a trace</span></span>

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -RemoveListener "Host"
```

<span data-ttu-id="2e9ea-119">Met deze opdracht stopt u de tracering van het ParameterBinding-onderdeel van Power shell.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-119">This command stops the trace of the ParameterBinding component of PowerShell.</span></span>
<span data-ttu-id="2e9ea-120">Hierbij wordt de para meter *name* gebruikt voor het identificeren van het onderdeel dat wordt getraceerd en de para meter *RemoveListener* voor het identificeren van de traceer-listener.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-120">It uses the *Name* parameter to identify the component that was being traced and the *RemoveListener* parameter to identify the trace listener.</span></span>

## <span data-ttu-id="2e9ea-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2e9ea-121">PARAMETERS</span></span>

### <span data-ttu-id="2e9ea-122">-Fout opsporingsprogramma</span><span class="sxs-lookup"><span data-stu-id="2e9ea-122">-Debugger</span></span>

<span data-ttu-id="2e9ea-123">Geeft aan dat de cmdlet de tracerings uitvoer naar het fout opsporingsprogramma verzendt.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-123">Indicates that the cmdlet sends the trace output to the debugger.</span></span>
<span data-ttu-id="2e9ea-124">U kunt de uitvoer bekijken in een fout opsporingsprogramma voor gebruikers modus of kernelmodus of in micro soft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-124">You can view the output in any user-mode or kernel mode debugger or in Microsoft Visual Studio.</span></span>
<span data-ttu-id="2e9ea-125">Met deze para meter selecteert u ook de standaard traceer-listener.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-125">This parameter also selects the default trace listener.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e9ea-126">-FilePath</span><span class="sxs-lookup"><span data-stu-id="2e9ea-126">-FilePath</span></span>

<span data-ttu-id="2e9ea-127">Hiermee geeft u een bestand op waarnaar met deze cmdlet de tracerings uitvoer wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-127">Specifies a file that this cmdlet sends the trace output to.</span></span>
<span data-ttu-id="2e9ea-128">Met deze para meter wordt ook de listener voor bestands tracering geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-128">This parameter also selects the file trace listener.</span></span>
<span data-ttu-id="2e9ea-129">Als u deze para meter gebruikt om de tracering te starten, gebruikt u de para meter *RemoveFileListener* om de tracering te stoppen.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-129">If you use this parameter to start the trace, use the *RemoveFileListener* parameter to stop the trace.</span></span>

```yaml
Type: System.String
Parameter Sets: optionsSet
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e9ea-130">-Force</span><span class="sxs-lookup"><span data-stu-id="2e9ea-130">-Force</span></span>

<span data-ttu-id="2e9ea-131">Geeft aan dat de cmdlet een alleen-lezen bestand overschrijft.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-131">Indicates that the cmdlet overwrites a read-only file.</span></span>
<span data-ttu-id="2e9ea-132">Gebruiken met de *filepath* -para meter.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-132">Use with the *FilePath* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e9ea-133">-ListenerOption</span><span class="sxs-lookup"><span data-stu-id="2e9ea-133">-ListenerOption</span></span>

<span data-ttu-id="2e9ea-134">Hiermee geeft u optionele gegevens op voor het voor voegsel van elk tracerings bericht in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-134">Specifies optional data to the prefix of each trace message in the output.</span></span>
<span data-ttu-id="2e9ea-135">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="2e9ea-135">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="2e9ea-136">Geen</span><span class="sxs-lookup"><span data-stu-id="2e9ea-136">None</span></span>
- <span data-ttu-id="2e9ea-137">LogicalOperationStack</span><span class="sxs-lookup"><span data-stu-id="2e9ea-137">LogicalOperationStack</span></span>
- <span data-ttu-id="2e9ea-138">DateTime</span><span class="sxs-lookup"><span data-stu-id="2e9ea-138">DateTime</span></span>
- <span data-ttu-id="2e9ea-139">Tijdstempel</span><span class="sxs-lookup"><span data-stu-id="2e9ea-139">Timestamp</span></span>
- <span data-ttu-id="2e9ea-140">Process</span><span class="sxs-lookup"><span data-stu-id="2e9ea-140">ProcessId</span></span>
- <span data-ttu-id="2e9ea-141">Thread</span><span class="sxs-lookup"><span data-stu-id="2e9ea-141">ThreadId</span></span>
- <span data-ttu-id="2e9ea-142">Procedures</span><span class="sxs-lookup"><span data-stu-id="2e9ea-142">Callstack</span></span>

<span data-ttu-id="2e9ea-143">Geen is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-143">None is the default.</span></span>

<span data-ttu-id="2e9ea-144">Als u meerdere opties wilt opgeven, scheidt u deze met komma's, maar zonder spaties, en plaatst u ze tussen dubbele aanhalings tekens, zoals ' ProcessID ', thread '.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-144">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "ProcessID,ThreadID".</span></span>

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e9ea-145">-Name</span><span class="sxs-lookup"><span data-stu-id="2e9ea-145">-Name</span></span>

<span data-ttu-id="2e9ea-146">Hiermee geeft u op welke onderdelen worden getraceerd.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-146">Specifies which components are traced.</span></span>
<span data-ttu-id="2e9ea-147">Voer de naam van de tracerings bron van elk onderdeel in.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-147">Enter the name of the trace source of each component.</span></span>
<span data-ttu-id="2e9ea-148">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-148">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="2e9ea-149">-Optie</span><span class="sxs-lookup"><span data-stu-id="2e9ea-149">-Option</span></span>

<span data-ttu-id="2e9ea-150">Hiermee geeft u het type gebeurtenissen op dat wordt getraceerd.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-150">Specifies the type of events that are traced.</span></span>
<span data-ttu-id="2e9ea-151">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="2e9ea-151">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="2e9ea-152">Geen</span><span class="sxs-lookup"><span data-stu-id="2e9ea-152">None</span></span>
- <span data-ttu-id="2e9ea-153">Constructor</span><span class="sxs-lookup"><span data-stu-id="2e9ea-153">Constructor</span></span>
- <span data-ttu-id="2e9ea-154">Gooien</span><span class="sxs-lookup"><span data-stu-id="2e9ea-154">Dispose</span></span>
- <span data-ttu-id="2e9ea-155">Volt ooien</span><span class="sxs-lookup"><span data-stu-id="2e9ea-155">Finalizer</span></span>
- <span data-ttu-id="2e9ea-156">Methode</span><span class="sxs-lookup"><span data-stu-id="2e9ea-156">Method</span></span>
- <span data-ttu-id="2e9ea-157">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="2e9ea-157">Property</span></span>
- <span data-ttu-id="2e9ea-158">Gedelegeerden</span><span class="sxs-lookup"><span data-stu-id="2e9ea-158">Delegates</span></span>
- <span data-ttu-id="2e9ea-159">Gebeurtenissen</span><span class="sxs-lookup"><span data-stu-id="2e9ea-159">Events</span></span>
- <span data-ttu-id="2e9ea-160">Uitzondering</span><span class="sxs-lookup"><span data-stu-id="2e9ea-160">Exception</span></span>
- <span data-ttu-id="2e9ea-161">Vergrendelen</span><span class="sxs-lookup"><span data-stu-id="2e9ea-161">Lock</span></span>
- <span data-ttu-id="2e9ea-162">Fout</span><span class="sxs-lookup"><span data-stu-id="2e9ea-162">Error</span></span>
- <span data-ttu-id="2e9ea-163">Fouten</span><span class="sxs-lookup"><span data-stu-id="2e9ea-163">Errors</span></span>
- <span data-ttu-id="2e9ea-164">Waarschuwing</span><span class="sxs-lookup"><span data-stu-id="2e9ea-164">Warning</span></span>
- <span data-ttu-id="2e9ea-165">Uitgebreid</span><span class="sxs-lookup"><span data-stu-id="2e9ea-165">Verbose</span></span>
- <span data-ttu-id="2e9ea-166">WriteLine</span><span class="sxs-lookup"><span data-stu-id="2e9ea-166">WriteLine</span></span>
- <span data-ttu-id="2e9ea-167">Gegevens</span><span class="sxs-lookup"><span data-stu-id="2e9ea-167">Data</span></span>
- <span data-ttu-id="2e9ea-168">Bereik</span><span class="sxs-lookup"><span data-stu-id="2e9ea-168">Scope</span></span>
- <span data-ttu-id="2e9ea-169">ExecutionFlow</span><span class="sxs-lookup"><span data-stu-id="2e9ea-169">ExecutionFlow</span></span>
- <span data-ttu-id="2e9ea-170">Assert</span><span class="sxs-lookup"><span data-stu-id="2e9ea-170">Assert</span></span>
- <span data-ttu-id="2e9ea-171">Alles</span><span class="sxs-lookup"><span data-stu-id="2e9ea-171">All</span></span>

<span data-ttu-id="2e9ea-172">Dit is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-172">All is the default.</span></span>

<span data-ttu-id="2e9ea-173">De volgende waarden zijn combi Naties van andere waarden:</span><span class="sxs-lookup"><span data-stu-id="2e9ea-173">The following values are combinations of other values:</span></span>

- <span data-ttu-id="2e9ea-174">ExecutionFlow: (constructor, Dispose, FINALIZE, methode, gemachtigden, gebeurtenissen en bereik)</span><span class="sxs-lookup"><span data-stu-id="2e9ea-174">ExecutionFlow: (Constructor, Dispose, Finalizer, Method, Delegates, Events, and Scope)</span></span>
- <span data-ttu-id="2e9ea-175">Gegevens: (constructor, Dispose, FINALIZE, eigenschap, verbose en WriteLine)</span><span class="sxs-lookup"><span data-stu-id="2e9ea-175">Data: (Constructor, Dispose, Finalizer, Property, Verbose, and WriteLine)</span></span>
- <span data-ttu-id="2e9ea-176">Fouten: (fout en uitzonde ring).</span><span class="sxs-lookup"><span data-stu-id="2e9ea-176">Errors: (Error and Exception).</span></span>

<span data-ttu-id="2e9ea-177">Als u meerdere opties wilt opgeven, scheidt u deze met komma's, maar zonder spaties, en plaatst u ze tussen dubbele aanhalings tekens, zoals ' constructor, Dispose '.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-177">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "Constructor,Dispose".</span></span>

```yaml
Type: System.Management.Automation.PSTraceSourceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2e9ea-178">-PassThru</span><span class="sxs-lookup"><span data-stu-id="2e9ea-178">-PassThru</span></span>

<span data-ttu-id="2e9ea-179">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-179">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="2e9ea-180">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-180">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e9ea-181">-PSHost</span><span class="sxs-lookup"><span data-stu-id="2e9ea-181">-PSHost</span></span>

<span data-ttu-id="2e9ea-182">ndicates dat deze cmdlet de tracerings uitvoer naar de Power shell-host verzendt.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-182">ndicates that this cmdlet sends the trace output to the PowerShell host.</span></span>
<span data-ttu-id="2e9ea-183">Met deze para meter wordt ook de PSHost Trace listener geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-183">This parameter also selects the PSHost trace listener.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e9ea-184">-RemoveFileListener</span><span class="sxs-lookup"><span data-stu-id="2e9ea-184">-RemoveFileListener</span></span>

<span data-ttu-id="2e9ea-185">Hiermee stopt u de tracering door de listener voor bestands tracering die is gekoppeld aan het opgegeven bestand te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-185">Stops the trace by removing the file trace listener associated with the specified file.</span></span>
<span data-ttu-id="2e9ea-186">Voer het pad en de bestands naam van het uitvoer bestand voor tracering in.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-186">Enter the path and file name of the trace output file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: removeFileListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e9ea-187">-RemoveListener</span><span class="sxs-lookup"><span data-stu-id="2e9ea-187">-RemoveListener</span></span>

<span data-ttu-id="2e9ea-188">Stopt de tracering door de traceer-listener te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-188">Stops the trace by removing the trace listener.</span></span>

<span data-ttu-id="2e9ea-189">Gebruik de volgende waarden met *RemoveListener* :</span><span class="sxs-lookup"><span data-stu-id="2e9ea-189">Use the following values with *RemoveListener* :</span></span>

- <span data-ttu-id="2e9ea-190">Als u PSHost (console) wilt verwijderen, typt u `Host` .</span><span class="sxs-lookup"><span data-stu-id="2e9ea-190">To remove PSHost (console), type `Host`.</span></span>
- <span data-ttu-id="2e9ea-191">Om het fout opsporingsprogramma te verwijderen, typt u `Debug` .</span><span class="sxs-lookup"><span data-stu-id="2e9ea-191">To remove Debugger, type `Debug`.</span></span>
- <span data-ttu-id="2e9ea-192">Als u alle traceer-listeners wilt verwijderen, typt u `*` .</span><span class="sxs-lookup"><span data-stu-id="2e9ea-192">To remove all trace listeners, type `*`.</span></span>

<span data-ttu-id="2e9ea-193">Als u de listener voor bestands tracering wilt verwijderen, gebruikt u de para meter *RemoveFileListener* .</span><span class="sxs-lookup"><span data-stu-id="2e9ea-193">To remove the file trace listener, use the *RemoveFileListener* parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: removeAllListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e9ea-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2e9ea-194">CommonParameters</span></span>

<span data-ttu-id="2e9ea-195">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-195">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2e9ea-196">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-196">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2e9ea-197">INVOER</span><span class="sxs-lookup"><span data-stu-id="2e9ea-197">INPUTS</span></span>

### <span data-ttu-id="2e9ea-198">System. String</span><span class="sxs-lookup"><span data-stu-id="2e9ea-198">System.String</span></span>

<span data-ttu-id="2e9ea-199">U kunt een teken reeks die een naam bevat, door sluizen naar **set-TraceSource**.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-199">You can pipe a string that contains a name to **Set-TraceSource**.</span></span>

## <span data-ttu-id="2e9ea-200">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2e9ea-200">OUTPUTS</span></span>

### <span data-ttu-id="2e9ea-201">Geen of System. Management. Automation. PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="2e9ea-201">None or System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="2e9ea-202">Wanneer u de para meter *PassThru* gebruikt, genereert **set-TraceSource** een **System. Management. Automation. PSTraceSource** -object dat de traceer sessie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-202">When you use the *PassThru* parameter, **Set-TraceSource** generates a **System.Management.Automation.PSTraceSource** object representing the trace session.</span></span>
<span data-ttu-id="2e9ea-203">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-203">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2e9ea-204">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2e9ea-204">NOTES</span></span>

* <span data-ttu-id="2e9ea-205">Tracering is een methode die ontwikkel aars gebruiken voor het opsporen van fouten en het verfijnen van Program ma's.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-205">Tracing is a method that developers use to debug and refine programs.</span></span> <span data-ttu-id="2e9ea-206">Bij het traceren worden gedetailleerde berichten over elke stap in de interne verwerking gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-206">When tracing, the program generates detailed messages about each step in its internal processing.</span></span>

  <span data-ttu-id="2e9ea-207">De Power shell-cmdlets voor tracering zijn ontworpen om Power shell-ontwikkel aars te helpen, maar ze zijn beschikbaar voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-207">The PowerShell tracing cmdlets are designed to help PowerShell developers, but they are available to all users.</span></span>
<span data-ttu-id="2e9ea-208">U kunt vrijwel elk aspect van de functionaliteit van Power shell bewaken.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-208">They let you monitor nearly every aspect of the functionality of PowerShell.</span></span>

  <span data-ttu-id="2e9ea-209">Een tracerings bron is het deel van elk Power Shell-onderdeel dat tracering beheert en tracerings berichten genereert voor het onderdeel.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-209">A trace source is the part of each PowerShell component that manages tracing and generates trace messages for the component.</span></span>
<span data-ttu-id="2e9ea-210">Als u een onderdeel wilt traceren, identificeert u de traceer bron.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-210">To trace a component, you identify its trace source.</span></span>

  <span data-ttu-id="2e9ea-211">Een traceer-listener ontvangt de uitvoer van de tracering en geeft deze weer voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-211">A trace listener receives the output of the trace and displays it to the user.</span></span>
<span data-ttu-id="2e9ea-212">U kunt ervoor kiezen om de tracerings gegevens te verzenden naar een fout opsporingsprogramma voor gebruikers modus of kernel-modus, naar de-console, naar een bestand of naar een aangepaste listener die is afgeleid van de **System. Diagnostics. TraceListener** -klasse.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-212">You can elect to send the trace data to a user-mode or kernel-mode debugger, to the console, to a file, or to a custom listener derived from the **System.Diagnostics.TraceListener** class.</span></span>

* <span data-ttu-id="2e9ea-213">Als u een tracering wilt starten, gebruikt u de para meter *name* om een tracerings bron op te geven en de para meters *filepath* , *debugger* of *PSHost* om een listener op te geven (een bestemming voor de uitvoer).</span><span class="sxs-lookup"><span data-stu-id="2e9ea-213">To start a trace, use the *Name* parameter to specify a trace source and the *FilePath* , *Debugger* , or *PSHost* parameters to specify a listener (a destination for the output).</span></span> <span data-ttu-id="2e9ea-214">Gebruik de para meter *Options* om te bepalen welke typen gebeurtenissen worden getraceerd en de para meter *ListenerOption* om de uitvoer van de tracering te configureren.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-214">Use the *Options* parameter to determine the types of events that are traced and the *ListenerOption* parameter to configure the trace output.</span></span>
* <span data-ttu-id="2e9ea-215">Als u de configuratie van een tracering wilt wijzigen, voert u de opdracht **set-TraceSource** in, zoals u een tracering wilt starten.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-215">To change the configuration of a trace, enter a **Set-TraceSource** command as you would to start a trace.</span></span> <span data-ttu-id="2e9ea-216">Power Shell heeft gedetecteerd dat de tracerings bron al wordt getraceerd.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-216">PowerShell recognizes that the trace source is already being traced.</span></span> <span data-ttu-id="2e9ea-217">De tracering wordt gestopt, de nieuwe configuratie wordt toegevoegd en de tracering wordt gestart of opnieuw gestart.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-217">It stops the trace, adds the new configuration, and starts or restarts the trace.</span></span>
* <span data-ttu-id="2e9ea-218">Als u een tracering wilt stoppen, gebruikt u de para meter *RemoveListener* .</span><span class="sxs-lookup"><span data-stu-id="2e9ea-218">To stop a trace, use the *RemoveListener* parameter.</span></span> <span data-ttu-id="2e9ea-219">Als u een tracering wilt stoppen die gebruikmaakt van de file listener (een tracering die is gestart met de para meter *filepath* ), gebruikt u de para meter *RemoveFileListener* .</span><span class="sxs-lookup"><span data-stu-id="2e9ea-219">To stop a trace that uses the file listener (a trace started by using the *FilePath* parameter), use the *RemoveFileListener* parameter.</span></span> <span data-ttu-id="2e9ea-220">Wanneer u de listener verwijdert, wordt de tracering gestopt.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-220">When you remove the listener, the trace stops.</span></span>
* <span data-ttu-id="2e9ea-221">Gebruik Get-TraceSource om te bepalen welke onderdelen kunnen worden getraceerd.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-221">To determine which components can be traced, use Get-TraceSource.</span></span> <span data-ttu-id="2e9ea-222">De tracerings bronnen voor elke module worden automatisch geladen wanneer het onderdeel wordt gebruikt en ze worden weer gegeven in de uitvoer van **Get-TraceSource**.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-222">The trace sources for each module are loaded automatically when the component is in use, and they appear in the output of **Get-TraceSource**.</span></span>

## <span data-ttu-id="2e9ea-223">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2e9ea-223">RELATED LINKS</span></span>

[<span data-ttu-id="2e9ea-224">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="2e9ea-224">Get-TraceSource</span></span>](Get-TraceSource.md)

[<span data-ttu-id="2e9ea-225">Tracering-opdracht</span><span class="sxs-lookup"><span data-stu-id="2e9ea-225">Trace-Command</span></span>](Trace-Command.md)
