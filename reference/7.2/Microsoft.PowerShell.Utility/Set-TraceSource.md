---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-tracesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TraceSource
ms.openlocfilehash: 6e7fd1c6eb3551906b4dd9d947b5e551cd05d30a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706152"
---
# <span data-ttu-id="8f1ac-102">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="8f1ac-102">Set-TraceSource</span></span>

## <span data-ttu-id="8f1ac-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="8f1ac-103">SYNOPSIS</span></span>
<span data-ttu-id="8f1ac-104">Hiermee configureert, start en stopt u het traceren van Power shell-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-104">Configures, starts, and stops a trace of PowerShell components.</span></span>

## <span data-ttu-id="8f1ac-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="8f1ac-105">SYNTAX</span></span>

### <span data-ttu-id="8f1ac-106">optieset (standaard)</span><span class="sxs-lookup"><span data-stu-id="8f1ac-106">optionsSet (Default)</span></span>

```
Set-TraceSource [-Name] <String[]> [[-Option] <PSTraceSourceOptions>] [-ListenerOption <TraceOptions>]
 [-FilePath <String>] [-Force] [-Debugger] [-PSHost] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="8f1ac-107">removeAllListenersSet</span><span class="sxs-lookup"><span data-stu-id="8f1ac-107">removeAllListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveListener <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="8f1ac-108">removeFileListenersSet</span><span class="sxs-lookup"><span data-stu-id="8f1ac-108">removeFileListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveFileListener <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="8f1ac-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8f1ac-109">DESCRIPTION</span></span>

<span data-ttu-id="8f1ac-110">De cmdlet **set-TraceSource** configureert, start en stopt een tracering van een Power Shell-onderdeel.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-110">The **Set-TraceSource** cmdlet configures, starts, and stops a trace of a PowerShell component.</span></span>
<span data-ttu-id="8f1ac-111">U kunt deze gebruiken om op te geven welke onderdelen moeten worden getraceerd en waar de tracerings uitvoer wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-111">You can use it to specify which components will be traced and where the tracing output is sent.</span></span>

## <span data-ttu-id="8f1ac-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8f1ac-112">EXAMPLES</span></span>

### <span data-ttu-id="8f1ac-113">Voor beeld 1: het ParameterBinding-onderdeel traceren</span><span class="sxs-lookup"><span data-stu-id="8f1ac-113">Example 1: Trace the ParameterBinding component</span></span>

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -Option ExecutionFlow -PSHost -ListenerOption "ProcessId,TimeStamp"
```

<span data-ttu-id="8f1ac-114">Met deze opdracht start u het traceren van het onderdeel ParameterBinding van Power shell.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-114">This command starts tracing for the ParameterBinding component of PowerShell.</span></span>
<span data-ttu-id="8f1ac-115">Hierbij wordt de para meter *name* gebruikt voor het opgeven van de tracerings bron, de *optie* parameter voor het selecteren van de ExecutionFlow tracerings gebeurtenissen en de para meter *PSHost* om de Power shell-host-listener te selecteren, die de uitvoer naar de-console verzendt.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-115">It uses the *Name* parameter to specify the trace source, the *Option* parameter to select the ExecutionFlow trace events, and the *PSHost* parameter to select the PowerShell host listener, which sends the output to the console.</span></span>
<span data-ttu-id="8f1ac-116">Met de para meter *ListenerOption* worden de ProcessID-en time stamp-waarden toegevoegd aan het voor voegsel van het tracerings bericht.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-116">The *ListenerOption* parameter adds the ProcessID and TimeStamp values to the trace message prefix.</span></span>

