---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-tracesource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TraceSource
ms.openlocfilehash: cef166404af546c35ccc3b0ffed4174515f74c15
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250369"
---
# <span data-ttu-id="12093-103">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="12093-103">Set-TraceSource</span></span>

## <span data-ttu-id="12093-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="12093-104">SYNOPSIS</span></span>
<span data-ttu-id="12093-105">Hiermee configureert, start en stopt u het traceren van Power shell-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="12093-105">Configures, starts, and stops a trace of PowerShell components.</span></span>

## <span data-ttu-id="12093-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="12093-106">SYNTAX</span></span>

### <span data-ttu-id="12093-107">optieset (standaard)</span><span class="sxs-lookup"><span data-stu-id="12093-107">optionsSet (Default)</span></span>

```
Set-TraceSource [-Name] <String[]> [[-Option] <PSTraceSourceOptions>] [-ListenerOption <TraceOptions>]
 [-FilePath <String>] [-Force] [-Debugger] [-PSHost] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="12093-108">removeAllListenersSet</span><span class="sxs-lookup"><span data-stu-id="12093-108">removeAllListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveListener <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="12093-109">removeFileListenersSet</span><span class="sxs-lookup"><span data-stu-id="12093-109">removeFileListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveFileListener <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="12093-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="12093-110">DESCRIPTION</span></span>

<span data-ttu-id="12093-111">De cmdlet **set-TraceSource** configureert, start en stopt een tracering van een Power Shell-onderdeel.</span><span class="sxs-lookup"><span data-stu-id="12093-111">The **Set-TraceSource** cmdlet configures, starts, and stops a trace of a PowerShell component.</span></span>
<span data-ttu-id="12093-112">U kunt deze gebruiken om op te geven welke onderdelen moeten worden getraceerd en waar de tracerings uitvoer wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="12093-112">You can use it to specify which components will be traced and where the tracing output is sent.</span></span>

## <span data-ttu-id="12093-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="12093-113">EXAMPLES</span></span>

### <span data-ttu-id="12093-114">Voor beeld 1: het ParameterBinding-onderdeel traceren</span><span class="sxs-lookup"><span data-stu-id="12093-114">Example 1: Trace the ParameterBinding component</span></span>

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -Option ExecutionFlow -PSHost -ListenerOption "ProcessId,TimeStamp"
```

<span data-ttu-id="12093-115">Met deze opdracht start u het traceren van het onderdeel ParameterBinding van Power shell.</span><span class="sxs-lookup"><span data-stu-id="12093-115">This command starts tracing for the ParameterBinding component of PowerShell.</span></span>
<span data-ttu-id="12093-116">Hierbij wordt de para meter *name* gebruikt voor het opgeven van de tracerings bron, de *optie* parameter voor het selecteren van de ExecutionFlow tracerings gebeurtenissen en de para meter *PSHost* om de Power shell-host-listener te selecteren, die de uitvoer naar de-console verzendt.</span><span class="sxs-lookup"><span data-stu-id="12093-116">It uses the *Name* parameter to specify the trace source, the *Option* parameter to select the ExecutionFlow trace events, and the *PSHost* parameter to select the PowerShell host listener, which sends the output to the console.</span></span>
<span data-ttu-id="12093-117">Met de para meter *ListenerOption* worden de ProcessID-en time stamp-waarden toegevoegd aan het voor voegsel van het tracerings bericht.</span><span class="sxs-lookup"><span data-stu-id="12093-117">The *ListenerOption* parameter adds the ProcessID and TimeStamp values to the trace message prefix.</span></span>

