---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-psbreakpoint?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSBreakpoint
ms.openlocfilehash: 6afabaf46907d317ec864519a658c500466d4c38
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250209"
---
# <span data-ttu-id="d932e-103">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="d932e-103">Get-PSBreakpoint</span></span>

## <span data-ttu-id="d932e-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d932e-104">SYNOPSIS</span></span>
<span data-ttu-id="d932e-105">Hiermee worden de onderbrekings punten opgehaald die in de huidige sessie zijn ingesteld.</span><span class="sxs-lookup"><span data-stu-id="d932e-105">Gets the breakpoints that are set in the current session.</span></span>

## <span data-ttu-id="d932e-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d932e-106">SYNTAX</span></span>

### <span data-ttu-id="d932e-107">Script (standaard)</span><span class="sxs-lookup"><span data-stu-id="d932e-107">Script (Default)</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="d932e-108">Variabele</span><span class="sxs-lookup"><span data-stu-id="d932e-108">Variable</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Variable <String[]> [<CommonParameters>]
```

### <span data-ttu-id="d932e-109">Opdracht</span><span class="sxs-lookup"><span data-stu-id="d932e-109">Command</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Command <String[]> [<CommonParameters>]
```

### <span data-ttu-id="d932e-110">Type</span><span class="sxs-lookup"><span data-stu-id="d932e-110">Type</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [-Type] <BreakpointType[]> [<CommonParameters>]
```

### <span data-ttu-id="d932e-111">Id</span><span class="sxs-lookup"><span data-stu-id="d932e-111">Id</span></span>

```
Get-PSBreakpoint [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="d932e-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d932e-112">DESCRIPTION</span></span>

<span data-ttu-id="d932e-113">De cmdlet **Get-PSBreakPoint** haalt de onderbrekings punten op die in de huidige sessie zijn ingesteld.</span><span class="sxs-lookup"><span data-stu-id="d932e-113">The **Get-PSBreakPoint** cmdlet gets the breakpoints that are set in the current session.</span></span>
<span data-ttu-id="d932e-114">U kunt de cmdlet-para meters gebruiken voor het ophalen van bepaalde onderbrekings punten.</span><span class="sxs-lookup"><span data-stu-id="d932e-114">You can use the cmdlet parameters to get particular breakpoints.</span></span>

<span data-ttu-id="d932e-115">Een onderbrekings punt is een Point in een opdracht of script waar uitvoering tijdelijk wordt gestopt zodat u de instructies kunt onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="d932e-115">A breakpoint is a point in a command or script where execution stops temporarily so that you can examine the instructions.</span></span>
<span data-ttu-id="d932e-116">**Get-PSBreakpoint** is een van de verschillende cmdlets die zijn ontworpen voor het opsporen van fouten in Power shell-scripts en-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="d932e-116">**Get-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts and commands.</span></span> <span data-ttu-id="d932e-117">Zie about_Debuggers voor meer informatie over de Power Shell-fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="d932e-117">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="d932e-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d932e-118">EXAMPLES</span></span>

### <span data-ttu-id="d932e-119">Voor beeld 1: alle onderbrekings punten ophalen voor alle scripts en functies</span><span class="sxs-lookup"><span data-stu-id="d932e-119">Example 1: Get all breakpoints for all scripts and functions</span></span>

```
PS C:\> Get-PSBreakpoint
```

<span data-ttu-id="d932e-120">Met deze opdracht worden alle onderbrekings punten opgehaald die zijn ingesteld voor alle scripts en functies in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="d932e-120">This command gets all breakpoints set on all scripts and functions in the current session.</span></span>

### <span data-ttu-id="d932e-121">Voor beeld 2: onderbrekings punten ophalen op ID</span><span class="sxs-lookup"><span data-stu-id="d932e-121">Example 2: Get breakpoints by ID</span></span>

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

<span data-ttu-id="d932e-122">Met deze opdracht wordt het onderbrekings punt met onderbrekings punt-ID 2 opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d932e-122">This command gets the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="d932e-123">Voor beeld 3: een ID Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="d932e-123">Example 3: Pipe an ID to Get-PSBreakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Command "Increment"
PS C:\> $B.Id | Get-PSBreakpoint
```

<span data-ttu-id="d932e-124">Deze opdrachten laten zien hoe een onderbrekings punt kan worden verkregen door een onderbrekings punt-ID op te **halen-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="d932e-124">These commands show how to get a breakpoint by piping a breakpoint ID to **Get-PSBreakpoint**.</span></span>

<span data-ttu-id="d932e-125">De eerste opdracht gebruikt de cmdlet Set-PSBreakpoint om een onderbrekings punt te maken voor de functie increment in het Sample.ps1 script.</span><span class="sxs-lookup"><span data-stu-id="d932e-125">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Increment function in the Sample.ps1 script.</span></span> <span data-ttu-id="d932e-126">Het object onderbrekings punt wordt opgeslagen in de variabele $B.</span><span class="sxs-lookup"><span data-stu-id="d932e-126">It saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="d932e-127">De tweede opdracht maakt gebruik van de punt operator (.) om de eigenschap ID van het object onderbrekings punt in de variabele $B te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="d932e-127">The second command uses the dot operator (.) to get the Id property of the breakpoint object in the $B variable.</span></span> <span data-ttu-id="d932e-128">Er wordt een pijplijn operator (|) gebruikt om de ID te verzenden naar de cmdlet **Get-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="d932e-128">It uses a pipeline operator (|) to send the ID to the **Get-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="d932e-129">Als gevolg hiervan **krijgt Get-PSBreakpoint** het onderbrekings punt met de opgegeven id.</span><span class="sxs-lookup"><span data-stu-id="d932e-129">As a result, **Get-PSBreakpoint** gets the breakpoint with the specified ID.</span></span>

### <span data-ttu-id="d932e-130">Voor beeld 4: onderbrekings punten in opgegeven script bestanden ophalen</span><span class="sxs-lookup"><span data-stu-id="d932e-130">Example 4: Get breakpoints in specified script files</span></span>

```
PS C:\> Get-PSBreakpoint -Script "Sample.ps1, SupportScript.ps1"
```

<span data-ttu-id="d932e-131">Met deze opdracht worden alle onderbrekings punten in de Sample.ps1-en SupportScript.ps1-bestanden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d932e-131">This command gets all of the breakpoints in the Sample.ps1 and SupportScript.ps1 files.</span></span>

<span data-ttu-id="d932e-132">Met deze opdracht worden geen andere onderbrekings punten opgehaald die kunnen worden ingesteld in andere scripts of op functies in de sessie.</span><span class="sxs-lookup"><span data-stu-id="d932e-132">This command does not get other breakpoints that might be set in other scripts or on functions in the session.</span></span>

### <span data-ttu-id="d932e-133">Voor beeld 5: onderbrekings punten in opgegeven cmdlets ophalen</span><span class="sxs-lookup"><span data-stu-id="d932e-133">Example 5: Get breakpoints in specified cmdlets</span></span>

```
PS C:\> Get-PSBreakpoint -Command "Read-Host, Write-Host" -Script "Sample.ps1"
```

<span data-ttu-id="d932e-134">Met deze opdracht worden alle opdracht onderbrekings punten opgehaald die zijn ingesteld op Read-Host of Write-Host opdrachten in het Sample.ps1-bestand.</span><span class="sxs-lookup"><span data-stu-id="d932e-134">This command gets all Command breakpoints that are set on Read-Host or Write-Host commands in the Sample.ps1 file.</span></span>

### <span data-ttu-id="d932e-135">Voor beeld 6: opdracht onderbrekings punten ophalen in een opgegeven bestand</span><span class="sxs-lookup"><span data-stu-id="d932e-135">Example 6: Get Command breakpoints in a specified file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Command -Script "Sample.ps1"
```

<span data-ttu-id="d932e-136">Met deze opdracht worden alle opdracht onderbrekings punten in het Sample.ps1-bestand opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d932e-136">This command gets all Command breakpoints in the Sample.ps1 file.</span></span>

### <span data-ttu-id="d932e-137">Voor beeld 7: onderbrekings punten ophalen per variabele</span><span class="sxs-lookup"><span data-stu-id="d932e-137">Example 7: Get breakpoints by variable</span></span>

```
PS C:\> Get-PSBreakpoint -Variable "Index, Swap"
```

<span data-ttu-id="d932e-138">Met deze opdracht worden onderbrekings punten opgehaald die zijn ingesteld voor de $Index en $Swap variabelen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="d932e-138">This command gets breakpoints that are set on the $Index and $Swap variables in the current session.</span></span>

### <span data-ttu-id="d932e-139">Voor beeld 8: alle regel-en variabele onderbrekings punten in een bestand ophalen</span><span class="sxs-lookup"><span data-stu-id="d932e-139">Example 8: Get all Line and Variable breakpoints in a file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Line, Variable -Script "Sample.ps1"
```

<span data-ttu-id="d932e-140">Met deze opdracht worden alle regel-en variabele onderbrekings punten in het Sample.ps1 script opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d932e-140">This command gets all line and variable breakpoints in the Sample.ps1 script.</span></span>

## <span data-ttu-id="d932e-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d932e-141">PARAMETERS</span></span>

### <span data-ttu-id="d932e-142">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="d932e-142">-Command</span></span>

<span data-ttu-id="d932e-143">Hiermee geeft u een matrix met opdracht onderbrekings punten op die zijn ingesteld voor de opgegeven opdracht namen.</span><span class="sxs-lookup"><span data-stu-id="d932e-143">Specifies an array of command breakpoints that are set on the specified command names.</span></span>
<span data-ttu-id="d932e-144">Voer de opdracht namen in, zoals de naam van een cmdlet of functie.</span><span class="sxs-lookup"><span data-stu-id="d932e-144">Enter the command names, such as the name of a cmdlet or function.</span></span>

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

### <span data-ttu-id="d932e-145">-Id</span><span class="sxs-lookup"><span data-stu-id="d932e-145">-Id</span></span>

<span data-ttu-id="d932e-146">Hiermee geeft u de onderbrekings punt-Id's op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d932e-146">Specifies the breakpoint IDs that this cmdlet gets.</span></span>
<span data-ttu-id="d932e-147">Geef de Id's op in een lijst met door komma's gescheiden waarden.</span><span class="sxs-lookup"><span data-stu-id="d932e-147">Enter the IDs in a comma-separated list.</span></span>
<span data-ttu-id="d932e-148">U kunt ook punt-Id's van de pijp **lijn naar Get-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="d932e-148">You can also pipe breakpoint IDs to **Get-PSBreakpoint**.</span></span>

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

### <span data-ttu-id="d932e-149">-Script</span><span class="sxs-lookup"><span data-stu-id="d932e-149">-Script</span></span>

<span data-ttu-id="d932e-150">Hiermee geeft u een matrix met scripts die de onderbrekings punten bevatten.</span><span class="sxs-lookup"><span data-stu-id="d932e-150">Specifies an array of scripts that contain the breakpoints.</span></span>
<span data-ttu-id="d932e-151">Voer het pad (optioneel) en de namen van een of meer script bestanden in.</span><span class="sxs-lookup"><span data-stu-id="d932e-151">Enter the path (optional) and names of one or more script files.</span></span>
<span data-ttu-id="d932e-152">Als u het pad weglaat, is de standaard locatie de huidige map.</span><span class="sxs-lookup"><span data-stu-id="d932e-152">If you omit the path, the default location is the current directory.</span></span>

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

### <span data-ttu-id="d932e-153">-Type</span><span class="sxs-lookup"><span data-stu-id="d932e-153">-Type</span></span>

<span data-ttu-id="d932e-154">Hiermee geeft u een matrix van typen onderbrekings punten op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d932e-154">Specifies an array of breakpoint types that this cmdlet gets.</span></span>
<span data-ttu-id="d932e-155">Voer een of meer typen in.</span><span class="sxs-lookup"><span data-stu-id="d932e-155">Enter one or more types.</span></span>
<span data-ttu-id="d932e-156">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="d932e-156">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d932e-157">Lijn</span><span class="sxs-lookup"><span data-stu-id="d932e-157">Line</span></span>
- <span data-ttu-id="d932e-158">Opdracht</span><span class="sxs-lookup"><span data-stu-id="d932e-158">Command</span></span>
- <span data-ttu-id="d932e-159">Variabele</span><span class="sxs-lookup"><span data-stu-id="d932e-159">Variable</span></span>

<span data-ttu-id="d932e-160">U kunt ook de PSBreakPoint van het type pijp **lijn ophalen**.</span><span class="sxs-lookup"><span data-stu-id="d932e-160">You can also pipe breakpoint types to **Get-PSBreakPoint**.</span></span>

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

### <span data-ttu-id="d932e-161">-Variabele</span><span class="sxs-lookup"><span data-stu-id="d932e-161">-Variable</span></span>

<span data-ttu-id="d932e-162">Hiermee geeft u een matrix met variabele onderbrekings punten op die zijn ingesteld voor de opgegeven namen van variabelen.</span><span class="sxs-lookup"><span data-stu-id="d932e-162">Specifies an array of variable breakpoints that are set on the specified variable names.</span></span>
<span data-ttu-id="d932e-163">Voer de namen van de variabelen in zonder dollar tekens.</span><span class="sxs-lookup"><span data-stu-id="d932e-163">Enter the variable names without dollar signs.</span></span>

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

### <span data-ttu-id="d932e-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d932e-164">CommonParameters</span></span>

<span data-ttu-id="d932e-165">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d932e-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d932e-166">Zie about_CommonParameters (voor meer informatie https://go.microsoft.com/fwlink/?LinkID=113216) .</span><span class="sxs-lookup"><span data-stu-id="d932e-166">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d932e-167">INVOER</span><span class="sxs-lookup"><span data-stu-id="d932e-167">INPUTS</span></span>

### <span data-ttu-id="d932e-168">System. Int32, micro soft. Power shell. commands. BreakpointType</span><span class="sxs-lookup"><span data-stu-id="d932e-168">System.Int32, Microsoft.PowerShell.Commands.BreakpointType</span></span>

<span data-ttu-id="d932e-169">U kunt de onderbrekings punt-Id's en typen onderbrekings punten voor **Get-PSBreakPoint**.</span><span class="sxs-lookup"><span data-stu-id="d932e-169">You can pipe breakpoint IDs and breakpoint types to **Get-PSBreakPoint**.</span></span>

## <span data-ttu-id="d932e-170">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d932e-170">OUTPUTS</span></span>

### <span data-ttu-id="d932e-171">System. Management. Automation. Break Point</span><span class="sxs-lookup"><span data-stu-id="d932e-171">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="d932e-172">**Get-PSBreakPoint** retourneert objecten die de onderbrekings punten in de sessie vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="d932e-172">**Get-PSBreakPoint** returns objects that represent the breakpoints in the session.</span></span>

## <span data-ttu-id="d932e-173">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d932e-173">NOTES</span></span>

* <span data-ttu-id="d932e-174">U kunt **Get-PSBreakpoint** of diens alias gebruiken, "GBP".</span><span class="sxs-lookup"><span data-stu-id="d932e-174">You can use **Get-PSBreakpoint** or its alias, "gbp".</span></span>

## <span data-ttu-id="d932e-175">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d932e-175">RELATED LINKS</span></span>

[<span data-ttu-id="d932e-176">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="d932e-176">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="d932e-177">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="d932e-177">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="d932e-178">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="d932e-178">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="d932e-179">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="d932e-179">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="d932e-180">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="d932e-180">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

