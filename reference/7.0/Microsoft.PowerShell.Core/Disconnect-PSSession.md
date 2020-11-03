---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disconnect-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-PSSession
ms.openlocfilehash: b3ee9ce8f699e66a091a017eb8c1b0c49f1b7636
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251561"
---
# <span data-ttu-id="e20c0-103">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="e20c0-103">Disconnect-PSSession</span></span>

## <span data-ttu-id="e20c0-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e20c0-104">SYNOPSIS</span></span>
<span data-ttu-id="e20c0-105">Verbreekt de verbinding met een sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-105">Disconnects from a session.</span></span>

## <span data-ttu-id="e20c0-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e20c0-106">SYNTAX</span></span>

### <span data-ttu-id="e20c0-107">Sessie (standaard)</span><span class="sxs-lookup"><span data-stu-id="e20c0-107">Session (Default)</span></span>

```
Disconnect-PSSession [-Session] <PSSession[]> [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="e20c0-108">Naam</span><span class="sxs-lookup"><span data-stu-id="e20c0-108">Name</span></span>

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e20c0-109">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e20c0-109">InstanceId</span></span>

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e20c0-110">Id</span><span class="sxs-lookup"><span data-stu-id="e20c0-110">Id</span></span>

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e20c0-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e20c0-111">DESCRIPTION</span></span>

<span data-ttu-id="e20c0-112">De `Disconnect-PSSession` cmdlet verbreekt de verbinding met een Power shell-sessie ("PSSession"), zoals een start met behulp `New-PSSession` van de cmdlet, vanuit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-112">The `Disconnect-PSSession` cmdlet disconnects a PowerShell session ("PSSession"), such as one started by using the `New-PSSession` cmdlet, from the current session.</span></span> <span data-ttu-id="e20c0-113">Als gevolg hiervan is de PSSession de status niet verbonden.</span><span class="sxs-lookup"><span data-stu-id="e20c0-113">As a result, the PSSession is in a disconnected state.</span></span> <span data-ttu-id="e20c0-114">U kunt verbinding maken met de losgekoppelde PSSession van de huidige sessie of van een andere sessie op de lokale computer of een andere computer.</span><span class="sxs-lookup"><span data-stu-id="e20c0-114">You can connect to the disconnected PSSession from the current session or from another session on the local computer or a different computer.</span></span>

<span data-ttu-id="e20c0-115">De `Disconnect-PSSession` cmdlet verbreekt alleen open PSSessions die zijn verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-115">The `Disconnect-PSSession` cmdlet disconnects only open PSSessions that are connected to the current session.</span></span> <span data-ttu-id="e20c0-116">`Disconnect-PSSession` kan geen verbinding met een verbroken of gesloten PSSessions of interactieve PSSessions is gestart met de `Enter-PSSession` cmdlet en de verbinding met de PSSessions die is verbonden met andere sessies, kan niet worden verbroken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-116">`Disconnect-PSSession` cannot disconnect broken or closed PSSessions, or interactive PSSessions started by using the `Enter-PSSession` cmdlet, and it cannot disconnect PSSessions that are connected to other sessions.</span></span>

<span data-ttu-id="e20c0-117">Als u opnieuw verbinding wilt maken met een niet-verbonden PSSession, gebruikt u de `Connect-PSSession` `Receive-PSSession` cmdlets of.</span><span class="sxs-lookup"><span data-stu-id="e20c0-117">To reconnect to a disconnected PSSession, use the `Connect-PSSession` or `Receive-PSSession` cmdlets.</span></span>

<span data-ttu-id="e20c0-118">Wanneer een PSSession wordt losgekoppeld, worden de opdrachten in de PSSession uitgevoerd totdat ze zijn voltooid, tenzij de PSSession een time-out heeft of de opdrachten in de PSSession worden geblokkeerd door een volledige uitvoer buffer.</span><span class="sxs-lookup"><span data-stu-id="e20c0-118">When a PSSession is disconnected, the commands in the PSSession continue to run until they complete, unless the PSSession times out or the commands in the PSSession are blocked by a full output buffer.</span></span> <span data-ttu-id="e20c0-119">Als u de time-out voor inactiviteit wilt wijzigen, gebruikt u de para meter **IdleTimeoutSec** .</span><span class="sxs-lookup"><span data-stu-id="e20c0-119">To change the idle timeout, use the **IdleTimeoutSec** parameter.</span></span> <span data-ttu-id="e20c0-120">Als u de uitvoer buffer modus wilt wijzigen, gebruikt u de para meter **OutputBufferingMode** u kunt ook de para meter **InDisconnectedSession** van de `Invoke-Command` cmdlet gebruiken om een opdracht uit te voeren in een niet-verbonden sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-120">To change the output buffering mode, use the **OutputBufferingMode** parameter You can also use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet to run a command in a disconnected session.</span></span>

<span data-ttu-id="e20c0-121">Zie [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)voor meer informatie over de functie voor verbroken sessies.</span><span class="sxs-lookup"><span data-stu-id="e20c0-121">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="e20c0-122">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e20c0-122">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="e20c0-123">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e20c0-123">EXAMPLES</span></span>

### <span data-ttu-id="e20c0-124">Voor beeld 1: een sessie verbreken op naam</span><span class="sxs-lookup"><span data-stu-id="e20c0-124">Example 1 - Disconnect a session by name</span></span>

<span data-ttu-id="e20c0-125">Met deze opdracht wordt de verbinding van de UpdateSession PSSession op de Server01-computer met de huidige sessie verbroken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-125">This command disconnects the UpdateSession PSSession on the Server01 computer from the current session.</span></span> <span data-ttu-id="e20c0-126">De opdracht gebruikt de para meter **name** om de PSSession te identificeren.</span><span class="sxs-lookup"><span data-stu-id="e20c0-126">The command uses the **Name** parameter to identify the PSSession.</span></span>

```
PS> Disconnect-PSSession -Name UpdateSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  UpdateSession   Server01        Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="e20c0-127">De uitvoer laat zien dat de poging om de verbinding te verbreken is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="e20c0-127">The output shows that the attempt to disconnect was successful.</span></span> <span data-ttu-id="e20c0-128">De sessie status is ontkoppeld en de beschik baarheid is geen, wat aangeeft dat de sessie niet bezet is en opnieuw verbinding kan maken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-128">The session state is Disconnected and the Availability is None, which indicates that the session is not busy and can be reconnected.</span></span>

