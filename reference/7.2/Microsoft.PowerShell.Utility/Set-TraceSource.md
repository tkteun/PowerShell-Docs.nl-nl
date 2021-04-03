---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/01/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-tracesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TraceSource
ms.openlocfilehash: 6113d9490872346c91769d9e7d0376c77ed4401f
ms.sourcegitcommit: 5b48fe7b2593581b7d4f7dd7c22206d8a45bb8af
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106184474"
---
# <span data-ttu-id="1dff0-102">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="1dff0-102">Set-TraceSource</span></span>

## <span data-ttu-id="1dff0-103">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="1dff0-103">Synopsis</span></span>
<span data-ttu-id="1dff0-104">Hiermee configureert, start en stopt u het traceren van Power shell-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="1dff0-104">Configures, starts, and stops a trace of PowerShell components.</span></span>

## <span data-ttu-id="1dff0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1dff0-105">Syntax</span></span>

### <span data-ttu-id="1dff0-106">optieset (standaard)</span><span class="sxs-lookup"><span data-stu-id="1dff0-106">optionsSet (Default)</span></span>

```
Set-TraceSource [-Name] <String[]> [[-Option] <PSTraceSourceOptions>] [-ListenerOption <TraceOptions>]
 [-FilePath <String>] [-Force] [-Debugger] [-PSHost] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="1dff0-107">removeAllListenersSet</span><span class="sxs-lookup"><span data-stu-id="1dff0-107">removeAllListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveListener <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="1dff0-108">removeFileListenersSet</span><span class="sxs-lookup"><span data-stu-id="1dff0-108">removeFileListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveFileListener <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="1dff0-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1dff0-109">Description</span></span>

<span data-ttu-id="1dff0-110">`Set-TraceSource`Met de cmdlet wordt tracering van een Power Shell-onderdeel geconfigureerd, gestart en gestopt.</span><span class="sxs-lookup"><span data-stu-id="1dff0-110">The `Set-TraceSource` cmdlet configures, starts, and stops a trace of a PowerShell component.</span></span> <span data-ttu-id="1dff0-111">U kunt deze gebruiken om op te geven welke onderdelen moeten worden getraceerd en waar de tracerings uitvoer wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="1dff0-111">You can use it to specify which components will be traced and where the tracing output is sent.</span></span>

## <span data-ttu-id="1dff0-112">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="1dff0-112">Examples</span></span>

### <span data-ttu-id="1dff0-113">Voor beeld 1: het ParameterBinding-onderdeel traceren</span><span class="sxs-lookup"><span data-stu-id="1dff0-113">Example 1: Trace the ParameterBinding component</span></span>

```
Set-TraceSource -Name "ParameterBinding" -Option ExecutionFlow -PSHost -ListenerOption "ProcessId,TimeStamp"
```

<span data-ttu-id="1dff0-114">Met deze opdracht start u het traceren van het onderdeel ParameterBinding van Power shell.</span><span class="sxs-lookup"><span data-stu-id="1dff0-114">This command starts tracing for the ParameterBinding component of PowerShell.</span></span> <span data-ttu-id="1dff0-115">Hierbij wordt de para meter **name** gebruikt voor het opgeven van de tracerings bron, de **optie** parameter om de `ExecutionFlow` tracerings gebeurtenissen te selecteren en de para meter **PSHost** om de Power shell-host-listener te selecteren, waarmee de uitvoer naar de-console wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="1dff0-115">It uses the **Name** parameter to specify the trace source, the **Option** parameter to select the `ExecutionFlow` trace events, and the **PSHost** parameter to select the PowerShell host listener, which sends the output to the console.</span></span> <span data-ttu-id="1dff0-116">De para meter **ListenerOption** voegt `ProcessID` de `TimeStamp` waarden en toe aan het voor voegsel van het tracerings bericht.</span><span class="sxs-lookup"><span data-stu-id="1dff0-116">The **ListenerOption** parameter adds the `ProcessID` and `TimeStamp` values to the trace message prefix.</span></span>

### <span data-ttu-id="1dff0-117">Voor beeld 2: een tracering stoppen</span><span class="sxs-lookup"><span data-stu-id="1dff0-117">Example 2: Stop a trace</span></span>

```
Set-TraceSource -Name "ParameterBinding" -RemoveListener "Host"
```

<span data-ttu-id="1dff0-118">Met deze opdracht stopt u de tracering van het **ParameterBinding** -onderdeel van Power shell.</span><span class="sxs-lookup"><span data-stu-id="1dff0-118">This command stops the trace of the **ParameterBinding** component of PowerShell.</span></span> <span data-ttu-id="1dff0-119">Hierbij wordt de para meter **name** gebruikt voor het identificeren van het onderdeel dat wordt getraceerd en de para meter **RemoveListener** voor het identificeren van de traceer-listener.</span><span class="sxs-lookup"><span data-stu-id="1dff0-119">It uses the **Name** parameter to identify the component that was being traced and the **RemoveListener** parameter to identify the trace listener.</span></span>

## <span data-ttu-id="1dff0-120">Parameters</span><span class="sxs-lookup"><span data-stu-id="1dff0-120">Parameters</span></span>

### <span data-ttu-id="1dff0-121">-Fout opsporingsprogramma</span><span class="sxs-lookup"><span data-stu-id="1dff0-121">-Debugger</span></span>

<span data-ttu-id="1dff0-122">Geeft aan dat de cmdlet de tracerings uitvoer naar het fout opsporingsprogramma verzendt.</span><span class="sxs-lookup"><span data-stu-id="1dff0-122">Indicates that the cmdlet sends the trace output to the debugger.</span></span> <span data-ttu-id="1dff0-123">U kunt de uitvoer bekijken in een fout opsporingsprogramma voor gebruikers modus of kernelmodus of in micro soft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1dff0-123">You can view the output in any user-mode or kernel mode debugger or in Microsoft Visual Studio.</span></span> <span data-ttu-id="1dff0-124">Met deze para meter selecteert u ook de standaard traceer-listener.</span><span class="sxs-lookup"><span data-stu-id="1dff0-124">This parameter also selects the default trace listener.</span></span>

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

### <span data-ttu-id="1dff0-125">-FilePath</span><span class="sxs-lookup"><span data-stu-id="1dff0-125">-FilePath</span></span>

<span data-ttu-id="1dff0-126">Hiermee geeft u een bestand op waarnaar met deze cmdlet de tracerings uitvoer wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="1dff0-126">Specifies a file that this cmdlet sends the trace output to.</span></span> <span data-ttu-id="1dff0-127">Met deze para meter wordt ook de listener voor bestands tracering geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="1dff0-127">This parameter also selects the file trace listener.</span></span> <span data-ttu-id="1dff0-128">Als u deze para meter gebruikt om de tracering te starten, gebruikt u de para meter **RemoveFileListener** om de tracering te stoppen.</span><span class="sxs-lookup"><span data-stu-id="1dff0-128">If you use this parameter to start the trace, use the **RemoveFileListener** parameter to stop the trace.</span></span>

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

### <span data-ttu-id="1dff0-129">-Force</span><span class="sxs-lookup"><span data-stu-id="1dff0-129">-Force</span></span>

<span data-ttu-id="1dff0-130">Geeft aan dat de cmdlet een alleen-lezen bestand overschrijft.</span><span class="sxs-lookup"><span data-stu-id="1dff0-130">Indicates that the cmdlet overwrites a read-only file.</span></span> <span data-ttu-id="1dff0-131">Gebruiken met de **filepath** -para meter.</span><span class="sxs-lookup"><span data-stu-id="1dff0-131">Use with the **FilePath** parameter.</span></span>

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

### <span data-ttu-id="1dff0-132">-ListenerOption</span><span class="sxs-lookup"><span data-stu-id="1dff0-132">-ListenerOption</span></span>

<span data-ttu-id="1dff0-133">Hiermee geeft u optionele gegevens op voor het voor voegsel van elk tracerings bericht in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="1dff0-133">Specifies optional data to the prefix of each trace message in the output.</span></span> <span data-ttu-id="1dff0-134">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="1dff0-134">The acceptable values for this parameter are:</span></span>

- `None`
- `LogicalOperationStack`
- `DateTime`
- `Timestamp`
- `ProcessId`
- `ThreadId`
- `Callstack`

<span data-ttu-id="1dff0-135">`None` is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="1dff0-135">`None` is the default.</span></span>

<span data-ttu-id="1dff0-136">Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag.</span><span class="sxs-lookup"><span data-stu-id="1dff0-136">These values are defined as a flag-based enumeration.</span></span> <span data-ttu-id="1dff0-137">U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="1dff0-137">You can combine multiple values together to set multiple flags using this parameter.</span></span> <span data-ttu-id="1dff0-138">De waarden kunnen worden door gegeven aan de **ListenerOption** -para meter als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden.</span><span class="sxs-lookup"><span data-stu-id="1dff0-138">The values can be passed to the **ListenerOption** parameter as an array of values or as a comma-separated string of those values.</span></span> <span data-ttu-id="1dff0-139">Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking.</span><span class="sxs-lookup"><span data-stu-id="1dff0-139">The cmdlet will combine the values using a binary-OR operation.</span></span> <span data-ttu-id="1dff0-140">Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien.</span><span class="sxs-lookup"><span data-stu-id="1dff0-140">Passing values as an array is the simplest option and also allows you to use tab-completion on the values.</span></span>

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

### <span data-ttu-id="1dff0-141">-Name</span><span class="sxs-lookup"><span data-stu-id="1dff0-141">-Name</span></span>

<span data-ttu-id="1dff0-142">Hiermee geeft u op welke onderdelen worden getraceerd.</span><span class="sxs-lookup"><span data-stu-id="1dff0-142">Specifies which components are traced.</span></span> <span data-ttu-id="1dff0-143">Voer de naam van de tracerings bron van elk onderdeel in.</span><span class="sxs-lookup"><span data-stu-id="1dff0-143">Enter the name of the trace source of each component.</span></span>
<span data-ttu-id="1dff0-144">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="1dff0-144">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="1dff0-145">-Optie</span><span class="sxs-lookup"><span data-stu-id="1dff0-145">-Option</span></span>

<span data-ttu-id="1dff0-146">Hiermee geeft u het type gebeurtenissen op dat wordt getraceerd.</span><span class="sxs-lookup"><span data-stu-id="1dff0-146">Specifies the type of events that are traced.</span></span> <span data-ttu-id="1dff0-147">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="1dff0-147">The acceptable values for this parameter are:</span></span>

- `None`
- `Constructor`
- `Dispose`
- `Finalizer`
- `Method`
- `Property`
- `Delegates`
- `Events`
- `Exception`
- `Lock`
- `Error`
- `Errors`
- `Warning`
- `Verbose`
- `WriteLine`
- `Data`
- `Scope`
- `ExecutionFlow`
- `Assert`
- `All`

<span data-ttu-id="1dff0-148">`All` is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="1dff0-148">`All` is the default.</span></span>

<span data-ttu-id="1dff0-149">De volgende waarden zijn combi Naties van andere waarden:</span><span class="sxs-lookup"><span data-stu-id="1dff0-149">The following values are combinations of other values:</span></span>

- <span data-ttu-id="1dff0-150">`ExecutionFlow`: `Constructor`, `Dispose`, `Finalizer`, `Method`, `Delegates`, `Events`, `Scope`</span><span class="sxs-lookup"><span data-stu-id="1dff0-150">`ExecutionFlow`: `Constructor`, `Dispose`, `Finalizer`, `Method`, `Delegates`, `Events`, `Scope`</span></span>
- <span data-ttu-id="1dff0-151">`Data`: `Constructor`, `Dispose`, `Finalizer`, `Property`, `Verbose`, `WriteLine`</span><span class="sxs-lookup"><span data-stu-id="1dff0-151">`Data`: `Constructor`, `Dispose`, `Finalizer`, `Property`, `Verbose`, `WriteLine`</span></span>
- <span data-ttu-id="1dff0-152">`Errors`: `Error`, `Exception`</span><span class="sxs-lookup"><span data-stu-id="1dff0-152">`Errors`: `Error`, `Exception`</span></span>

<span data-ttu-id="1dff0-153">Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag.</span><span class="sxs-lookup"><span data-stu-id="1dff0-153">These values are defined as a flag-based enumeration.</span></span> <span data-ttu-id="1dff0-154">U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="1dff0-154">You can combine multiple values together to set multiple flags using this parameter.</span></span> <span data-ttu-id="1dff0-155">De waarden kunnen worden door gegeven aan de para meter **Option** als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden.</span><span class="sxs-lookup"><span data-stu-id="1dff0-155">The values can be passed to the **Option** parameter as an array of values or as a comma-separated string of those values.</span></span> <span data-ttu-id="1dff0-156">Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking.</span><span class="sxs-lookup"><span data-stu-id="1dff0-156">The cmdlet will combine the values using a binary-OR operation.</span></span> <span data-ttu-id="1dff0-157">Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien.</span><span class="sxs-lookup"><span data-stu-id="1dff0-157">Passing values as an array is the simplest option and also allows you to use tab-completion on the values.</span></span>

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

### <span data-ttu-id="1dff0-158">-PassThru</span><span class="sxs-lookup"><span data-stu-id="1dff0-158">-PassThru</span></span>

<span data-ttu-id="1dff0-159">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="1dff0-159">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="1dff0-160">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="1dff0-160">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="1dff0-161">-PSHost</span><span class="sxs-lookup"><span data-stu-id="1dff0-161">-PSHost</span></span>

<span data-ttu-id="1dff0-162">Geeft aan dat deze cmdlet de tracerings uitvoer naar de Power shell-host verzendt.</span><span class="sxs-lookup"><span data-stu-id="1dff0-162">Indicates that this cmdlet sends the trace output to the PowerShell host.</span></span> <span data-ttu-id="1dff0-163">Met deze para meter wordt ook de PSHost Trace listener geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="1dff0-163">This parameter also selects the PSHost trace listener.</span></span>

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

### <span data-ttu-id="1dff0-164">-RemoveFileListener</span><span class="sxs-lookup"><span data-stu-id="1dff0-164">-RemoveFileListener</span></span>

<span data-ttu-id="1dff0-165">Hiermee stopt u de tracering door de listener voor bestands tracering die is gekoppeld aan het opgegeven bestand te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="1dff0-165">Stops the trace by removing the file trace listener associated with the specified file.</span></span> <span data-ttu-id="1dff0-166">Voer het pad en de bestands naam van het uitvoer bestand voor tracering in.</span><span class="sxs-lookup"><span data-stu-id="1dff0-166">Enter the path and file name of the trace output file.</span></span>

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

### <span data-ttu-id="1dff0-167">-RemoveListener</span><span class="sxs-lookup"><span data-stu-id="1dff0-167">-RemoveListener</span></span>

<span data-ttu-id="1dff0-168">Stopt de tracering door de traceer-listener te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="1dff0-168">Stops the trace by removing the trace listener.</span></span>

<span data-ttu-id="1dff0-169">Gebruik de volgende waarden met **RemoveListener**:</span><span class="sxs-lookup"><span data-stu-id="1dff0-169">Use the following values with **RemoveListener**:</span></span>

- <span data-ttu-id="1dff0-170">Als u PSHost (console) wilt verwijderen, typt u `Host` .</span><span class="sxs-lookup"><span data-stu-id="1dff0-170">To remove PSHost (console), type `Host`.</span></span>
- <span data-ttu-id="1dff0-171">Om het fout opsporingsprogramma te verwijderen, typt u `Debug` .</span><span class="sxs-lookup"><span data-stu-id="1dff0-171">To remove Debugger, type `Debug`.</span></span>
- <span data-ttu-id="1dff0-172">Als u alle traceer-listeners wilt verwijderen, typt u `*` .</span><span class="sxs-lookup"><span data-stu-id="1dff0-172">To remove all trace listeners, type `*`.</span></span>

<span data-ttu-id="1dff0-173">Als u de listener voor bestands tracering wilt verwijderen, gebruikt u de para meter **RemoveFileListener** .</span><span class="sxs-lookup"><span data-stu-id="1dff0-173">To remove the file trace listener, use the **RemoveFileListener** parameter.</span></span>

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

### <span data-ttu-id="1dff0-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1dff0-174">CommonParameters</span></span>

<span data-ttu-id="1dff0-175">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1dff0-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1dff0-176">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1dff0-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1dff0-177">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="1dff0-177">Inputs</span></span>

### <span data-ttu-id="1dff0-178">System. String</span><span class="sxs-lookup"><span data-stu-id="1dff0-178">System.String</span></span>

<span data-ttu-id="1dff0-179">U kunt een teken reeks die een naam bevat door sluizen naar `Set-TraceSource` .</span><span class="sxs-lookup"><span data-stu-id="1dff0-179">You can pipe a string that contains a name to `Set-TraceSource`.</span></span>

## <span data-ttu-id="1dff0-180">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="1dff0-180">Outputs</span></span>

### <span data-ttu-id="1dff0-181">Geen of System. Management. Automation. PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="1dff0-181">None or System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="1dff0-182">Wanneer u de para meter **PassThru** gebruikt, `Set-TraceSource` genereert een **System. Management. Automation. PSTraceSource** -object dat de traceer sessie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="1dff0-182">When you use the **PassThru** parameter, `Set-TraceSource` generates a **System.Management.Automation.PSTraceSource** object representing the trace session.</span></span> <span data-ttu-id="1dff0-183">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="1dff0-183">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1dff0-184">Notities</span><span class="sxs-lookup"><span data-stu-id="1dff0-184">Notes</span></span>

- <span data-ttu-id="1dff0-185">Tracering is een methode die ontwikkel aars gebruiken voor het opsporen van fouten en het verfijnen van Program ma's.</span><span class="sxs-lookup"><span data-stu-id="1dff0-185">Tracing is a method that developers use to debug and refine programs.</span></span> <span data-ttu-id="1dff0-186">Bij het traceren worden gedetailleerde berichten over elke stap in de interne verwerking gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="1dff0-186">When tracing, the program generates detailed messages about each step in its internal processing.</span></span>

  <span data-ttu-id="1dff0-187">De Power shell-cmdlets voor tracering zijn ontworpen om Power shell-ontwikkel aars te helpen, maar ze zijn beschikbaar voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="1dff0-187">The PowerShell tracing cmdlets are designed to help PowerShell developers, but they are available to all users.</span></span> <span data-ttu-id="1dff0-188">U kunt vrijwel elk aspect van de functionaliteit van Power shell bewaken.</span><span class="sxs-lookup"><span data-stu-id="1dff0-188">They let you monitor nearly every aspect of the functionality of PowerShell.</span></span>

  <span data-ttu-id="1dff0-189">Een tracerings bron is het deel van elk Power Shell-onderdeel dat tracering beheert en tracerings berichten genereert voor het onderdeel.</span><span class="sxs-lookup"><span data-stu-id="1dff0-189">A trace source is the part of each PowerShell component that manages tracing and generates trace messages for the component.</span></span> <span data-ttu-id="1dff0-190">Als u een onderdeel wilt traceren, identificeert u de traceer bron.</span><span class="sxs-lookup"><span data-stu-id="1dff0-190">To trace a component, you identify its trace source.</span></span>

  <span data-ttu-id="1dff0-191">Een traceer-listener ontvangt de uitvoer van de tracering en geeft deze weer voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="1dff0-191">A trace listener receives the output of the trace and displays it to the user.</span></span> <span data-ttu-id="1dff0-192">U kunt ervoor kiezen om de tracerings gegevens te verzenden naar een fout opsporingsprogramma voor gebruikers modus of kernel-modus, naar de-console, naar een bestand of naar een aangepaste listener die is afgeleid van de **System. Diagnostics. TraceListener** -klasse.</span><span class="sxs-lookup"><span data-stu-id="1dff0-192">You can elect to send the trace data to a user-mode or kernel-mode debugger, to the console, to a file, or to a custom listener derived from the **System.Diagnostics.TraceListener** class.</span></span>

- <span data-ttu-id="1dff0-193">Als u een tracering wilt starten, gebruikt u de para meter **name** om een tracerings bron op te geven en de para meters **filepath**, **debugger** of **PSHost** om een listener op te geven (een bestemming voor de uitvoer).</span><span class="sxs-lookup"><span data-stu-id="1dff0-193">To start a trace, use the **Name** parameter to specify a trace source and the **FilePath**, **Debugger**, or **PSHost** parameters to specify a listener (a destination for the output).</span></span> <span data-ttu-id="1dff0-194">Gebruik de para meter **Options** om te bepalen welke typen gebeurtenissen worden getraceerd en de para meter **ListenerOption** om de uitvoer van de tracering te configureren.</span><span class="sxs-lookup"><span data-stu-id="1dff0-194">Use the **Options** parameter to determine the types of events that are traced and the **ListenerOption** parameter to configure the trace output.</span></span>
- <span data-ttu-id="1dff0-195">Als u de configuratie van een tracering wilt wijzigen, voert `Set-TraceSource` u een opdracht in als u een tracering wilt starten.</span><span class="sxs-lookup"><span data-stu-id="1dff0-195">To change the configuration of a trace, enter a `Set-TraceSource` command as you would to start a trace.</span></span> <span data-ttu-id="1dff0-196">Power Shell heeft gedetecteerd dat de tracerings bron al wordt getraceerd.</span><span class="sxs-lookup"><span data-stu-id="1dff0-196">PowerShell recognizes that the trace source is already being traced.</span></span> <span data-ttu-id="1dff0-197">De tracering wordt gestopt, de nieuwe configuratie wordt toegevoegd en de tracering wordt gestart of opnieuw gestart.</span><span class="sxs-lookup"><span data-stu-id="1dff0-197">It stops the trace, adds the new configuration, and starts or restarts the trace.</span></span>
- <span data-ttu-id="1dff0-198">Als u een tracering wilt stoppen, gebruikt u de para meter **RemoveListener** .</span><span class="sxs-lookup"><span data-stu-id="1dff0-198">To stop a trace, use the **RemoveListener** parameter.</span></span> <span data-ttu-id="1dff0-199">Als u een tracering wilt stoppen die gebruikmaakt van de file listener (een tracering die is gestart met de para meter **filepath** ), gebruikt u de para meter **RemoveFileListener** .</span><span class="sxs-lookup"><span data-stu-id="1dff0-199">To stop a trace that uses the file listener (a trace started by using the **FilePath** parameter), use the **RemoveFileListener** parameter.</span></span>
  <span data-ttu-id="1dff0-200">Wanneer u de listener verwijdert, wordt de tracering gestopt.</span><span class="sxs-lookup"><span data-stu-id="1dff0-200">When you remove the listener, the trace stops.</span></span>
- <span data-ttu-id="1dff0-201">Gebruik Get-TraceSource om te bepalen welke onderdelen kunnen worden getraceerd.</span><span class="sxs-lookup"><span data-stu-id="1dff0-201">To determine which components can be traced, use Get-TraceSource.</span></span> <span data-ttu-id="1dff0-202">De tracerings bronnen voor elke module worden automatisch geladen wanneer het onderdeel wordt gebruikt en ze worden weer gegeven in de uitvoer van `Get-TraceSource` .</span><span class="sxs-lookup"><span data-stu-id="1dff0-202">The trace sources for each module are loaded automatically when the component is in use, and they appear in the output of `Get-TraceSource`.</span></span>

## <span data-ttu-id="1dff0-203">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="1dff0-203">Related Links</span></span>

[<span data-ttu-id="1dff0-204">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="1dff0-204">Get-TraceSource</span></span>](Get-TraceSource.md)

[<span data-ttu-id="1dff0-205">Tracering-opdracht</span><span class="sxs-lookup"><span data-stu-id="1dff0-205">Trace-Command</span></span>](Trace-Command.md)