### <span data-ttu-id="12093-118">Voor beeld 2: een tracering stoppen</span><span class="sxs-lookup"><span data-stu-id="12093-118">Example 2: Stop a trace</span></span>

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -RemoveListener "Host"
```

<span data-ttu-id="12093-119">Met deze opdracht stopt u de tracering van het ParameterBinding-onderdeel van Power shell.</span><span class="sxs-lookup"><span data-stu-id="12093-119">This command stops the trace of the ParameterBinding component of PowerShell.</span></span>
<span data-ttu-id="12093-120">Hierbij wordt de para meter *name* gebruikt voor het identificeren van het onderdeel dat wordt getraceerd en de para meter *RemoveListener* voor het identificeren van de traceer-listener.</span><span class="sxs-lookup"><span data-stu-id="12093-120">It uses the *Name* parameter to identify the component that was being traced and the *RemoveListener* parameter to identify the trace listener.</span></span>

## <span data-ttu-id="12093-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="12093-121">PARAMETERS</span></span>

### <span data-ttu-id="12093-122">-Fout opsporingsprogramma</span><span class="sxs-lookup"><span data-stu-id="12093-122">-Debugger</span></span>

<span data-ttu-id="12093-123">Geeft aan dat de cmdlet de tracerings uitvoer naar het fout opsporingsprogramma verzendt.</span><span class="sxs-lookup"><span data-stu-id="12093-123">Indicates that the cmdlet sends the trace output to the debugger.</span></span>
<span data-ttu-id="12093-124">U kunt de uitvoer bekijken in een fout opsporingsprogramma voor gebruikers modus of kernelmodus of in micro soft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="12093-124">You can view the output in any user-mode or kernel mode debugger or in Microsoft Visual Studio.</span></span>
<span data-ttu-id="12093-125">Met deze para meter selecteert u ook de standaard traceer-listener.</span><span class="sxs-lookup"><span data-stu-id="12093-125">This parameter also selects the default trace listener.</span></span>

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

### <span data-ttu-id="12093-126">-FilePath</span><span class="sxs-lookup"><span data-stu-id="12093-126">-FilePath</span></span>

<span data-ttu-id="12093-127">Hiermee geeft u een bestand op waarnaar met deze cmdlet de tracerings uitvoer wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="12093-127">Specifies a file that this cmdlet sends the trace output to.</span></span>
<span data-ttu-id="12093-128">Met deze para meter wordt ook de listener voor bestands tracering geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="12093-128">This parameter also selects the file trace listener.</span></span>
<span data-ttu-id="12093-129">Als u deze para meter gebruikt om de tracering te starten, gebruikt u de para meter *RemoveFileListener* om de tracering te stoppen.</span><span class="sxs-lookup"><span data-stu-id="12093-129">If you use this parameter to start the trace, use the *RemoveFileListener* parameter to stop the trace.</span></span>

```yaml
Type: System.String
Parameter Sets: optionsSet
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="12093-130">-Force</span><span class="sxs-lookup"><span data-stu-id="12093-130">-Force</span></span>

<span data-ttu-id="12093-131">Geeft aan dat de cmdlet een alleen-lezen bestand overschrijft.</span><span class="sxs-lookup"><span data-stu-id="12093-131">Indicates that the cmdlet overwrites a read-only file.</span></span>
<span data-ttu-id="12093-132">Gebruiken met de *filepath* -para meter.</span><span class="sxs-lookup"><span data-stu-id="12093-132">Use with the *FilePath* parameter.</span></span>

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

### <span data-ttu-id="12093-133">-ListenerOption</span><span class="sxs-lookup"><span data-stu-id="12093-133">-ListenerOption</span></span>

<span data-ttu-id="12093-134">Hiermee geeft u optionele gegevens op voor het voor voegsel van elk tracerings bericht in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="12093-134">Specifies optional data to the prefix of each trace message in the output.</span></span>
<span data-ttu-id="12093-135">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="12093-135">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="12093-136">Geen</span><span class="sxs-lookup"><span data-stu-id="12093-136">None</span></span>
- <span data-ttu-id="12093-137">LogicalOperationStack</span><span class="sxs-lookup"><span data-stu-id="12093-137">LogicalOperationStack</span></span>
- <span data-ttu-id="12093-138">DateTime</span><span class="sxs-lookup"><span data-stu-id="12093-138">DateTime</span></span>
- <span data-ttu-id="12093-139">Tijdstempel</span><span class="sxs-lookup"><span data-stu-id="12093-139">Timestamp</span></span>
- <span data-ttu-id="12093-140">Process</span><span class="sxs-lookup"><span data-stu-id="12093-140">ProcessId</span></span>
- <span data-ttu-id="12093-141">Thread</span><span class="sxs-lookup"><span data-stu-id="12093-141">ThreadId</span></span>
- <span data-ttu-id="12093-142">Procedures</span><span class="sxs-lookup"><span data-stu-id="12093-142">Callstack</span></span>

