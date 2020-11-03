---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pshostprocess?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSHostProcess
ms.openlocfilehash: 14f6173e318c6abd223ddff85a3694cfaac75c93
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/24/2020
ms.locfileid: "93251675"
---
# <span data-ttu-id="232da-103">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="232da-103">Enter-PSHostProcess</span></span>

## <span data-ttu-id="232da-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="232da-104">SYNOPSIS</span></span>
<span data-ttu-id="232da-105">Hiermee maakt u verbinding met en voert u een interactieve sessie in met een lokaal proces.</span><span class="sxs-lookup"><span data-stu-id="232da-105">Connects to and enters into an interactive session with a local process.</span></span>

## <span data-ttu-id="232da-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="232da-106">SYNTAX</span></span>

### <span data-ttu-id="232da-107">ProcessIdParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="232da-107">ProcessIdParameterSet (Default)</span></span>

```
Enter-PSHostProcess [-Id] <Int32> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="232da-108">ProcessParameterSet</span><span class="sxs-lookup"><span data-stu-id="232da-108">ProcessParameterSet</span></span>

```
Enter-PSHostProcess [-Process] <Process> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="232da-109">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="232da-109">ProcessNameParameterSet</span></span>

```
Enter-PSHostProcess [-Name] <String> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="232da-110">PSHostProcessInfoParameterSet</span><span class="sxs-lookup"><span data-stu-id="232da-110">PSHostProcessInfoParameterSet</span></span>

```
Enter-PSHostProcess [-HostProcessInfo] <PSHostProcessInfo> [[-AppDomainName] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="232da-111">PipeNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="232da-111">PipeNameParameterSet</span></span>

```
Enter-PSHostProcess -CustomPipeName <String> [<CommonParameters>]
```

## <span data-ttu-id="232da-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="232da-112">DESCRIPTION</span></span>

<span data-ttu-id="232da-113">`Enter-PSHostProcess`Met de cmdlet maakt u verbinding met en voert u een interactieve sessie in met een lokaal proces.</span><span class="sxs-lookup"><span data-stu-id="232da-113">The `Enter-PSHostProcess` cmdlet connects to and enters into an interactive session with a local process.</span></span> <span data-ttu-id="232da-114">Vanaf Power shell 6,2 wordt deze cmdlet ondersteund op niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="232da-114">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

<span data-ttu-id="232da-115">In plaats van een nieuw proces te maken voor het hosten van Power shell en het uitvoeren van een externe sessie, wordt de externe, interactieve sessie uitgevoerd in een bestaand proces dat Power shell al uitvoert.</span><span class="sxs-lookup"><span data-stu-id="232da-115">Instead of creating a new process to host PowerShell and run a remote session, the remote, interactive session is run in an existing process that is already running PowerShell.</span></span> <span data-ttu-id="232da-116">Wanneer u met een externe sessie op een opgegeven proces werkt, kunt u het uitvoeren van runspaces opsommen en vervolgens een runs Pace voor fout opsporing selecteren door ofwel of toe te voeren `Debug-Runspace` `Enable-RunspaceDebug` .</span><span class="sxs-lookup"><span data-stu-id="232da-116">When you are interacting with a remote session on a specified process, you can enumerate running runspaces, and then select a runspace to debug by running either `Debug-Runspace` or `Enable-RunspaceDebug`.</span></span>

<span data-ttu-id="232da-117">Het proces dat u wilt invoeren, moet de Power shell (System.Management.Automation.dll) hosten.</span><span class="sxs-lookup"><span data-stu-id="232da-117">The process that you want to enter must be hosting PowerShell (System.Management.Automation.dll).</span></span>
<span data-ttu-id="232da-118">U moet lid zijn van de groep Administrators op de computer waarop het proces is gevonden, of u moet de gebruiker zijn die het script uitvoert waarmee het proces is gestart.</span><span class="sxs-lookup"><span data-stu-id="232da-118">You must be either a member of the Administrators group on the computer on which the process is found, or you must be the user who is running the script that started the process.</span></span>

<span data-ttu-id="232da-119">Nadat u een runs Pace hebt geselecteerd om fouten op te sporen, wordt een sessie voor fout opsporing op afstand geopend voor de runs Pace als dit op dit moment een opdracht wordt uitgevoerd of wordt gestopt in het fout opsporingsprogramma.</span><span class="sxs-lookup"><span data-stu-id="232da-119">After you have selected a runspace to debug, a remote debug session is opened for the runspace if it is either currently running a command or is stopped in the debugger.</span></span> <span data-ttu-id="232da-120">U kunt vervolgens fouten opsporen in het runs Pace-script op dezelfde manier als u fouten opspoort voor andere externe sessie scripts.</span><span class="sxs-lookup"><span data-stu-id="232da-120">You can then debug the runspace script in the same way you would debug other remote session scripts.</span></span>

<span data-ttu-id="232da-121">Loskoppelen van een foutopsporingssessie en vervolgens de interactieve sessie met het proces, door twee keer af te sluiten of de uitvoering van het script te stoppen door de bestaande opdracht debug afsluiten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="232da-121">Detach from a debugging session, and then the interactive session with the process, by running exit twice, or stop script execution by running the existing debugger quit command.</span></span>

<span data-ttu-id="232da-122">Als u een proces opgeeft met de para meter **name** en er slechts één proces met de opgegeven naam wordt gevonden, wordt het proces ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="232da-122">If you specify a process by using the **Name** parameter, and there is only one process found with the specified name, the process is entered.</span></span> <span data-ttu-id="232da-123">Als er meer dan één proces met de opgegeven naam wordt gevonden, retourneert Power shell een fout en worden alle processen vermeld die met de opgegeven naam zijn gevonden.</span><span class="sxs-lookup"><span data-stu-id="232da-123">If more than one process with the specified name is found, PowerShell returns an error, and lists all processes found with the specified name.</span></span>

<span data-ttu-id="232da-124">Ter ondersteuning van het koppelen van processen op externe computers, `Enter-PSHostProcess` wordt de cmdlet ingeschakeld in een opgegeven externe computer, zodat u kunt koppelen aan een lokaal proces binnen een externe Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="232da-124">To support attaching to processes on remote computers, the `Enter-PSHostProcess` cmdlet is enabled in a specified remote computer, so that you can attach to a local process within a remote PowerShell session.</span></span>

## <span data-ttu-id="232da-125">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="232da-125">EXAMPLES</span></span>

### <span data-ttu-id="232da-126">Voor beeld 1: fouten opsporen in een runs Pace binnen het Power shell ISE-proces</span><span class="sxs-lookup"><span data-stu-id="232da-126">Example 1: Start debugging a runspace within the PowerShell ISE process</span></span>

<span data-ttu-id="232da-127">In dit voor beeld voert u `Enter-PSHostProcess` uit vanuit de Power shell-console om het Power shell ISE-proces in te voeren.</span><span class="sxs-lookup"><span data-stu-id="232da-127">In this example, you run `Enter-PSHostProcess` from within the PowerShell console to enter the PowerShell ISE process.</span></span> <span data-ttu-id="232da-128">In de resulterende interactieve sessie kunt u een runs Pace vinden die u wilt debuggen door uit te voeren `Get-Runspace` en vervolgens fouten opsporen in de runs Pace.</span><span class="sxs-lookup"><span data-stu-id="232da-128">In the resulting interactive session, you can find a runspace that you want to debug by running `Get-Runspace`, and then debug the runspace.</span></span>

```
PS C:\> Enter-PSHostProcess -Name powershell_ise
[Process:1520]: PS C:\Test\Documents>

Next, get available runspaces within the process you have entered.
PS C:\> [Process:1520]: PS C:\>  Get-Runspace
Id    Name          InstanceId                               State           Availability
--    -------       -----------                              ------          -------------
1     Runspace1     2d91211d-9cce-42f0-ab0e-71ac258b32b5     Opened          Available
2     Runspace2     a3855043-cb16-424a-a616-685360c3763b     Opened          RemoteDebug
3     MyLocalRS     2236dbd8-2105-4dec-a15a-a27d0bfaacb5     Opened          LocalDebug
4     MyRunspace    771356e9-8c44-4b70-9de5-dd17cb41e48e     Opened          Busy
5     Runspace8     3e517382-a97a-49ba-9c3c-fd21f6664288     Broken          None

The runspace objects returned by Get-Runspace also have a NoteProperty called ScriptStackTrace of
the running command stack, if available.Next, debug runspace ID 4, that is running another user's
long-running script. From the list returned from Get-Runspace, note that the runspace state is
Opened, and Availability is Busy, meaning that the runspace is still running the long-running
script.

PS C:\> [Process:1520]: PS C:\>  (Get-Runspace -Id 4).ScriptStackTrace
Command                    Arguments                           Location
-------                    ---------                           --------
MyModuleWorkflowF1         {}                                  TestNoFile3.psm1: line 6
WFTest1                    {}                                  TestNoFile2.ps1: line 14
TestNoFile2.ps1            {}                                  TestNoFile2.ps1: line 22
<ScriptBlock>              {}                                  <No file>

Start an interactive debugging session with this runspace by running the Debug-Runspace cmdlet.

PS C:\> [Process: 1520]: PS C:\>  Debug-Runspace -Id 4
Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'

At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[Process: 1520]: [RSDBG: 4]: PS C:\> >

After you are finished debugging, allow the script to continue running without the debugger attached
by running the exit debugger command. Alternatively, you can quit the debugger with the q or Stop
commands.

PS C:\> [Process:346]: [RSDBG: 3]: PS C:\> > exit
[Process:1520]: PS C:\>

When you are finished working in the process, exit the process by running the Exit-PSHostProcess
cmdlet. This returns you to the PS C:\> prompt.

PS C:\> [Process:1520]: PS C:\>  Exit-PSHostProcess
PS C:\>
```

## <span data-ttu-id="232da-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="232da-129">PARAMETERS</span></span>

### <span data-ttu-id="232da-130">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="232da-130">-AppDomainName</span></span>

<span data-ttu-id="232da-131">Hiermee geeft u de naam van een toepassings domein waarmee verbinding moet worden gemaakt als u dit weglaat, wordt **DefaultAppDomain** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="232da-131">Specifies an application domain name to connect to if omitted, uses **DefaultAppDomain**.</span></span> <span data-ttu-id="232da-132">Gebruiken `Get-PSHostProcessInfo` om de namen van de toepassings domeinen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="232da-132">Use `Get-PSHostProcessInfo` to display the application domain names.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessIdParameterSet, ProcessParameterSet, ProcessNameParameterSet, PSHostProcessInfoParameterSet
Aliases:

Required: False
Position: 1
Default value: DefaultAppDomain
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="232da-133">-HostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="232da-133">-HostProcessInfo</span></span>

<span data-ttu-id="232da-134">Hiermee geeft u een **PSHostProcessInfo** -object op dat kan worden verbonden met Power shell.</span><span class="sxs-lookup"><span data-stu-id="232da-134">Specifies a **PSHostProcessInfo** object that can be connected to with PowerShell.</span></span> <span data-ttu-id="232da-135">Gebruiken `Get-PSHostProcessInfo` om het object op te halen.</span><span class="sxs-lookup"><span data-stu-id="232da-135">Use `Get-PSHostProcessInfo` to get the object.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSHostProcessInfo
Parameter Sets: PSHostProcessInfoParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="232da-136">-Id</span><span class="sxs-lookup"><span data-stu-id="232da-136">-Id</span></span>

<span data-ttu-id="232da-137">Hiermee geeft u een proces met de proces-ID op.</span><span class="sxs-lookup"><span data-stu-id="232da-137">Specifies a process by the process ID.</span></span> <span data-ttu-id="232da-138">Voer de cmdlet uit om een proces-ID op te halen `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="232da-138">To get a process ID, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="232da-139">-Name</span><span class="sxs-lookup"><span data-stu-id="232da-139">-Name</span></span>

<span data-ttu-id="232da-140">Hiermee geeft u een proces op met de proces naam.</span><span class="sxs-lookup"><span data-stu-id="232da-140">Specifies a process by the process name.</span></span> <span data-ttu-id="232da-141">Voer de cmdlet uit om een proces naam op te halen `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="232da-141">To get a process name, run the `Get-Process` cmdlet.</span></span> <span data-ttu-id="232da-142">U kunt ook proces namen ophalen uit het dialoog venster Eigenschappen van een proces in taak beheer.</span><span class="sxs-lookup"><span data-stu-id="232da-142">You can also get process names from the Properties dialog box of a process in Task Manager.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="232da-143">-Proces</span><span class="sxs-lookup"><span data-stu-id="232da-143">-Process</span></span>

<span data-ttu-id="232da-144">Hiermee geeft u een proces op voor het proces object.</span><span class="sxs-lookup"><span data-stu-id="232da-144">Specifies a process by the process object.</span></span> <span data-ttu-id="232da-145">De eenvoudigste manier om deze para meter te gebruiken is het opslaan van de resultaten van een `Get-Process` opdracht die het proces retourneert dat u in een variabele wilt invoeren, en vervolgens geeft u de variabele op als de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="232da-145">The simplest way to use this parameter is to save the results of a `Get-Process` command that returns process that you want to enter in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Diagnostics.Process
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="232da-146">-CustomPipeName</span><span class="sxs-lookup"><span data-stu-id="232da-146">-CustomPipeName</span></span>

<span data-ttu-id="232da-147">Hiermee wordt de naam van de aangepaste named pipe opgehaald of ingesteld waarmee verbinding moet worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="232da-147">Gets or sets the custom named pipe name to connect to.</span></span> <span data-ttu-id="232da-148">Dit wordt meestal gebruikt in combi natie met `pwsh -CustomPipeName` .</span><span class="sxs-lookup"><span data-stu-id="232da-148">This is usually used in conjunction with `pwsh -CustomPipeName`.</span></span>

<span data-ttu-id="232da-149">Deze para meter is geïntroduceerd in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="232da-149">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.String
Parameter Sets: PipeNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="232da-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="232da-150">CommonParameters</span></span>

<span data-ttu-id="232da-151">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="232da-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="232da-152">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="232da-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="232da-153">INVOER</span><span class="sxs-lookup"><span data-stu-id="232da-153">INPUTS</span></span>

### <span data-ttu-id="232da-154">System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="232da-154">System.Diagnostics.Process</span></span>

## <span data-ttu-id="232da-155">UITVOER</span><span class="sxs-lookup"><span data-stu-id="232da-155">OUTPUTS</span></span>

## <span data-ttu-id="232da-156">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="232da-156">NOTES</span></span>

<span data-ttu-id="232da-157">`Enter-PSHostProcess` kan het proces van de Power shell-sessie niet invoeren waarin de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="232da-157">`Enter-PSHostProcess` cannot enter the process of the PowerShell session in which you are running the command.</span></span> <span data-ttu-id="232da-158">U kunt echter wel het proces van een andere Power shell-sessie invoeren, of een Power shell ISE-sessie die wordt uitgevoerd op hetzelfde moment als de sessie waarin u uitvoert `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="232da-158">You can, however, enter the process of another PowerShell session, or a PowerShell ISE session that is running at the same time as the session in which you are running `Enter-PSHostProcess`.</span></span>

<span data-ttu-id="232da-159">`Enter-PSHostProcess` alleen de processen die Power shell hosten, kunnen worden ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="232da-159">`Enter-PSHostProcess` can enter only those processes that are hosting PowerShell.</span></span> <span data-ttu-id="232da-160">Dat wil zeggen dat ze de Power shell-Engine hebben geladen.</span><span class="sxs-lookup"><span data-stu-id="232da-160">That is, they have loaded the PowerShell engine.</span></span>

<span data-ttu-id="232da-161">Als u een proces wilt afsluiten vanuit het proces, typt u **Exit** en drukt u vervolgens op <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="232da-161">To exit a process from within the process, type **exit** , and then press <kbd>Enter</kbd>.</span></span>

<span data-ttu-id="232da-162">Voorafgaand aan Power shell 7,1 heeft externe toegang via SSH geen ondersteuning voor externe sessies van de tweede hop.</span><span class="sxs-lookup"><span data-stu-id="232da-162">Prior to PowerShell 7.1, remoting over SSH did not support second-hop remote sessions.</span></span> <span data-ttu-id="232da-163">Deze mogelijkheid is beperkt tot sessies met WinRM.</span><span class="sxs-lookup"><span data-stu-id="232da-163">This capability was limited to sessions using WinRM.</span></span> <span data-ttu-id="232da-164">Met Power shell 7,1 kunt `Enter-PSSession` `Enter-PSHostProcess` u binnen elke interactieve externe sessie werken.</span><span class="sxs-lookup"><span data-stu-id="232da-164">PowerShell 7.1 allows `Enter-PSSession` and `Enter-PSHostProcess` to work from within any interactive remote session.</span></span>

## <span data-ttu-id="232da-165">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="232da-165">RELATED LINKS</span></span>

[<span data-ttu-id="232da-166">Afsluiten-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="232da-166">Exit-PSHostProcess</span></span>](Exit-PSHostProcess.md)

[<span data-ttu-id="232da-167">Get-PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="232da-167">Get-PSHostProcessInfo</span></span>](Get-PSHostProcessInfo.md)

