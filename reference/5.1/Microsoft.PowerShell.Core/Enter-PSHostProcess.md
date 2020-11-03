---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pshostprocess?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSHostProcess
ms.openlocfilehash: 56b8cef1911d1365f9568483921bfb49fbc32451
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249969"
---
# <span data-ttu-id="d2ac8-103">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="d2ac8-103">Enter-PSHostProcess</span></span>

## <span data-ttu-id="d2ac8-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d2ac8-104">SYNOPSIS</span></span>
<span data-ttu-id="d2ac8-105">Hiermee maakt u verbinding met en voert u een interactieve sessie in met een lokaal proces.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-105">Connects to and enters into an interactive session with a local process.</span></span>

## <span data-ttu-id="d2ac8-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d2ac8-106">SYNTAX</span></span>

### <span data-ttu-id="d2ac8-107">ProcessIdParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="d2ac8-107">ProcessIdParameterSet (Default)</span></span>

```
Enter-PSHostProcess [-Id] <Int32> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="d2ac8-108">ProcessParameterSet</span><span class="sxs-lookup"><span data-stu-id="d2ac8-108">ProcessParameterSet</span></span>

```
Enter-PSHostProcess [-Process] <Process> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="d2ac8-109">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="d2ac8-109">ProcessNameParameterSet</span></span>