<span data-ttu-id="12093-143">Geen is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="12093-143">None is the default.</span></span>

<span data-ttu-id="12093-144">Als u meerdere opties wilt opgeven, scheidt u deze met komma's, maar zonder spaties, en plaatst u ze tussen dubbele aanhalings tekens, zoals ' ProcessID ', thread '.</span><span class="sxs-lookup"><span data-stu-id="12093-144">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "ProcessID,ThreadID".</span></span>

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

### <span data-ttu-id="12093-145">-Name</span><span class="sxs-lookup"><span data-stu-id="12093-145">-Name</span></span>

<span data-ttu-id="12093-146">Hiermee geeft u op welke onderdelen worden getraceerd.</span><span class="sxs-lookup"><span data-stu-id="12093-146">Specifies which components are traced.</span></span>
<span data-ttu-id="12093-147">Voer de naam van de tracerings bron van elk onderdeel in.</span><span class="sxs-lookup"><span data-stu-id="12093-147">Enter the name of the trace source of each component.</span></span>
<span data-ttu-id="12093-148">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="12093-148">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="12093-149">-Optie</span><span class="sxs-lookup"><span data-stu-id="12093-149">-Option</span></span>

<span data-ttu-id="12093-150">Hiermee geeft u het type gebeurtenissen op dat wordt getraceerd.</span><span class="sxs-lookup"><span data-stu-id="12093-150">Specifies the type of events that are traced.</span></span>
<span data-ttu-id="12093-151">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="12093-151">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="12093-152">Geen</span><span class="sxs-lookup"><span data-stu-id="12093-152">None</span></span>
- <span data-ttu-id="12093-153">Constructor</span><span class="sxs-lookup"><span data-stu-id="12093-153">Constructor</span></span>
- <span data-ttu-id="12093-154">Gooien</span><span class="sxs-lookup"><span data-stu-id="12093-154">Dispose</span></span>
- <span data-ttu-id="12093-155">Volt ooien</span><span class="sxs-lookup"><span data-stu-id="12093-155">Finalizer</span></span>
- <span data-ttu-id="12093-156">Methode</span><span class="sxs-lookup"><span data-stu-id="12093-156">Method</span></span>
- <span data-ttu-id="12093-157">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="12093-157">Property</span></span>
- <span data-ttu-id="12093-158">Gedelegeerden</span><span class="sxs-lookup"><span data-stu-id="12093-158">Delegates</span></span>
- <span data-ttu-id="12093-159">Gebeurtenissen</span><span class="sxs-lookup"><span data-stu-id="12093-159">Events</span></span>
- <span data-ttu-id="12093-160">Uitzondering</span><span class="sxs-lookup"><span data-stu-id="12093-160">Exception</span></span>
- <span data-ttu-id="12093-161">Vergrendelen</span><span class="sxs-lookup"><span data-stu-id="12093-161">Lock</span></span>
- <span data-ttu-id="12093-162">Fout</span><span class="sxs-lookup"><span data-stu-id="12093-162">Error</span></span>
- <span data-ttu-id="12093-163">Fouten</span><span class="sxs-lookup"><span data-stu-id="12093-163">Errors</span></span>
- <span data-ttu-id="12093-164">Waarschuwing</span><span class="sxs-lookup"><span data-stu-id="12093-164">Warning</span></span>
- <span data-ttu-id="12093-165">Uitgebreid</span><span class="sxs-lookup"><span data-stu-id="12093-165">Verbose</span></span>
- <span data-ttu-id="12093-166">WriteLine</span><span class="sxs-lookup"><span data-stu-id="12093-166">WriteLine</span></span>
- <span data-ttu-id="12093-167">Gegevens</span><span class="sxs-lookup"><span data-stu-id="12093-167">Data</span></span>
- <span data-ttu-id="12093-168">Bereik</span><span class="sxs-lookup"><span data-stu-id="12093-168">Scope</span></span>
- <span data-ttu-id="12093-169">ExecutionFlow</span><span class="sxs-lookup"><span data-stu-id="12093-169">ExecutionFlow</span></span>
- <span data-ttu-id="12093-170">Assert</span><span class="sxs-lookup"><span data-stu-id="12093-170">Assert</span></span>
- <span data-ttu-id="12093-171">Alles</span><span class="sxs-lookup"><span data-stu-id="12093-171">All</span></span>