### <span data-ttu-id="e20c0-129">Voor beeld 2: een sessie van een specifieke computer verbreken</span><span class="sxs-lookup"><span data-stu-id="e20c0-129">Example 2 - Disconnect a session from a specific computer</span></span>

<span data-ttu-id="e20c0-130">Met deze opdracht wordt de verbinding van de ITTask PSSession op de Server12-computer met de huidige sessie verbroken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-130">This command disconnects the ITTask PSSession on the Server12 computer from the current session.</span></span>
<span data-ttu-id="e20c0-131">De ITTask-sessie is gemaakt in de huidige sessie en maakt verbinding met de Server12-computer.</span><span class="sxs-lookup"><span data-stu-id="e20c0-131">The ITTask session was created in the current session and connects to the Server12 computer.</span></span> <span data-ttu-id="e20c0-132">De opdracht gebruikt de `Get-PSSession` cmdlet om de sessie en de `Disconnect-PSSession` cmdlet te verkrijgen om deze te verbreken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-132">The command uses the `Get-PSSession` cmdlet to get the session and the `Disconnect-PSSession` cmdlet to disconnect it.</span></span>

```
PS> Get-PSSession -ComputerName Server12 -Name ITTask |
  Disconnect-PSSession -OutputBufferingMode Drop -IdleTimeoutSec 86400
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  ITTask          Server12        Disconnected  ITTasks               None
```

<span data-ttu-id="e20c0-133">De `Disconnect-PSSession` opdracht gebruikt de para meter **OutputBufferingMode** om de uitvoer modus in te stellen op **neerzetten**.</span><span class="sxs-lookup"><span data-stu-id="e20c0-133">The `Disconnect-PSSession` command uses the **OutputBufferingMode** parameter to set the output mode to **Drop**.</span></span> <span data-ttu-id="e20c0-134">Deze instelling zorgt ervoor dat het script dat wordt uitgevoerd in de sessie, zelfs kan blijven worden uitgevoerd als de buffer voor de sessie-uitvoer vol is.</span><span class="sxs-lookup"><span data-stu-id="e20c0-134">This setting ensures that the script that is running in the session can continue to run even if the session output buffer is full.</span></span> <span data-ttu-id="e20c0-135">Omdat de uitvoer van het script naar een rapport op een bestands share wordt geschreven, kan een andere uitvoer zonder enige consequentie verloren gaan.</span><span class="sxs-lookup"><span data-stu-id="e20c0-135">Because the script writes its output to a report on a file share, other output can be lost without consequence.</span></span>

<span data-ttu-id="e20c0-136">De opdracht gebruikt ook de para meter **IdleTimeoutSec** om de time-out voor inactiviteit van de sessie tot 24 uur uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="e20c0-136">The command also uses the **IdleTimeoutSec** parameter to extend the idle timeout of the session to 24 hours.</span></span> <span data-ttu-id="e20c0-137">Deze instelling zorgt ervoor dat deze beheerder of andere beheerders opnieuw verbinding maken met de sessie om te controleren of het script is uitgevoerd en zo nodig problemen kan oplossen.</span><span class="sxs-lookup"><span data-stu-id="e20c0-137">This setting allows time for this administrator or other administrators to reconnect to the session to verify that the script ran and troubleshoot if needed.</span></span>

### <span data-ttu-id="e20c0-138">Voor beeld 3: meerdere PSSessions gebruiken op meerdere computers</span><span class="sxs-lookup"><span data-stu-id="e20c0-138">Example 3 - Using multiple PSSessions on multiple computers</span></span>

<span data-ttu-id="e20c0-139">In deze reeks opdrachten ziet u hoe de `Disconnect-PSSession` cmdlet kan worden gebruikt in een bedrijfs scenario.</span><span class="sxs-lookup"><span data-stu-id="e20c0-139">This series of commands shows how the `Disconnect-PSSession` cmdlet might be used in an enterprise scenario.</span></span> <span data-ttu-id="e20c0-140">In dit geval start een nieuwe technicus een script in een sessie op een externe computer en wordt er een probleem opgetreden.</span><span class="sxs-lookup"><span data-stu-id="e20c0-140">In this case, a new technician starts a script in a session on a remote computer and runs into a problem.</span></span> <span data-ttu-id="e20c0-141">De technicus verbreekt de verbinding met de sessie, zodat een ervaren manager verbinding kan maken met de sessie en het probleem kan oplossen.</span><span class="sxs-lookup"><span data-stu-id="e20c0-141">The technician disconnects from the session so that a more experienced manager can connect to the session and resolve the problem.</span></span>

```
PS> $s = New-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
PS> Invoke-Command $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Get-PSSession -Name ITTask -ComputerName Srv1 | Disconnect-PSSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1 ITTask           Srv1            Disconnected  Microsoft.PowerShell          None

PS> Get-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None
 2 ITTask          Srv2            Opened        Microsoft.PowerShell     Available
 3 ITTask          Srv30           Opened        Microsoft.PowerShell     Available

PS> Get-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None

PS> $s = Connect-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
PS> Invoke-Command -Session $s {dir $home\Scripts\PatchStatusOutput.ps1}
PS> Invoke-Command -Session $s {mkdir $home\Scripts\PatchStatusOutput}
PS> Invoke-Command -Session $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Disconnect-PSSession -Session $s
```

