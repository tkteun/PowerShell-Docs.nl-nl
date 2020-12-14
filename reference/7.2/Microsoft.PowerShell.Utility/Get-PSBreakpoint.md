---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSBreakpoint
ms.openlocfilehash: 78691b806fe68aaa8d9e502d28e6f3967867f95b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705438"
---
# <span data-ttu-id="eaa26-102">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="eaa26-102">Get-PSBreakpoint</span></span>

## <span data-ttu-id="eaa26-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="eaa26-103">SYNOPSIS</span></span>
<span data-ttu-id="eaa26-104">Hiermee worden de onderbrekings punten opgehaald die in de huidige sessie zijn ingesteld.</span><span class="sxs-lookup"><span data-stu-id="eaa26-104">Gets the breakpoints that are set in the current session.</span></span>

## <span data-ttu-id="eaa26-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="eaa26-105">SYNTAX</span></span>

### <span data-ttu-id="eaa26-106">Script (standaard)</span><span class="sxs-lookup"><span data-stu-id="eaa26-106">Script (Default)</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="eaa26-107">Variabele</span><span class="sxs-lookup"><span data-stu-id="eaa26-107">Variable</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Variable <String[]> [<CommonParameters>]
```

### <span data-ttu-id="eaa26-108">Opdracht</span><span class="sxs-lookup"><span data-stu-id="eaa26-108">Command</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Command <String[]> [<CommonParameters>]
```