<span data-ttu-id="12093-172">Dit is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="12093-172">All is the default.</span></span>

<span data-ttu-id="12093-173">De volgende waarden zijn combi Naties van andere waarden:</span><span class="sxs-lookup"><span data-stu-id="12093-173">The following values are combinations of other values:</span></span>

- <span data-ttu-id="12093-174">ExecutionFlow: (constructor, Dispose, FINALIZE, methode, gemachtigden, gebeurtenissen en bereik)</span><span class="sxs-lookup"><span data-stu-id="12093-174">ExecutionFlow: (Constructor, Dispose, Finalizer, Method, Delegates, Events, and Scope)</span></span>
- <span data-ttu-id="12093-175">Gegevens: (constructor, Dispose, FINALIZE, eigenschap, verbose en WriteLine)</span><span class="sxs-lookup"><span data-stu-id="12093-175">Data: (Constructor, Dispose, Finalizer, Property, Verbose, and WriteLine)</span></span>
- <span data-ttu-id="12093-176">Fouten: (fout en uitzonde ring).</span><span class="sxs-lookup"><span data-stu-id="12093-176">Errors: (Error and Exception).</span></span>

<span data-ttu-id="12093-177">Als u meerdere opties wilt opgeven, scheidt u deze met komma's, maar zonder spaties, en plaatst u ze tussen dubbele aanhalings tekens, zoals ' constructor, Dispose '.</span><span class="sxs-lookup"><span data-stu-id="12093-177">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "Constructor,Dispose".</span></span>

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

### <span data-ttu-id="12093-178">-PassThru</span><span class="sxs-lookup"><span data-stu-id="12093-178">-PassThru</span></span>

<span data-ttu-id="12093-179">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="12093-179">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="12093-180">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="12093-180">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="12093-181">-PSHost</span><span class="sxs-lookup"><span data-stu-id="12093-181">-PSHost</span></span>

<span data-ttu-id="12093-182">ndicates dat deze cmdlet de tracerings uitvoer naar de Power shell-host verzendt.</span><span class="sxs-lookup"><span data-stu-id="12093-182">ndicates that this cmdlet sends the trace output to the PowerShell host.</span></span>
<span data-ttu-id="12093-183">Met deze para meter wordt ook de PSHost Trace listener geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="12093-183">This parameter also selects the PSHost trace listener.</span></span>

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

### <span data-ttu-id="12093-184">-RemoveFileListener</span><span class="sxs-lookup"><span data-stu-id="12093-184">-RemoveFileListener</span></span>

<span data-ttu-id="12093-185">Hiermee stopt u de tracering door de listener voor bestands tracering die is gekoppeld aan het opgegeven bestand te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="12093-185">Stops the trace by removing the file trace listener associated with the specified file.</span></span>
<span data-ttu-id="12093-186">Voer het pad en de bestands naam van het uitvoer bestand voor tracering in.</span><span class="sxs-lookup"><span data-stu-id="12093-186">Enter the path and file name of the trace output file.</span></span>

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

### <span data-ttu-id="12093-187">-RemoveListener</span><span class="sxs-lookup"><span data-stu-id="12093-187">-RemoveListener</span></span>

<span data-ttu-id="12093-188">Stopt de tracering door de traceer-listener te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="12093-188">Stops the trace by removing the trace listener.</span></span>

<span data-ttu-id="12093-189">Gebruik de volgende waarden met *RemoveListener* :</span><span class="sxs-lookup"><span data-stu-id="12093-189">Use the following values with *RemoveListener* :</span></span>

