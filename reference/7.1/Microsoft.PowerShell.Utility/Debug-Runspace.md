---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/debug-runspace?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Runspace
ms.openlocfilehash: fd1da10b3a64e0fe9b43dfec1289eebaf31ed739
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250906"
---
# <span data-ttu-id="6e3f1-103">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="6e3f1-103">Debug-Runspace</span></span>

## <span data-ttu-id="6e3f1-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="6e3f1-104">SYNOPSIS</span></span>
<span data-ttu-id="6e3f1-105">Hiermee wordt een interactieve foutopsporingssessie gestart met een runs Pace.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-105">Starts an interactive debugging session with a runspace.</span></span>

## <span data-ttu-id="6e3f1-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6e3f1-106">SYNTAX</span></span>

### <span data-ttu-id="6e3f1-107">RunspaceParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="6e3f1-107">RunspaceParameterSet (Default)</span></span>

```
Debug-Runspace [-Runspace] <Runspace> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6e3f1-108">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="6e3f1-108">NameParameterSet</span></span>

```
Debug-Runspace [-Name] <String> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6e3f1-109">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="6e3f1-109">IdParameterSet</span></span>

```
Debug-Runspace [-Id] <Int32> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6e3f1-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="6e3f1-110">InstanceIdParameterSet</span></span>

```
Debug-Runspace [-InstanceId] <Guid> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6e3f1-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6e3f1-111">DESCRIPTION</span></span>

<span data-ttu-id="6e3f1-112">De `Debug-Runspace` cmdlet start een interactieve foutopsporingssessie met een lokale of externe actief runs Pace.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-112">The `Debug-Runspace` cmdlet starts an interactive debugging session with a local or remote active runspace.</span></span> <span data-ttu-id="6e3f1-113">U kunt een runs Pace vinden waarvoor u fouten wilt opsporen door eerst uit `Get-Process` te voeren naar processen die zijn gekoppeld aan Power shell, vervolgens `Enter-PSHostProcess` met de proces-id die is opgegeven in de **id-** para meter om aan het proces te koppelen en vervolgens `Get-Runspace` runspaces binnen het Power shell-hostproces weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-113">You can find a runspace that you want to debug by first running `Get-Process` to find processes associated with PowerShell, then `Enter-PSHostProcess` with the process ID specified in the **Id** parameter to attach to the process, and then `Get-Runspace` to list runspaces within the PowerShell host process.</span></span>

<span data-ttu-id="6e3f1-114">Nadat u een runs Pace hebt geselecteerd voor het opsporen van fouten, als de runs Pace momenteel een opdracht of script uitvoert, of als het script op een onderbrekings punt is gestopt, opent Power shell een sessie voor externe fout opsporing voor de runs Pace.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-114">After you have selected a runspace to debug, if the runspace is currently running a command or script, or if the script has stopped at a breakpoint, PowerShell opens a remote debugger session for the runspace.</span></span> <span data-ttu-id="6e3f1-115">U kunt fouten opsporen in het runs Pace-script op dezelfde manier als met externe-sessie scripts worden opgespoord.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-115">You can debug the runspace script in the same way remote session scripts are debugged.</span></span>

<span data-ttu-id="6e3f1-116">U kunt alleen koppelen aan een Power shell-hostproces als u een beheerder bent op de computer waarop het proces wordt uitgevoerd, of als u het script uitvoert dat u wilt fouten opsporen.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-116">You can only attach to a PowerShell host process if you are an administrator on the computer that is running the process, or you are running the script that you want to debug.</span></span> <span data-ttu-id="6e3f1-117">U kunt ook het hostproces met de huidige Power shell-sessie niet invoeren.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-117">Also, you cannot enter the host process that is running the current PowerShell session.</span></span> <span data-ttu-id="6e3f1-118">U kunt alleen een hostproces invoeren waarop een andere Power shell-sessie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-118">You can only enter a host process that is running a different PowerShell session.</span></span>

## <span data-ttu-id="6e3f1-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6e3f1-119">EXAMPLES</span></span>

### <span data-ttu-id="6e3f1-120">Voor beeld 1: fouten opsporen in een externe runs Pace</span><span class="sxs-lookup"><span data-stu-id="6e3f1-120">Example 1: Debug a remote runspace</span></span>

```
PS C:\> Get-Process -ComputerName "WS10TestServer" -Name "*powershell*"

Handles      WS(K)   VM(M)      CPU(s)    Id  ProcessName
-------      -----   -----      ------    --  -----------
    377      69912     63     2.09      2420  powershell
    399     123396    829     4.48      1152  powershell_ise

PS C:\> Enter-PSSession -ComputerName "WS10TestServer"
[WS10TestServer]:PS C:\> Enter-PSHostProcess -Id 1152
[WS10TestServer:][Process:1152]: PS C:\Users\Test\Documents> Get-Runspace

Id Name            ComputerName    Type          State         Availability
-- ----            ------------    ----          -----         ------------
 1 Runspace1       WS10TestServer  Remote        Opened        Available
 2 RemoteHost      WS10TestServer  Remote        Opened        Busy

PS C:\> [WS10TestServer][Process:1152]: PS C:\Users\Test\Documents> Debug-Runspace -Id 2

Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'
At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[Process:1152]: [RSDBG: 2]: PS C:\> >
```