### <span data-ttu-id="eaa26-109">Type</span><span class="sxs-lookup"><span data-stu-id="eaa26-109">Type</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [-Type] <BreakpointType[]> [<CommonParameters>]
```

### <span data-ttu-id="eaa26-110">Id</span><span class="sxs-lookup"><span data-stu-id="eaa26-110">Id</span></span>

```
Get-PSBreakpoint [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="eaa26-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="eaa26-111">DESCRIPTION</span></span>

<span data-ttu-id="eaa26-112">De cmdlet **Get-PSBreakPoint** haalt de onderbrekings punten op die in de huidige sessie zijn ingesteld.</span><span class="sxs-lookup"><span data-stu-id="eaa26-112">The **Get-PSBreakPoint** cmdlet gets the breakpoints that are set in the current session.</span></span>
<span data-ttu-id="eaa26-113">U kunt de cmdlet-para meters gebruiken voor het ophalen van bepaalde onderbrekings punten.</span><span class="sxs-lookup"><span data-stu-id="eaa26-113">You can use the cmdlet parameters to get particular breakpoints.</span></span>

<span data-ttu-id="eaa26-114">Een onderbrekings punt is een Point in een opdracht of script waar uitvoering tijdelijk wordt gestopt zodat u de instructies kunt onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="eaa26-114">A breakpoint is a point in a command or script where execution stops temporarily so that you can examine the instructions.</span></span>
<span data-ttu-id="eaa26-115">**Get-PSBreakpoint** is een van de verschillende cmdlets die zijn ontworpen voor het opsporen van fouten in Power shell-scripts en-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="eaa26-115">**Get-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts and commands.</span></span> <span data-ttu-id="eaa26-116">Zie about_Debuggers voor meer informatie over de Power Shell-fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="eaa26-116">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="eaa26-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="eaa26-117">EXAMPLES</span></span>

### <span data-ttu-id="eaa26-118">Voor beeld 1: alle onderbrekings punten ophalen voor alle scripts en functies</span><span class="sxs-lookup"><span data-stu-id="eaa26-118">Example 1: Get all breakpoints for all scripts and functions</span></span>

```
PS C:\> Get-PSBreakpoint
```

<span data-ttu-id="eaa26-119">Met deze opdracht worden alle onderbrekings punten opgehaald die zijn ingesteld voor alle scripts en functies in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="eaa26-119">This command gets all breakpoints set on all scripts and functions in the current session.</span></span>

### <span data-ttu-id="eaa26-120">Voor beeld 2: onderbrekings punten ophalen op ID</span><span class="sxs-lookup"><span data-stu-id="eaa26-120">Example 2: Get breakpoints by ID</span></span>

```
PS C:\> Get-PSBreakpoint -Id 2
Function   :
IncrementAction     :
Enabled    :
TrueHitCount   : 0
Id         : 2
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="eaa26-121">Met deze opdracht wordt het onderbrekings punt met onderbrekings punt-ID 2 opgehaald.</span><span class="sxs-lookup"><span data-stu-id="eaa26-121">This command gets the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="eaa26-122">Voor beeld 3: een ID Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="eaa26-122">Example 3: Pipe an ID to Get-PSBreakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Command "Increment"
PS C:\> $B.Id | Get-PSBreakpoint
```

<span data-ttu-id="eaa26-123">Deze opdrachten laten zien hoe een onderbrekings punt kan worden verkregen door een onderbrekings punt-ID op te **halen-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="eaa26-123">These commands show how to get a breakpoint by piping a breakpoint ID to **Get-PSBreakpoint**.</span></span>

<span data-ttu-id="eaa26-124">De eerste opdracht gebruikt de cmdlet Set-PSBreakpoint om een onderbrekings punt te maken voor de functie increment in het Sample.ps1 script.</span><span class="sxs-lookup"><span data-stu-id="eaa26-124">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Increment function in the Sample.ps1 script.</span></span> <span data-ttu-id="eaa26-125">Het object onderbrekings punt wordt opgeslagen in de variabele $B.</span><span class="sxs-lookup"><span data-stu-id="eaa26-125">It saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="eaa26-126">De tweede opdracht maakt gebruik van de punt operator (.) om de eigenschap ID van het object onderbrekings punt in de variabele $B te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="eaa26-126">The second command uses the dot operator (.) to get the Id property of the breakpoint object in the $B variable.</span></span> <span data-ttu-id="eaa26-127">Er wordt een pijplijn operator (|) gebruikt om de ID te verzenden naar de cmdlet **Get-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="eaa26-127">It uses a pipeline operator (|) to send the ID to the **Get-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="eaa26-128">Als gevolg hiervan **krijgt Get-PSBreakpoint** het onderbrekings punt met de opgegeven id.</span><span class="sxs-lookup"><span data-stu-id="eaa26-128">As a result, **Get-PSBreakpoint** gets the breakpoint with the specified ID.</span></span>

### <span data-ttu-id="eaa26-129">Voor beeld 4: onderbrekings punten in opgegeven script bestanden ophalen</span><span class="sxs-lookup"><span data-stu-id="eaa26-129">Example 4: Get breakpoints in specified script files</span></span>

```
PS C:\> Get-PSBreakpoint -Script "Sample.ps1, SupportScript.ps1"
```

<span data-ttu-id="eaa26-130">Met deze opdracht worden alle onderbrekings punten in de Sample.ps1-en SupportScript.ps1-bestanden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="eaa26-130">This command gets all of the breakpoints in the Sample.ps1 and SupportScript.ps1 files.</span></span>

<span data-ttu-id="eaa26-131">Met deze opdracht worden geen andere onderbrekings punten opgehaald die kunnen worden ingesteld in andere scripts of op functies in de sessie.</span><span class="sxs-lookup"><span data-stu-id="eaa26-131">This command does not get other breakpoints that might be set in other scripts or on functions in the session.</span></span>

### <span data-ttu-id="eaa26-132">Voor beeld 5: onderbrekings punten in opgegeven cmdlets ophalen</span><span class="sxs-lookup"><span data-stu-id="eaa26-132">Example 5: Get breakpoints in specified cmdlets</span></span>

```
PS C:\> Get-PSBreakpoint -Command "Read-Host, Write-Host" -Script "Sample.ps1"
```

<span data-ttu-id="eaa26-133">Met deze opdracht worden alle opdracht onderbrekings punten opgehaald die zijn ingesteld op Read-Host of Write-Host opdrachten in het Sample.ps1-bestand.</span><span class="sxs-lookup"><span data-stu-id="eaa26-133">This command gets all Command breakpoints that are set on Read-Host or Write-Host commands in the Sample.ps1 file.</span></span>

### <span data-ttu-id="eaa26-134">Voor beeld 6: opdracht onderbrekings punten ophalen in een opgegeven bestand</span><span class="sxs-lookup"><span data-stu-id="eaa26-134">Example 6: Get Command breakpoints in a specified file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Command -Script "Sample.ps1"
```

<span data-ttu-id="eaa26-135">Met deze opdracht worden alle opdracht onderbrekings punten in het Sample.ps1-bestand opgehaald.</span><span class="sxs-lookup"><span data-stu-id="eaa26-135">This command gets all Command breakpoints in the Sample.ps1 file.</span></span>

### <span data-ttu-id="eaa26-136">Voor beeld 7: onderbrekings punten ophalen per variabele</span><span class="sxs-lookup"><span data-stu-id="eaa26-136">Example 7: Get breakpoints by variable</span></span>

```
PS C:\> Get-PSBreakpoint -Variable "Index, Swap"
```

<span data-ttu-id="eaa26-137">Met deze opdracht worden onderbrekings punten opgehaald die zijn ingesteld voor de $Index en $Swap variabelen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="eaa26-137">This command gets breakpoints that are set on the $Index and $Swap variables in the current session.</span></span>

### <span data-ttu-id="eaa26-138">Voor beeld 8: alle regel-en variabele onderbrekings punten in een bestand ophalen</span><span class="sxs-lookup"><span data-stu-id="eaa26-138">Example 8: Get all Line and Variable breakpoints in a file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Line, Variable -Script "Sample.ps1"
```

<span data-ttu-id="eaa26-139">Met deze opdracht worden alle regel-en variabele onderbrekings punten in het Sample.ps1 script opgehaald.</span><span class="sxs-lookup"><span data-stu-id="eaa26-139">This command gets all line and variable breakpoints in the Sample.ps1 script.</span></span>

## <span data-ttu-id="eaa26-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="eaa26-140">PARAMETERS</span></span>

### <span data-ttu-id="eaa26-141">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="eaa26-141">-Command</span></span>

<span data-ttu-id="eaa26-142">Hiermee geeft u een matrix met opdracht onderbrekings punten op die zijn ingesteld voor de opgegeven opdracht namen.</span><span class="sxs-lookup"><span data-stu-id="eaa26-142">Specifies an array of command breakpoints that are set on the specified command names.</span></span>
<span data-ttu-id="eaa26-143">Voer de opdracht namen in, zoals de naam van een cmdlet of functie.</span><span class="sxs-lookup"><span data-stu-id="eaa26-143">Enter the command names, such as the name of a cmdlet or function.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eaa26-144">-Id</span><span class="sxs-lookup"><span data-stu-id="eaa26-144">-Id</span></span>

<span data-ttu-id="eaa26-145">Hiermee geeft u de onderbrekings punt-Id's op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="eaa26-145">Specifies the breakpoint IDs that this cmdlet gets.</span></span>
<span data-ttu-id="eaa26-146">Geef de Id's op in een lijst met door komma's gescheiden waarden.</span><span class="sxs-lookup"><span data-stu-id="eaa26-146">Enter the IDs in a comma-separated list.</span></span>
<span data-ttu-id="eaa26-147">U kunt ook punt-Id's van de pijp **lijn naar Get-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="eaa26-147">You can also pipe breakpoint IDs to **Get-PSBreakpoint**.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="eaa26-148">-Script</span><span class="sxs-lookup"><span data-stu-id="eaa26-148">-Script</span></span>

<span data-ttu-id="eaa26-149">Hiermee geeft u een matrix met scripts die de onderbrekings punten bevatten.</span><span class="sxs-lookup"><span data-stu-id="eaa26-149">Specifies an array of scripts that contain the breakpoints.</span></span>
<span data-ttu-id="eaa26-150">Voer het pad (optioneel) en de namen van een of meer script bestanden in.</span><span class="sxs-lookup"><span data-stu-id="eaa26-150">Enter the path (optional) and names of one or more script files.</span></span>
<span data-ttu-id="eaa26-151">Als u het pad weglaat, is de standaard locatie de huidige map.</span><span class="sxs-lookup"><span data-stu-id="eaa26-151">If you omit the path, the default location is the current directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Script, Variable, Command, Type
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="eaa26-152">-Type</span><span class="sxs-lookup"><span data-stu-id="eaa26-152">-Type</span></span>

<span data-ttu-id="eaa26-153">Hiermee geeft u een matrix van typen onderbrekings punten op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="eaa26-153">Specifies an array of breakpoint types that this cmdlet gets.</span></span>
<span data-ttu-id="eaa26-154">Voer een of meer typen in.</span><span class="sxs-lookup"><span data-stu-id="eaa26-154">Enter one or more types.</span></span>
<span data-ttu-id="eaa26-155">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="eaa26-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="eaa26-156">Lijn</span><span class="sxs-lookup"><span data-stu-id="eaa26-156">Line</span></span>
- <span data-ttu-id="eaa26-157">Opdracht</span><span class="sxs-lookup"><span data-stu-id="eaa26-157">Command</span></span>
- <span data-ttu-id="eaa26-158">Variabele</span><span class="sxs-lookup"><span data-stu-id="eaa26-158">Variable</span></span>

<span data-ttu-id="eaa26-159">U kunt ook de PSBreakPoint van het type pijp **lijn ophalen**.</span><span class="sxs-lookup"><span data-stu-id="eaa26-159">You can also pipe breakpoint types to **Get-PSBreakPoint**.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.BreakpointType[]
Parameter Sets: Type
Aliases:
Accepted values: Line, Variable, Command

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="eaa26-160">-Variabele</span><span class="sxs-lookup"><span data-stu-id="eaa26-160">-Variable</span></span>

<span data-ttu-id="eaa26-161">Hiermee geeft u een matrix met variabele onderbrekings punten op die zijn ingesteld voor de opgegeven namen van variabelen.</span><span class="sxs-lookup"><span data-stu-id="eaa26-161">Specifies an array of variable breakpoints that are set on the specified variable names.</span></span>
<span data-ttu-id="eaa26-162">Voer de namen van de variabelen in zonder dollar tekens.</span><span class="sxs-lookup"><span data-stu-id="eaa26-162">Enter the variable names without dollar signs.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eaa26-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eaa26-163">CommonParameters</span></span>

<span data-ttu-id="eaa26-164">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="eaa26-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eaa26-165">Zie about_CommonParameters (voor meer informatie https://go.microsoft.com/fwlink/?LinkID=113216) .</span><span class="sxs-lookup"><span data-stu-id="eaa26-165">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="eaa26-166">INVOER</span><span class="sxs-lookup"><span data-stu-id="eaa26-166">INPUTS</span></span>

### <span data-ttu-id="eaa26-167">System. Int32, micro soft. Power shell. commands. BreakpointType</span><span class="sxs-lookup"><span data-stu-id="eaa26-167">System.Int32, Microsoft.PowerShell.Commands.BreakpointType</span></span>

<span data-ttu-id="eaa26-168">U kunt de onderbrekings punt-Id's en typen onderbrekings punten voor **Get-PSBreakPoint**.</span><span class="sxs-lookup"><span data-stu-id="eaa26-168">You can pipe breakpoint IDs and breakpoint types to **Get-PSBreakPoint**.</span></span>

## <span data-ttu-id="eaa26-169">UITVOER</span><span class="sxs-lookup"><span data-stu-id="eaa26-169">OUTPUTS</span></span>

### <span data-ttu-id="eaa26-170">System. Management. Automation. Break Point</span><span class="sxs-lookup"><span data-stu-id="eaa26-170">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="eaa26-171">**Get-PSBreakPoint** retourneert objecten die de onderbrekings punten in de sessie vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="eaa26-171">**Get-PSBreakPoint** returns objects that represent the breakpoints in the session.</span></span>

## <span data-ttu-id="eaa26-172">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="eaa26-172">NOTES</span></span>

* <span data-ttu-id="eaa26-173">U kunt **Get-PSBreakpoint** of diens alias gebruiken, "GBP".</span><span class="sxs-lookup"><span data-stu-id="eaa26-173">You can use **Get-PSBreakpoint** or its alias, "gbp".</span></span>

## <span data-ttu-id="eaa26-174">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="eaa26-174">RELATED LINKS</span></span>

[<span data-ttu-id="eaa26-175">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="eaa26-175">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="eaa26-176">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="eaa26-176">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="eaa26-177">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="eaa26-177">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="eaa26-178">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="eaa26-178">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="eaa26-179">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="eaa26-179">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