- <span data-ttu-id="12093-190">Als u PSHost (console) wilt verwijderen, typt u `Host` .</span><span class="sxs-lookup"><span data-stu-id="12093-190">To remove PSHost (console), type `Host`.</span></span>
- <span data-ttu-id="12093-191">Om het fout opsporingsprogramma te verwijderen, typt u `Debug` .</span><span class="sxs-lookup"><span data-stu-id="12093-191">To remove Debugger, type `Debug`.</span></span>
- <span data-ttu-id="12093-192">Als u alle traceer-listeners wilt verwijderen, typt u `*` .</span><span class="sxs-lookup"><span data-stu-id="12093-192">To remove all trace listeners, type `*`.</span></span>

<span data-ttu-id="12093-193">Als u de listener voor bestands tracering wilt verwijderen, gebruikt u de para meter *RemoveFileListener* .</span><span class="sxs-lookup"><span data-stu-id="12093-193">To remove the file trace listener, use the *RemoveFileListener* parameter.</span></span>

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

### <span data-ttu-id="12093-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12093-194">CommonParameters</span></span>

<span data-ttu-id="12093-195">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="12093-195">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12093-196">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="12093-196">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="12093-197">INVOER</span><span class="sxs-lookup"><span data-stu-id="12093-197">INPUTS</span></span>

### <span data-ttu-id="12093-198">System. String</span><span class="sxs-lookup"><span data-stu-id="12093-198">System.String</span></span>

<span data-ttu-id="12093-199">U kunt een teken reeks die een naam bevat, door sluizen naar **set-TraceSource**.</span><span class="sxs-lookup"><span data-stu-id="12093-199">You can pipe a string that contains a name to **Set-TraceSource**.</span></span>

## <span data-ttu-id="12093-200">UITVOER</span><span class="sxs-lookup"><span data-stu-id="12093-200">OUTPUTS</span></span>

### <span data-ttu-id="12093-201">Geen of System. Management. Automation. PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="12093-201">None or System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="12093-202">Wanneer u de para meter *PassThru* gebruikt, genereert **set-TraceSource** een **System. Management. Automation. PSTraceSource** -object dat de traceer sessie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="12093-202">When you use the *PassThru* parameter, **Set-TraceSource** generates a **System.Management.Automation.PSTraceSource** object representing the trace session.</span></span>
<span data-ttu-id="12093-203">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="12093-203">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="12093-204">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="12093-204">NOTES</span></span>

* <span data-ttu-id="12093-205">Tracering is een methode die ontwikkel aars gebruiken voor het opsporen van fouten en het verfijnen van Program ma's.</span><span class="sxs-lookup"><span data-stu-id="12093-205">Tracing is a method that developers use to debug and refine programs.</span></span> <span data-ttu-id="12093-206">Bij het traceren worden gedetailleerde berichten over elke stap in de interne verwerking gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="12093-206">When tracing, the program generates detailed messages about each step in its internal processing.</span></span>

  <span data-ttu-id="12093-207">De Power shell-cmdlets voor tracering zijn ontworpen om Power shell-ontwikkel aars te helpen, maar ze zijn beschikbaar voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="12093-207">The PowerShell tracing cmdlets are designed to help PowerShell developers, but they are available to all users.</span></span>
<span data-ttu-id="12093-208">U kunt vrijwel elk aspect van de functionaliteit van Power shell bewaken.</span><span class="sxs-lookup"><span data-stu-id="12093-208">They let you monitor nearly every aspect of the functionality of PowerShell.</span></span>

  <span data-ttu-id="12093-209">Een tracerings bron is het deel van elk Power Shell-onderdeel dat tracering beheert en tracerings berichten genereert voor het onderdeel.</span><span class="sxs-lookup"><span data-stu-id="12093-209">A trace source is the part of each PowerShell component that manages tracing and generates trace messages for the component.</span></span>
<span data-ttu-id="12093-210">Als u een onderdeel wilt traceren, identificeert u de traceer bron.</span><span class="sxs-lookup"><span data-stu-id="12093-210">To trace a component, you identify its trace source.</span></span>

  <span data-ttu-id="12093-211">Een traceer-listener ontvangt de uitvoer van de tracering en geeft deze weer voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="12093-211">A trace listener receives the output of the trace and displays it to the user.</span></span>
