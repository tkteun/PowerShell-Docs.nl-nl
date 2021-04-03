---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/01/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/trace-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Trace-Command
ms.openlocfilehash: 97571023c1428de5db0c2e6e13e285cafe609843
ms.sourcegitcommit: 5b48fe7b2593581b7d4f7dd7c22206d8a45bb8af
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106184406"
---
# <span data-ttu-id="32f3f-102">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="32f3f-102">Trace-Command</span></span>

## <span data-ttu-id="32f3f-103">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="32f3f-103">Synopsis</span></span>
<span data-ttu-id="32f3f-104">Hiermee wordt een tracering van de opgegeven expressie of opdracht geconfigureerd en gestart.</span><span class="sxs-lookup"><span data-stu-id="32f3f-104">Configures and starts a trace of the specified expression or command.</span></span>

## <span data-ttu-id="32f3f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="32f3f-105">Syntax</span></span>

### <span data-ttu-id="32f3f-106">expressieset (standaard)</span><span class="sxs-lookup"><span data-stu-id="32f3f-106">expressionSet (Default)</span></span>

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Expression] <ScriptBlock> [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force] [-Debugger]
 [-PSHost] [<CommonParameters>]
```

### <span data-ttu-id="32f3f-107">opdrachtset</span><span class="sxs-lookup"><span data-stu-id="32f3f-107">commandSet</span></span>

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Command] <String> [-ArgumentList <Object[]>] [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force]
 [-Debugger] [-PSHost] [<CommonParameters>]
```

## <span data-ttu-id="32f3f-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="32f3f-108">Description</span></span>

<span data-ttu-id="32f3f-109">De `Trace-Command` cmdlet configureert en start een tracering van de opgegeven expressie of opdracht.</span><span class="sxs-lookup"><span data-stu-id="32f3f-109">The `Trace-Command` cmdlet configures and starts a trace of the specified expression or command.</span></span>
<span data-ttu-id="32f3f-110">Het werkt zoals set-TraceSource, behalve dat deze alleen van toepassing is op de opgegeven opdracht.</span><span class="sxs-lookup"><span data-stu-id="32f3f-110">It works like Set-TraceSource, except that it applies only to the specified command.</span></span>

## <span data-ttu-id="32f3f-111">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="32f3f-111">Examples</span></span>

### <span data-ttu-id="32f3f-112">Voor beeld 1: verwerking van meta gegevens volgen, parameter binding en een expressie</span><span class="sxs-lookup"><span data-stu-id="32f3f-112">Example 1: Trace metadata processing, parameter binding, and an expression</span></span>

<span data-ttu-id="32f3f-113">In dit voor beeld wordt een tracering gestart van meta gegevens verwerking, parameter binding en het maken van de cmdlet en vernietiging van de `Get-Process Notepad` expressie.</span><span class="sxs-lookup"><span data-stu-id="32f3f-113">This example starts a trace of metadata processing, parameter binding, and cmdlet creation and destruction of the `Get-Process Notepad` expression.</span></span>

```powershell
Trace-Command -Name metadata,parameterbinding,cmdlet -Expression {Get-Process Notepad} -PSHost
```

<span data-ttu-id="32f3f-114">Hierbij wordt de para meter **name** gebruikt voor het opgeven van de tracerings bronnen, de **expressie** parameter voor het opgeven van de opdracht en de para meter **PSHost** voor het verzenden van de uitvoer naar de-console.</span><span class="sxs-lookup"><span data-stu-id="32f3f-114">It uses the **Name** parameter to specify the trace sources, the **Expression** parameter to specify the command, and the **PSHost** parameter to send the output to the console.</span></span> <span data-ttu-id="32f3f-115">Omdat er geen tracerings opties of listener-opties worden opgegeven, gebruikt de opdracht de standaard waarden:</span><span class="sxs-lookup"><span data-stu-id="32f3f-115">Because it does not specify any tracing options or listener options, the command uses the defaults:</span></span>