```
Enter-PSHostProcess [-Name] <String> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="d2ac8-110">PSHostProcessInfoParameterSet</span><span class="sxs-lookup"><span data-stu-id="d2ac8-110">PSHostProcessInfoParameterSet</span></span>

```
Enter-PSHostProcess [-HostProcessInfo] <PSHostProcessInfo> [[-AppDomainName] <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="d2ac8-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d2ac8-111">DESCRIPTION</span></span>

<span data-ttu-id="d2ac8-112">`Enter-PSHostProcess`Met de cmdlet maakt u verbinding met en voert u een interactieve sessie in met een lokaal proces.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-112">The `Enter-PSHostProcess` cmdlet connects to and enters into an interactive session with a local process.</span></span>

<span data-ttu-id="d2ac8-113">In plaats van een nieuw proces te maken voor het hosten van Power shell en het uitvoeren van een externe sessie, wordt de externe, interactieve sessie uitgevoerd in een bestaand proces dat Power shell al uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-113">Instead of creating a new process to host PowerShell and run a remote session, the remote, interactive session is run in an existing process that is already running PowerShell.</span></span> <span data-ttu-id="d2ac8-114">Wanneer u met een externe sessie op een opgegeven proces werkt, kunt u het uitvoeren van runspaces opsommen en vervolgens een runs Pace voor fout opsporing selecteren door ofwel of toe te voeren `Debug-Runspace` `Enable-RunspaceDebug` .</span><span class="sxs-lookup"><span data-stu-id="d2ac8-114">When you are interacting with a remote session on a specified process, you can enumerate running runspaces, and then select a runspace to debug by running either `Debug-Runspace` or `Enable-RunspaceDebug`.</span></span>

<span data-ttu-id="d2ac8-115">Het proces dat u wilt invoeren, moet de Power shell (System.Management.Automation.dll) hosten.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-115">The process that you want to enter must be hosting PowerShell (System.Management.Automation.dll).</span></span>
<span data-ttu-id="d2ac8-116">U moet lid zijn van de groep Administrators op de computer waarop het proces is gevonden, of u moet de gebruiker zijn die het script uitvoert waarmee het proces is gestart.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-116">You must be either a member of the Administrators group on the computer on which the process is found, or you must be the user who is running the script that started the process.</span></span>

<span data-ttu-id="d2ac8-117">Nadat u een runs Pace hebt geselecteerd om fouten op te sporen, wordt een sessie voor fout opsporing op afstand geopend voor de runs Pace als dit op dit moment een opdracht wordt uitgevoerd of wordt gestopt in het fout opsporingsprogramma.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-117">After you have selected a runspace to debug, a remote debug session is opened for the runspace if it is either currently running a command or is stopped in the debugger.</span></span> <span data-ttu-id="d2ac8-118">U kunt vervolgens fouten opsporen in het runs Pace-script op dezelfde manier als u fouten opspoort voor andere externe sessie scripts.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-118">You can then debug the runspace script in the same way you would debug other remote session scripts.</span></span>

<span data-ttu-id="d2ac8-119">Loskoppelen van een foutopsporingssessie en vervolgens de interactieve sessie met het proces, door twee keer af te sluiten of de uitvoering van het script te stoppen door de bestaande opdracht debug afsluiten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-119">Detach from a debugging session, and then the interactive session with the process, by running exit twice, or stop script execution by running the existing debugger quit command.</span></span>

<span data-ttu-id="d2ac8-120">Als u een proces opgeeft met de para meter **name** en er slechts één proces met de opgegeven naam wordt gevonden, wordt het proces ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-120">If you specify a process by using the **Name** parameter, and there is only one process found with the specified name, the process is entered.</span></span> <span data-ttu-id="d2ac8-121">Als er meer dan één proces met de opgegeven naam wordt gevonden, retourneert Power shell een fout en worden alle processen vermeld die met de opgegeven naam zijn gevonden.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-121">If more than one process with the specified name is found, PowerShell returns an error, and lists all processes found with the specified name.</span></span>

<span data-ttu-id="d2ac8-122">Ter ondersteuning van het koppelen van processen op externe computers, `Enter-PSHostProcess` wordt de cmdlet ingeschakeld in een opgegeven externe computer, zodat u kunt koppelen aan een lokaal proces binnen een externe Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-122">To support attaching to processes on remote computers, the `Enter-PSHostProcess` cmdlet is enabled in a specified remote computer, so that you can attach to a local process within a remote PowerShell session.</span></span>

## <span data-ttu-id="d2ac8-123">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d2ac8-123">EXAMPLES</span></span>

### <span data-ttu-id="d2ac8-124">Voor beeld 1: fouten opsporen in een runs Pace binnen het Power shell ISE-proces</span><span class="sxs-lookup"><span data-stu-id="d2ac8-124">Example 1: Start debugging a runspace within the PowerShell ISE process</span></span>

<span data-ttu-id="d2ac8-125">In dit voor beeld voert u `Enter-PSHostProcess` uit vanuit de Power shell-console om het Power shell ISE-proces in te voeren.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-125">In this example, you run `Enter-PSHostProcess` from within the PowerShell console to enter the PowerShell ISE process.</span></span> <span data-ttu-id="d2ac8-126">In de resulterende interactieve sessie kunt u een runs Pace vinden die u wilt debuggen door uit te voeren `Get-Runspace` en vervolgens fouten opsporen in de runs Pace.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-126">In the resulting interactive session, you can find a runspace that you want to debug by running `Get-Runspace`, and then debug the runspace.</span></span>

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

## <span data-ttu-id="d2ac8-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d2ac8-127">PARAMETERS</span></span>

### <span data-ttu-id="d2ac8-128">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="d2ac8-128">-AppDomainName</span></span>

<span data-ttu-id="d2ac8-129">Hiermee geeft u de naam van een toepassings domein waarmee verbinding moet worden gemaakt als u dit weglaat, wordt **DefaultAppDomain** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-129">Specifies an application domain name to connect to if omitted, uses **DefaultAppDomain**.</span></span> <span data-ttu-id="d2ac8-130">Gebruiken `Get-PSHostProcessInfo` om de namen van de toepassings domeinen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-130">Use `Get-PSHostProcessInfo` to display the application domain names.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: DefaultAppDomain
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d2ac8-131">-HostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="d2ac8-131">-HostProcessInfo</span></span>

<span data-ttu-id="d2ac8-132">Hiermee geeft u een **PSHostProcessInfo** -object op dat kan worden verbonden met Power shell.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-132">Specifies a **PSHostProcessInfo** object that can be connected to with PowerShell.</span></span> <span data-ttu-id="d2ac8-133">Gebruiken `Get-PSHostProcessInfo` om het object op te halen.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-133">Use `Get-PSHostProcessInfo` to get the object.</span></span>

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

### <span data-ttu-id="d2ac8-134">-Id</span><span class="sxs-lookup"><span data-stu-id="d2ac8-134">-Id</span></span>

<span data-ttu-id="d2ac8-135">Hiermee geeft u een proces met de proces-ID op.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-135">Specifies a process by the process ID.</span></span> <span data-ttu-id="d2ac8-136">Voer de cmdlet uit om een proces-ID op te halen `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="d2ac8-136">To get a process ID, run the `Get-Process` cmdlet.</span></span>

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

### <span data-ttu-id="d2ac8-137">-Name</span><span class="sxs-lookup"><span data-stu-id="d2ac8-137">-Name</span></span>

<span data-ttu-id="d2ac8-138">Hiermee geeft u een proces op met de proces naam.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-138">Specifies a process by the process name.</span></span> <span data-ttu-id="d2ac8-139">Voer de cmdlet uit om een proces naam op te halen `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="d2ac8-139">To get a process name, run the `Get-Process` cmdlet.</span></span> <span data-ttu-id="d2ac8-140">U kunt ook proces namen ophalen uit het dialoog venster Eigenschappen van een proces in taak beheer.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-140">You can also get process names from the Properties dialog box of a process in Task Manager.</span></span>

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

### <span data-ttu-id="d2ac8-141">-Proces</span><span class="sxs-lookup"><span data-stu-id="d2ac8-141">-Process</span></span>

<span data-ttu-id="d2ac8-142">Hiermee geeft u een proces op voor het proces object.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-142">Specifies a process by the process object.</span></span> <span data-ttu-id="d2ac8-143">De eenvoudigste manier om deze para meter te gebruiken is het opslaan van de resultaten van een `Get-Process` opdracht die het proces retourneert dat u in een variabele wilt invoeren, en vervolgens geeft u de variabele op als de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-143">The simplest way to use this parameter is to save the results of a `Get-Process` command that returns process that you want to enter in a variable, and then specify the variable as the value of this parameter.</span></span>

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

### <span data-ttu-id="d2ac8-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d2ac8-144">CommonParameters</span></span>

<span data-ttu-id="d2ac8-145">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d2ac8-146">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d2ac8-147">INVOER</span><span class="sxs-lookup"><span data-stu-id="d2ac8-147">INPUTS</span></span>

### <span data-ttu-id="d2ac8-148">System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="d2ac8-148">System.Diagnostics.Process</span></span>

## <span data-ttu-id="d2ac8-149">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d2ac8-149">OUTPUTS</span></span>

## <span data-ttu-id="d2ac8-150">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d2ac8-150">NOTES</span></span>

<span data-ttu-id="d2ac8-151">`Enter-PSHostProcess` kan het proces van de Power shell-sessie niet invoeren waarin de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-151">`Enter-PSHostProcess` cannot enter the process of the PowerShell session in which you are running the command.</span></span> <span data-ttu-id="d2ac8-152">U kunt echter wel het proces van een andere Power shell-sessie invoeren, of een Power shell ISE-sessie die wordt uitgevoerd op hetzelfde moment als de sessie waarin u uitvoert `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="d2ac8-152">You can, however, enter the process of another PowerShell session, or a PowerShell ISE session that is running at the same time as the session in which you are running `Enter-PSHostProcess`.</span></span>

<span data-ttu-id="d2ac8-153">`Enter-PSHostProcess` alleen de processen die Power shell hosten, kunnen worden ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-153">`Enter-PSHostProcess` can enter only those processes that are hosting PowerShell.</span></span> <span data-ttu-id="d2ac8-154">Dat wil zeggen dat ze de Power shell-Engine hebben geladen.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-154">That is, they have loaded the PowerShell engine.</span></span>

<span data-ttu-id="d2ac8-155">Als u een proces wilt afsluiten vanuit het proces, typt u **Exit** en drukt u vervolgens op <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d2ac8-155">To exit a process from within the process, type **exit** , and then press <kbd>Enter</kbd>.</span></span>

## <span data-ttu-id="d2ac8-156">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d2ac8-156">RELATED LINKS</span></span>

[<span data-ttu-id="d2ac8-157">Afsluiten-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="d2ac8-157">Exit-PSHostProcess</span></span>](Exit-PSHostProcess.md)

[<span data-ttu-id="d2ac8-158">Get-PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="d2ac8-158">Get-PSHostProcessInfo</span></span>](Get-PSHostProcessInfo.md)
