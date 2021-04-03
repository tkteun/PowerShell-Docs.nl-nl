---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/01/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-tracesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TraceSource
ms.openlocfilehash: 5bbf51c08e64e0bce0ac1879624e0d75a6b5533d
ms.sourcegitcommit: 5b48fe7b2593581b7d4f7dd7c22206d8a45bb8af
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106184457"
---
# <span data-ttu-id="f4dc6-103">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="f4dc6-103">Set-TraceSource</span></span>

## <span data-ttu-id="f4dc6-104">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="f4dc6-104">Synopsis</span></span>
<span data-ttu-id="f4dc6-105">Hiermee configureert, start en stopt u het traceren van Power shell-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-105">Configures, starts, and stops a trace of PowerShell components.</span></span>

## <span data-ttu-id="f4dc6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f4dc6-106">Syntax</span></span>

### <span data-ttu-id="f4dc6-107">optieset (standaard)</span><span class="sxs-lookup"><span data-stu-id="f4dc6-107">optionsSet (Default)</span></span>

```
Set-TraceSource [-Name] <String[]> [[-Option] <PSTraceSourceOptions>] [-ListenerOption <TraceOptions>]
 [-FilePath <String>] [-Force] [-Debugger] [-PSHost] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="f4dc6-108">removeAllListenersSet</span><span class="sxs-lookup"><span data-stu-id="f4dc6-108">removeAllListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveListener <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="f4dc6-109">removeFileListenersSet</span><span class="sxs-lookup"><span data-stu-id="f4dc6-109">removeFileListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveFileListener <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="f4dc6-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f4dc6-110">Description</span></span>

<span data-ttu-id="f4dc6-111">`Set-TraceSource`Met de cmdlet wordt tracering van een Power Shell-onderdeel geconfigureerd, gestart en gestopt.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-111">The `Set-TraceSource` cmdlet configures, starts, and stops a trace of a PowerShell component.</span></span> <span data-ttu-id="f4dc6-112">U kunt deze gebruiken om op te geven welke onderdelen moeten worden getraceerd en waar de tracerings uitvoer wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-112">You can use it to specify which components will be traced and where the tracing output is sent.</span></span>

## <span data-ttu-id="f4dc6-113">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="f4dc6-113">Examples</span></span>

### <span data-ttu-id="f4dc6-114">Voor beeld 1: het ParameterBinding-onderdeel traceren</span><span class="sxs-lookup"><span data-stu-id="f4dc6-114">Example 1: Trace the ParameterBinding component</span></span>

```
Set-TraceSource -Name "ParameterBinding" -Option ExecutionFlow -PSHost -ListenerOption "ProcessId,TimeStamp"
```

<span data-ttu-id="f4dc6-115">Met deze opdracht start u het traceren van het onderdeel ParameterBinding van Power shell.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-115">This command starts tracing for the ParameterBinding component of PowerShell.</span></span> <span data-ttu-id="f4dc6-116">Hierbij wordt de para meter **name** gebruikt voor het opgeven van de tracerings bron, de **optie** parameter om de `ExecutionFlow` tracerings gebeurtenissen te selecteren en de para meter **PSHost** om de Power shell-host-listener te selecteren, waarmee de uitvoer naar de-console wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-116">It uses the **Name** parameter to specify the trace source, the **Option** parameter to select the `ExecutionFlow` trace events, and the **PSHost** parameter to select the PowerShell host listener, which sends the output to the console.</span></span> <span data-ttu-id="f4dc6-117">De para meter **ListenerOption** voegt `ProcessID` de `TimeStamp` waarden en toe aan het voor voegsel van het tracerings bericht.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-117">The **ListenerOption** parameter adds the `ProcessID` and `TimeStamp` values to the trace message prefix.</span></span>

### <span data-ttu-id="f4dc6-118">Voor beeld 2: een tracering stoppen</span><span class="sxs-lookup"><span data-stu-id="f4dc6-118">Example 2: Stop a trace</span></span>

```
Set-TraceSource -Name "ParameterBinding" -RemoveListener "Host"
```

<span data-ttu-id="f4dc6-119">Met deze opdracht stopt u de tracering van het **ParameterBinding** -onderdeel van Power shell.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-119">This command stops the trace of the **ParameterBinding** component of PowerShell.</span></span> <span data-ttu-id="f4dc6-120">Hierbij wordt de para meter **name** gebruikt voor het identificeren van het onderdeel dat wordt getraceerd en de para meter **RemoveListener** voor het identificeren van de traceer-listener.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-120">It uses the **Name** parameter to identify the component that was being traced and the **RemoveListener** parameter to identify the trace listener.</span></span>

## <span data-ttu-id="f4dc6-121">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4dc6-121">Parameters</span></span>

### <span data-ttu-id="f4dc6-122">-Fout opsporingsprogramma</span><span class="sxs-lookup"><span data-stu-id="f4dc6-122">-Debugger</span></span>

<span data-ttu-id="f4dc6-123">Geeft aan dat de cmdlet de tracerings uitvoer naar het fout opsporingsprogramma verzendt.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-123">Indicates that the cmdlet sends the trace output to the debugger.</span></span> <span data-ttu-id="f4dc6-124">U kunt de uitvoer bekijken in een fout opsporingsprogramma voor gebruikers modus of kernelmodus of in micro soft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-124">You can view the output in any user-mode or kernel mode debugger or in Microsoft Visual Studio.</span></span> <span data-ttu-id="f4dc6-125">Met deze para meter selecteert u ook de standaard traceer-listener.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-125">This parameter also selects the default trace listener.</span></span>

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

### <span data-ttu-id="f4dc6-126">-FilePath</span><span class="sxs-lookup"><span data-stu-id="f4dc6-126">-FilePath</span></span>

<span data-ttu-id="f4dc6-127">Hiermee geeft u een bestand op waarnaar met deze cmdlet de tracerings uitvoer wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-127">Specifies a file that this cmdlet sends the trace output to.</span></span> <span data-ttu-id="f4dc6-128">Met deze para meter wordt ook de listener voor bestands tracering geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-128">This parameter also selects the file trace listener.</span></span> <span data-ttu-id="f4dc6-129">Als u deze para meter gebruikt om de tracering te starten, gebruikt u de para meter **RemoveFileListener** om de tracering te stoppen.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-129">If you use this parameter to start the trace, use the **RemoveFileListener** parameter to stop the trace.</span></span>

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

### <span data-ttu-id="f4dc6-130">-Force</span><span class="sxs-lookup"><span data-stu-id="f4dc6-130">-Force</span></span>

<span data-ttu-id="f4dc6-131">Geeft aan dat de cmdlet een alleen-lezen bestand overschrijft.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-131">Indicates that the cmdlet overwrites a read-only file.</span></span> <span data-ttu-id="f4dc6-132">Gebruiken met de **filepath** -para meter.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-132">Use with the **FilePath** parameter.</span></span>

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

### <span data-ttu-id="f4dc6-133">-ListenerOption</span><span class="sxs-lookup"><span data-stu-id="f4dc6-133">-ListenerOption</span></span>

<span data-ttu-id="f4dc6-134">Hiermee geeft u optionele gegevens op voor het voor voegsel van elk tracerings bericht in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-134">Specifies optional data to the prefix of each trace message in the output.</span></span> <span data-ttu-id="f4dc6-135">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="f4dc6-135">The acceptable values for this parameter are:</span></span>

- `None`
- `LogicalOperationStack`
- `DateTime`
- `Timestamp`
- `ProcessId`
- `ThreadId`
- `Callstack`

<span data-ttu-id="f4dc6-136">`None` is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-136">`None` is the default.</span></span>

<span data-ttu-id="f4dc6-137">Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-137">These values are defined as a flag-based enumeration.</span></span> <span data-ttu-id="f4dc6-138">U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-138">You can combine multiple values together to set multiple flags using this parameter.</span></span> <span data-ttu-id="f4dc6-139">De waarden kunnen worden door gegeven aan de **ListenerOption** -para meter als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-139">The values can be passed to the **ListenerOption** parameter as an array of values or as a comma-separated string of those values.</span></span> <span data-ttu-id="f4dc6-140">Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-140">The cmdlet will combine the values using a binary-OR operation.</span></span> <span data-ttu-id="f4dc6-141">Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-141">Passing values as an array is the simplest option and also allows you to use tab-completion on the values.</span></span>

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

### <span data-ttu-id="f4dc6-142">-Name</span><span class="sxs-lookup"><span data-stu-id="f4dc6-142">-Name</span></span>

<span data-ttu-id="f4dc6-143">Hiermee geeft u op welke onderdelen worden getraceerd.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-143">Specifies which components are traced.</span></span> <span data-ttu-id="f4dc6-144">Voer de naam van de tracerings bron van elk onderdeel in.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-144">Enter the name of the trace source of each component.</span></span>
<span data-ttu-id="f4dc6-145">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-145">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="f4dc6-146">-Optie</span><span class="sxs-lookup"><span data-stu-id="f4dc6-146">-Option</span></span>

<span data-ttu-id="f4dc6-147">Hiermee geeft u het type gebeurtenissen op dat wordt getraceerd.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-147">Specifies the type of events that are traced.</span></span> <span data-ttu-id="f4dc6-148">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="f4dc6-148">The acceptable values for this parameter are:</span></span>

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

<span data-ttu-id="f4dc6-149">`All` is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-149">`All` is the default.</span></span>

<span data-ttu-id="f4dc6-150">De volgende waarden zijn combi Naties van andere waarden:</span><span class="sxs-lookup"><span data-stu-id="f4dc6-150">The following values are combinations of other values:</span></span>

- <span data-ttu-id="f4dc6-151">`ExecutionFlow`: `Constructor`, `Dispose`, `Finalizer`, `Method`, `Delegates`, `Events`, `Scope`</span><span class="sxs-lookup"><span data-stu-id="f4dc6-151">`ExecutionFlow`: `Constructor`, `Dispose`, `Finalizer`, `Method`, `Delegates`, `Events`, `Scope`</span></span>
- <span data-ttu-id="f4dc6-152">`Data`: `Constructor`, `Dispose`, `Finalizer`, `Property`, `Verbose`, `WriteLine`</span><span class="sxs-lookup"><span data-stu-id="f4dc6-152">`Data`: `Constructor`, `Dispose`, `Finalizer`, `Property`, `Verbose`, `WriteLine`</span></span>
- <span data-ttu-id="f4dc6-153">`Errors`: `Error`, `Exception`</span><span class="sxs-lookup"><span data-stu-id="f4dc6-153">`Errors`: `Error`, `Exception`</span></span>

<span data-ttu-id="f4dc6-154">Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-154">These values are defined as a flag-based enumeration.</span></span> <span data-ttu-id="f4dc6-155">U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-155">You can combine multiple values together to set multiple flags using this parameter.</span></span> <span data-ttu-id="f4dc6-156">De waarden kunnen worden door gegeven aan de para meter **Option** als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-156">The values can be passed to the **Option** parameter as an array of values or as a comma-separated string of those values.</span></span> <span data-ttu-id="f4dc6-157">Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-157">The cmdlet will combine the values using a binary-OR operation.</span></span> <span data-ttu-id="f4dc6-158">Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-158">Passing values as an array is the simplest option and also allows you to use tab-completion on the values.</span></span>

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

### <span data-ttu-id="f4dc6-159">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f4dc6-159">-PassThru</span></span>

<span data-ttu-id="f4dc6-160">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-160">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="f4dc6-161">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-161">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="f4dc6-162">-PSHost</span><span class="sxs-lookup"><span data-stu-id="f4dc6-162">-PSHost</span></span>

<span data-ttu-id="f4dc6-163">Geeft aan dat deze cmdlet de tracerings uitvoer naar de Power shell-host verzendt.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-163">Indicates that this cmdlet sends the trace output to the PowerShell host.</span></span> <span data-ttu-id="f4dc6-164">Met deze para meter wordt ook de PSHost Trace listener geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-164">This parameter also selects the PSHost trace listener.</span></span>

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

### <span data-ttu-id="f4dc6-165">-RemoveFileListener</span><span class="sxs-lookup"><span data-stu-id="f4dc6-165">-RemoveFileListener</span></span>

<span data-ttu-id="f4dc6-166">Hiermee stopt u de tracering door de listener voor bestands tracering die is gekoppeld aan het opgegeven bestand te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-166">Stops the trace by removing the file trace listener associated with the specified file.</span></span> <span data-ttu-id="f4dc6-167">Voer het pad en de bestands naam van het uitvoer bestand voor tracering in.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-167">Enter the path and file name of the trace output file.</span></span>

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

### <span data-ttu-id="f4dc6-168">-RemoveListener</span><span class="sxs-lookup"><span data-stu-id="f4dc6-168">-RemoveListener</span></span>

<span data-ttu-id="f4dc6-169">Stopt de tracering door de traceer-listener te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-169">Stops the trace by removing the trace listener.</span></span>

<span data-ttu-id="f4dc6-170">Gebruik de volgende waarden met **RemoveListener**:</span><span class="sxs-lookup"><span data-stu-id="f4dc6-170">Use the following values with **RemoveListener**:</span></span>

- <span data-ttu-id="f4dc6-171">Als u PSHost (console) wilt verwijderen, typt u `Host` .</span><span class="sxs-lookup"><span data-stu-id="f4dc6-171">To remove PSHost (console), type `Host`.</span></span>
- <span data-ttu-id="f4dc6-172">Om het fout opsporingsprogramma te verwijderen, typt u `Debug` .</span><span class="sxs-lookup"><span data-stu-id="f4dc6-172">To remove Debugger, type `Debug`.</span></span>
- <span data-ttu-id="f4dc6-173">Als u alle traceer-listeners wilt verwijderen, typt u `*` .</span><span class="sxs-lookup"><span data-stu-id="f4dc6-173">To remove all trace listeners, type `*`.</span></span>

<span data-ttu-id="f4dc6-174">Als u de listener voor bestands tracering wilt verwijderen, gebruikt u de para meter **RemoveFileListener** .</span><span class="sxs-lookup"><span data-stu-id="f4dc6-174">To remove the file trace listener, use the **RemoveFileListener** parameter.</span></span>

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

### <span data-ttu-id="f4dc6-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f4dc6-175">CommonParameters</span></span>

<span data-ttu-id="f4dc6-176">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f4dc6-177">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f4dc6-178">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="f4dc6-178">Inputs</span></span>

### <span data-ttu-id="f4dc6-179">System. String</span><span class="sxs-lookup"><span data-stu-id="f4dc6-179">System.String</span></span>

<span data-ttu-id="f4dc6-180">U kunt een teken reeks die een naam bevat door sluizen naar `Set-TraceSource` .</span><span class="sxs-lookup"><span data-stu-id="f4dc6-180">You can pipe a string that contains a name to `Set-TraceSource`.</span></span>

## <span data-ttu-id="f4dc6-181">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="f4dc6-181">Outputs</span></span>

### <span data-ttu-id="f4dc6-182">Geen of System. Management. Automation. PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="f4dc6-182">None or System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="f4dc6-183">Wanneer u de para meter **PassThru** gebruikt, `Set-TraceSource` genereert een **System. Management. Automation. PSTraceSource** -object dat de traceer sessie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-183">When you use the **PassThru** parameter, `Set-TraceSource` generates a **System.Management.Automation.PSTraceSource** object representing the trace session.</span></span> <span data-ttu-id="f4dc6-184">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-184">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f4dc6-185">Notities</span><span class="sxs-lookup"><span data-stu-id="f4dc6-185">Notes</span></span>

- <span data-ttu-id="f4dc6-186">Tracering is een methode die ontwikkel aars gebruiken voor het opsporen van fouten en het verfijnen van Program ma's.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-186">Tracing is a method that developers use to debug and refine programs.</span></span> <span data-ttu-id="f4dc6-187">Bij het traceren worden gedetailleerde berichten over elke stap in de interne verwerking gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-187">When tracing, the program generates detailed messages about each step in its internal processing.</span></span>

  <span data-ttu-id="f4dc6-188">De Power shell-cmdlets voor tracering zijn ontworpen om Power shell-ontwikkel aars te helpen, maar ze zijn beschikbaar voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-188">The PowerShell tracing cmdlets are designed to help PowerShell developers, but they are available to all users.</span></span> <span data-ttu-id="f4dc6-189">U kunt vrijwel elk aspect van de functionaliteit van Power shell bewaken.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-189">They let you monitor nearly every aspect of the functionality of PowerShell.</span></span>

  <span data-ttu-id="f4dc6-190">Een tracerings bron is het deel van elk Power Shell-onderdeel dat tracering beheert en tracerings berichten genereert voor het onderdeel.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-190">A trace source is the part of each PowerShell component that manages tracing and generates trace messages for the component.</span></span> <span data-ttu-id="f4dc6-191">Als u een onderdeel wilt traceren, identificeert u de traceer bron.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-191">To trace a component, you identify its trace source.</span></span>

  <span data-ttu-id="f4dc6-192">Een traceer-listener ontvangt de uitvoer van de tracering en geeft deze weer voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-192">A trace listener receives the output of the trace and displays it to the user.</span></span> <span data-ttu-id="f4dc6-193">U kunt ervoor kiezen om de tracerings gegevens te verzenden naar een fout opsporingsprogramma voor gebruikers modus of kernel-modus, naar de-console, naar een bestand of naar een aangepaste listener die is afgeleid van de **System. Diagnostics. TraceListener** -klasse.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-193">You can elect to send the trace data to a user-mode or kernel-mode debugger, to the console, to a file, or to a custom listener derived from the **System.Diagnostics.TraceListener** class.</span></span>

- <span data-ttu-id="f4dc6-194">Als u een tracering wilt starten, gebruikt u de para meter **name** om een tracerings bron op te geven en de para meters **filepath**, **debugger** of **PSHost** om een listener op te geven (een bestemming voor de uitvoer).</span><span class="sxs-lookup"><span data-stu-id="f4dc6-194">To start a trace, use the **Name** parameter to specify a trace source and the **FilePath**, **Debugger**, or **PSHost** parameters to specify a listener (a destination for the output).</span></span> <span data-ttu-id="f4dc6-195">Gebruik de para meter **Options** om te bepalen welke typen gebeurtenissen worden getraceerd en de para meter **ListenerOption** om de uitvoer van de tracering te configureren.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-195">Use the **Options** parameter to determine the types of events that are traced and the **ListenerOption** parameter to configure the trace output.</span></span>
- <span data-ttu-id="f4dc6-196">Als u de configuratie van een tracering wilt wijzigen, voert `Set-TraceSource` u een opdracht in als u een tracering wilt starten.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-196">To change the configuration of a trace, enter a `Set-TraceSource` command as you would to start a trace.</span></span> <span data-ttu-id="f4dc6-197">Power Shell heeft gedetecteerd dat de tracerings bron al wordt getraceerd.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-197">PowerShell recognizes that the trace source is already being traced.</span></span> <span data-ttu-id="f4dc6-198">De tracering wordt gestopt, de nieuwe configuratie wordt toegevoegd en de tracering wordt gestart of opnieuw gestart.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-198">It stops the trace, adds the new configuration, and starts or restarts the trace.</span></span>
- <span data-ttu-id="f4dc6-199">Als u een tracering wilt stoppen, gebruikt u de para meter **RemoveListener** .</span><span class="sxs-lookup"><span data-stu-id="f4dc6-199">To stop a trace, use the **RemoveListener** parameter.</span></span> <span data-ttu-id="f4dc6-200">Als u een tracering wilt stoppen die gebruikmaakt van de file listener (een tracering die is gestart met de para meter **filepath** ), gebruikt u de para meter **RemoveFileListener** .</span><span class="sxs-lookup"><span data-stu-id="f4dc6-200">To stop a trace that uses the file listener (a trace started by using the **FilePath** parameter), use the **RemoveFileListener** parameter.</span></span>
  <span data-ttu-id="f4dc6-201">Wanneer u de listener verwijdert, wordt de tracering gestopt.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-201">When you remove the listener, the trace stops.</span></span>
- <span data-ttu-id="f4dc6-202">Gebruik Get-TraceSource om te bepalen welke onderdelen kunnen worden getraceerd.</span><span class="sxs-lookup"><span data-stu-id="f4dc6-202">To determine which components can be traced, use Get-TraceSource.</span></span> <span data-ttu-id="f4dc6-203">De tracerings bronnen voor elke module worden automatisch geladen wanneer het onderdeel wordt gebruikt en ze worden weer gegeven in de uitvoer van `Get-TraceSource` .</span><span class="sxs-lookup"><span data-stu-id="f4dc6-203">The trace sources for each module are loaded automatically when the component is in use, and they appear in the output of `Get-TraceSource`.</span></span>

## <span data-ttu-id="f4dc6-204">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="f4dc6-204">Related Links</span></span>

[<span data-ttu-id="f4dc6-205">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="f4dc6-205">Get-TraceSource</span></span>](Get-TraceSource.md)

[<span data-ttu-id="f4dc6-206">Tracering-opdracht</span><span class="sxs-lookup"><span data-stu-id="f4dc6-206">Trace-Command</span></span>](Trace-Command.md)