- <span data-ttu-id="32f3f-116">Alle voor de tracerings opties</span><span class="sxs-lookup"><span data-stu-id="32f3f-116">All for the tracing options</span></span>
- <span data-ttu-id="32f3f-117">Geen voor de opties voor de listener</span><span class="sxs-lookup"><span data-stu-id="32f3f-117">None for the listener options</span></span>

### <span data-ttu-id="32f3f-118">Voor beeld 2: de acties van ParameterBinding-bewerkingen traceren</span><span class="sxs-lookup"><span data-stu-id="32f3f-118">Example 2: Trace the actions of ParameterBinding operations</span></span>

<span data-ttu-id="32f3f-119">In dit voor beeld worden de acties van de **ParameterBinding** -bewerkingen van Power shell getraceerd tijdens het verwerken van een `Get-Alias` expressie die invoer van de pijp lijn afneemt.</span><span class="sxs-lookup"><span data-stu-id="32f3f-119">This example traces the actions of the **ParameterBinding** operations of PowerShell while it processes a `Get-Alias` expression that takes input from the pipeline.</span></span>

```powershell
$A = "i*"
Trace-Command ParameterBinding {Get-Alias $Input} -PSHost -InputObject $A
```

<span data-ttu-id="32f3f-120">In `Trace-Command` geeft de para meter **input object** een object door aan de expressie die tijdens de tracering wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="32f3f-120">In `Trace-Command`, the **InputObject** parameter passes an object to the expression that is being processed during the trace.</span></span>

<span data-ttu-id="32f3f-121">Met de eerste opdracht wordt de teken reeks `i*` in de `$A` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="32f3f-121">The first command stores the string `i*` in the `$A` variable.</span></span> <span data-ttu-id="32f3f-122">De tweede opdracht maakt gebruik `Trace-Command` van de cmdlet met de tracerings bron ParameterBinding.</span><span class="sxs-lookup"><span data-stu-id="32f3f-122">The second command uses the `Trace-Command` cmdlet with the ParameterBinding trace source.</span></span> <span data-ttu-id="32f3f-123">De **PSHost** para meter verzendt de uitvoer naar de-console.</span><span class="sxs-lookup"><span data-stu-id="32f3f-123">The **PSHost** parameter sends the output to the console.</span></span>

<span data-ttu-id="32f3f-124">De expressie die wordt verwerkt `Get-Alias $Input` , is, waarbij de `$Input` variabele is gekoppeld aan de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="32f3f-124">The expression being processed is `Get-Alias $Input`, where the `$Input` variable is associated with the **InputObject** parameter.</span></span> <span data-ttu-id="32f3f-125">De **input object** para meter geeft de variabele door `$A` aan de expressie.</span><span class="sxs-lookup"><span data-stu-id="32f3f-125">The **InputObject** parameter passes the variable `$A` to the expression.</span></span> <span data-ttu-id="32f3f-126">In feite is de opdracht die wordt verwerkt tijdens de tracering `Get-Alias -InputObject $A" or "$A | Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="32f3f-126">In effect, the command being processed during the trace is `Get-Alias -InputObject $A" or "$A | Get-Alias`.</span></span>

## <span data-ttu-id="32f3f-127">Parameters</span><span class="sxs-lookup"><span data-stu-id="32f3f-127">Parameters</span></span>

### <span data-ttu-id="32f3f-128">-Argument List</span><span class="sxs-lookup"><span data-stu-id="32f3f-128">-ArgumentList</span></span>

<span data-ttu-id="32f3f-129">Hiermee geeft u de para meters en parameter waarden voor de opdracht die wordt getraceerd.</span><span class="sxs-lookup"><span data-stu-id="32f3f-129">Specifies the parameters and parameter values for the command being traced.</span></span> <span data-ttu-id="32f3f-130">De alias voor **argument List** is **args**.</span><span class="sxs-lookup"><span data-stu-id="32f3f-130">The alias for **ArgumentList** is **Args**.</span></span> <span data-ttu-id="32f3f-131">Deze functie is vooral nuttig voor het opsporen van fouten in dynamische para meters.</span><span class="sxs-lookup"><span data-stu-id="32f3f-131">This feature is especially useful for debugging dynamic parameters.</span></span>

<span data-ttu-id="32f3f-132">Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="32f3f-132">For more information about the behavior of **ArgumentList**, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: commandSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32f3f-133">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="32f3f-133">-Command</span></span>

<span data-ttu-id="32f3f-134">Hiermee geeft u een opdracht die tijdens de tracering wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="32f3f-134">Specifies a command that is being processed during the trace.</span></span>

```yaml
Type: System.String
Parameter Sets: commandSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32f3f-135">-Fout opsporingsprogramma</span><span class="sxs-lookup"><span data-stu-id="32f3f-135">-Debugger</span></span>