<span data-ttu-id="e20c0-142">De technicus begint met het maken van sessies op verschillende externe computers en het uitvoeren van een script in elke sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-142">The technician begins by creating sessions on several remote computers and running a script in each session.</span></span> <span data-ttu-id="e20c0-143">De eerste opdracht gebruikt de `New-PSSession` cmdlet om de ITTask-sessie op drie externe computers te maken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-143">The first command uses the `New-PSSession` cmdlet to create the ITTask session on three remote computers.</span></span> <span data-ttu-id="e20c0-144">De-opdracht slaat de sessies op in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="e20c0-144">The command saves the sessions in the $s variable.</span></span> <span data-ttu-id="e20c0-145">De tweede opdracht gebruikt de **filepath** -para meter van de `Invoke-Command` cmdlet om een script uit te voeren in de sessies in de $s variabele.</span><span class="sxs-lookup"><span data-stu-id="e20c0-145">The second command uses the **FilePath** parameter of the `Invoke-Command` cmdlet to run a script in the sessions in the $s variable.</span></span>

<span data-ttu-id="e20c0-146">Het script dat wordt uitgevoerd op de Srv1-computer genereert onverwachte fouten.</span><span class="sxs-lookup"><span data-stu-id="e20c0-146">The script running on the Srv1 computer generates unexpected errors.</span></span> <span data-ttu-id="e20c0-147">De technicus neemt contact op met zijn manager en vraagt om hulp.</span><span class="sxs-lookup"><span data-stu-id="e20c0-147">The technician contacts his manager and asks for assistance.</span></span> <span data-ttu-id="e20c0-148">De Manager geeft de technicus de opdracht om de verbinding met de sessie te verbreken zodat hij deze kan onderzoeken. De tweede opdracht gebruikt de `Get-PSSession` cmdlet om de ITTask-sessie op de Srv1-computer op te halen en de `Disconnect-PSSession` cmdlet om deze te verbreken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-148">The manager directs the technician to disconnect from the session so he can investigate.The second command uses the `Get-PSSession` cmdlet to get the ITTask session on the Srv1 computer and the `Disconnect-PSSession` cmdlet to disconnect it.</span></span> <span data-ttu-id="e20c0-149">Deze opdracht heeft geen invloed op de ITTask-sessies op de andere computers.</span><span class="sxs-lookup"><span data-stu-id="e20c0-149">This command does not affect the ITTask sessions on the other computers.</span></span>

<span data-ttu-id="e20c0-150">De derde opdracht gebruikt de `Get-PSSession` cmdlet om de ITTask-sessies op te halen.</span><span class="sxs-lookup"><span data-stu-id="e20c0-150">The third command uses the `Get-PSSession` cmdlet to get the ITTask sessions.</span></span> <span data-ttu-id="e20c0-151">De uitvoer laat zien dat de ITTask-sessies op de Srv2-en Srv30-computers niet worden beïnvloed door de opdracht om de verbinding te verbreken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-151">The output shows that the ITTask sessions on the Srv2 and Srv30 computers were not affected by the command to disconnect.</span></span>

<span data-ttu-id="e20c0-152">De Manager meldt zich aan bij zijn thuis computer, maakt verbinding met zijn bedrijfs netwerk, start Power shell en gebruikt de `Get-PSSession` cmdlet om de ITTask-sessie op de Srv1-computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="e20c0-152">The manager logs on to his home computer, connects to his corporate network, starts PowerShell, and uses the `Get-PSSession` cmdlet to get the ITTask session on the Srv1 computer.</span></span> <span data-ttu-id="e20c0-153">Hij gebruikt de referenties van de technicus om toegang te krijgen tot de sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-153">He uses the credentials of the technician to access the session.</span></span>

<span data-ttu-id="e20c0-154">Vervolgens gebruikt de Manager de `Connect-PSSession` cmdlet om verbinding te maken met de ITTask-sessie op de Srv1-computer.</span><span class="sxs-lookup"><span data-stu-id="e20c0-154">Next, the manager uses the `Connect-PSSession` cmdlet to connect to the ITTask session on the Srv1 computer.</span></span> <span data-ttu-id="e20c0-155">Met de opdracht wordt de sessie opgeslagen in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="e20c0-155">The command saves the session in the $s variable.</span></span>

<span data-ttu-id="e20c0-156">De Manager gebruikt de `Invoke-Command` cmdlet om enkele diagnostische opdrachten uit te voeren in de sessie in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="e20c0-156">The manager uses the `Invoke-Command` cmdlet to run some diagnostic commands in the session in the `$s` variable.</span></span> <span data-ttu-id="e20c0-157">Hij erkent dat het script is mislukt omdat het geen vereiste map heeft gevonden.</span><span class="sxs-lookup"><span data-stu-id="e20c0-157">He recognizes that the script failed because it did not find a required directory.</span></span>
<span data-ttu-id="e20c0-158">De Manager gebruikt de `MkDir` functie om de map te maken en vervolgens wordt het script opnieuw gestart `Get-PatchStatus.ps1` en wordt de verbinding met de sessie verbroken. De manager rapporteert zijn bevindingen aan de technicus, stelt voor dat hij opnieuw verbinding maakt met de sessie voor het volt ooien van de taken en vraagt hem een opdracht toe te voegen aan het `Get-PatchStatus.ps1` script waarmee de vereiste map wordt gemaakt als deze niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="e20c0-158">The manager uses the `MkDir` function to create the directory, and then he restarts the `Get-PatchStatus.ps1` script and disconnects from the session.The manager reports his findings to the technician, suggests that he reconnect to the session to complete the tasks, and asks him to add a command to the `Get-PatchStatus.ps1` script that creates the required directory if it does not exist.</span></span>