<span data-ttu-id="12093-212">U kunt ervoor kiezen om de tracerings gegevens te verzenden naar een fout opsporingsprogramma voor gebruikers modus of kernel-modus, naar de-console, naar een bestand of naar een aangepaste listener die is afgeleid van de **System. Diagnostics. TraceListener** -klasse.</span><span class="sxs-lookup"><span data-stu-id="12093-212">You can elect to send the trace data to a user-mode or kernel-mode debugger, to the console, to a file, or to a custom listener derived from the **System.Diagnostics.TraceListener** class.</span></span>

* <span data-ttu-id="12093-213">Als u een tracering wilt starten, gebruikt u de para meter *name* om een tracerings bron op te geven en de para meters *filepath* , *debugger* of *PSHost* om een listener op te geven (een bestemming voor de uitvoer).</span><span class="sxs-lookup"><span data-stu-id="12093-213">To start a trace, use the *Name* parameter to specify a trace source and the *FilePath* , *Debugger* , or *PSHost* parameters to specify a listener (a destination for the output).</span></span> <span data-ttu-id="12093-214">Gebruik de para meter *Options* om te bepalen welke typen gebeurtenissen worden getraceerd en de para meter *ListenerOption* om de uitvoer van de tracering te configureren.</span><span class="sxs-lookup"><span data-stu-id="12093-214">Use the *Options* parameter to determine the types of events that are traced and the *ListenerOption* parameter to configure the trace output.</span></span>
* <span data-ttu-id="12093-215">Als u de configuratie van een tracering wilt wijzigen, voert u de opdracht **set-TraceSource** in, zoals u een tracering wilt starten.</span><span class="sxs-lookup"><span data-stu-id="12093-215">To change the configuration of a trace, enter a **Set-TraceSource** command as you would to start a trace.</span></span> <span data-ttu-id="12093-216">Power Shell heeft gedetecteerd dat de tracerings bron al wordt getraceerd.</span><span class="sxs-lookup"><span data-stu-id="12093-216">PowerShell recognizes that the trace source is already being traced.</span></span> <span data-ttu-id="12093-217">De tracering wordt gestopt, de nieuwe configuratie wordt toegevoegd en de tracering wordt gestart of opnieuw gestart.</span><span class="sxs-lookup"><span data-stu-id="12093-217">It stops the trace, adds the new configuration, and starts or restarts the trace.</span></span>
* <span data-ttu-id="12093-218">Als u een tracering wilt stoppen, gebruikt u de para meter *RemoveListener* .</span><span class="sxs-lookup"><span data-stu-id="12093-218">To stop a trace, use the *RemoveListener* parameter.</span></span> <span data-ttu-id="12093-219">Als u een tracering wilt stoppen die gebruikmaakt van de file listener (een tracering die is gestart met de para meter *filepath* ), gebruikt u de para meter *RemoveFileListener* .</span><span class="sxs-lookup"><span data-stu-id="12093-219">To stop a trace that uses the file listener (a trace started by using the *FilePath* parameter), use the *RemoveFileListener* parameter.</span></span> <span data-ttu-id="12093-220">Wanneer u de listener verwijdert, wordt de tracering gestopt.</span><span class="sxs-lookup"><span data-stu-id="12093-220">When you remove the listener, the trace stops.</span></span>
* <span data-ttu-id="12093-221">Gebruik Get-TraceSource om te bepalen welke onderdelen kunnen worden getraceerd.</span><span class="sxs-lookup"><span data-stu-id="12093-221">To determine which components can be traced, use Get-TraceSource.</span></span> <span data-ttu-id="12093-222">De tracerings bronnen voor elke module worden automatisch geladen wanneer het onderdeel wordt gebruikt en ze worden weer gegeven in de uitvoer van **Get-TraceSource**.</span><span class="sxs-lookup"><span data-stu-id="12093-222">The trace sources for each module are loaded automatically when the component is in use, and they appear in the output of **Get-TraceSource**.</span></span>

## <span data-ttu-id="12093-223">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="12093-223">RELATED LINKS</span></span>

[<span data-ttu-id="12093-224">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="12093-224">Get-TraceSource</span></span>](Get-TraceSource.md)

[<span data-ttu-id="12093-225">Tracering-opdracht</span><span class="sxs-lookup"><span data-stu-id="12093-225">Trace-Command</span></span>](Trace-Command.md)