<span data-ttu-id="32f3f-136">Geeft aan dat de cmdlet de tracerings uitvoer naar het fout opsporingsprogramma verzendt.</span><span class="sxs-lookup"><span data-stu-id="32f3f-136">Indicates that the cmdlet sends the trace output to the debugger.</span></span> <span data-ttu-id="32f3f-137">U kunt de uitvoer bekijken in een fout opsporingsprogramma voor gebruikers modus of kernelmodus of in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="32f3f-137">You can view the output in any user-mode or kernel mode debugger or in Visual Studio.</span></span> <span data-ttu-id="32f3f-138">Met deze para meter selecteert u ook de standaard traceer-listener.</span><span class="sxs-lookup"><span data-stu-id="32f3f-138">This parameter also selects the default trace listener.</span></span>

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

### <span data-ttu-id="32f3f-139">-Expressie</span><span class="sxs-lookup"><span data-stu-id="32f3f-139">-Expression</span></span>

<span data-ttu-id="32f3f-140">Hiermee geeft u de expressie op die tijdens de tracering wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="32f3f-140">Specifies the expression that is being processed during the trace.</span></span> <span data-ttu-id="32f3f-141">Plaats de expressie tussen accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="32f3f-141">Enclose the expression in braces (`{}`).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: expressionSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32f3f-142">-FilePath</span><span class="sxs-lookup"><span data-stu-id="32f3f-142">-FilePath</span></span>

<span data-ttu-id="32f3f-143">Hiermee geeft u een bestand op waarnaar de-cmdlet de tracerings uitvoer verzendt.</span><span class="sxs-lookup"><span data-stu-id="32f3f-143">Specifies a file that the cmdlet sends the trace output to.</span></span> <span data-ttu-id="32f3f-144">Met deze para meter wordt ook de listener voor bestands tracering geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="32f3f-144">This parameter also selects the file trace listener.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32f3f-145">-Force</span><span class="sxs-lookup"><span data-stu-id="32f3f-145">-Force</span></span>

<span data-ttu-id="32f3f-146">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="32f3f-146">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="32f3f-147">Wordt gebruikt met de **filepath** -para meter.</span><span class="sxs-lookup"><span data-stu-id="32f3f-147">Used with the **FilePath** parameter.</span></span> <span data-ttu-id="32f3f-148">Zelfs met behulp van de para meter **forceren** , kan de cmdlet geen beveiligings beperkingen opheffen.</span><span class="sxs-lookup"><span data-stu-id="32f3f-148">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="32f3f-149">-Input object</span><span class="sxs-lookup"><span data-stu-id="32f3f-149">-InputObject</span></span>

<span data-ttu-id="32f3f-150">Hiermee wordt de invoer opgegeven van de expressie die tijdens de tracering wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="32f3f-150">Specifies input to the expression that is being processed during the trace.</span></span> <span data-ttu-id="32f3f-151">U kunt een variabele opgeven die de invoer vertegenwoordigt die de expressie accepteert, of een object door geven via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="32f3f-151">You can enter a variable that represents the input that the expression accepts, or pass an object through the pipeline.</span></span>

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

### <span data-ttu-id="32f3f-152">-ListenerOption</span><span class="sxs-lookup"><span data-stu-id="32f3f-152">-ListenerOption</span></span>