### <span data-ttu-id="e20c0-159">Voor beeld 4: de time-outwaarde voor een PSSession wijzigen</span><span class="sxs-lookup"><span data-stu-id="e20c0-159">Example 4 - Change the timeout value for a PSSession</span></span>

<span data-ttu-id="e20c0-160">In dit voor beeld ziet u hoe u de waarde van de eigenschap **IdleTimeout** van een sessie kunt corrigeren zodat deze kan worden losgekoppeld.</span><span class="sxs-lookup"><span data-stu-id="e20c0-160">This example shows how to correct the value of the **IdleTimeout** property of a session so that it can be disconnected.</span></span>

<span data-ttu-id="e20c0-161">De eigenschap time-out voor inactiviteit van een sessie is essentieel voor verbroken sessies, omdat deze bepaalt hoe lang een verbroken sessie wordt behouden voordat deze wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="e20c0-161">The idle timeout property of a session is critical to disconnected sessions, because it determines how long a disconnected session is maintained before it is deleted.</span></span> <span data-ttu-id="e20c0-162">U kunt de optie time-out voor inactiviteit instellen wanneer u een sessie maakt en wanneer u de verbinding verbreekt.</span><span class="sxs-lookup"><span data-stu-id="e20c0-162">You can set the idle timeout option when you create a session and when you disconnect it.</span></span> <span data-ttu-id="e20c0-163">De standaard waarden voor de time-out voor inactiviteit van een sessie worden ingesteld in de `$PSSessionOption` Voorkeurs variabele op de lokale computer en in de sessie configuratie op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="e20c0-163">The default values for the idle timeout of a session are set in the `$PSSessionOption` preference variable on the local computer and in the session configuration on the remote computer.</span></span> <span data-ttu-id="e20c0-164">De waarden die voor de sessie zijn ingesteld, hebben voor rang op de waarden die zijn ingesteld in de sessie configuratie, maar sessie waarden mogen niet groter zijn dan de quota die zijn ingesteld in de sessie configuratie, zoals de **MaxIdleTimeoutMs** -waarde.</span><span class="sxs-lookup"><span data-stu-id="e20c0-164">Values set for the session take precedence over values set in the session configuration, but session values cannot exceed quotas set in the session configuration, such as the **MaxIdleTimeoutMs** value.</span></span>

```
PS> $Timeout = New-PSSessionOption -IdleTimeout 172800000
PS> $s = New-PSSession -Computer Server01 -Name ITTask -SessionOption $Timeout
PS> Disconnect-PSSession -Session $s
Disconnect-PSSession : The session ITTask cannot be disconnected because the specified
idle timeout value 172800(seconds) is either greater than the server maximum allowed
43200 (seconds) or less that the minimum allowed60(seconds).  Choose an idle time out
value that is within the allowed range and try again.

PS> Invoke-Command -ComputerName Server01 {Get-PSSessionConfiguration Microsoft.PowerShell} |
 Format-List -Property *

Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/microsoft.powershell
MaxConcurrentCommandsPerShell : 1000
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
SecurityDescriptorSddl        : O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GXGW;;;WD)
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 2147483647
Uri                           : http://schemas.microsoft.com/powershell/microsoft.powershell
SDKVersion                    : 2
Name                          : microsoft.powershell
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
ParentResourceUri             : http://schemas.microsoft.com/powershell/microsoft.powershell
Enabled                       : true
MaxShells                     : 25
MaxShellsPerUser              : 25
Permission                    : BUILTIN\Administrators AccessAllowed
PSComputerName                : localhost
RunspaceId                    : aea84310-6dbf-4c21-90ac-13980039925a
PSShowComputerName            : True


PS> $s.Runspace.ConnectionInfo
ConnectionUri                     : http://Server01/wsman
ComputerName                      : Server01
Scheme                            : http
Port                              : 80
AppName                           : /wsman
Credential                        :
ShellUri                          : http://schemas.microsoft.com/powershell/Microsoft.PowerShell
AuthenticationMechanism           : Default
CertificateThumbprint             :
MaximumConnectionRedirectionCount : 5
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
UseCompression                    : True
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
NoEncryption                      : False
UseUTF16                          : False
OutputBufferingMode               : Drop
IncludePortInSPN                  : False
Culture                           : en-US
UICulture                         : en-US
OpenTimeout                       : 180000
CancelTimeout                     : 60000
OperationTimeout                  : 180000
IdleTimeout                       : 172800000

PS> Disconnect-PSSession $s -IdleTimeoutSec 43200
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Disconnected  Microsoft.PowerShell          None

PS> $s.Runspace.ConnectionInfo.IdleTimeout
43200000
```

<span data-ttu-id="e20c0-165">De eerste opdracht maakt gebruik van de `New-PSSessionOption` cmdlet om een sessie optie object te maken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-165">The first command uses the `New-PSSessionOption` cmdlet to create a session option object.</span></span> <span data-ttu-id="e20c0-166">De para meter **IdleTimeout** wordt gebruikt om een time-out van 48 uur (172800000 milliseconden) in te stellen.</span><span class="sxs-lookup"><span data-stu-id="e20c0-166">It uses the **IdleTimeout** parameter to set an idle timeout of 48 hours (172800000 milliseconds).</span></span> <span data-ttu-id="e20c0-167">Met de opdracht slaat u het sessie optie object op in de variabele $Timeout.</span><span class="sxs-lookup"><span data-stu-id="e20c0-167">The command saves the session option object in the $Timeout variable.</span></span>

