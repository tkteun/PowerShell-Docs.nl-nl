---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSBreakpoint
ms.openlocfilehash: ee2229866bdbee530230fbd5cf04ae362722bf2f
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249441"
---
# <span data-ttu-id="49264-103">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="49264-103">Set-PSBreakpoint</span></span>

## <span data-ttu-id="49264-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="49264-104">SYNOPSIS</span></span>
<span data-ttu-id="49264-105">Hiermee stelt u een onderbrekings punt in voor een regel, opdracht of variabele.</span><span class="sxs-lookup"><span data-stu-id="49264-105">Sets a breakpoint on a line, command, or variable.</span></span>

## <span data-ttu-id="49264-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="49264-106">SYNTAX</span></span>

### <span data-ttu-id="49264-107">Regel (standaard)</span><span class="sxs-lookup"><span data-stu-id="49264-107">Line (Default)</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Column] <Int32>] [-Line] <Int32[]> [-Script] <String[]>
 [<CommonParameters>]
```

### <span data-ttu-id="49264-108">Opdracht</span><span class="sxs-lookup"><span data-stu-id="49264-108">Command</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] -Command <String[]> [[-Script] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="49264-109">Variabele</span><span class="sxs-lookup"><span data-stu-id="49264-109">Variable</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Script] <String[]>] -Variable <String[]>
 [-Mode <VariableAccessMode>] [<CommonParameters>]
```

## <span data-ttu-id="49264-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="49264-110">DESCRIPTION</span></span>

<span data-ttu-id="49264-111">Met de `Set-PSBreakpoint` cmdlet wordt een onderbrekings punt ingesteld in een script of in een opdracht die wordt uitgevoerd in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="49264-111">The `Set-PSBreakpoint` cmdlet sets a breakpoint in a script or in any command run in the current session.</span></span> <span data-ttu-id="49264-112">U kunt gebruiken `Set-PSBreakpoint` om een onderbrekings punt in te stellen voordat u een script uitvoert of een opdracht uitvoert, of tijdens fout opsporing, wanneer deze op een ander onderbrekings punt wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="49264-112">You can use `Set-PSBreakpoint` to set a breakpoint before executing a script or running a command, or during debugging, when stopped at another breakpoint.</span></span>

<span data-ttu-id="49264-113">`Set-PSBreakpoint` kan geen onderbrekings punt instellen op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="49264-113">`Set-PSBreakpoint` cannot set a breakpoint on a remote computer.</span></span> <span data-ttu-id="49264-114">Als u fouten wilt opsporen in een script op een externe computer, kopieert u het script naar de lokale computer en voert u de fout opsporing lokaal uit.</span><span class="sxs-lookup"><span data-stu-id="49264-114">To debug a script on a remote computer, copy the script to the local computer and then debug it locally.</span></span>

<span data-ttu-id="49264-115">`Set-PSBreakpoint`Met elke opdracht maakt u een van de volgende drie typen onderbrekings punten:</span><span class="sxs-lookup"><span data-stu-id="49264-115">Each `Set-PSBreakpoint` command creates one of the following three types of breakpoints:</span></span>

- <span data-ttu-id="49264-116">Regel onderbrekings punt: stelt onderbrekings punten in voor bepaalde lijn-en kolom coördinaten.</span><span class="sxs-lookup"><span data-stu-id="49264-116">Line breakpoint - Sets breakpoints at particular line and column coordinates.</span></span>
- <span data-ttu-id="49264-117">Opdracht onderbrekings punt: Hiermee stelt u onderbrekings punten in voor opdrachten en functies.</span><span class="sxs-lookup"><span data-stu-id="49264-117">Command breakpoint - Sets breakpoints on commands and functions.</span></span>
- <span data-ttu-id="49264-118">Variabele onderbrekings punt: Hiermee stelt u onderbrekings punten in voor variabelen.</span><span class="sxs-lookup"><span data-stu-id="49264-118">Variable breakpoint - Sets breakpoints on variables.</span></span>