<span data-ttu-id="32f3f-153">Hiermee geeft u optionele gegevens op voor het voor voegsel van elk tracerings bericht in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="32f3f-153">Specifies optional data to the prefix of each trace message in the output.</span></span> <span data-ttu-id="32f3f-154">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="32f3f-154">The acceptable values for this parameter are:</span></span>

- `None`
- `LogicalOperationStack`
- `DateTime`
- `Timestamp`
- `ProcessId`
- `ThreadId`
- `Callstack`

<span data-ttu-id="32f3f-155">`None` is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="32f3f-155">`None` is the default.</span></span>

<span data-ttu-id="32f3f-156">Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag.</span><span class="sxs-lookup"><span data-stu-id="32f3f-156">These values are defined as a flag-based enumeration.</span></span> <span data-ttu-id="32f3f-157">U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="32f3f-157">You can combine multiple values together to set multiple flags using this parameter.</span></span> <span data-ttu-id="32f3f-158">De waarden kunnen worden door gegeven aan de **ListenerOption** -para meter als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden.</span><span class="sxs-lookup"><span data-stu-id="32f3f-158">The values can be passed to the **ListenerOption** parameter as an array of values or as a comma-separated string of those values.</span></span> <span data-ttu-id="32f3f-159">Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking.</span><span class="sxs-lookup"><span data-stu-id="32f3f-159">The cmdlet will combine the values using a binary-OR operation.</span></span> <span data-ttu-id="32f3f-160">Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien.</span><span class="sxs-lookup"><span data-stu-id="32f3f-160">Passing values as an array is the simplest option and also allows you to use tab-completion on the values.</span></span>

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32f3f-161">-Name</span><span class="sxs-lookup"><span data-stu-id="32f3f-161">-Name</span></span>

<span data-ttu-id="32f3f-162">Hiermee geeft u een matrix van Power shell-onderdelen die worden getraceerd.</span><span class="sxs-lookup"><span data-stu-id="32f3f-162">Specifies an array of PowerShell components that are traced.</span></span> <span data-ttu-id="32f3f-163">Voer de naam van de tracerings bron van elk onderdeel in.</span><span class="sxs-lookup"><span data-stu-id="32f3f-163">Enter the name of the trace source of each component.</span></span> <span data-ttu-id="32f3f-164">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="32f3f-164">Wildcards are permitted.</span></span> <span data-ttu-id="32f3f-165">Als u de tracerings bronnen op uw computer wilt zoeken, typt u `Get-TraceSource` .</span><span class="sxs-lookup"><span data-stu-id="32f3f-165">To find the trace sources on your computer, type `Get-TraceSource`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32f3f-166">-Optie</span><span class="sxs-lookup"><span data-stu-id="32f3f-166">-Option</span></span>

<span data-ttu-id="32f3f-167">Bepaalt het type gebeurtenissen dat wordt getraceerd.</span><span class="sxs-lookup"><span data-stu-id="32f3f-167">Determines the type of events that are traced.</span></span> <span data-ttu-id="32f3f-168">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="32f3f-168">The acceptable values for this parameter are:</span></span>

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

<span data-ttu-id="32f3f-169">`All` is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="32f3f-169">`All` is the default.</span></span>

<span data-ttu-id="32f3f-170">De volgende waarden zijn combi Naties van andere waarden:</span><span class="sxs-lookup"><span data-stu-id="32f3f-170">The following values are combinations of other values:</span></span>

- <span data-ttu-id="32f3f-171">`ExecutionFlow`: `Constructor`, `Dispose`, `Finalizer`, `Method`, `Delegates`, `Events`, `Scope`</span><span class="sxs-lookup"><span data-stu-id="32f3f-171">`ExecutionFlow`: `Constructor`, `Dispose`, `Finalizer`, `Method`, `Delegates`, `Events`, `Scope`</span></span>
- <span data-ttu-id="32f3f-172">`Data`: `Constructor`, `Dispose`, `Finalizer`, `Property`, `Verbose`, `WriteLine`</span><span class="sxs-lookup"><span data-stu-id="32f3f-172">`Data`: `Constructor`, `Dispose`, `Finalizer`, `Property`, `Verbose`, `WriteLine`</span></span>
- <span data-ttu-id="32f3f-173">`Errors`: `Error`, `Exception`</span><span class="sxs-lookup"><span data-stu-id="32f3f-173">`Errors`: `Error`, `Exception`</span></span>