### <span data-ttu-id="8f1ac-117">Voor beeld 2: een tracering stoppen</span><span class="sxs-lookup"><span data-stu-id="8f1ac-117">Example 2: Stop a trace</span></span>

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -RemoveListener "Host"
```

<span data-ttu-id="8f1ac-118">Met deze opdracht stopt u de tracering van het ParameterBinding-onderdeel van Power shell.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-118">This command stops the trace of the ParameterBinding component of PowerShell.</span></span>
<span data-ttu-id="8f1ac-119">Hierbij wordt de para meter *name* gebruikt voor het identificeren van het onderdeel dat wordt getraceerd en de para meter *RemoveListener* voor het identificeren van de traceer-listener.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-119">It uses the *Name* parameter to identify the component that was being traced and the *RemoveListener* parameter to identify the trace listener.</span></span>

## <span data-ttu-id="8f1ac-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8f1ac-120">PARAMETERS</span></span>

### <span data-ttu-id="8f1ac-121">-Fout opsporingsprogramma</span><span class="sxs-lookup"><span data-stu-id="8f1ac-121">-Debugger</span></span>

<span data-ttu-id="8f1ac-122">Geeft aan dat de cmdlet de tracerings uitvoer naar het fout opsporingsprogramma verzendt.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-122">Indicates that the cmdlet sends the trace output to the debugger.</span></span>
<span data-ttu-id="8f1ac-123">U kunt de uitvoer bekijken in een fout opsporingsprogramma voor gebruikers modus of kernelmodus of in micro soft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-123">You can view the output in any user-mode or kernel mode debugger or in Microsoft Visual Studio.</span></span>
<span data-ttu-id="8f1ac-124">Met deze para meter selecteert u ook de standaard traceer-listener.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-124">This parameter also selects the default trace listener.</span></span>

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

### <span data-ttu-id="8f1ac-125">-FilePath</span><span class="sxs-lookup"><span data-stu-id="8f1ac-125">-FilePath</span></span>

<span data-ttu-id="8f1ac-126">Hiermee geeft u een bestand op waarnaar met deze cmdlet de tracerings uitvoer wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-126">Specifies a file that this cmdlet sends the trace output to.</span></span>
<span data-ttu-id="8f1ac-127">Met deze para meter wordt ook de listener voor bestands tracering geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-127">This parameter also selects the file trace listener.</span></span>
<span data-ttu-id="8f1ac-128">Als u deze para meter gebruikt om de tracering te starten, gebruikt u de para meter *RemoveFileListener* om de tracering te stoppen.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-128">If you use this parameter to start the trace, use the *RemoveFileListener* parameter to stop the trace.</span></span>

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

### <span data-ttu-id="8f1ac-129">-Force</span><span class="sxs-lookup"><span data-stu-id="8f1ac-129">-Force</span></span>

<span data-ttu-id="8f1ac-130">Geeft aan dat de cmdlet een alleen-lezen bestand overschrijft.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-130">Indicates that the cmdlet overwrites a read-only file.</span></span>
<span data-ttu-id="8f1ac-131">Gebruiken met de *filepath* -para meter.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-131">Use with the *FilePath* parameter.</span></span>

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

### <span data-ttu-id="8f1ac-132">-ListenerOption</span><span class="sxs-lookup"><span data-stu-id="8f1ac-132">-ListenerOption</span></span>

<span data-ttu-id="8f1ac-133">Hiermee geeft u optionele gegevens op voor het voor voegsel van elk tracerings bericht in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-133">Specifies optional data to the prefix of each trace message in the output.</span></span>
<span data-ttu-id="8f1ac-134">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="8f1ac-134">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8f1ac-135">Geen</span><span class="sxs-lookup"><span data-stu-id="8f1ac-135">None</span></span>
- <span data-ttu-id="8f1ac-136">LogicalOperationStack</span><span class="sxs-lookup"><span data-stu-id="8f1ac-136">LogicalOperationStack</span></span>
- <span data-ttu-id="8f1ac-137">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f1ac-137">DateTime</span></span>
- <span data-ttu-id="8f1ac-138">Timestamp</span><span class="sxs-lookup"><span data-stu-id="8f1ac-138">Timestamp</span></span>
- <span data-ttu-id="8f1ac-139">Process</span><span class="sxs-lookup"><span data-stu-id="8f1ac-139">ProcessId</span></span>
- <span data-ttu-id="8f1ac-140">Thread</span><span class="sxs-lookup"><span data-stu-id="8f1ac-140">ThreadId</span></span>
- <span data-ttu-id="8f1ac-141">Procedures</span><span class="sxs-lookup"><span data-stu-id="8f1ac-141">Callstack</span></span>

<span data-ttu-id="8f1ac-142">Geen is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-142">None is the default.</span></span>

<span data-ttu-id="8f1ac-143">Als u meerdere opties wilt opgeven, scheidt u deze met komma's, maar zonder spaties, en plaatst u ze tussen dubbele aanhalings tekens, zoals ' ProcessID ', thread '.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-143">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "ProcessID,ThreadID".</span></span>

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

### <span data-ttu-id="8f1ac-144">-Name</span><span class="sxs-lookup"><span data-stu-id="8f1ac-144">-Name</span></span>

<span data-ttu-id="8f1ac-145">Hiermee geeft u op welke onderdelen worden getraceerd.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-145">Specifies which components are traced.</span></span>
<span data-ttu-id="8f1ac-146">Voer de naam van de tracerings bron van elk onderdeel in.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-146">Enter the name of the trace source of each component.</span></span>
<span data-ttu-id="8f1ac-147">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-147">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="8f1ac-148">-Optie</span><span class="sxs-lookup"><span data-stu-id="8f1ac-148">-Option</span></span>

<span data-ttu-id="8f1ac-149">Hiermee geeft u het type gebeurtenissen op dat wordt getraceerd.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-149">Specifies the type of events that are traced.</span></span>
<span data-ttu-id="8f1ac-150">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="8f1ac-150">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8f1ac-151">Geen</span><span class="sxs-lookup"><span data-stu-id="8f1ac-151">None</span></span>
- <span data-ttu-id="8f1ac-152">Constructor</span><span class="sxs-lookup"><span data-stu-id="8f1ac-152">Constructor</span></span>
- <span data-ttu-id="8f1ac-153">Gooien</span><span class="sxs-lookup"><span data-stu-id="8f1ac-153">Dispose</span></span>
- <span data-ttu-id="8f1ac-154">Volt ooien</span><span class="sxs-lookup"><span data-stu-id="8f1ac-154">Finalizer</span></span>
- <span data-ttu-id="8f1ac-155">Methode</span><span class="sxs-lookup"><span data-stu-id="8f1ac-155">Method</span></span>
- <span data-ttu-id="8f1ac-156">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="8f1ac-156">Property</span></span>
- <span data-ttu-id="8f1ac-157">Gedelegeerden</span><span class="sxs-lookup"><span data-stu-id="8f1ac-157">Delegates</span></span>
- <span data-ttu-id="8f1ac-158">Gebeurtenissen</span><span class="sxs-lookup"><span data-stu-id="8f1ac-158">Events</span></span>
- <span data-ttu-id="8f1ac-159">Uitzondering</span><span class="sxs-lookup"><span data-stu-id="8f1ac-159">Exception</span></span>
- <span data-ttu-id="8f1ac-160">Vergrendelen</span><span class="sxs-lookup"><span data-stu-id="8f1ac-160">Lock</span></span>
- <span data-ttu-id="8f1ac-161">Fout</span><span class="sxs-lookup"><span data-stu-id="8f1ac-161">Error</span></span>
- <span data-ttu-id="8f1ac-162">Fouten</span><span class="sxs-lookup"><span data-stu-id="8f1ac-162">Errors</span></span>
- <span data-ttu-id="8f1ac-163">Waarschuwing</span><span class="sxs-lookup"><span data-stu-id="8f1ac-163">Warning</span></span>
- <span data-ttu-id="8f1ac-164">Uitgebreid</span><span class="sxs-lookup"><span data-stu-id="8f1ac-164">Verbose</span></span>
- <span data-ttu-id="8f1ac-165">WriteLine</span><span class="sxs-lookup"><span data-stu-id="8f1ac-165">WriteLine</span></span>
- <span data-ttu-id="8f1ac-166">Gegevens</span><span class="sxs-lookup"><span data-stu-id="8f1ac-166">Data</span></span>
- <span data-ttu-id="8f1ac-167">Bereik</span><span class="sxs-lookup"><span data-stu-id="8f1ac-167">Scope</span></span>
- <span data-ttu-id="8f1ac-168">ExecutionFlow</span><span class="sxs-lookup"><span data-stu-id="8f1ac-168">ExecutionFlow</span></span>
- <span data-ttu-id="8f1ac-169">Assert</span><span class="sxs-lookup"><span data-stu-id="8f1ac-169">Assert</span></span>
- <span data-ttu-id="8f1ac-170">Alles</span><span class="sxs-lookup"><span data-stu-id="8f1ac-170">All</span></span>

<span data-ttu-id="8f1ac-171">Dit is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-171">All is the default.</span></span>

<span data-ttu-id="8f1ac-172">De volgende waarden zijn combi Naties van andere waarden:</span><span class="sxs-lookup"><span data-stu-id="8f1ac-172">The following values are combinations of other values:</span></span>

- <span data-ttu-id="8f1ac-173">ExecutionFlow: (constructor, Dispose, FINALIZE, methode, gemachtigden, gebeurtenissen en bereik)</span><span class="sxs-lookup"><span data-stu-id="8f1ac-173">ExecutionFlow: (Constructor, Dispose, Finalizer, Method, Delegates, Events, and Scope)</span></span>
- <span data-ttu-id="8f1ac-174">Gegevens: (constructor, Dispose, FINALIZE, eigenschap, verbose en WriteLine)</span><span class="sxs-lookup"><span data-stu-id="8f1ac-174">Data: (Constructor, Dispose, Finalizer, Property, Verbose, and WriteLine)</span></span>
- <span data-ttu-id="8f1ac-175">Fouten: (fout en uitzonde ring).</span><span class="sxs-lookup"><span data-stu-id="8f1ac-175">Errors: (Error and Exception).</span></span>

<span data-ttu-id="8f1ac-176">Als u meerdere opties wilt opgeven, scheidt u deze met komma's, maar zonder spaties, en plaatst u ze tussen dubbele aanhalings tekens, zoals ' constructor, Dispose '.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-176">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "Constructor,Dispose".</span></span>

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

### <span data-ttu-id="8f1ac-177">-PassThru</span><span class="sxs-lookup"><span data-stu-id="8f1ac-177">-PassThru</span></span>

<span data-ttu-id="8f1ac-178">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-178">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="8f1ac-179">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-179">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="8f1ac-180">-PSHost</span><span class="sxs-lookup"><span data-stu-id="8f1ac-180">-PSHost</span></span>

<span data-ttu-id="8f1ac-181">ndicates dat deze cmdlet de tracerings uitvoer naar de Power shell-host verzendt.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-181">ndicates that this cmdlet sends the trace output to the PowerShell host.</span></span>
<span data-ttu-id="8f1ac-182">Met deze para meter wordt ook de PSHost Trace listener geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-182">This parameter also selects the PSHost trace listener.</span></span>

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

### <span data-ttu-id="8f1ac-183">-RemoveFileListener</span><span class="sxs-lookup"><span data-stu-id="8f1ac-183">-RemoveFileListener</span></span>

<span data-ttu-id="8f1ac-184">Hiermee stopt u de tracering door de listener voor bestands tracering die is gekoppeld aan het opgegeven bestand te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-184">Stops the trace by removing the file trace listener associated with the specified file.</span></span>
<span data-ttu-id="8f1ac-185">Voer het pad en de bestands naam van het uitvoer bestand voor tracering in.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-185">Enter the path and file name of the trace output file.</span></span>

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

### <span data-ttu-id="8f1ac-186">-RemoveListener</span><span class="sxs-lookup"><span data-stu-id="8f1ac-186">-RemoveListener</span></span>

<span data-ttu-id="8f1ac-187">Stopt de tracering door de traceer-listener te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-187">Stops the trace by removing the trace listener.</span></span>

<span data-ttu-id="8f1ac-188">Gebruik de volgende waarden met *RemoveListener*:</span><span class="sxs-lookup"><span data-stu-id="8f1ac-188">Use the following values with *RemoveListener*:</span></span>

- <span data-ttu-id="8f1ac-189">Als u PSHost (console) wilt verwijderen, typt u `Host` .</span><span class="sxs-lookup"><span data-stu-id="8f1ac-189">To remove PSHost (console), type `Host`.</span></span>
- <span data-ttu-id="8f1ac-190">Om het fout opsporingsprogramma te verwijderen, typt u `Debug` .</span><span class="sxs-lookup"><span data-stu-id="8f1ac-190">To remove Debugger, type `Debug`.</span></span>
- <span data-ttu-id="8f1ac-191">Als u alle traceer-listeners wilt verwijderen, typt u `*` .</span><span class="sxs-lookup"><span data-stu-id="8f1ac-191">To remove all trace listeners, type `*`.</span></span>

<span data-ttu-id="8f1ac-192">Als u de listener voor bestands tracering wilt verwijderen, gebruikt u de para meter *RemoveFileListener* .</span><span class="sxs-lookup"><span data-stu-id="8f1ac-192">To remove the file trace listener, use the *RemoveFileListener* parameter.</span></span>

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

### <span data-ttu-id="8f1ac-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8f1ac-193">CommonParameters</span></span>

<span data-ttu-id="8f1ac-194">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8f1ac-195">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-195">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8f1ac-196">INVOER</span><span class="sxs-lookup"><span data-stu-id="8f1ac-196">INPUTS</span></span>

### <span data-ttu-id="8f1ac-197">System. String</span><span class="sxs-lookup"><span data-stu-id="8f1ac-197">System.String</span></span>

<span data-ttu-id="8f1ac-198">U kunt een teken reeks die een naam bevat, door sluizen naar **set-TraceSource**.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-198">You can pipe a string that contains a name to **Set-TraceSource**.</span></span>

## <span data-ttu-id="8f1ac-199">UITVOER</span><span class="sxs-lookup"><span data-stu-id="8f1ac-199">OUTPUTS</span></span>

### <span data-ttu-id="8f1ac-200">Geen of System. Management. Automation. PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="8f1ac-200">None or System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="8f1ac-201">Wanneer u de para meter *PassThru* gebruikt, genereert **set-TraceSource** een **System. Management. Automation. PSTraceSource** -object dat de traceer sessie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-201">When you use the *PassThru* parameter, **Set-TraceSource** generates a **System.Management.Automation.PSTraceSource** object representing the trace session.</span></span>
<span data-ttu-id="8f1ac-202">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-202">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="8f1ac-203">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="8f1ac-203">NOTES</span></span>

* <span data-ttu-id="8f1ac-204">Tracering is een methode die ontwikkel aars gebruiken voor het opsporen van fouten en het verfijnen van Program ma's.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-204">Tracing is a method that developers use to debug and refine programs.</span></span> <span data-ttu-id="8f1ac-205">Bij het traceren worden gedetailleerde berichten over elke stap in de interne verwerking gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-205">When tracing, the program generates detailed messages about each step in its internal processing.</span></span>

  <span data-ttu-id="8f1ac-206">De Power shell-cmdlets voor tracering zijn ontworpen om Power shell-ontwikkel aars te helpen, maar ze zijn beschikbaar voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-206">The PowerShell tracing cmdlets are designed to help PowerShell developers, but they are available to all users.</span></span>
<span data-ttu-id="8f1ac-207">U kunt vrijwel elk aspect van de functionaliteit van Power shell bewaken.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-207">They let you monitor nearly every aspect of the functionality of PowerShell.</span></span>

  <span data-ttu-id="8f1ac-208">Een tracerings bron is het deel van elk Power Shell-onderdeel dat tracering beheert en tracerings berichten genereert voor het onderdeel.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-208">A trace source is the part of each PowerShell component that manages tracing and generates trace messages for the component.</span></span>
<span data-ttu-id="8f1ac-209">Als u een onderdeel wilt traceren, identificeert u de traceer bron.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-209">To trace a component, you identify its trace source.</span></span>

  <span data-ttu-id="8f1ac-210">Een traceer-listener ontvangt de uitvoer van de tracering en geeft deze weer voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-210">A trace listener receives the output of the trace and displays it to the user.</span></span>
<span data-ttu-id="8f1ac-211">U kunt ervoor kiezen om de tracerings gegevens te verzenden naar een fout opsporingsprogramma voor gebruikers modus of kernel-modus, naar de-console, naar een bestand of naar een aangepaste listener die is afgeleid van de **System. Diagnostics. TraceListener** -klasse.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-211">You can elect to send the trace data to a user-mode or kernel-mode debugger, to the console, to a file, or to a custom listener derived from the **System.Diagnostics.TraceListener** class.</span></span>

* <span data-ttu-id="8f1ac-212">Als u een tracering wilt starten, gebruikt u de para meter *name* om een tracerings bron op te geven en de para meters *filepath*, *debugger* of *PSHost* om een listener op te geven (een bestemming voor de uitvoer).</span><span class="sxs-lookup"><span data-stu-id="8f1ac-212">To start a trace, use the *Name* parameter to specify a trace source and the *FilePath*, *Debugger*, or *PSHost* parameters to specify a listener (a destination for the output).</span></span> <span data-ttu-id="8f1ac-213">Gebruik de para meter *Options* om te bepalen welke typen gebeurtenissen worden getraceerd en de para meter *ListenerOption* om de uitvoer van de tracering te configureren.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-213">Use the *Options* parameter to determine the types of events that are traced and the *ListenerOption* parameter to configure the trace output.</span></span>
* <span data-ttu-id="8f1ac-214">Als u de configuratie van een tracering wilt wijzigen, voert u de opdracht **set-TraceSource** in, zoals u een tracering wilt starten.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-214">To change the configuration of a trace, enter a **Set-TraceSource** command as you would to start a trace.</span></span> <span data-ttu-id="8f1ac-215">Power Shell heeft gedetecteerd dat de tracerings bron al wordt getraceerd.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-215">PowerShell recognizes that the trace source is already being traced.</span></span> <span data-ttu-id="8f1ac-216">De tracering wordt gestopt, de nieuwe configuratie wordt toegevoegd en de tracering wordt gestart of opnieuw gestart.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-216">It stops the trace, adds the new configuration, and starts or restarts the trace.</span></span>
* <span data-ttu-id="8f1ac-217">Als u een tracering wilt stoppen, gebruikt u de para meter *RemoveListener* .</span><span class="sxs-lookup"><span data-stu-id="8f1ac-217">To stop a trace, use the *RemoveListener* parameter.</span></span> <span data-ttu-id="8f1ac-218">Als u een tracering wilt stoppen die gebruikmaakt van de file listener (een tracering die is gestart met de para meter *filepath* ), gebruikt u de para meter *RemoveFileListener* .</span><span class="sxs-lookup"><span data-stu-id="8f1ac-218">To stop a trace that uses the file listener (a trace started by using the *FilePath* parameter), use the *RemoveFileListener* parameter.</span></span> <span data-ttu-id="8f1ac-219">Wanneer u de listener verwijdert, wordt de tracering gestopt.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-219">When you remove the listener, the trace stops.</span></span>
* <span data-ttu-id="8f1ac-220">Gebruik Get-TraceSource om te bepalen welke onderdelen kunnen worden getraceerd.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-220">To determine which components can be traced, use Get-TraceSource.</span></span> <span data-ttu-id="8f1ac-221">De tracerings bronnen voor elke module worden automatisch geladen wanneer het onderdeel wordt gebruikt en ze worden weer gegeven in de uitvoer van **Get-TraceSource**.</span><span class="sxs-lookup"><span data-stu-id="8f1ac-221">The trace sources for each module are loaded automatically when the component is in use, and they appear in the output of **Get-TraceSource**.</span></span>

## <span data-ttu-id="8f1ac-222">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="8f1ac-222">RELATED LINKS</span></span>

[<span data-ttu-id="8f1ac-223">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="8f1ac-223">Get-TraceSource</span></span>](Get-TraceSource.md)

[<span data-ttu-id="8f1ac-224">Tracering-opdracht</span><span class="sxs-lookup"><span data-stu-id="8f1ac-224">Trace-Command</span></span>](Trace-Command.md)