<span data-ttu-id="49264-119">U kunt een onderbrekings punt op meerdere regels, opdrachten of variabelen instellen in één `Set-PSBreakpoint` opdracht, maar met elke `Set-PSBreakpoint` opdracht wordt slechts één type onderbrekings punt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="49264-119">You can set a breakpoint on multiple lines, commands, or variables in a single `Set-PSBreakpoint` command, but each `Set-PSBreakpoint` command sets only one type of breakpoint.</span></span>

<span data-ttu-id="49264-120">Bij een onderbrekings punt wordt het uitvoeren van Power shell tijdelijk gestopt en krijgt de fout opsporing controle.</span><span class="sxs-lookup"><span data-stu-id="49264-120">At a breakpoint, PowerShell temporarily stops executing and gives control to the debugger.</span></span> <span data-ttu-id="49264-121">De opdracht prompt wordt gewijzigd in `DBG\>` en er worden een aantal opdrachten voor fout opsporing beschikbaar voor gebruik.</span><span class="sxs-lookup"><span data-stu-id="49264-121">The command prompt changes to `DBG\>`, and a set of debugger commands become available for use.</span></span> <span data-ttu-id="49264-122">U kunt echter de **actie** parameter gebruiken om een ander antwoord op te geven, zoals de voor waarden voor het onderbrekings punt of de instructies voor het uitvoeren van aanvullende taken, zoals logboek registratie of diagnose.</span><span class="sxs-lookup"><span data-stu-id="49264-122">However, you can use the **Action** parameter to specify an alternate response, such as conditions for the breakpoint or instructions to perform additional tasks such as logging or diagnostics.</span></span>