<span data-ttu-id="e20c0-168">De tweede opdracht gebruikt de `New-PSSession` cmdlet om de ITTask-sessie te maken op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="e20c0-168">The second command uses the `New-PSSession` cmdlet to create the ITTask session on the Server01 computer.</span></span> <span data-ttu-id="e20c0-169">Met de opdracht wordt de sessie in de $s variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="e20c0-169">The command save the session in the $s variable.</span></span> <span data-ttu-id="e20c0-170">De waarde van de para meter **SessionOption** is de time-out van 48 uur in de variabele $timeout.</span><span class="sxs-lookup"><span data-stu-id="e20c0-170">The value of the **SessionOption** parameter is the 48-hour idle timeout in the $Timeout variable.</span></span>

<span data-ttu-id="e20c0-171">Met de derde opdracht wordt de ITTask-sessie in de variabele $s verbroken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-171">The third command disconnects the ITTask session in the $s variable.</span></span> <span data-ttu-id="e20c0-172">De opdracht mislukt omdat de waarde van de time-out voor inactiviteit van de sessie groter is dan de **MaxIdleTimeoutMs** quota in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-172">The command fails because the idle timeout value of the session exceeds the **MaxIdleTimeoutMs** quota in the session configuration.</span></span> <span data-ttu-id="e20c0-173">Omdat de time-out voor inactiviteit niet wordt gebruikt totdat de verbinding met de sessie wordt verbroken, kan deze schending niet worden gedetecteerd wanneer de sessie in gebruik is.</span><span class="sxs-lookup"><span data-stu-id="e20c0-173">Because the idle timeout is not used until the session is disconnected, this violation can go undetected while the session is in use.</span></span>

<span data-ttu-id="e20c0-174">De vierde opdracht gebruikt de `Invoke-Command` cmdlet om een opdracht uit te voeren `Get-PSSessionConfiguration` voor de micro soft. Power shell-sessie configuratie op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="e20c0-174">The fourth command uses the `Invoke-Command` cmdlet to run a `Get-PSSessionConfiguration` command for the Microsoft.PowerShell session configuration on the Server01 computer.</span></span> <span data-ttu-id="e20c0-175">De opdracht gebruikt de `Format-List` cmdlet om alle eigenschappen van de sessie configuratie in een lijst weer te geven. In de uitvoer ziet u dat de eigenschap **MaxIdleTimeoutMS** , waarmee de Maxi maal toegestane **IdleTimeout** -waarde wordt ingesteld voor sessies die gebruikmaken van de sessie configuratie, 43200000 milliseconden (12 uur) is.</span><span class="sxs-lookup"><span data-stu-id="e20c0-175">The command uses the `Format-List` cmdlet to display all properties of the session configuration in a list.The output shows that the **MaxIdleTimeoutMS** property, which establishes the maximum permitted **IdleTimeout** value for sessions that use the session configuration, is 43200000 milliseconds (12 hours).</span></span>

<span data-ttu-id="e20c0-176">De vijfde opdracht haalt de sessie optie waarden van de sessie op in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="e20c0-176">The fifth command gets the session option values of the session in the $s variable.</span></span> <span data-ttu-id="e20c0-177">De waarden van veel sessie opties zijn eigenschappen van de eigenschap **Connection info** van de eigenschap **runs Pace** van de sessie. De uitvoer laat zien dat de waarde van de eigenschap **IdleTimeout** van de sessie 172800000 milliseconden (48 uur) is, wat in strijd is met het **MaxIdleTimeoutMs** -quotum van 12 uur in de sessie configuratie. Als u dit conflict wilt oplossen, kunt u de para meter **configuratiepad** gebruiken om een andere sessie configuratie te selecteren of de para meter **IdleTimeout** gebruiken om de time-out voor de sessie niet actief te maken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-177">The values of many session options are properties of the **ConnectionInfo** property of the **Runspace** property of the session.The output shows that the value of the **IdleTimeout** property of the session is 172800000 milliseconds (48 hours), which violates the **MaxIdleTimeoutMs** quota of 12 hours in the session configuration.To resolve this conflict, you can use the **ConfigurationName** parameter to select a different session configuration or use the **IdleTimeout** parameter to reduce the idle timeout of the session.</span></span>

<span data-ttu-id="e20c0-178">Met de zesde opdracht wordt de sessie verbroken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-178">The sixth command disconnects the session.</span></span> <span data-ttu-id="e20c0-179">De para meter **IdleTimeoutSec** wordt gebruikt om de time-out voor inactiviteit in te stellen op het maximum van 12 uur.</span><span class="sxs-lookup"><span data-stu-id="e20c0-179">It uses the **IdleTimeoutSec** parameter to set the idle timeout to the 12-hour maximum.</span></span>

<span data-ttu-id="e20c0-180">Met de zevende opdracht wordt de waarde van de eigenschap **IdleTimeout** van de niet-verbonden sessie opgehaald, die wordt gemeten in milliseconden.</span><span class="sxs-lookup"><span data-stu-id="e20c0-180">The seventh command gets the value of the **IdleTimeout** property of the disconnected session, which is measured in milliseconds.</span></span> <span data-ttu-id="e20c0-181">De uitvoer bevestigt dat de opdracht is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="e20c0-181">The output confirms that the command was successful.</span></span>

## <span data-ttu-id="e20c0-182">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e20c0-182">PARAMETERS</span></span>

### <span data-ttu-id="e20c0-183">-Id</span><span class="sxs-lookup"><span data-stu-id="e20c0-183">-Id</span></span>