<span data-ttu-id="6e3f1-121">In dit voor beeld kunt u fouten opsporen in een runs Pace die is geopend op een externe computer, WS10TestServer.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-121">In this example, you debug a runspace that is open on a remote computer, WS10TestServer.</span></span> <span data-ttu-id="6e3f1-122">Op de eerste regel van de opdracht voert u uit `Get-Process` op de externe computer en filtert u op Windows Power shell-host-processen.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-122">In the first line of the command, you run `Get-Process` on the remote computer, and filter for Windows PowerShell host processes.</span></span> <span data-ttu-id="6e3f1-123">In dit voor beeld wilt u de proces-ID 1152, het Windows PowerShell ISE-hostproces, fout opsporing uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-123">In this example, you want to debug process ID 1152, the Windows PowerShell ISE host process.</span></span>

<span data-ttu-id="6e3f1-124">In de tweede opdracht voert u uit `Enter-PSSession` om een externe sessie op WS10TestServer te openen.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-124">In the second command, you run `Enter-PSSession` to open a remote session on WS10TestServer.</span></span> <span data-ttu-id="6e3f1-125">In de derde opdracht koppelt u aan het Windows PowerShell ISE-hostproces dat wordt uitgevoerd op de externe server door uit te voeren `Enter-PSHostProcess` en geeft u de id op van het hostproces dat u hebt verkregen in de eerste opdracht, 1152.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-125">In the third command, you attach to the Windows PowerShell ISE host process running on the remote server by running `Enter-PSHostProcess`, and specifying the ID of the host process that you obtained in the first command, 1152.</span></span>

<span data-ttu-id="6e3f1-126">In de vierde opdracht vermeldt u beschik bare runspaces voor proces-ID 1152 door uit te voeren `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="6e3f1-126">In the fourth command, you list available runspaces for process ID 1152 by running `Get-Runspace`.</span></span>
<span data-ttu-id="6e3f1-127">U noteert het ID-nummer van de bezet runs Pace; Er wordt een script uitgevoerd waarvoor u fouten wilt opsporen.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-127">You note the ID number of the Busy runspace; it is running a script that you want to debug.</span></span>

<span data-ttu-id="6e3f1-128">In de laatste opdracht start u de fout opsporing van een geopende runs Pace met een script, TestWFVar1.ps1, door uit `Debug-Runspace` te voeren en de runs Pace te identificeren met de id, 2, door de **id-** para meter toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-128">In the last command, you start debugging an opened runspace that is running a script, TestWFVar1.ps1, by running `Debug-Runspace`, and identifying the runspace by its ID, 2, by adding the **Id** parameter.</span></span> <span data-ttu-id="6e3f1-129">Omdat het script een onderbrekings punt bevat, wordt het fout opsporingsprogramma geopend.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-129">Because there's a breakpoint in the script, the debugger opens.</span></span>

## <span data-ttu-id="6e3f1-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6e3f1-130">PARAMETERS</span></span>

### <span data-ttu-id="6e3f1-131">-Id</span><span class="sxs-lookup"><span data-stu-id="6e3f1-131">-Id</span></span>

<span data-ttu-id="6e3f1-132">Hiermee wordt het ID-nummer van een runs Pace opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-132">Specifies the ID number of a runspace.</span></span> <span data-ttu-id="6e3f1-133">U kunt uitvoeren `Get-Runspace` om runs Pace-id's weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-133">You can run `Get-Runspace` to show runspace IDs.</span></span>

```yaml
Type: System.Int32
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e3f1-134">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="6e3f1-134">-InstanceId</span></span>