<span data-ttu-id="49264-123">De `Set-PSBreakpoint` cmdlet is een van de verschillende cmdlets die zijn ontworpen voor het opsporen van fouten in Power shell-scripts.</span><span class="sxs-lookup"><span data-stu-id="49264-123">The `Set-PSBreakpoint` cmdlet is one of several cmdlets designed for debugging PowerShell scripts.</span></span>
<span data-ttu-id="49264-124">Zie [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)voor meer informatie over de Power Shell-fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="49264-124">For more information about the PowerShell debugger, see [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span></span>

## <span data-ttu-id="49264-125">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="49264-125">EXAMPLES</span></span>

### <span data-ttu-id="49264-126">Voor beeld 1: een onderbrekings punt op een regel instellen</span><span class="sxs-lookup"><span data-stu-id="49264-126">Example 1: Set a breakpoint on a line</span></span>

<span data-ttu-id="49264-127">In dit voor beeld wordt een onderbrekings punt ingesteld op regel 5 in het Sample.ps1 script.</span><span class="sxs-lookup"><span data-stu-id="49264-127">This example sets a breakpoint at line 5 in the Sample.ps1 script.</span></span> <span data-ttu-id="49264-128">Wanneer het script wordt uitgevoerd, stopt de uitvoering onmiddellijk voordat regel 5 wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="49264-128">When the script runs, execution stops immediately before line 5 would execute.</span></span>

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Line 5
```

```output
Column     : 0
Line       : 5
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="49264-129">Wanneer u een nieuw onderbrekings punt op regel nummer instelt, `Set-PSBreakpoint` genereert de cmdlet een regel onderbrekings object ( **System. Management. Automation. LineBreakpoint** ) met daarin de ONDERBREKINGS punt-id en het aantal treffers.</span><span class="sxs-lookup"><span data-stu-id="49264-129">When you set a new breakpoint by line number, the `Set-PSBreakpoint` cmdlet generates a line breakpoint object ( **System.Management.Automation.LineBreakpoint** ) that includes the breakpoint ID and hit count.</span></span>

### <span data-ttu-id="49264-130">Voor beeld 2: een onderbrekings punt instellen voor een functie</span><span class="sxs-lookup"><span data-stu-id="49264-130">Example 2: Set a breakpoint on a function</span></span>

<span data-ttu-id="49264-131">In dit voor beeld wordt een onderbrekings punt voor opdrachten gemaakt voor de `Increment` functie in de cmdlet Sample.ps1.</span><span class="sxs-lookup"><span data-stu-id="49264-131">This example creates a command breakpoint on the `Increment` function in the Sample.ps1 cmdlet.</span></span> <span data-ttu-id="49264-132">Het script stopt direct voor elke aanroep van de opgegeven functie.</span><span class="sxs-lookup"><span data-stu-id="49264-132">The script stops executing immediately before each call to the specified function.</span></span>

```powershell
Set-PSBreakpoint -Command "Increment" -Script "sample.ps1"
```

```Output
Command    : Increment
Action     :
Enabled    : True
HitCount   : 0
Id         : 1
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="49264-133">Het resultaat is een opdracht onderbrekings object.</span><span class="sxs-lookup"><span data-stu-id="49264-133">The result is a command breakpoint object.</span></span> <span data-ttu-id="49264-134">Voordat het script wordt uitgevoerd, is de waarde van de eigenschap **HitCount** 0.</span><span class="sxs-lookup"><span data-stu-id="49264-134">Before the script runs, the value of the **HitCount** property is 0.</span></span>

### <span data-ttu-id="49264-135">Voor beeld 3: een onderbrekings punt instellen voor een variabele</span><span class="sxs-lookup"><span data-stu-id="49264-135">Example 3: Set a breakpoint on a variable</span></span>

<span data-ttu-id="49264-136">In dit voor beeld wordt een onderbrekings punt ingesteld voor de **Server** variabele in het Sample.ps1 script.</span><span class="sxs-lookup"><span data-stu-id="49264-136">This example sets a breakpoint on the **Server** variable in the Sample.ps1 script.</span></span> <span data-ttu-id="49264-137">De **modus** para meter met de waarde **readwrite** wordt gebruikt om de uitvoering te stoppen wanneer de waarde van de variabele wordt gelezen en net voordat de waarde wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="49264-137">It uses the **Mode** parameter with a value of **ReadWrite** to stop execution when the value of the variable is read and just before the value changes.</span></span>

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Variable "Server" -Mode ReadWrite
```

### <span data-ttu-id="49264-138">Voor beeld 4: een onderbrekings punt instellen voor elke opdracht die begint met opgegeven tekst</span><span class="sxs-lookup"><span data-stu-id="49264-138">Example 4: Set a breakpoint on every command that begins with specified text</span></span>

<span data-ttu-id="49264-139">In dit voor beeld wordt een onderbrekings punt ingesteld voor elke opdracht in het Sample.ps1 script dat begint met schrijven, zoals `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="49264-139">This example sets a breakpoint on every command in the Sample.ps1 script that begins with "write", such as `Write-Host`.</span></span>

```powershell
Set-PSBreakpoint -Script Sample.ps1 -Command "write*"
```

### <span data-ttu-id="49264-140">Voor beeld 5: een onderbrekings punt instellen, afhankelijk van de waarde van een variabele</span><span class="sxs-lookup"><span data-stu-id="49264-140">Example 5: Set a breakpoint depending on the value of a variable</span></span>

<span data-ttu-id="49264-141">In dit voor beeld wordt de uitvoering van de `DiskTest` functie in het Test.ps1 script alleen gestopt als de waarde van de `$Disk` variabele groter is dan 2.</span><span class="sxs-lookup"><span data-stu-id="49264-141">This example stops execution at the `DiskTest` function in the Test.ps1 script only when the value of the `$Disk` variable is greater than 2.</span></span>

```powershell
Set-PSBreakpoint -Script "test.ps1" -Command "DiskTest" -Action { if ($Disk -gt 2) { break } }
```

<span data-ttu-id="49264-142">De waarde van de **actie** is een script blok waarmee de waarde van de `$Disk` variabele in de functie wordt getest.</span><span class="sxs-lookup"><span data-stu-id="49264-142">The value of the **Action** is a script block that tests the value of the `$Disk` variable in the function.</span></span>

<span data-ttu-id="49264-143">De actie gebruikt het `break` tref woord om de uitvoering te stoppen als aan de voor waarde is voldaan.</span><span class="sxs-lookup"><span data-stu-id="49264-143">The action uses the `break` keyword to stop execution if the condition is met.</span></span> <span data-ttu-id="49264-144">Het alternatief (en de standaard instelling) wordt **voortgezet**.</span><span class="sxs-lookup"><span data-stu-id="49264-144">The alternative (and the default) is **Continue**.</span></span>

### <span data-ttu-id="49264-145">Voor beeld 6: een onderbrekings punt instellen voor een functie</span><span class="sxs-lookup"><span data-stu-id="49264-145">Example 6: Set a breakpoint on a function</span></span>

<span data-ttu-id="49264-146">In dit voor beeld wordt een onderbrekings punt voor de `CheckLog` functie ingesteld.</span><span class="sxs-lookup"><span data-stu-id="49264-146">This example sets a breakpoint on the `CheckLog` function.</span></span> <span data-ttu-id="49264-147">Omdat met de opdracht geen script wordt opgegeven, wordt het onderbrekings punt ingesteld op alles dat wordt uitgevoerd in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="49264-147">Because the command does not specify a script, the breakpoint is set on anything that runs in the current session.</span></span> <span data-ttu-id="49264-148">Het fout opsporingsprogramma breekt wanneer de functie wordt aangeroepen, niet wanneer deze wordt gedeclareerd.</span><span class="sxs-lookup"><span data-stu-id="49264-148">The debugger breaks when the function is called, not when it is declared.</span></span>

```
PS> Set-PSBreakpoint -Command "checklog"
Id       : 0
Command  : checklog
Enabled  : True
HitCount : 0
Action   :

function CheckLog {
>> get-eventlog -log Application |
>> where {($_.source -like "TestApp") -and ($_.Message -like "*failed*")}
>>}
>>
PS> Checklog
DEBUG: Hit breakpoint(s)
DEBUG:  Function breakpoint on 'prompt:Checklog'
```

### <span data-ttu-id="49264-149">Voor beeld 7: onderbrekings punten op meerdere regels instellen</span><span class="sxs-lookup"><span data-stu-id="49264-149">Example 7: Set breakpoints on multiple lines</span></span>

<span data-ttu-id="49264-150">In dit voor beeld worden drie regel onderbrekingen in het Sample.ps1 script ingesteld.</span><span class="sxs-lookup"><span data-stu-id="49264-150">This example sets three line breakpoints in the Sample.ps1 script.</span></span> <span data-ttu-id="49264-151">Er wordt één onderbrekings punt op kolom 2 ingesteld op elk van de regels die zijn opgegeven in het script.</span><span class="sxs-lookup"><span data-stu-id="49264-151">It sets one breakpoint at column 2 on each of the lines specified in the script.</span></span> <span data-ttu-id="49264-152">De actie die is opgegeven in de **actie** parameter is van toepassing op alle onderbrekings punten.</span><span class="sxs-lookup"><span data-stu-id="49264-152">The action specified in the **Action** parameter applies to all breakpoints.</span></span>

```powershell
PS C:\> Set-PSBreakpoint -Script "sample.ps1" -Line 1, 14, 19 -Column 2 -Action {&(log.ps1)}
```

```Output
Column     : 2
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 6
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 14
Action     :
Enabled    : True
HitCount   : 0
Id         : 7
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 19
Action     :
Enabled    : True
HitCount   : 0
Id         : 8
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

## <span data-ttu-id="49264-153">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="49264-153">PARAMETERS</span></span>

### <span data-ttu-id="49264-154">-Actie</span><span class="sxs-lookup"><span data-stu-id="49264-154">-Action</span></span>

<span data-ttu-id="49264-155">Geeft opdrachten die worden uitgevoerd op elke onderbrekings punt in plaats van te breken.</span><span class="sxs-lookup"><span data-stu-id="49264-155">Specifies commands that run at each breakpoint instead of breaking.</span></span> <span data-ttu-id="49264-156">Voer een script blok in dat de opdrachten bevat.</span><span class="sxs-lookup"><span data-stu-id="49264-156">Enter a script block that contains the commands.</span></span> <span data-ttu-id="49264-157">U kunt deze para meter gebruiken om voorwaardelijke onderbrekings punten in te stellen of om andere taken uit te voeren, zoals testen of logboek registratie.</span><span class="sxs-lookup"><span data-stu-id="49264-157">You can use this parameter to set conditional breakpoints or to perform other tasks, such as testing or logging.</span></span>

<span data-ttu-id="49264-158">Als deze para meter wordt wegge laten of er geen actie is opgegeven, wordt de uitvoering gestopt bij het onderbrekings punt en wordt het fout opsporingsprogramma gestart.</span><span class="sxs-lookup"><span data-stu-id="49264-158">If this parameter is omitted, or no action is specified, execution stops at the breakpoint, and the debugger starts.</span></span>

<span data-ttu-id="49264-159">Wanneer de **actie** parameter wordt gebruikt, wordt het actie script blok uitgevoerd op elke onderbrekings punt.</span><span class="sxs-lookup"><span data-stu-id="49264-159">When the **Action** parameter is used, the Action script block runs at each breakpoint.</span></span> <span data-ttu-id="49264-160">De uitvoering stopt alleen als het sleutel woord Outstore is opgenomen in het script blok.</span><span class="sxs-lookup"><span data-stu-id="49264-160">Execution does not stop unless the script block includes the Break keyword.</span></span> <span data-ttu-id="49264-161">Als u het sleutel woord door gaan in het script blok gebruikt, wordt de uitvoering hervat tot het volgende onderbrekings punt.</span><span class="sxs-lookup"><span data-stu-id="49264-161">If you use the Continue keyword in the script block, execution resumes until the next breakpoint.</span></span>

<span data-ttu-id="49264-162">Zie [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md), [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md)en [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="49264-162">For more information, see [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md), [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md), and [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49264-163">-Kolom</span><span class="sxs-lookup"><span data-stu-id="49264-163">-Column</span></span>

<span data-ttu-id="49264-164">Hiermee geeft u het kolom nummer van de kolom in het script bestand op waarop de uitvoering wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="49264-164">Specifies the column number of the column in the script file on which execution stops.</span></span> <span data-ttu-id="49264-165">Voer slechts één kolom nummer in.</span><span class="sxs-lookup"><span data-stu-id="49264-165">Enter only one column number.</span></span> <span data-ttu-id="49264-166">De standaard waarde is kolom 1.</span><span class="sxs-lookup"><span data-stu-id="49264-166">The default is column 1.</span></span>

<span data-ttu-id="49264-167">De waarde van de kolom wordt gebruikt in combi natie met de waarde van de **regel** parameter om het onderbrekings punt op te geven.</span><span class="sxs-lookup"><span data-stu-id="49264-167">The Column value is used with the value of the **Line** parameter to specify the breakpoint.</span></span> <span data-ttu-id="49264-168">Als met de **regel** parameter meerdere regels worden opgegeven, stelt de **kolom** parameter een onderbrekings punt in op de opgegeven kolom op elk van de opgegeven regels.</span><span class="sxs-lookup"><span data-stu-id="49264-168">If the **Line** parameter specifies multiple lines, the **Column** parameter sets a breakpoint at the specified column on each of the specified lines.</span></span> <span data-ttu-id="49264-169">Power shell stopt met het uitvoeren van de instructie of expressie die het teken op de opgegeven regel en kolom positie bevat.</span><span class="sxs-lookup"><span data-stu-id="49264-169">PowerShell stops executing before the statement or expression that includes the character at the specified line and column position.</span></span>

<span data-ttu-id="49264-170">Kolommen worden geteld vanaf de bovenste linkermarge, beginnend met kolom nummer 1 (niet 0).</span><span class="sxs-lookup"><span data-stu-id="49264-170">Columns are counted from the top left margin beginning with column number 1 (not 0).</span></span> <span data-ttu-id="49264-171">Als u een kolom opgeeft die niet voor komt in het script, wordt een fout niet gedeclareerd, maar wordt het onderbrekings punt nooit uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="49264-171">If you specify a column that does not exist in the script, an error is not declared, but the breakpoint is never executed.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Line
Aliases:

Required: False
Position: 2
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49264-172">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="49264-172">-Command</span></span>

<span data-ttu-id="49264-173">Hiermee stelt u een opdracht onderbrekings punt in.</span><span class="sxs-lookup"><span data-stu-id="49264-173">Sets a command breakpoint.</span></span> <span data-ttu-id="49264-174">Voer de namen van de cmdlets, zoals `Get-Process` , of functie namen in.</span><span class="sxs-lookup"><span data-stu-id="49264-174">Enter cmdlet names, such as `Get-Process`, or function names.</span></span> <span data-ttu-id="49264-175">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="49264-175">Wildcards are permitted.</span></span>

<span data-ttu-id="49264-176">De uitvoering stopt net voordat elk exemplaar van elke opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="49264-176">Execution stops just before each instance of each command is executed.</span></span> <span data-ttu-id="49264-177">Als de opdracht een functie is, stopt de uitvoering telkens wanneer de functie wordt aangeroepen en aan elk van de BEGIN-, proces-en END-secties.</span><span class="sxs-lookup"><span data-stu-id="49264-177">If the command is a function, execution stops each time the function is called and at each BEGIN, PROCESS, and END section.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases: C

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="49264-178">-Regel</span><span class="sxs-lookup"><span data-stu-id="49264-178">-Line</span></span>

<span data-ttu-id="49264-179">Hiermee stelt u een onderbrekings punt in een script.</span><span class="sxs-lookup"><span data-stu-id="49264-179">Sets a line breakpoint in a script.</span></span> <span data-ttu-id="49264-180">Voer een of meer regel nummers in, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="49264-180">Enter one or more line numbers, separated by commas.</span></span> <span data-ttu-id="49264-181">Power shell stopt onmiddellijk voor het uitvoeren van de instructie die begint op elk van de opgegeven regels.</span><span class="sxs-lookup"><span data-stu-id="49264-181">PowerShell stops immediately before executing the statement that begins on each of the specified lines.</span></span>

<span data-ttu-id="49264-182">De regels worden geteld vanaf de linkermarge van het script bestand, beginnend met regel nummer 1 (niet 0).</span><span class="sxs-lookup"><span data-stu-id="49264-182">Lines are counted from the top left margin of the script file beginning with line number 1 (not 0).</span></span>
<span data-ttu-id="49264-183">Als u een lege regel opgeeft, wordt de uitvoering gestopt voor de volgende niet-lege regel.</span><span class="sxs-lookup"><span data-stu-id="49264-183">If you specify a blank line, execution stops before the next non-blank line.</span></span> <span data-ttu-id="49264-184">Als de regel zich buiten het bereik bevindt, wordt het onderbrekings punt nooit bereikt.</span><span class="sxs-lookup"><span data-stu-id="49264-184">If the line is out of range, the breakpoint is never hit.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Line
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49264-185">-Modus</span><span class="sxs-lookup"><span data-stu-id="49264-185">-Mode</span></span>

<span data-ttu-id="49264-186">Hiermee geeft u de toegangs modus voor het activeren van variabele onderbrekings punten.</span><span class="sxs-lookup"><span data-stu-id="49264-186">Specifies the mode of access that triggers variable breakpoints.</span></span> <span data-ttu-id="49264-187">De standaard waarde is **schrijven**.</span><span class="sxs-lookup"><span data-stu-id="49264-187">The default is **Write**.</span></span>

<span data-ttu-id="49264-188">Deze para meter is alleen geldig wanneer de **variabele** para meter in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="49264-188">This parameter is valid only when the **Variable** parameter is used in the command.</span></span> <span data-ttu-id="49264-189">De modus is van toepassing op alle onderbrekings punten die in de opdracht zijn ingesteld.</span><span class="sxs-lookup"><span data-stu-id="49264-189">The mode applies to all breakpoints set in the command.</span></span> <span data-ttu-id="49264-190">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="49264-190">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="49264-191">De uitvoering van **Write** -stop stopt direct voordat een nieuwe waarde naar de variabele wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="49264-191">**Write** - Stops execution immediately before a new value is written to the variable.</span></span>
- <span data-ttu-id="49264-192">**Lezen** -stopt de uitvoering wanneer de variabele wordt gelezen, dat wil zeggen, wanneer de waarde ervan wordt geopend, wordt toegewezen, weer gegeven of gebruikt.</span><span class="sxs-lookup"><span data-stu-id="49264-192">**Read** - Stops execution when the variable is read, that is, when its value is accessed, either to be assigned, displayed, or used.</span></span> <span data-ttu-id="49264-193">In Lees modus stopt de uitvoering niet wanneer de waarde van de variabele wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="49264-193">In read mode, execution does not stop when the value of the variable changes.</span></span>
- <span data-ttu-id="49264-194">**Readwrite** -stopt de uitvoering wanneer de variabele wordt gelezen of geschreven.</span><span class="sxs-lookup"><span data-stu-id="49264-194">**ReadWrite** - Stops execution when the variable is read or written.</span></span>

```yaml
Type: System.Management.Automation.VariableAccessMode
Parameter Sets: Variable
Aliases:
Accepted values: Read, Write, ReadWrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49264-195">-Script</span><span class="sxs-lookup"><span data-stu-id="49264-195">-Script</span></span>

<span data-ttu-id="49264-196">Hiermee wordt een reeks script bestanden opgegeven die met deze cmdlet een onderbrekings punt in worden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="49264-196">Specifies an array of script files that this cmdlet sets a breakpoint in.</span></span> <span data-ttu-id="49264-197">Voer de paden en bestands namen in van een of meer script bestanden.</span><span class="sxs-lookup"><span data-stu-id="49264-197">Enter the paths and file names of one or more script files.</span></span> <span data-ttu-id="49264-198">Als de bestanden zich in de huidige map bevinden, kunt u het pad weglaten.</span><span class="sxs-lookup"><span data-stu-id="49264-198">If the files are in the current directory, you can omit the path.</span></span>
<span data-ttu-id="49264-199">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="49264-199">Wildcards are permitted.</span></span>

<span data-ttu-id="49264-200">Standaard worden onderbrekings punten en opdracht onderbrekings punten ingesteld voor elke opdracht die in de huidige sessie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="49264-200">By default, variable breakpoints and command breakpoints are set on any command that runs in the current session.</span></span> <span data-ttu-id="49264-201">Deze para meter is alleen vereist bij het instellen van een onderbrekings punt van een regel.</span><span class="sxs-lookup"><span data-stu-id="49264-201">This parameter is required only when setting a line breakpoint.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Line, Command, Variable
Aliases:

Required: True (Line), False (Command, Variable)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49264-202">-Variabele</span><span class="sxs-lookup"><span data-stu-id="49264-202">-Variable</span></span>

<span data-ttu-id="49264-203">Hiermee geeft u een matrix van variabelen op waarvoor met deze cmdlet onderbrekings punten worden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="49264-203">Specifies an array of variables that this cmdlet sets breakpoints on.</span></span> <span data-ttu-id="49264-204">Voer een door komma's gescheiden lijst met variabelen in zonder dollar tekens ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="49264-204">Enter a comma-separated list of variables without dollar signs (`$`).</span></span>

<span data-ttu-id="49264-205">Gebruik de **modus** para meter om de toegangs modus te bepalen die de onderbrekings punten activeert.</span><span class="sxs-lookup"><span data-stu-id="49264-205">Use the **Mode** parameter to determine the mode of access that triggers the breakpoints.</span></span> <span data-ttu-id="49264-206">De standaard modus, schrijven en stopt de uitvoering, net voordat een nieuwe waarde naar de variabele wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="49264-206">The default mode, Write, stops execution just before a new value is written to the variable.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases: V

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49264-207">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="49264-207">CommonParameters</span></span>

<span data-ttu-id="49264-208">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="49264-208">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="49264-209">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="49264-209">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="49264-210">INVOER</span><span class="sxs-lookup"><span data-stu-id="49264-210">INPUTS</span></span>

### <span data-ttu-id="49264-211">Geen</span><span class="sxs-lookup"><span data-stu-id="49264-211">None</span></span>
<span data-ttu-id="49264-212">U kunt geen pipe invoer naar `Set-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="49264-212">You cannot pipe input to `Set-PSBreakpoint`.</span></span>

## <span data-ttu-id="49264-213">UITVOER</span><span class="sxs-lookup"><span data-stu-id="49264-213">OUTPUTS</span></span>

### <span data-ttu-id="49264-214">Break Point object (System. Management. Automation. LineBreakpoint, System. Management. Automation. VariableBreakpoint, System. Management. Automation. CommandBreakpoint)</span><span class="sxs-lookup"><span data-stu-id="49264-214">Breakpoint object (System.Management.Automation.LineBreakpoint, System.Management.Automation.VariableBreakpoint, System.Management.Automation.CommandBreakpoint)</span></span>

<span data-ttu-id="49264-215">`Set-PSBreakpoint` retourneert een object dat staat voor elk onderbrekings punt dat wordt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="49264-215">`Set-PSBreakpoint` returns an object that represents each breakpoint that it sets.</span></span>

## <span data-ttu-id="49264-216">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="49264-216">NOTES</span></span>

- <span data-ttu-id="49264-217">`Set-PSBreakpoint` kan geen onderbrekings punt instellen op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="49264-217">`Set-PSBreakpoint` cannot set a breakpoint on a remote computer.</span></span> <span data-ttu-id="49264-218">Als u fouten wilt opsporen in een script op een externe computer, kopieert u het script naar de lokale computer en voert u de fout opsporing lokaal uit.</span><span class="sxs-lookup"><span data-stu-id="49264-218">To debug a script on a remote computer, copy the script to the local computer and then debug it locally.</span></span>
- <span data-ttu-id="49264-219">Wanneer u een onderbrekings punt instelt op meer dan één regel, opdracht of variabele, `Set-PSBreakpoint` genereert een onderbrekings punt object voor elk item.</span><span class="sxs-lookup"><span data-stu-id="49264-219">When you set a breakpoint on more than one line, command, or variable, `Set-PSBreakpoint` generates a breakpoint object for each entry.</span></span>
- <span data-ttu-id="49264-220">Bij het instellen van een onderbrekings punt voor een functie of variabele bij de opdracht prompt, kunt u het onderbrekings punt instellen vóór of na het maken van de functie of variabele.</span><span class="sxs-lookup"><span data-stu-id="49264-220">When setting a breakpoint on a function or variable at the command prompt, you can set the breakpoint before or after you create the function or variable.</span></span>

## <span data-ttu-id="49264-221">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="49264-221">RELATED LINKS</span></span>

[<span data-ttu-id="49264-222">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="49264-222">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="49264-223">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="49264-223">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="49264-224">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="49264-224">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="49264-225">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="49264-225">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="49264-226">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="49264-226">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)