<span data-ttu-id="e20c0-184">Verbreekt de verbinding met sessies met de opgegeven sessie-ID.</span><span class="sxs-lookup"><span data-stu-id="e20c0-184">Disconnects from sessions with the specified session ID.</span></span> <span data-ttu-id="e20c0-185">Typ een of meer Id's (gescheiden door komma's) of gebruik de operator Range (..) om een bereik van Id's op te geven.</span><span class="sxs-lookup"><span data-stu-id="e20c0-185">Type one or more IDs (separated by commas), or use the range operator (..) to specify a range of IDs.</span></span>

<span data-ttu-id="e20c0-186">Als u de ID van een sessie wilt ophalen, gebruikt u de `Get-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e20c0-186">To get the ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="e20c0-187">De exemplaar-ID wordt opgeslagen in de eigenschap **id** van de sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-187">The instance ID is stored in the **ID** property of the session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e20c0-188">-IdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="e20c0-188">-IdleTimeoutSec</span></span>

<span data-ttu-id="e20c0-189">Hiermee wijzigt u de time-outwaarde voor niet-verbonden PSSession.</span><span class="sxs-lookup"><span data-stu-id="e20c0-189">Changes the idle timeout value of the disconnected PSSession.</span></span> <span data-ttu-id="e20c0-190">Voer een waarde in seconden in.</span><span class="sxs-lookup"><span data-stu-id="e20c0-190">Enter a value in seconds.</span></span> <span data-ttu-id="e20c0-191">De minimum waarde is 60 (1 minuut).</span><span class="sxs-lookup"><span data-stu-id="e20c0-191">The minimum value is 60 (1 minute).</span></span>

<span data-ttu-id="e20c0-192">De time-out voor inactiviteit bepaalt hoe lang de losgekoppelde PSSession op de externe computer wordt onderhouden.</span><span class="sxs-lookup"><span data-stu-id="e20c0-192">The idle timeout determines how long the disconnected PSSession is maintained on the remote computer.</span></span> <span data-ttu-id="e20c0-193">Wanneer de time-out is verlopen, wordt het PSSession verwijderd.</span><span class="sxs-lookup"><span data-stu-id="e20c0-193">When the timeout expires, the PSSession is deleted.</span></span>

<span data-ttu-id="e20c0-194">Ontkoppelde PSSessions worden beschouwd als niet-actief vanaf het moment dat ze worden losgekoppeld, zelfs als opdrachten worden uitgevoerd in de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-194">Disconnected PSSessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

<span data-ttu-id="e20c0-195">De standaard waarde voor de time-out voor inactiviteit van een sessie wordt ingesteld op basis van de waarde van de eigenschap **IdleTimeoutMs** van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-195">The default value for the idle timeout of a session is set by the value of the **IdleTimeoutMs** property of the session configuration.</span></span> <span data-ttu-id="e20c0-196">De standaard waarde is 7200000 milliseconden (2 uur).</span><span class="sxs-lookup"><span data-stu-id="e20c0-196">The default value is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="e20c0-197">De waarde van deze para meter heeft voor rang op de waarde van de eigenschap **IdleTimeout** van de variabele $PSSessionOption voor keur en de standaard waarde voor de time-out voor inactiviteit in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-197">The value of this parameter takes precedence over the value of the **IdleTimeout** property of the $PSSessionOption preference variable and the default idle timeout value in the session configuration.</span></span> <span data-ttu-id="e20c0-198">Deze waarde mag echter niet groter zijn dan de waarde van de eigenschap **MaxIdleTimeoutMs** van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-198">However, this value cannot exceed the value of the **MaxIdleTimeoutMs** property of the session configuration.</span></span> <span data-ttu-id="e20c0-199">De standaard waarde van **MaxIdleTimeoutMs** is 12 uur (43200000 milliseconden).</span><span class="sxs-lookup"><span data-stu-id="e20c0-199">The default value of **MaxIdleTimeoutMs** is 12 hours (43200000 milliseconds).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e20c0-200">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="e20c0-200">-InstanceId</span></span>

<span data-ttu-id="e20c0-201">Verbreekt de verbinding met sessies met de opgegeven exemplaar-Id's.</span><span class="sxs-lookup"><span data-stu-id="e20c0-201">Disconnects from sessions with the specified instance IDs.</span></span>

<span data-ttu-id="e20c0-202">De exemplaar-ID is een GUID waarmee een sessie op een lokale of externe computer uniek wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="e20c0-202">The instance ID is a GUID that uniquely identifies a session on a local or remote computer.</span></span> <span data-ttu-id="e20c0-203">De exemplaar-ID is uniek, zelfs op meerdere sessies op meerdere computers.</span><span class="sxs-lookup"><span data-stu-id="e20c0-203">The instance ID is unique, even across multiple sessions on multiple computers.</span></span>

<span data-ttu-id="e20c0-204">Als u de exemplaar-ID van een sessie wilt ophalen, gebruikt u de `Get-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e20c0-204">To get the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="e20c0-205">De exemplaar-ID wordt opgeslagen in de eigenschap **InstanceId** van de sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-205">The instance ID is stored in the **InstanceID** property of the session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e20c0-206">-Name</span><span class="sxs-lookup"><span data-stu-id="e20c0-206">-Name</span></span>

<span data-ttu-id="e20c0-207">Verbreekt de verbinding met sessies met de opgegeven beschrijvende namen.</span><span class="sxs-lookup"><span data-stu-id="e20c0-207">Disconnects from sessions with the specified friendly names.</span></span> <span data-ttu-id="e20c0-208">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e20c0-208">Wildcards are permitted.</span></span>