<span data-ttu-id="6e3f1-135">Hiermee geeft u een runs Pace op met de instantie-ID, een GUID die u kunt weer geven door uit te voeren `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="6e3f1-135">Specifies a runspace by its instance ID, a GUID that you can show by running `Get-Runspace`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e3f1-136">-Name</span><span class="sxs-lookup"><span data-stu-id="6e3f1-136">-Name</span></span>

<span data-ttu-id="6e3f1-137">Hiermee geeft u een runs Pace op met de naam.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-137">Specifies a runspace by its name.</span></span> <span data-ttu-id="6e3f1-138">U kunt uitvoeren `Get-Runspace` om de namen van runspaces weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-138">You can run `Get-Runspace` to show the names of runspaces.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e3f1-139">-Runs Pace</span><span class="sxs-lookup"><span data-stu-id="6e3f1-139">-Runspace</span></span>

<span data-ttu-id="6e3f1-140">Hiermee geeft u een runs Pace-object op.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-140">Specifies a runspace object.</span></span> <span data-ttu-id="6e3f1-141">De eenvoudigste manier om een waarde voor deze para meter op te geven, is door een variabele op te geven die de resultaten van een gefilterde `Get-Runspace` opdracht bevat.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-141">The simplest way to provide a value for this parameter is to specify a variable that contains the results of a filtered `Get-Runspace` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.Runspace
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6e3f1-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6e3f1-142">-Confirm</span></span>

<span data-ttu-id="6e3f1-143">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-143">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e3f1-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6e3f1-144">-WhatIf</span></span>

<span data-ttu-id="6e3f1-145">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-145">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="6e3f1-146">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-146">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6e3f1-147">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="6e3f1-147">-BreakAll</span></span>

<span data-ttu-id="6e3f1-148">{{Opvulling BreakAll beschrijving}}</span><span class="sxs-lookup"><span data-stu-id="6e3f1-148">{{ Fill BreakAll Description }}</span></span>

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

### <span data-ttu-id="6e3f1-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6e3f1-149">CommonParameters</span></span>

<span data-ttu-id="6e3f1-150">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6e3f1-151">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6e3f1-152">INVOER</span><span class="sxs-lookup"><span data-stu-id="6e3f1-152">INPUTS</span></span>

### <span data-ttu-id="6e3f1-153">System. Management. Automation. Runspaces. runs Pace</span><span class="sxs-lookup"><span data-stu-id="6e3f1-153">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="6e3f1-154">U kunt de resultaten van een opdracht door sluizen `Get-Runspace` naar **debug-runs Pace.**</span><span class="sxs-lookup"><span data-stu-id="6e3f1-154">You can pipe the results of a `Get-Runspace` command to **Debug-Runspace.**</span></span>

## <span data-ttu-id="6e3f1-155">UITVOER</span><span class="sxs-lookup"><span data-stu-id="6e3f1-155">OUTPUTS</span></span>

## <span data-ttu-id="6e3f1-156">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="6e3f1-156">NOTES</span></span>

<span data-ttu-id="6e3f1-157">`Debug-Runspace` werkt op runspaces met de status Opened.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-157">`Debug-Runspace` works on runspaces that are in the Opened state.</span></span> <span data-ttu-id="6e3f1-158">Als de status van een runs Pace wordt gewijzigd van geopend in een andere status, wordt die runs Pace automatisch verwijderd uit de lijst met actieve.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-158">If a runspace state changes from Opened to another state, that runspace is automatically removed from the running list.</span></span> <span data-ttu-id="6e3f1-159">Een runs Pace wordt alleen toegevoegd aan de actieve lijst als deze voldoet aan de volgende criteria.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-159">A runspace is added to the running list only if it meets the following criteria.</span></span>

- <span data-ttu-id="6e3f1-160">Als deze afkomstig is van invoke-opdracht; dat wil zeggen dat het een `Invoke-Command` GUID-id heeft.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-160">If it is coming from Invoke-Command; that is, it has an `Invoke-Command` GUID ID.</span></span>
- <span data-ttu-id="6e3f1-161">Als dat het geval is `Debug-Runspace` , heeft het een `Debug-Runspace` GUID-id.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-161">If it is coming from `Debug-Runspace`; that is, it has a `Debug-Runspace` GUID ID.</span></span>
- <span data-ttu-id="6e3f1-162">Als het afkomstig is van een Power shell-werk stroom en de werk stroom taak-ID hetzelfde is als de huidige actieve debugger werk stroom taak-ID.</span><span class="sxs-lookup"><span data-stu-id="6e3f1-162">If it is coming from a PowerShell workflow, and its workflow job ID is the same as the current active debugger workflow job ID.</span></span>

## <span data-ttu-id="6e3f1-163">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6e3f1-163">RELATED LINKS</span></span>

[<span data-ttu-id="6e3f1-164">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="6e3f1-164">about_Debuggers</span></span>](../Microsoft.PowerShell.Core/About/about_Debuggers.md)

[<span data-ttu-id="6e3f1-165">Fout opsporing-taak</span><span class="sxs-lookup"><span data-stu-id="6e3f1-165">Debug-Job</span></span>](../Microsoft.PowerShell.Core/Debug-Job.md)

[<span data-ttu-id="6e3f1-166">Get-runs Pace</span><span class="sxs-lookup"><span data-stu-id="6e3f1-166">Get-Runspace</span></span>](Get-Runspace.md)

[<span data-ttu-id="6e3f1-167">Get-Process</span><span class="sxs-lookup"><span data-stu-id="6e3f1-167">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)

[<span data-ttu-id="6e3f1-168">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="6e3f1-168">Enter-PSHostProcess</span></span>](../Microsoft.PowerShell.Core/Enter-PSHostProcess.md)

[<span data-ttu-id="6e3f1-169">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="6e3f1-169">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