<span data-ttu-id="32f3f-174">Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag.</span><span class="sxs-lookup"><span data-stu-id="32f3f-174">These values are defined as a flag-based enumeration.</span></span> <span data-ttu-id="32f3f-175">U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="32f3f-175">You can combine multiple values together to set multiple flags using this parameter.</span></span> <span data-ttu-id="32f3f-176">De waarden kunnen worden door gegeven aan de para meter **Option** als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden.</span><span class="sxs-lookup"><span data-stu-id="32f3f-176">The values can be passed to the **Option** parameter as an array of values or as a comma-separated string of those values.</span></span> <span data-ttu-id="32f3f-177">Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking.</span><span class="sxs-lookup"><span data-stu-id="32f3f-177">The cmdlet will combine the values using a binary-OR operation.</span></span> <span data-ttu-id="32f3f-178">Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien.</span><span class="sxs-lookup"><span data-stu-id="32f3f-178">Passing values as an array is the simplest option and also allows you to use tab-completion on the values.</span></span>

```yaml
Type: System.Management.Automation.PSTraceSourceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32f3f-179">-PSHost</span><span class="sxs-lookup"><span data-stu-id="32f3f-179">-PSHost</span></span>

<span data-ttu-id="32f3f-180">Geeft aan dat de cmdlet de tracerings uitvoer naar de Power shell-host verzendt.</span><span class="sxs-lookup"><span data-stu-id="32f3f-180">Indicates that the cmdlet sends the trace output to the PowerShell host.</span></span> <span data-ttu-id="32f3f-181">Met deze para meter wordt ook de PSHost Trace listener geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="32f3f-181">This parameter also selects the PSHost trace listener.</span></span>

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

### <span data-ttu-id="32f3f-182">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="32f3f-182">CommonParameters</span></span>

<span data-ttu-id="32f3f-183">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="32f3f-183">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="32f3f-184">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="32f3f-184">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="32f3f-185">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="32f3f-185">Inputs</span></span>

### <span data-ttu-id="32f3f-186">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="32f3f-186">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="32f3f-187">U kunt objecten pipeen die de invoer voor de expressie vertegenwoordigen `Trace-Command` .</span><span class="sxs-lookup"><span data-stu-id="32f3f-187">You can pipe objects that represent input to the expression to `Trace-Command`.</span></span>

## <span data-ttu-id="32f3f-188">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="32f3f-188">Outputs</span></span>

### <span data-ttu-id="32f3f-189">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="32f3f-189">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="32f3f-190">Retourneert de opdracht tracering in de stroom voor fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="32f3f-190">Returns the command trace in the debug stream.</span></span>

## <span data-ttu-id="32f3f-191">Notities</span><span class="sxs-lookup"><span data-stu-id="32f3f-191">Notes</span></span>

- <span data-ttu-id="32f3f-192">Tracering is een methode die ontwikkel aars gebruiken voor het opsporen van fouten en het verfijnen van Program ma's.</span><span class="sxs-lookup"><span data-stu-id="32f3f-192">Tracing is a method that developers use to debug and refine programs.</span></span> <span data-ttu-id="32f3f-193">Bij het traceren worden gedetailleerde berichten over elke stap in de interne verwerking gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="32f3f-193">When tracing, the program generates detailed messages about each step in its internal processing.</span></span>

- <span data-ttu-id="32f3f-194">De Power shell-cmdlets voor tracering zijn ontworpen om Power shell-ontwikkel aars te helpen, maar ze zijn beschikbaar voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="32f3f-194">The PowerShell tracing cmdlets are designed to help PowerShell developers, but they are available to all users.</span></span> <span data-ttu-id="32f3f-195">U kunt vrijwel elk aspect van de functionaliteit van de shell bewaken.</span><span class="sxs-lookup"><span data-stu-id="32f3f-195">They let you monitor nearly every aspect of the functionality of the shell.</span></span>

- <span data-ttu-id="32f3f-196">Als u de Power shell-onderdelen wilt vinden die zijn ingeschakeld voor tracering, typt u `Get-Help Get-TraceSource` .</span><span class="sxs-lookup"><span data-stu-id="32f3f-196">To find the PowerShell components that are enabled for tracing, type `Get-Help Get-TraceSource`.</span></span>

  <span data-ttu-id="32f3f-197">Een tracerings bron is het deel van elk Power Shell-onderdeel dat tracering beheert en tracerings berichten genereert voor het onderdeel.</span><span class="sxs-lookup"><span data-stu-id="32f3f-197">A trace source is the part of each PowerShell component that manages tracing and generates trace messages for the component.</span></span> <span data-ttu-id="32f3f-198">Als u een onderdeel wilt traceren, identificeert u de traceer bron.</span><span class="sxs-lookup"><span data-stu-id="32f3f-198">To trace a component, you identify its trace source.</span></span>

  <span data-ttu-id="32f3f-199">Een traceer-listener ontvangt de uitvoer van de tracering en geeft deze weer voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="32f3f-199">A trace listener receives the output of the trace and displays it to the user.</span></span> <span data-ttu-id="32f3f-200">U kunt ervoor kiezen om de tracerings gegevens naar een gebruikers modus of kernel-modus debugger te verzenden naar de host of console, naar een bestand of naar een aangepaste listener die is afgeleid van de **System. Diagnostics. TraceListener** -klasse.</span><span class="sxs-lookup"><span data-stu-id="32f3f-200">You can elect to send the trace data to a user-mode or kernel-mode debugger, to the host or console, to a file, or to a custom listener derived from the **System.Diagnostics.TraceListener** class.</span></span>

- <span data-ttu-id="32f3f-201">Wanneer u de opdrachtset para meter set gebruikt, verwerkt Power shell de opdracht net zoals deze in een pijp lijn zou worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="32f3f-201">When you use the commandSet parameter set, PowerShell processes the command just as it would be processed in a pipeline.</span></span> <span data-ttu-id="32f3f-202">Bijvoorbeeld: opdracht detectie wordt niet herhaald voor elk binnenkomend object.</span><span class="sxs-lookup"><span data-stu-id="32f3f-202">For example, command discovery is not repeated for each incoming object.</span></span>

- <span data-ttu-id="32f3f-203">De namen van de para meters **name**, **expressie**, **Option** en **Command** zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="32f3f-203">The names of the **Name**, **Expression**, **Option**, and **Command** parameters are optional.</span></span> <span data-ttu-id="32f3f-204">Als u de parameter namen weglaat, moeten de niet-genaamde parameter waarden in deze volg orde worden weer gegeven: **naam**, **expressie**, **optie** of **naam**, **opdracht**, **optie**.</span><span class="sxs-lookup"><span data-stu-id="32f3f-204">If you omit the parameter names, the unnamed parameter values must appear in this order: **Name**, **Expression**, **Option** or **Name**, **Command**, **Option**.</span></span> <span data-ttu-id="32f3f-205">Als u de parameter namen toevoegt, kunnen de para meters in een wille keurige volg orde worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="32f3f-205">If you include the parameter names, the parameters can appear in any order.</span></span>

## <span data-ttu-id="32f3f-206">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="32f3f-206">Related Links</span></span>

[<span data-ttu-id="32f3f-207">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="32f3f-207">Get-TraceSource</span></span>](Get-TraceSource.md)

[<span data-ttu-id="32f3f-208">Measure-Command</span><span class="sxs-lookup"><span data-stu-id="32f3f-208">Measure-Command</span></span>](Measure-Command.md)

[<span data-ttu-id="32f3f-209">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="32f3f-209">Set-TraceSource</span></span>](Set-TraceSource.md)