<span data-ttu-id="e20c0-209">Gebruik de cmdlet om de beschrijvende naam van een sessie te verkrijgen `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e20c0-209">To get the friendly name of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="e20c0-210">De beschrijvende naam wordt opgeslagen in de eigenschap **naam** van de sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-210">The friendly name is stored in the **Name** property of the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="e20c0-211">-Sessie</span><span class="sxs-lookup"><span data-stu-id="e20c0-211">-Session</span></span>

<span data-ttu-id="e20c0-212">De verbinding met de opgegeven PSSessions wordt verbroken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-212">Disconnects from the specified PSSessions.</span></span> <span data-ttu-id="e20c0-213">Voer PSSession-objecten in, zoals die worden `New-PSSession` geretourneerd door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e20c0-213">Enter PSSession objects, such as those that the `New-PSSession` cmdlet returns.</span></span> <span data-ttu-id="e20c0-214">U kunt ook een PSSession-object pipeen naar `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e20c0-214">You can also pipe a PSSession object to `Disconnect-PSSession`.</span></span>

<span data-ttu-id="e20c0-215">De `Get-PSSession` cmdlet kan alle PSSessions ophalen die eindigen op een externe computer, waaronder PSSessions die niet zijn verbonden en PSSessions die zijn verbonden met andere sessies op andere computers.</span><span class="sxs-lookup"><span data-stu-id="e20c0-215">The `Get-PSSession` cmdlet can get all PSSessions that terminate at a remote computer, including PSSessions that are disconnected and PSSessions that are connected to other sessions on other computers.</span></span> <span data-ttu-id="e20c0-216">`Disconnect-PSSession` koppelt alleen PSSession die zijn verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-216">`Disconnect-PSSession` disconnects only PSSession that are connected to the current session.</span></span> <span data-ttu-id="e20c0-217">Als u andere PSSessions naar wilt `Disconnect-PSSession` door sluizen, `Disconnect-PSSession` mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="e20c0-217">If you pipe other PSSessions to `Disconnect-PSSession`, the `Disconnect-PSSession` command fails.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e20c0-218">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="e20c0-218">-ThrottleLimit</span></span>

<span data-ttu-id="e20c0-219">Hiermee stelt u de beperkings limiet voor de `Disconnect-PSSession` opdracht in.</span><span class="sxs-lookup"><span data-stu-id="e20c0-219">Sets the throttle limit for the `Disconnect-PSSession` command.</span></span>

<span data-ttu-id="e20c0-220">De beperkings limiet is het maximum aantal gelijktijdige verbindingen dat tot stand kan worden gebracht om deze opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="e20c0-220">The throttle limit is the maximum number of concurrent connections that can be established to run this command.</span></span> <span data-ttu-id="e20c0-221">Als u deze para meter weglaat of een waarde van 0 invoert, wordt de standaard waarde 32 gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e20c0-221">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="e20c0-222">De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="e20c0-222">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e20c0-223">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="e20c0-223">-OutputBufferingMode</span></span>

<span data-ttu-id="e20c0-224">Hiermee wordt bepaald hoe de uitvoer van de opdracht wordt beheerd in de verbroken sessie wanneer de uitvoer buffer vol is.</span><span class="sxs-lookup"><span data-stu-id="e20c0-224">Determines how command output is managed in the disconnected session when the output buffer is full.</span></span> <span data-ttu-id="e20c0-225">De standaard waarde is **blok keren**.</span><span class="sxs-lookup"><span data-stu-id="e20c0-225">The default value is **Block**.</span></span>

<span data-ttu-id="e20c0-226">Als de opdracht in de verbroken sessie uitvoer retourneert en de uitvoer buffer vol is, bepaalt de waarde van deze para meter effectief of de opdracht wordt uitgevoerd wanneer de sessie wordt verbroken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-226">If the command in the disconnected session is returning output and the output buffer fills, the value of this parameter effectively determines whether the command continues to run while the session is disconnected.</span></span> <span data-ttu-id="e20c0-227">De waarde **blok** wordt onderbroken totdat de sessie opnieuw is verbonden.</span><span class="sxs-lookup"><span data-stu-id="e20c0-227">A value of **Block** suspends the command until the session is reconnected.</span></span> <span data-ttu-id="e20c0-228">Met de waarde **Drop** kan de opdracht worden voltooid, hoewel gegevens verloren kunnen gaan.</span><span class="sxs-lookup"><span data-stu-id="e20c0-228">A value of **Drop** allows the command to complete, although data might be lost.</span></span> <span data-ttu-id="e20c0-229">Wanneer u de waarde voor **neerzetten** gebruikt, moet u de uitvoer van de opdracht omleiden naar een bestand op schijf.</span><span class="sxs-lookup"><span data-stu-id="e20c0-229">When using the **Drop** value, redirect the command output to a file on disk.</span></span>

<span data-ttu-id="e20c0-230">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="e20c0-230">Valid values are:</span></span>

- <span data-ttu-id="e20c0-231">**Blok keren** : wanneer de uitvoer buffer vol is, wordt de uitvoering onderbroken totdat de buffer leeg is.</span><span class="sxs-lookup"><span data-stu-id="e20c0-231">**Block** : When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="e20c0-232">**Drop** : de uitvoering wordt voortgezet wanneer de uitvoer buffer vol is.</span><span class="sxs-lookup"><span data-stu-id="e20c0-232">**Drop** : When the output buffer is full, execution continues.</span></span> <span data-ttu-id="e20c0-233">Wanneer er een nieuwe uitvoer wordt opgeslagen, wordt de oudste uitvoer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="e20c0-233">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="e20c0-234">**Geen** : er is geen uitvoer buffer modus opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e20c0-234">**None** : No output buffering mode is specified.</span></span> <span data-ttu-id="e20c0-235">De waarde van de eigenschap **OutputBufferingMode** van de sessie configuratie wordt gebruikt voor de niet-verbonden sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-235">The value of the **OutputBufferingMode** property of the session configuration is used for the disconnected session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Block
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e20c0-236">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e20c0-236">-Confirm</span></span>

<span data-ttu-id="e20c0-237">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e20c0-237">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e20c0-238">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e20c0-238">-WhatIf</span></span>

<span data-ttu-id="e20c0-239">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e20c0-239">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e20c0-240">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e20c0-240">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e20c0-241">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e20c0-241">CommonParameters</span></span>

<span data-ttu-id="e20c0-242">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e20c0-242">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e20c0-243">Zie [about_CommonParameters](./About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-243">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="e20c0-244">INVOER</span><span class="sxs-lookup"><span data-stu-id="e20c0-244">INPUTS</span></span>

### <span data-ttu-id="e20c0-245">System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="e20c0-245">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="e20c0-246">U kunt een sessie door sluizen naar `Disconnect-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e20c0-246">You can pipe a session to `Disconnect-PSSession`.</span></span>

## <span data-ttu-id="e20c0-247">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e20c0-247">OUTPUTS</span></span>

### <span data-ttu-id="e20c0-248">System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="e20c0-248">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="e20c0-249">`Disconnect-PSSession` retourneert een object dat de sessie vertegenwoordigt waarvan de verbinding is verbroken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-249">`Disconnect-PSSession` returns an object that represents the session that it disconnected.</span></span>

## <span data-ttu-id="e20c0-250">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e20c0-250">NOTES</span></span>

- <span data-ttu-id="e20c0-251">De `Disconnect-PSSession` cmdlet werkt alleen als op de lokale en externe computers Power shell 3,0 of hoger wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e20c0-251">The `Disconnect-PSSession` cmdlet works only when the local and remote computers are running PowerShell 3.0 or later.</span></span>
- <span data-ttu-id="e20c0-252">Als u de `Disconnect-PSSession` cmdlet gebruikt voor een niet-verbonden sessie, heeft de opdracht geen effect op de sessie en worden er geen fouten gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="e20c0-252">If you use the `Disconnect-PSSession` cmdlet on a disconnected session, the command has no effect on the session and it does not generate errors.</span></span>
- <span data-ttu-id="e20c0-253">Verbroken loop Back-sessies met interactieve beveiligings tokens (die zijn gemaakt met de para meter **EnableNetworkAccess** ) kunnen alleen opnieuw worden verbonden vanaf de computer waarop de sessie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e20c0-253">Disconnected loopback sessions with interactive security tokens (those created with the **EnableNetworkAccess** parameter) can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="e20c0-254">Met deze beperking wordt de computer beschermd tegen kwaadwillende toegang.</span><span class="sxs-lookup"><span data-stu-id="e20c0-254">This restriction protects the computer from malicious access.</span></span>
- <span data-ttu-id="e20c0-255">Wanneer u een PSSession verbreekt, wordt de sessie status **losgekoppeld** en is de beschik baarheid **geen**.</span><span class="sxs-lookup"><span data-stu-id="e20c0-255">When you disconnect a PSSession, the session state is **Disconnected** and the availability is **None**.</span></span>

  <span data-ttu-id="e20c0-256">De waarde van de eigenschap **State** is relatief ten opzichte van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-256">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="e20c0-257">Als de waarde voor de **verbinding is verbroken** , betekent dit daarom dat de PSSession niet is verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-257">Therefore, a value of **Disconnected** means that the PSSession is not connected to the current session.</span></span> <span data-ttu-id="e20c0-258">Het betekent echter niet dat de PSSession-verbinding met alle sessies is verbroken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-258">However, it does not mean that the PSSession is disconnected from all sessions.</span></span> <span data-ttu-id="e20c0-259">Deze is mogelijk verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-259">It might be connected to a different session.</span></span> <span data-ttu-id="e20c0-260">Gebruik de eigenschap **Beschik baarheid** om te bepalen of u verbinding kunt maken met de sessie of er opnieuw verbinding mee wilt maken.</span><span class="sxs-lookup"><span data-stu-id="e20c0-260">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

  <span data-ttu-id="e20c0-261">Een **beschikbaarheids** waarde van **geen** geeft aan dat u verbinding kunt maken met de sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-261">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="e20c0-262">De waarde **bezet** geeft aan dat u geen verbinding kunt maken met de PSSession omdat deze is verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="e20c0-262">A value of **Busy** indicates that you cannot connect to the PSSession because it is connected to another session.</span></span>

  <span data-ttu-id="e20c0-263">Zie [RunspaceState Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.runspacestate)voor meer informatie over de waarden van de eigenschap **State** van sessies.</span><span class="sxs-lookup"><span data-stu-id="e20c0-263">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>

  <span data-ttu-id="e20c0-264">Zie [RunspaceAvailability Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.runspaceavailability)voor meer informatie over de waarden van de eigenschap **Beschik baarheid** van sessies.</span><span class="sxs-lookup"><span data-stu-id="e20c0-264">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="e20c0-265">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e20c0-265">RELATED LINKS</span></span>

[<span data-ttu-id="e20c0-266">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="e20c0-266">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="e20c0-267">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="e20c0-267">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="e20c0-268">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="e20c0-268">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="e20c0-269">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="e20c0-269">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="e20c0-270">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e20c0-270">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="e20c0-271">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="e20c0-271">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="e20c0-272">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="e20c0-272">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="e20c0-273">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="e20c0-273">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="e20c0-274">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="e20c0-274">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="e20c0-275">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e20c0-275">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="e20c0-276">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="e20c0-276">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="e20c0-277">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="e20c0-277">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="e20c0-278">about_Remote</span><span class="sxs-lookup"><span data-stu-id="e20c0-278">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="e20c0-279">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="e20c0-279">about_Remote_Disconnected_Sessions</span></span>](About/about_Remote_Disconnected_Sessions.md)
