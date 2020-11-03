---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/11/2019
Module Name: Microsoft.PowerShell.Core
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-PSSession
ms.openlocfilehash: 39501e0992ba10ae3638dd5178f2913001b5cd32
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251486"
---
# <span data-ttu-id="f4dba-103">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="f4dba-103">Receive-PSSession</span></span>

## <span data-ttu-id="f4dba-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f4dba-104">SYNOPSIS</span></span>

<span data-ttu-id="f4dba-105">Hiermee worden de resultaten van opdrachten in verbroken sessies opgehaald</span><span class="sxs-lookup"><span data-stu-id="f4dba-105">Gets results of commands in disconnected sessions</span></span>

## <span data-ttu-id="f4dba-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f4dba-106">SYNTAX</span></span>

### <span data-ttu-id="f4dba-107">Sessie (standaard)</span><span class="sxs-lookup"><span data-stu-id="f4dba-107">Session (Default)</span></span>

```
Receive-PSSession [-Session] <PSSession> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f4dba-108">Id</span><span class="sxs-lookup"><span data-stu-id="f4dba-108">Id</span></span>

```
Receive-PSSession [-Id] <Int32> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="f4dba-109">ComputerSessionName</span><span class="sxs-lookup"><span data-stu-id="f4dba-109">ComputerSessionName</span></span>

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f4dba-110">ComputerInstanceId</span><span class="sxs-lookup"><span data-stu-id="f4dba-110">ComputerInstanceId</span></span>

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f4dba-111">ConnectionUriSessionName</span><span class="sxs-lookup"><span data-stu-id="f4dba-111">ConnectionUriSessionName</span></span>

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f4dba-112">ConnectionUriInstanceId</span><span class="sxs-lookup"><span data-stu-id="f4dba-112">ConnectionUriInstanceId</span></span>

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f4dba-113">InstanceId</span><span class="sxs-lookup"><span data-stu-id="f4dba-113">InstanceId</span></span>

```
Receive-PSSession [-InstanceId] <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f4dba-114">Sessie naam</span><span class="sxs-lookup"><span data-stu-id="f4dba-114">SessionName</span></span>

```
Receive-PSSession [-Name] <String> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="f4dba-115">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f4dba-115">DESCRIPTION</span></span>

<span data-ttu-id="f4dba-116">De `Receive-PSSession` cmdlet haalt de resultaten op van de opdrachten die worden uitgevoerd in Power shell-sessies ( **PSSession** ) die zijn losgekoppeld.</span><span class="sxs-lookup"><span data-stu-id="f4dba-116">The `Receive-PSSession` cmdlet gets the results of commands running in PowerShell sessions ( **PSSession** ) that were disconnected.</span></span> <span data-ttu-id="f4dba-117">Als de sessie momenteel is verbonden, worden `Receive-PSSession` de resultaten opgehaald van opdrachten die werden uitgevoerd toen de verbinding met de sessie werd verbroken.</span><span class="sxs-lookup"><span data-stu-id="f4dba-117">If the session is currently connected, `Receive-PSSession` gets the results of commands that were running when the session was disconnected.</span></span> <span data-ttu-id="f4dba-118">Als de sessie nog steeds is verbroken, `Receive-PSSession` maakt verbinding met de sessie, worden alle opdrachten die zijn onderbroken, hervat en worden de resultaten opgehaald van de opdrachten die in de sessie worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-118">If the session is still disconnected, `Receive-PSSession` connects to the session, resumes any commands that were suspended, and gets the results of commands running in the session.</span></span>

<span data-ttu-id="f4dba-119">Deze cmdlet is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f4dba-119">This cmdlet was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="f4dba-120">U kunt een gebruiken `Receive-PSSession` naast of in plaats van een `Connect-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="f4dba-120">You can use a `Receive-PSSession` in addition to or instead of a `Connect-PSSession` command.</span></span>
<span data-ttu-id="f4dba-121">`Receive-PSSession` kan verbinding maken met elke verbroken of opnieuw verbonden sessie die is gestart in andere sessies of op andere computers.</span><span class="sxs-lookup"><span data-stu-id="f4dba-121">`Receive-PSSession` can connect to any disconnected or reconnected session that was started in other sessions or on other computers.</span></span>

<span data-ttu-id="f4dba-122">`Receive-PSSession` werkt op **PSSessions** die opzettelijk zijn losgekoppeld met de `Disconnect-PSSession` cmdlet of de `Invoke-Command` para meter **InDisconnectedSession** .</span><span class="sxs-lookup"><span data-stu-id="f4dba-122">`Receive-PSSession` works on **PSSessions** that were disconnected intentionally using the `Disconnect-PSSession` cmdlet or the `Invoke-Command` **InDisconnectedSession** parameter.</span></span> <span data-ttu-id="f4dba-123">Of de verbinding met een netwerk onderbreking per ongeluk verbroken.</span><span class="sxs-lookup"><span data-stu-id="f4dba-123">Or disconnected unintentionally by a network interruption.</span></span>

<span data-ttu-id="f4dba-124">Als u de `Receive-PSSession` cmdlet gebruikt om verbinding te maken met een sessie waarin geen opdrachten worden uitgevoerd of onderbroken, `Receive-PSSession` maakt verbinding met de sessie, maar worden geen uitvoer of fouten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-124">If you use the `Receive-PSSession` cmdlet to connect to a session in which no commands are running or suspended, `Receive-PSSession` connects to the session, but returns no output or errors.</span></span>

<span data-ttu-id="f4dba-125">Zie [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)voor meer informatie over de functie voor verbroken sessies.</span><span class="sxs-lookup"><span data-stu-id="f4dba-125">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="f4dba-126">Enkele voor beelden gebruiken splatting om de lengte van de lijn te verkleinen en de Lees baarheid te verbeteren.</span><span class="sxs-lookup"><span data-stu-id="f4dba-126">Some examples use splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="f4dba-127">Zie [about_Splatting](./About/about_Splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-127">For more information, see [about_Splatting](./About/about_Splatting.md).</span></span>

## <span data-ttu-id="f4dba-128">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f4dba-128">EXAMPLES</span></span>

### <span data-ttu-id="f4dba-129">Voor beeld 1: verbinding maken met een PSSession</span><span class="sxs-lookup"><span data-stu-id="f4dba-129">Example 1: Connect to a PSSession</span></span>

<span data-ttu-id="f4dba-130">In dit voor beeld wordt verbinding gemaakt met een sessie op een externe computer en worden de resultaten opgehaald van opdrachten die in een sessie worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-130">This example connects to a session on a remote computer and gets the results of commands that are running in a session.</span></span>

```powershell
Receive-PSSession -ComputerName Server01 -Name ITTask
```

<span data-ttu-id="f4dba-131">De `Receive-PSSession` specificeert de externe computer met de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="f4dba-131">The `Receive-PSSession` specifies the remote computer with the **ComputerName** parameter.</span></span> <span data-ttu-id="f4dba-132">De para meter **name** identificeert de ITTask-sessie op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="f4dba-132">The **Name** parameter identifies the ITTask session on the Server01 computer.</span></span> <span data-ttu-id="f4dba-133">In het voor beeld worden de resultaten opgehaald van opdrachten die werden uitgevoerd in de ITTask-sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-133">The example gets the results of commands that were running in the ITTask session.</span></span>

<span data-ttu-id="f4dba-134">Omdat de opdracht geen gebruik maakt van de para meter **outtarget** , worden de resultaten weer gegeven op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="f4dba-134">Because the command doesn't use the **OutTarget** parameter, the results appear on the command line.</span></span>

### <span data-ttu-id="f4dba-135">Voor beeld 2: resultaten van alle opdrachten in sessies zonder verbinding ophalen</span><span class="sxs-lookup"><span data-stu-id="f4dba-135">Example 2: Get results of all commands on disconnected sessions</span></span>

<span data-ttu-id="f4dba-136">In dit voor beeld worden de resultaten opgehaald van alle opdrachten die worden uitgevoerd in alle verbroken sessies op twee externe computers.</span><span class="sxs-lookup"><span data-stu-id="f4dba-136">This example gets the results of all commands running in all disconnected sessions on two remote computers.</span></span>

<span data-ttu-id="f4dba-137">Als een sessie niet is verbroken of als er geen opdrachten worden uitgevoerd, `Receive-PSSession` wordt er geen verbinding met de sessie gemaakt en worden er geen uitvoer of fouten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-137">If any session wasn't disconnected or isn't running commands, `Receive-PSSession` doesn't connect to the session and doesn't return any output or errors.</span></span>

```powershell
Get-PSSession -ComputerName Server01, Server02 | Receive-PSSession
```

<span data-ttu-id="f4dba-138">`Get-PSSession` maakt gebruik van de para meter **ComputerName** om de externe computers op te geven.</span><span class="sxs-lookup"><span data-stu-id="f4dba-138">`Get-PSSession` uses the **ComputerName** parameter to specify the remote computers.</span></span> <span data-ttu-id="f4dba-139">De objecten worden naar beneden verzonden in de pijp lijn `Receive-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f4dba-139">The objects are sent down the pipeline to `Receive-PSSession`.</span></span>

### <span data-ttu-id="f4dba-140">Voor beeld 3: de resultaten ophalen van een script dat wordt uitgevoerd in een sessie</span><span class="sxs-lookup"><span data-stu-id="f4dba-140">Example 3: Get the results of a script running in a session</span></span>

<span data-ttu-id="f4dba-141">In dit voor beeld wordt de `Receive-PSSession` cmdlet gebruikt om de resultaten op te halen van een script dat werd uitgevoerd in de sessie van een externe computer.</span><span class="sxs-lookup"><span data-stu-id="f4dba-141">This example uses the `Receive-PSSession` cmdlet to get the results of a script that was running in a remote computer's session.</span></span>

```powershell
$parms = @{
  ComputerName = "Server01"
  Name = "ITTask"
  OutTarget = "Job"
  JobName = "ITTaskJob01"
  Credential = "Domain01\Admin01"
}
Receive-PSSession @parms
```

```Output
Id     Name            State         HasMoreData     Location
--     ----            -----         -----------     --------
16     ITTaskJob01     Running       True            Server01
```

<span data-ttu-id="f4dba-142">De opdracht maakt gebruik van de para meters **ComputerName** en **name** om de verbroken sessie te identificeren.</span><span class="sxs-lookup"><span data-stu-id="f4dba-142">The command uses the **ComputerName** and **Name** parameters to identify the disconnected session.</span></span>
<span data-ttu-id="f4dba-143">De para meter **outtarget** wordt gebruikt met de waarde taak om `Receive-PSSession` de resultaten te retour neren als een taak.</span><span class="sxs-lookup"><span data-stu-id="f4dba-143">It uses the **OutTarget** parameter with a value of Job to direct `Receive-PSSession` to return the results as a job.</span></span> <span data-ttu-id="f4dba-144">De **JobName** para meter geeft een naam voor de taak in de opnieuw verbonden sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-144">The **JobName** parameter specifies a name for the job in the reconnected session.</span></span>
<span data-ttu-id="f4dba-145">De para meter **Credential** voert de `Receive-PSSession` opdracht uit met de machtigingen van een domein beheerder.</span><span class="sxs-lookup"><span data-stu-id="f4dba-145">The **Credential** parameter runs the `Receive-PSSession` command using the permissions of a domain administrator.</span></span>

<span data-ttu-id="f4dba-146">In de uitvoer ziet u dat `Receive-PSSession` de resultaten als een taak in de huidige sessie zijn geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-146">The output shows that `Receive-PSSession` returned the results as a job in the current session.</span></span> <span data-ttu-id="f4dba-147">Als u de resultaten van de taak wilt weer geven, gebruikt u een `Receive-Job` opdracht</span><span class="sxs-lookup"><span data-stu-id="f4dba-147">To get the job results, use a `Receive-Job` command</span></span>

### <span data-ttu-id="f4dba-148">Voor beeld 4: resultaten ophalen na een storing in het netwerk</span><span class="sxs-lookup"><span data-stu-id="f4dba-148">Example 4: Get results after a network outage</span></span>

<span data-ttu-id="f4dba-149">In dit voor beeld wordt de `Receive-PSSession` cmdlet gebruikt om de resultaten van een taak op te halen nadat een netwerk onderbreking een sessie verbinding verstoort.</span><span class="sxs-lookup"><span data-stu-id="f4dba-149">This example uses the `Receive-PSSession` cmdlet to get the results of a job after a network outage disrupts a session connection.</span></span> <span data-ttu-id="f4dba-150">Power shell probeert automatisch opnieuw verbinding te maken met de sessie per seconde voor de komende vier minuten. de taak wordt alleen uitgevoerd als alle pogingen van het interval van vier minuten mislukken.</span><span class="sxs-lookup"><span data-stu-id="f4dba-150">PowerShell automatically attempts to reconnect the session once per second for the next four minutes and abandons the effort only if all attempts in the four-minute interval fail.</span></span>

```
PS> $s = New-PSSession -ComputerName Server01 -Name AD -ConfigurationName ADEndpoint
PS> $s

Id  Name   ComputerName    State        ConfigurationName     Availability
--  ----   ------------    -----        -----------------     ------------
8   AD      Server01       Opened       ADEndpoint               Available


PS> Invoke-Command -Session $s -FilePath \\Server12\Scripts\SharedScripts\New-ADResolve.ps1

Running "New-ADResolve.ps1"

# Network outage
# Restart local computer
# Network access is not re-established within 4 minutes


PS> Get-PSSession -ComputerName Server01

Id  Name   ComputerName    State          ConfigurationName      Availability
--  ----   ------------    -----          -----------------      ------------
1  Backup  Server01        Disconnected   Microsoft.PowerShell           None
8  AD      Server01        Disconnected   ADEndpoint                     None


PS> Receive-PSSession -ComputerName Server01 -Name AD -OutTarget Job -JobName AD

Job Id   Name      State         HasMoreData     Location
--       ----      -----         -----------     --------
16       ADJob     Running       True            Server01


PS> Get-PSSession -ComputerName Server01

Id  Name    ComputerName    State         ConfigurationName     Availability
--  ----    ------------    -----         -----------------     ------------
1  Backup   Server01        Disconnected  Microsoft.PowerShell          Busy
8  AD       Server01        Opened        ADEndpoint               Available
```

<span data-ttu-id="f4dba-151">Met de `New-PSSession` cmdlet wordt een sessie gemaakt op de Server01-computer en wordt de sessie opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4dba-151">The `New-PSSession` cmdlet creates a session on the Server01 computer and saves the session in the `$s` variable.</span></span> <span data-ttu-id="f4dba-152">De `$s` variabele geeft aan dat de **status** is geopend en de **Beschik baarheid** beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="f4dba-152">The `$s` variable displays that the **State** is Opened and the **Availability** is Available.</span></span> <span data-ttu-id="f4dba-153">Deze waarden geven aan dat u verbonden bent met de sessie en dat er opdrachten kunnen worden uitgevoerd in de sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-153">These values indicate that you're connected to the session and can run commands in the session.</span></span>

<span data-ttu-id="f4dba-154">Met de `Invoke-Command` cmdlet wordt een script uitgevoerd in de sessie in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4dba-154">The `Invoke-Command` cmdlet runs a script in the session in the `$s` variable.</span></span> <span data-ttu-id="f4dba-155">Het script begint met het uitvoeren en retour neren van gegevens, maar er treedt een netwerk storing op waardoor de sessie wordt onderbroken.</span><span class="sxs-lookup"><span data-stu-id="f4dba-155">The script begins to run and return data, but a network outage occurs that interrupts the session.</span></span> <span data-ttu-id="f4dba-156">De gebruiker moet de sessie afsluiten en de lokale computer opnieuw opstarten.</span><span class="sxs-lookup"><span data-stu-id="f4dba-156">The user has to exit the session and restart the local computer.</span></span>

<span data-ttu-id="f4dba-157">Wanneer de computer opnieuw wordt opgestart, start Power shell en voert de gebruiker een `Get-PSSession` opdracht uit om sessies op de Server01-computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="f4dba-157">When the computer restarts, the user starts PowerShell and runs a `Get-PSSession` command to get sessions on the Server01 computer.</span></span> <span data-ttu-id="f4dba-158">In de uitvoer ziet u dat de **ad** -sessie nog bestaat op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="f4dba-158">The output shows that the **AD** session still exists on the Server01 computer.</span></span> <span data-ttu-id="f4dba-159">De **status** geeft aan dat de **ad** -sessie is beëindigd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-159">The **State** indicates that the **AD** session is disconnected.</span></span> <span data-ttu-id="f4dba-160">De **beschikbaarheids** waarde geen, geeft aan dat de sessie niet is verbonden met een client sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-160">The **Availability** value of None, indicates that the session isn't connected to any client sessions.</span></span>

<span data-ttu-id="f4dba-161">`Receive-PSSession`Met de cmdlet wordt opnieuw verbinding gemaakt met de **ad** -sessie en worden de resultaten opgehaald van het script dat is uitgevoerd in de sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-161">The `Receive-PSSession` cmdlet reconnects to the **AD** session and gets the results of the script that ran in the session.</span></span> <span data-ttu-id="f4dba-162">De opdracht gebruikt de para meter **outtarget** om de resultaten aan te vragen in een taak met de naam **ADJob**.</span><span class="sxs-lookup"><span data-stu-id="f4dba-162">The command uses the **OutTarget** parameter to request the results in a job named **ADJob**.</span></span> <span data-ttu-id="f4dba-163">De opdracht retourneert een taak object en de uitvoer geeft aan dat het script nog steeds wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-163">The command returns a job object and the output indicates that the script is still running.</span></span>

<span data-ttu-id="f4dba-164">De `Get-PSSession` cmdlet wordt gebruikt om de taak status te controleren.</span><span class="sxs-lookup"><span data-stu-id="f4dba-164">The `Get-PSSession` cmdlet is used to check the job state.</span></span> <span data-ttu-id="f4dba-165">De uitvoer bevestigt dat de `Receive-PSSession` cmdlet opnieuw is verbonden met de **ad** -sessie, die nu is geopend en beschikbaar is voor-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="f4dba-165">The output confirms that the `Receive-PSSession` cmdlet reconnected to the **AD** session, which is now open and available for commands.</span></span> <span data-ttu-id="f4dba-166">En de uitvoering van het script wordt hervat en de resultaten van het script worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f4dba-166">And, the script resumed execution and is getting the script results.</span></span>

### <span data-ttu-id="f4dba-167">Voor beeld 5: opnieuw verbinding maken met verbroken sessies</span><span class="sxs-lookup"><span data-stu-id="f4dba-167">Example 5: Reconnect to disconnected sessions</span></span>

<span data-ttu-id="f4dba-168">In dit voor beeld wordt de `Receive-PSSession` cmdlet gebruikt om opnieuw verbinding te maken met sessies die opzettelijk zijn losgekoppeld en de resultaten te krijgen van taken die in de sessies werden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-168">This example uses the `Receive-PSSession` cmdlet to reconnect to sessions that were intentionally disconnected and get the results of jobs that were running in the sessions.</span></span>

```
PS> $parms = @{
      InDisconnectedSession = $True
      ComputerName = "Server01", "Server02", "Server30"
      FilePath = "\\Server12\Scripts\SharedScripts\Get-BugStatus.ps1"
      Name = "BugStatus"
      SessionOption = @{IdleTimeout = 86400000}
      ConfigurationName = "ITTasks"
    }
PS> Invoke-Command @parms
PS> Exit


PS> $s = Get-PSSession -ComputerName Server01, Server02, Server30 -Name BugStatus
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Disconnected  ITTasks                       None
8  ITTask  Server02        Disconnected  ITTasks                       None
2  ITTask  Server30        Disconnected  ITTasks                       None


PS> $Results = Receive-PSSession -Session $s
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Opened        ITTasks                  Available
8  ITTask  Server02        Opened        ITTasks                  Available
2  ITTask  Server30        Opened        ITTasks                  Available


PS> $Results

Bug Report - Domain 01
----------------------
ComputerName          BugCount          LastUpdated
--------------        ---------         ------------
Server01              121               Friday, December 30, 2011 5:03:34 PM
```

<span data-ttu-id="f4dba-169">`Invoke-Command`Met de cmdlet wordt een script uitgevoerd op drie externe computers.</span><span class="sxs-lookup"><span data-stu-id="f4dba-169">The `Invoke-Command` cmdlet runs a script on three remote computers.</span></span> <span data-ttu-id="f4dba-170">Omdat in het script gegevens uit meerdere data bases worden verzameld en samenvatten, neemt het script vaak een lange tijd in beslag om te worden voltooid.</span><span class="sxs-lookup"><span data-stu-id="f4dba-170">Because the script gathers and summarizes data from multiple databases, it often takes the script an extended time to finish.</span></span> <span data-ttu-id="f4dba-171">De opdracht maakt gebruik van de para meter **InDisconnectedSession** waarmee de scripts worden gestart. vervolgens wordt de verbinding met de sessies onmiddellijk verbroken.</span><span class="sxs-lookup"><span data-stu-id="f4dba-171">The command uses the **InDisconnectedSession** parameter that starts the scripts and then immediately disconnects the sessions.</span></span> <span data-ttu-id="f4dba-172">De para meter **SessionOption** breidt de waarde **IdleTimeout** van de niet-verbonden sessie uit.</span><span class="sxs-lookup"><span data-stu-id="f4dba-172">The **SessionOption** parameter extends the **IdleTimeout** value of the disconnected session.</span></span> <span data-ttu-id="f4dba-173">Sessies waarbij de verbinding is verbroken, worden niet meer gebruikt vanaf het moment dat de verbinding wordt verbroken.</span><span class="sxs-lookup"><span data-stu-id="f4dba-173">Disconnected sessions are considered idle from the moment they're disconnected.</span></span> <span data-ttu-id="f4dba-174">Het is belang rijk om de time-out voor inactiviteit lang genoeg in te stellen, zodat de opdrachten kunnen worden voltooid en u opnieuw verbinding kunt maken met de sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-174">It's important to set the idle time-out for long enough so that the commands can complete and you can reconnect to the session.</span></span> <span data-ttu-id="f4dba-175">U kunt de **IdleTimeout** alleen instellen wanneer u de **PSSession** maakt en deze alleen wijzigen wanneer u de verbinding verbreekt.</span><span class="sxs-lookup"><span data-stu-id="f4dba-175">You can set the **IdleTimeout** only when you create the **PSSession** and change it only when you disconnect from it.</span></span> <span data-ttu-id="f4dba-176">U kunt de waarde voor **IdleTimeout** niet wijzigen wanneer u verbinding maakt met een **PSSession** of de resultaten ontvangt.</span><span class="sxs-lookup"><span data-stu-id="f4dba-176">You can't change the **IdleTimeout** value when you connect to a **PSSession** or receiving its results.</span></span> <span data-ttu-id="f4dba-177">Na het uitvoeren van de opdracht, sluit de gebruiker Power shell af en sluit de computer.</span><span class="sxs-lookup"><span data-stu-id="f4dba-177">After running the command, the user exits PowerShell and closes the computer.</span></span>

<span data-ttu-id="f4dba-178">De volgende dag, de gebruiker hervat Windows, start Power shell en gebruikt `Get-PSSession` om de sessies te verkrijgen waarin de scripts worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-178">The next day, the user resumes Windows, starts PowerShell, and uses `Get-PSSession` to get the sessions in which the scripts were running.</span></span> <span data-ttu-id="f4dba-179">De opdracht identificeert de sessies op basis van de computer naam, sessie naam en de naam van de sessie configuratie en slaat de sessies op in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4dba-179">The command identifies the sessions by the computer name, session name, and the name of the session configuration and saves the sessions in the `$s` variable.</span></span> <span data-ttu-id="f4dba-180">De waarde van de `$s` variabele wordt weer gegeven en er wordt aangegeven dat de sessies zijn losgekoppeld, maar niet actief.</span><span class="sxs-lookup"><span data-stu-id="f4dba-180">The value of the `$s` variable is displayed and shows that the sessions are disconnected, but aren't busy.</span></span>

<span data-ttu-id="f4dba-181">De `Receive-PSSession` cmdlet maakt verbinding met de sessies in de `$s` variabele en haalt de resultaten op.</span><span class="sxs-lookup"><span data-stu-id="f4dba-181">The `Receive-PSSession` cmdlet connects to the sessions in the `$s` variable and gets their results.</span></span>
<span data-ttu-id="f4dba-182">Met de opdracht worden de resultaten opgeslagen in de `$Results` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4dba-182">The command saves the results in the `$Results` variable.</span></span> <span data-ttu-id="f4dba-183">De `$s` variabele wordt weer gegeven en er wordt aangegeven dat de sessies zijn verbonden en beschikbaar zijn voor opdrachten.</span><span class="sxs-lookup"><span data-stu-id="f4dba-183">The `$s` variable is displayed and shows that the sessions are connected and available for commands.</span></span>

<span data-ttu-id="f4dba-184">De resultaten van het script in de `$Results` variabele worden weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="f4dba-184">The script results in the `$Results` variable are displayed in the PowerShell console.</span></span> <span data-ttu-id="f4dba-185">Als een van de resultaten onverwacht is, kan de gebruiker opdrachten uitvoeren in de sessies om de hoofd oorzaak te onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="f4dba-185">If any of the results are unexpected, the user can run commands in the sessions to investigate the root cause.</span></span>

### <span data-ttu-id="f4dba-186">Voor beeld 6: een taak uitvoeren in een sessie zonder verbinding</span><span class="sxs-lookup"><span data-stu-id="f4dba-186">Example 6: Running a job in a disconnected session</span></span>

<span data-ttu-id="f4dba-187">In dit voor beeld ziet u wat er gebeurt met een taak die wordt uitgevoerd in een sessie waarbij de verbinding is verbroken.</span><span class="sxs-lookup"><span data-stu-id="f4dba-187">This example shows what happens to a job that's running in a disconnected session.</span></span>

```
PS> $s = New-PSSession -ComputerName Server01 -Name Test
PS> $j = Invoke-Command -Session $s { 1..1500 | Foreach-Object {"Return $_"; sleep 30}} -AsJob
PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Running       True            Server01


PS> $s | Disconnect-PSSession

Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server01        Disconnected  Microsoft.PowerShell          None


PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Disconnected  True            Server01


PS> Receive-Job $j -Keep

Return 1
Return 2


PS> $s2 = Connect-PSSession -ComputerName Server01 -Name Test
PS> $j2 = Receive-PSSession -ComputerName Server01 -Name Test
PS> Receive-Job $j

Return 3
Return 4
```

<span data-ttu-id="f4dba-188">De `New-PSSession` cmdlet maakt de test sessie op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="f4dba-188">The `New-PSSession` cmdlet creates the Test session on the Server01 computer.</span></span> <span data-ttu-id="f4dba-189">Met de opdracht wordt de sessie opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4dba-189">The command saves the session in the `$s` variable.</span></span>

<span data-ttu-id="f4dba-190">Met de `Invoke-Command` cmdlet wordt een opdracht uitgevoerd in de sessie in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4dba-190">The `Invoke-Command` cmdlet runs a command in the session in the `$s` variable.</span></span> <span data-ttu-id="f4dba-191">De opdracht gebruikt de para meter **AsJob** om de opdracht uit te voeren als een taak en het taak object in de huidige sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="f4dba-191">The command uses the **AsJob** parameter to run the command as a job and creates the job object in the current session.</span></span>
<span data-ttu-id="f4dba-192">De opdracht retourneert een taak object dat is opgeslagen in de `$j` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4dba-192">The command returns a job object that's saved in the `$j` variable.</span></span> <span data-ttu-id="f4dba-193">Met de `$j` variabele wordt het taak object weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f4dba-193">The `$j` variable displays the job object.</span></span>

<span data-ttu-id="f4dba-194">Het sessie object in de `$s` variabele wordt verzonden naar de pijp lijn `Disconnect-PSSession` en de sessie wordt verbroken.</span><span class="sxs-lookup"><span data-stu-id="f4dba-194">The session object in the `$s` variable is sent down the pipeline to `Disconnect-PSSession` and the session is disconnected.</span></span>

<span data-ttu-id="f4dba-195">De `$j` variabele wordt weer gegeven en toont het effect van het verbreken van de verbinding tussen het taak object in de `$j` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4dba-195">The `$j` variable is displayed and shows the effect of disconnecting the job object in the `$j` variable.</span></span> <span data-ttu-id="f4dba-196">De taak status is nu verbroken.</span><span class="sxs-lookup"><span data-stu-id="f4dba-196">The job state is now Disconnected.</span></span>

<span data-ttu-id="f4dba-197">De `Receive-Job` wordt uitgevoerd op de taak in de `$j` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4dba-197">The `Receive-Job` is run on the job in the `$j` variable.</span></span> <span data-ttu-id="f4dba-198">In de uitvoer ziet u dat de taak is gestart met het retour neren van de uitvoer voordat de sessie en de taak zijn losgekoppeld.</span><span class="sxs-lookup"><span data-stu-id="f4dba-198">The output shows that the job began to return output before the session and the job were disconnected.</span></span>

<span data-ttu-id="f4dba-199">De `Connect-PSSession` cmdlet wordt uitgevoerd in dezelfde client sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-199">The `Connect-PSSession` cmdlet is run in the same client session.</span></span> <span data-ttu-id="f4dba-200">Met de opdracht wordt opnieuw verbinding gemaakt met de test sessie op de Server01-computer en wordt de sessie opgeslagen in de `$s2` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4dba-200">The command reconnects to the Test session on the Server01 computer and saves the session in the `$s2` variable.</span></span>

<span data-ttu-id="f4dba-201">De `Receive-PSSession` cmdlet haalt de resultaten op van de taak die werd uitgevoerd in de sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-201">The `Receive-PSSession` cmdlet gets the results of the job that was running in the session.</span></span> <span data-ttu-id="f4dba-202">Omdat de opdracht wordt uitgevoerd in dezelfde sessie, `Receive-PSSession` retourneert de resultaten standaard als een taak en gebruikt hetzelfde taak object opnieuw.</span><span class="sxs-lookup"><span data-stu-id="f4dba-202">Because the command is run in the same session, `Receive-PSSession` returns the results as a job by default and reuses the same job object.</span></span> <span data-ttu-id="f4dba-203">Met de opdracht wordt de taak opgeslagen in de `$j2` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4dba-203">The command saves the job in the `$j2` variable.</span></span> <span data-ttu-id="f4dba-204">De `Receive-Job` cmdlet haalt de resultaten van de taak op in de `$j` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4dba-204">The `Receive-Job` cmdlet gets the results of the job in the `$j` variable.</span></span>

## <span data-ttu-id="f4dba-205">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f4dba-205">PARAMETERS</span></span>

### <span data-ttu-id="f4dba-206">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="f4dba-206">-AllowRedirection</span></span>

<span data-ttu-id="f4dba-207">Geeft aan dat deze cmdlet omleiding van deze verbinding met een alternatieve URI (Uniform Resource Identifier) mogelijk maakt.</span><span class="sxs-lookup"><span data-stu-id="f4dba-207">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="f4dba-208">Wanneer u de para meter **ConnectionURI** gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI.</span><span class="sxs-lookup"><span data-stu-id="f4dba-208">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="f4dba-209">Standaard worden verbindingen niet door Power shell omgeleid, maar u kunt deze para meter gebruiken om de verbinding in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="f4dba-209">By default, PowerShell doesn't redirect connections, but you can use this parameter to enable it to redirect the connection.</span></span>

<span data-ttu-id="f4dba-210">U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de waarde van de **MaximumConnectionRedirectionCount** -sessie optie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="f4dba-210">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="f4dba-211">Gebruik de para meter **MaximumRedirection** van de `New-PSSessionOption` cmdlet of stel de eigenschap **MaximumConnectionRedirectionCount** van de `$PSSessionOption` Voorkeurs variabele in.</span><span class="sxs-lookup"><span data-stu-id="f4dba-211">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="f4dba-212">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="f4dba-212">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-213">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="f4dba-213">-ApplicationName</span></span>

<span data-ttu-id="f4dba-214">Hiermee geeft u een toepassing op.</span><span class="sxs-lookup"><span data-stu-id="f4dba-214">Specifies an application.</span></span> <span data-ttu-id="f4dba-215">Deze cmdlet maakt alleen verbinding met sessies die gebruikmaken van de opgegeven toepassing.</span><span class="sxs-lookup"><span data-stu-id="f4dba-215">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="f4dba-216">Voer het segment van de toepassings naam van de verbindings-URI in.</span><span class="sxs-lookup"><span data-stu-id="f4dba-216">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="f4dba-217">In de volgende verbindings-URI is WSMan bijvoorbeeld de naam van de toepassing: `http://localhost:5985/WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="f4dba-217">For example, in the following connection URI, WSMan is the application name: `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="f4dba-218">De toepassings naam van een sessie wordt opgeslagen in de eigenschap **runs Pace. Connection info. appName** van de sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-218">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="f4dba-219">De waarde van de para meter wordt gebruikt voor het selecteren en filteren van sessies.</span><span class="sxs-lookup"><span data-stu-id="f4dba-219">The parameter's value is used to select and filter sessions.</span></span> <span data-ttu-id="f4dba-220">De toepassing die door de sessie wordt gebruikt, wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-220">It doesn't change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-221">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="f4dba-221">-Authentication</span></span>

<span data-ttu-id="f4dba-222">Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van de gebruikers referenties in de opdracht om opnieuw verbinding te maken met een verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-222">Specifies the mechanism that's used to authenticate the user credentials in the command to reconnect to a disconnected session.</span></span> <span data-ttu-id="f4dba-223">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="f4dba-223">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f4dba-224">Standaard</span><span class="sxs-lookup"><span data-stu-id="f4dba-224">Default</span></span>
- <span data-ttu-id="f4dba-225">Basic</span><span class="sxs-lookup"><span data-stu-id="f4dba-225">Basic</span></span>
- <span data-ttu-id="f4dba-226">CredSSP</span><span class="sxs-lookup"><span data-stu-id="f4dba-226">Credssp</span></span>
- <span data-ttu-id="f4dba-227">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="f4dba-227">Digest</span></span>
- <span data-ttu-id="f4dba-228">Kerberos</span><span class="sxs-lookup"><span data-stu-id="f4dba-228">Kerberos</span></span>
- <span data-ttu-id="f4dba-229">Negotiate</span><span class="sxs-lookup"><span data-stu-id="f4dba-229">Negotiate</span></span>
- <span data-ttu-id="f4dba-230">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="f4dba-230">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="f4dba-231">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="f4dba-231">The default value is Default.</span></span>

<span data-ttu-id="f4dba-232">Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="f4dba-232">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="f4dba-233">CredSSP-verificatie (Credential Security Support Provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="f4dba-233">Credential Security Support Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="f4dba-234">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="f4dba-234">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="f4dba-235">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="f4dba-235">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-236">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="f4dba-236">-CertificateThumbprint</span></span>

<span data-ttu-id="f4dba-237">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om verbinding te maken met de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-237">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="f4dba-238">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="f4dba-238">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="f4dba-239">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="f4dba-239">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="f4dba-240">Certificaten kunnen alleen worden toegewezen aan lokale gebruikers accounts en werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="f4dba-240">Certificates can be mapped only to local user accounts, and don't work with domain accounts.</span></span>

<span data-ttu-id="f4dba-241">Als u een vinger afdruk van een certificaat wilt ontvangen, gebruikt u een- `Get-Item` of- `Get-ChildItem` opdracht in het Power shell- `Cert:` station.</span><span class="sxs-lookup"><span data-stu-id="f4dba-241">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-242">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="f4dba-242">-ComputerName</span></span>

<span data-ttu-id="f4dba-243">Hiermee geeft u de computer waarop de verbroken sessie wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="f4dba-243">Specifies the computer on which the disconnected session is stored.</span></span> <span data-ttu-id="f4dba-244">Sessies worden opgeslagen op de computer die zich aan de server zijde bevindt of die het einde van een verbinding ontvangt.</span><span class="sxs-lookup"><span data-stu-id="f4dba-244">Sessions are stored on the computer that's at the server-side, or receiving end of a connection.</span></span> <span data-ttu-id="f4dba-245">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f4dba-245">The default is the local computer.</span></span>

<span data-ttu-id="f4dba-246">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name (FQDN) van een computer.</span><span class="sxs-lookup"><span data-stu-id="f4dba-246">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of one computer.</span></span>
<span data-ttu-id="f4dba-247">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f4dba-247">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="f4dba-248">Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt ( `.` ), `$env:COMPUTERNAME` of localhost.</span><span class="sxs-lookup"><span data-stu-id="f4dba-248">To specify the local computer, type the computer name, a dot (`.`), `$env:COMPUTERNAME`, or localhost.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-249">-Configuratiepad</span><span class="sxs-lookup"><span data-stu-id="f4dba-249">-ConfigurationName</span></span>

<span data-ttu-id="f4dba-250">Hiermee geeft u de naam van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-250">Specifies the name of a session configuration.</span></span> <span data-ttu-id="f4dba-251">Deze cmdlet maakt alleen verbinding met sessies die gebruikmaken van de opgegeven sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-251">This cmdlet connects only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="f4dba-252">Voer een configuratie naam of de volledig gekwalificeerde resource-URI in voor een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-252">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="f4dba-253">Als u alleen de configuratie naam opgeeft, wordt de volgende schema-URI voor het voor voegsel geplaatst:</span><span class="sxs-lookup"><span data-stu-id="f4dba-253">If you specify only the configuration name, the following schema URI is prepended:</span></span>

<span data-ttu-id="f4dba-254">`http://schemas.microsoft.com/powershell`.</span><span class="sxs-lookup"><span data-stu-id="f4dba-254">`http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="f4dba-255">De configuratie naam van een sessie wordt opgeslagen in de eigenschap **configuratiepad** van de sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-255">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="f4dba-256">De waarde van de para meter wordt gebruikt voor het selecteren en filteren van sessies.</span><span class="sxs-lookup"><span data-stu-id="f4dba-256">The parameter's value is used to select and filter sessions.</span></span> <span data-ttu-id="f4dba-257">De sessie configuratie die door de sessie wordt gebruikt, wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-257">It doesn't change the session configuration that the session uses.</span></span>

<span data-ttu-id="f4dba-258">Zie [about_Session_Configurations](./About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="f4dba-258">For more information about session configurations, see [about_Session_Configurations](./About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-259">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="f4dba-259">-ConnectionUri</span></span>

<span data-ttu-id="f4dba-260">Hiermee geeft u een URI op die het verbindings eindpunt definieert dat wordt gebruikt om opnieuw verbinding te maken met de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-260">Specifies a URI that defines the connection endpoint that is used to reconnect to the disconnected session.</span></span>

<span data-ttu-id="f4dba-261">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="f4dba-261">The URI must be fully qualified.</span></span> <span data-ttu-id="f4dba-262">De indeling van de teken reeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="f4dba-262">The string's format is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="f4dba-263">De standaard waarde is als volgt:</span><span class="sxs-lookup"><span data-stu-id="f4dba-263">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="f4dba-264">Als u geen verbindings-URI opgeeft, kunt u de para meters **UseSSL** , **ComputerName** , **Port** en **ApplicationName** gebruiken om de verbindings-URI-waarden op te geven.</span><span class="sxs-lookup"><span data-stu-id="f4dba-264">If you don't specify a connection URI, you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="f4dba-265">Geldige waarden voor het **transport** segment van de URI zijn http en HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f4dba-265">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="f4dba-266">Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met standaard poorten: 80 voor HTTP en 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f4dba-266">If you specify a connection URI with a Transport segment, but don't specify a port, the session is created with standard ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="f4dba-267">Als u de standaard poorten voor externe communicatie van Power shell wilt gebruiken, geeft u poort 5985 voor HTTP of 5986 op voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f4dba-267">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="f4dba-268">Als de doel computer de verbinding omleidt naar een andere URI, wordt de omleiding door Power shell voor komen, tenzij u de para meter **AllowRedirection** in de opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f4dba-268">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases: URI, CU

Required: True
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-269">-Credential</span><span class="sxs-lookup"><span data-stu-id="f4dba-269">-Credential</span></span>

<span data-ttu-id="f4dba-270">Hiermee geeft u een gebruikers account op dat is gemachtigd om verbinding te maken met de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-270">Specifies a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="f4dba-271">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f4dba-271">The default is the current user.</span></span>

<span data-ttu-id="f4dba-272">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="f4dba-272">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="f4dba-273">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="f4dba-273">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="f4dba-274">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="f4dba-274">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="f4dba-275">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="f4dba-275">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-276">-Id</span><span class="sxs-lookup"><span data-stu-id="f4dba-276">-Id</span></span>

<span data-ttu-id="f4dba-277">Hiermee geeft u de ID van een niet-verbonden sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-277">Specifies the ID of a disconnected session.</span></span> <span data-ttu-id="f4dba-278">De **id-** para meter werkt alleen wanneer de verbroken sessie eerder is verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-278">The **Id** parameter works only when the disconnected session was previously connected to the current session.</span></span>

<span data-ttu-id="f4dba-279">Deze para meter is geldig, maar niet effectief, wanneer de sessie wordt opgeslagen op de lokale computer, maar niet is verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-279">This parameter is valid, but not effective, when the session is stored on the local computer, but wasn't connected to the current session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-280">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="f4dba-280">-InstanceId</span></span>

<span data-ttu-id="f4dba-281">Hiermee geeft u de exemplaar-ID van de niet-verbonden sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-281">Specifies the instance ID of the disconnected session.</span></span> <span data-ttu-id="f4dba-282">De exemplaar-ID is een unieke aanduiding voor een **PSSession** op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="f4dba-282">The instance ID is a GUID that uniquely identifies a **PSSession** on a local or remote computer.</span></span> <span data-ttu-id="f4dba-283">De exemplaar-ID wordt opgeslagen in de eigenschap **InstanceId** van de **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="f4dba-283">The instance ID is stored in the **InstanceID** property of the **PSSession**.</span></span>

```yaml
Type: System.Guid
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-284">-JobName</span><span class="sxs-lookup"><span data-stu-id="f4dba-284">-JobName</span></span>

<span data-ttu-id="f4dba-285">Hiermee geeft u een beschrijvende naam op voor de taak die `Receive-PSSession` wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-285">Specifies a friendly name for the job that `Receive-PSSession` returns.</span></span>

<span data-ttu-id="f4dba-286">`Receive-PSSession` retourneert een taak wanneer de waarde van de para meter **outtarget** een taak is of de taak die wordt uitgevoerd in de verbroken sessie, is gestart in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-286">`Receive-PSSession` returns a job when the value of the **OutTarget** parameter is Job or the job that's running in the disconnected session was started in the current session.</span></span>

<span data-ttu-id="f4dba-287">Als de taak die in de verbroken sessie wordt uitgevoerd in de huidige sessie is gestart, gebruikt Power shell het oorspronkelijke taak object in de sessie opnieuw en wordt de waarde van de para meter **JobName** genegeerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-287">If the job that's running in the disconnected session was started in the current session, PowerShell reuses the original job object in the session and ignores the value of the **JobName** parameter.</span></span>

<span data-ttu-id="f4dba-288">Als de taak die wordt uitgevoerd in de verbroken sessie is gestart in een andere sessie, maakt Power shell een nieuw taak object.</span><span class="sxs-lookup"><span data-stu-id="f4dba-288">If the job that's running in the disconnected session was started in a different session, PowerShell creates a new job object.</span></span> <span data-ttu-id="f4dba-289">Er wordt een standaard naam gebruikt, maar u kunt deze para meter gebruiken om de naam te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="f4dba-289">It uses a default name, but you can use this parameter to change the name.</span></span>

<span data-ttu-id="f4dba-290">Als de standaard waarde of expliciete waarde van de para meter **outtarget** niet taak is, is de opdracht geslaagd, maar de para meter **JobName** heeft geen effect.</span><span class="sxs-lookup"><span data-stu-id="f4dba-290">If the default value or explicit value of the **OutTarget** parameter isn't Job, the command succeeds, but the **JobName** parameter has no effect.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-291">-Name</span><span class="sxs-lookup"><span data-stu-id="f4dba-291">-Name</span></span>

<span data-ttu-id="f4dba-292">Hiermee geeft u de beschrijvende naam van de sessie zonder verbinding.</span><span class="sxs-lookup"><span data-stu-id="f4dba-292">Specifies the friendly name of the disconnected session.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ConnectionUriSessionName, SessionName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-293">-Outdoel</span><span class="sxs-lookup"><span data-stu-id="f4dba-293">-OutTarget</span></span>

<span data-ttu-id="f4dba-294">Hiermee wordt bepaald hoe de sessie resultaten worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-294">Determines how the session results are returned.</span></span> <span data-ttu-id="f4dba-295">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="f4dba-295">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f4dba-296">**Taak**.</span><span class="sxs-lookup"><span data-stu-id="f4dba-296">**Job**.</span></span> <span data-ttu-id="f4dba-297">Retourneert de resultaten asynchroon in een taak object.</span><span class="sxs-lookup"><span data-stu-id="f4dba-297">Returns the results asynchronously in a job object.</span></span> <span data-ttu-id="f4dba-298">U kunt de para meter **JobName** gebruiken om een naam of een nieuwe naam voor de taak op te geven.</span><span class="sxs-lookup"><span data-stu-id="f4dba-298">You can use the **JobName** parameter to specify a name or new name for the job.</span></span>
- <span data-ttu-id="f4dba-299">**Host**.</span><span class="sxs-lookup"><span data-stu-id="f4dba-299">**Host**.</span></span> <span data-ttu-id="f4dba-300">Retourneert de resultaten naar de opdracht regel (synchroon).</span><span class="sxs-lookup"><span data-stu-id="f4dba-300">Returns the results to the command line (synchronously).</span></span> <span data-ttu-id="f4dba-301">Als de opdracht wordt hervat of de resultaten uit een groot aantal objecten bestaan, kan de reactie vertraging oplopen.</span><span class="sxs-lookup"><span data-stu-id="f4dba-301">If the command is being resumed or the results consist of a large number of objects, the response might be delayed.</span></span>

<span data-ttu-id="f4dba-302">De standaard waarde van de para meter **outtarget** is host.</span><span class="sxs-lookup"><span data-stu-id="f4dba-302">The default value of the **OutTarget** parameter is Host.</span></span> <span data-ttu-id="f4dba-303">Als de opdracht die wordt ontvangen in een verbroken sessie is gestart in de huidige sessie, is de standaard waarde van de para meter **outtarget** de vorm waarin de opdracht is gestart.</span><span class="sxs-lookup"><span data-stu-id="f4dba-303">If the command that's being received in a disconnected session was started in the current session, the default value of the **OutTarget** parameter is the form in which the command was started.</span></span> <span data-ttu-id="f4dba-304">Als de opdracht als een taak is gestart, wordt deze als een taak geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-304">If the command was started as a job, by default, it's returned as a job.</span></span> <span data-ttu-id="f4dba-305">Als dat niet het geval is, wordt de standaard waarde naar het hostprogramma geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-305">Otherwise, it's returned to the host program by default.</span></span>

<span data-ttu-id="f4dba-306">Normaal gesp roken geeft het hostprogramma geretourneerde objecten zonder vertraging weer op de opdracht regel, maar dit kan variëren.</span><span class="sxs-lookup"><span data-stu-id="f4dba-306">Typically, the host program displays returned objects at the command line without delay, but this behavior can vary.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutTarget
Parameter Sets: (All)
Aliases:
Accepted values: Default, Host, Job

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-307">-Port</span><span class="sxs-lookup"><span data-stu-id="f4dba-307">-Port</span></span>

<span data-ttu-id="f4dba-308">Hiermee geeft u de netwerk poort van de externe computer op die wordt gebruikt om opnieuw verbinding te maken met de sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-308">Specifies the remote computer's network port that's used to reconnect to the session.</span></span> <span data-ttu-id="f4dba-309">Als u verbinding wilt maken met een externe computer, moet deze Luis teren op de poort die door de verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f4dba-309">To connect to a remote computer, it must be listening on the port that the connection uses.</span></span> <span data-ttu-id="f4dba-310">De standaard poorten zijn 5985, de WinRM-poort voor HTTP en 5986, de WinRM-poort voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f4dba-310">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="f4dba-311">Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren.</span><span class="sxs-lookup"><span data-stu-id="f4dba-311">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen on that port.</span></span> <span data-ttu-id="f4dba-312">Als u de listener wilt configureren, typt u de volgende twee opdrachten bij de Power shell-prompt:</span><span class="sxs-lookup"><span data-stu-id="f4dba-312">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="f4dba-313">Gebruik de para meter **poort** alleen als dit nodig is.</span><span class="sxs-lookup"><span data-stu-id="f4dba-313">Don't use the **Port** parameter unless it's necessary.</span></span> <span data-ttu-id="f4dba-314">De poort die in de opdracht is ingesteld, is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-314">The port that's set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="f4dba-315">Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.</span><span class="sxs-lookup"><span data-stu-id="f4dba-315">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-316">-Sessie</span><span class="sxs-lookup"><span data-stu-id="f4dba-316">-Session</span></span>

<span data-ttu-id="f4dba-317">Hiermee geeft u de sessie zonder verbinding.</span><span class="sxs-lookup"><span data-stu-id="f4dba-317">Specifies the disconnected session.</span></span> <span data-ttu-id="f4dba-318">Voer een variabele in die de **PSSession** bevat of een opdracht die de **PSSession** , zoals een opdracht, maakt of ontvangt `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f4dba-318">Enter a variable that contains the **PSSession** or a command that creates or gets the **PSSession** , such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-319">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="f4dba-319">-SessionOption</span></span>

<span data-ttu-id="f4dba-320">Hiermee geeft u geavanceerde opties voor de sessie op.</span><span class="sxs-lookup"><span data-stu-id="f4dba-320">Specifies advanced options for the session.</span></span> <span data-ttu-id="f4dba-321">Voer een **SessionOption** -object in, zoals het, dat u maakt met behulp van de `New-PSSessionOption` cmdlet of een hash-tabel waarin de sleutels de naam van de sessie optie zijn en de waarden voor de waarden van de sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-321">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="f4dba-322">De standaard waarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="f4dba-322">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it's set.</span></span> <span data-ttu-id="f4dba-323">Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-323">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="f4dba-324">De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-324">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="f4dba-325">Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-325">However, they don't take precedence over maximum values, quotas, or limits set in the session configuration.</span></span>

<span data-ttu-id="f4dba-326">Zie voor een beschrijving van de sessie opties die de standaard waarden bevatten `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="f4dba-326">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="f4dba-327">Zie [about_Preference_Variables](./About/about_Preference_Variables.md)voor meer informatie over de **$PSSessionOption** voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="f4dba-327">For information about the **$PSSessionOption** preference variable, see [about_Preference_Variables](./About/about_Preference_Variables.md).</span></span> <span data-ttu-id="f4dba-328">Zie [about_Session_Configurations](./About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="f4dba-328">For more information about session configurations, see [about_Session_Configurations](./About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-329">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="f4dba-329">-UseSSL</span></span>

<span data-ttu-id="f4dba-330">Geeft aan dat deze cmdlet het Secure Sockets Layer-Protocol (SSL) gebruikt om verbinding te maken met de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-330">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to connect to the disconnected session.</span></span> <span data-ttu-id="f4dba-331">SSL wordt standaard niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f4dba-331">By default, SSL isn't used.</span></span>

<span data-ttu-id="f4dba-332">WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="f4dba-332">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="f4dba-333">**UseSSL** is een extra bescherming waarmee de gegevens worden verzonden via een HTTPS-verbinding in plaats van via een http-verbinding.</span><span class="sxs-lookup"><span data-stu-id="f4dba-333">**UseSSL** is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="f4dba-334">Als u deze para meter gebruikt en SSL niet beschikbaar is op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f4dba-334">If you use this parameter and SSL isn't available on the port that's used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f4dba-335">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f4dba-335">-Confirm</span></span>

<span data-ttu-id="f4dba-336">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f4dba-336">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f4dba-337">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f4dba-337">-WhatIf</span></span>

<span data-ttu-id="f4dba-338">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f4dba-338">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f4dba-339">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-339">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="f4dba-340">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f4dba-340">CommonParameters</span></span>

<span data-ttu-id="f4dba-341">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f4dba-341">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f4dba-342">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-342">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f4dba-343">INVOER</span><span class="sxs-lookup"><span data-stu-id="f4dba-343">INPUTS</span></span>

### <span data-ttu-id="f4dba-344">System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="f4dba-344">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="f4dba-345">U kunt sessie objecten door sluizen naar deze cmdlet, zoals objecten die door de `Get-PSSession` cmdlet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-345">You can pipe session objects to this cmdlet, such as objects returned by the `Get-PSSession` cmdlet.</span></span>

### <span data-ttu-id="f4dba-346">System. Int32</span><span class="sxs-lookup"><span data-stu-id="f4dba-346">System.Int32</span></span>

<span data-ttu-id="f4dba-347">U kunt sessie-Id's door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4dba-347">You can pipe session Ids to this cmdlet.</span></span>

### <span data-ttu-id="f4dba-348">System. GUID</span><span class="sxs-lookup"><span data-stu-id="f4dba-348">System.Guid</span></span>

<span data-ttu-id="f4dba-349">U kunt de exemplaar-Id's van sessies met deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="f4dba-349">You can pipe the instance Ids of sessions this cmdlet.</span></span>

### <span data-ttu-id="f4dba-350">System. String</span><span class="sxs-lookup"><span data-stu-id="f4dba-350">System.String</span></span>

<span data-ttu-id="f4dba-351">U kunt sessie namen aan deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="f4dba-351">You can pipe session names to this cmdlet.</span></span>

## <span data-ttu-id="f4dba-352">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f4dba-352">OUTPUTS</span></span>

### <span data-ttu-id="f4dba-353">System. Management. Automation. job of PSObject</span><span class="sxs-lookup"><span data-stu-id="f4dba-353">System.Management.Automation.Job or PSObject</span></span>

<span data-ttu-id="f4dba-354">Met deze cmdlet worden de resultaten geretourneerd van opdrachten die zijn uitgevoerd in de verbroken sessie, indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="f4dba-354">This cmdlet returns the results of commands that ran in the disconnected session, if any.</span></span> <span data-ttu-id="f4dba-355">Als de waarde of de standaard waarde van de para meter **outtarget** een taak is, `Receive-PSSession` wordt een taak object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-355">If the value or default value of the **OutTarget** parameter is Job, `Receive-PSSession` returns a job object.</span></span> <span data-ttu-id="f4dba-356">Anders worden objecten geretourneerd die de opdracht resultaten vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="f4dba-356">Otherwise, it returns objects that represent that command results.</span></span>

## <span data-ttu-id="f4dba-357">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f4dba-357">NOTES</span></span>

<span data-ttu-id="f4dba-358">`Receive-PSSession` Hiermee worden alleen resultaten opgehaald van sessies die zijn losgekoppeld.</span><span class="sxs-lookup"><span data-stu-id="f4dba-358">`Receive-PSSession` gets results only from sessions that were disconnected.</span></span> <span data-ttu-id="f4dba-359">Alleen sessies die zijn verbonden met of eindigen op computers waarop Power Shell 3,0 of hoger wordt uitgevoerd, kunnen worden losgekoppeld en opnieuw worden aangesloten.</span><span class="sxs-lookup"><span data-stu-id="f4dba-359">Only sessions that are connected to, or terminate at, computers that run PowerShell 3.0 or later versions can be disconnected and reconnected.</span></span>

<span data-ttu-id="f4dba-360">Als de opdrachten die werden uitgevoerd in de verbroken sessie geen resultaten genereren of als de resultaten al naar een andere sessie zijn geretourneerd, `Receive-PSSession` wordt er geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="f4dba-360">If the commands that were running in the disconnected session didn't generate results or if the results were already returned to another session, `Receive-PSSession` doesn't generate any output.</span></span>

<span data-ttu-id="f4dba-361">De modus uitvoer buffer van een sessie bepaalt hoe opdrachten in de sessie uitvoer beheren wanneer de sessie wordt verbroken.</span><span class="sxs-lookup"><span data-stu-id="f4dba-361">A session's output buffering mode determines how commands in the session manage output when the session is disconnected.</span></span> <span data-ttu-id="f4dba-362">Wanneer de waarde van de **OutputBufferingMode** -optie van de sessie wordt verwijderd en de uitvoer buffer vol is, begint de opdracht uitvoer te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="f4dba-362">When the value of the **OutputBufferingMode** option of the session is Drop and the output buffer is full, the command starts to delete output.</span></span> <span data-ttu-id="f4dba-363">`Receive-PSSession` kan deze uitvoer niet herstellen.</span><span class="sxs-lookup"><span data-stu-id="f4dba-363">`Receive-PSSession` can't recover this output.</span></span> <span data-ttu-id="f4dba-364">Zie de Help-artikelen voor de cmdlets [New-PSSessionOption](New-PSSessionOption.md) en [New-PSTransportOption](New-PSTransportOption.md) voor meer informatie over de optie voor de modus uitvoer buffer.</span><span class="sxs-lookup"><span data-stu-id="f4dba-364">For more information about the output buffering mode option, see the help articles for the [New-PSSessionOption](New-PSSessionOption.md) and [New-PSTransportOption](New-PSTransportOption.md) cmdlets.</span></span>

<span data-ttu-id="f4dba-365">U kunt de time-outwaarde van een **PSSession** niet wijzigen wanneer u verbinding maakt met de **PSSession** of resultaten ontvangt.</span><span class="sxs-lookup"><span data-stu-id="f4dba-365">You can't change the idle time-out value of a **PSSession** when you connect to the **PSSession** or receive results.</span></span> <span data-ttu-id="f4dba-366">De para meter **SessionOption** van `Receive-PSSession` maakt een **SessionOption** -object met een **IdleTimeout** -waarde.</span><span class="sxs-lookup"><span data-stu-id="f4dba-366">The **SessionOption** parameter of `Receive-PSSession` takes a **SessionOption** object that has an **IdleTimeout** value.</span></span> <span data-ttu-id="f4dba-367">De waarde **IdleTimeout** van het object **SessionOption** en de waarde **IdleTimeout** van de `$PSSessionOption` variabele wordt echter genegeerd wanneer verbinding wordt gemaakt met een **PSSession** of als er resultaten worden ontvangen.</span><span class="sxs-lookup"><span data-stu-id="f4dba-367">However, the **IdleTimeout** value of the **SessionOption** object and the **IdleTimeout** value of the `$PSSessionOption` variable are ignored when it connects to a **PSSession** or receiving results.</span></span>

- <span data-ttu-id="f4dba-368">U kunt de time-out voor inactiviteit van een **PSSession** instellen en wijzigen wanneer u de **PSSession** maakt met behulp van de- `New-PSSession` of `Invoke-Command` -cmdlets en wanneer u de verbinding met de **PSSession** verbreekt.</span><span class="sxs-lookup"><span data-stu-id="f4dba-368">You can set and change the idle time-out of a **PSSession** when you create the **PSSession** , by using the `New-PSSession` or `Invoke-Command` cmdlets, and when you disconnect from the **PSSession**.</span></span>
- <span data-ttu-id="f4dba-369">De eigenschap **IdleTimeout** van een **PSSession** is essentieel voor verbroken sessies, omdat deze bepaalt hoe lang een verbroken sessie op de externe computer wordt onderhouden.</span><span class="sxs-lookup"><span data-stu-id="f4dba-369">The **IdleTimeout** property of a **PSSession** is critical to disconnected sessions because it determines how long a disconnected session is maintained on the remote computer.</span></span> <span data-ttu-id="f4dba-370">Verbroken sessies worden beschouwd als niet-actief vanaf het moment dat ze worden losgekoppeld, zelfs als opdrachten worden uitgevoerd in de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-370">Disconnected sessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

<span data-ttu-id="f4dba-371">Als u begint met het starten van een taak in een externe sessie met behulp van de para meter **AsJob** van de `Invoke-Command` cmdlet, wordt het taak object gemaakt in de huidige sessie, zelfs als de taak wordt uitgevoerd in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-371">If you start a start a job in a remote session by using the **AsJob** parameter of the `Invoke-Command` cmdlet, the job object is created in the current session, even though the job runs in the remote session.</span></span> <span data-ttu-id="f4dba-372">Als u de externe sessie verbreekt, wordt het taak object in de huidige sessie losgekoppeld van de taak.</span><span class="sxs-lookup"><span data-stu-id="f4dba-372">If you disconnect the remote session, the job object in the current session is disconnected from the job.</span></span> <span data-ttu-id="f4dba-373">Het taak object bevat alle resultaten die zijn geretourneerd, maar er worden geen nieuwe resultaten van de taak in de verbroken sessie ontvangen.</span><span class="sxs-lookup"><span data-stu-id="f4dba-373">The job object contains any results that were returned to it, but doesn't receive new results from the job in the disconnected session.</span></span>

<span data-ttu-id="f4dba-374">Als een andere client verbinding maakt met de sessie die de actieve taak bevat, zijn de resultaten die zijn geleverd aan het oorspronkelijke taak object in de oorspronkelijke sessie niet beschikbaar in de zojuist verbonden sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-374">If a different client connects to the session that contains the running job, the results that were delivered to the original job object in the original session aren't available in the newly connected session.</span></span> <span data-ttu-id="f4dba-375">Alleen resultaten die niet aan het oorspronkelijke taak object zijn geleverd, zijn beschikbaar in de opnieuw verbonden sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-375">Only results that were not delivered to the original job object are available in the reconnected session.</span></span>

<span data-ttu-id="f4dba-376">Als u een script in een sessie start en vervolgens de verbinding met de sessie verbreekt, zijn alle resultaten die het script naar de sessie levert voordat de verbinding wordt verbroken, niet beschikbaar voor een andere client die verbinding maakt met de sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-376">Similarly, if you start a script in a session and then disconnect from the session, any results that the script delivers to the session before disconnecting aren't available to another client that connects to the session.</span></span>

<span data-ttu-id="f4dba-377">Gebruik de para meter **InDisconnectedSession** van de cmdlet om gegevens verlies te voor komen in sessies die u wilt verbreken `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="f4dba-377">To prevent data loss in sessions that you intend to disconnect, use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="f4dba-378">Omdat deze para meter voor komt dat resultaten worden geretourneerd naar de huidige sessie, zijn alle resultaten beschikbaar wanneer de sessie opnieuw wordt verbonden.</span><span class="sxs-lookup"><span data-stu-id="f4dba-378">Because this parameter prevents results from being returned to the current session, all results are available when the session is reconnected.</span></span>

<span data-ttu-id="f4dba-379">U kunt gegevens verlies ook voor komen door met behulp van de `Invoke-Command` cmdlet een `Start-Job` opdracht uit te voeren in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-379">You can also prevent data loss by using the `Invoke-Command` cmdlet to run a `Start-Job` command in the remote session.</span></span> <span data-ttu-id="f4dba-380">In dit geval wordt het taak object in de externe sessie gemaakt.</span><span class="sxs-lookup"><span data-stu-id="f4dba-380">In this case, the job object is created in the remote session.</span></span> <span data-ttu-id="f4dba-381">U kunt de cmdlet niet gebruiken `Receive-PSSession` om de taak resultaten op te halen.</span><span class="sxs-lookup"><span data-stu-id="f4dba-381">You can't use the `Receive-PSSession` cmdlet to get the job results.</span></span> <span data-ttu-id="f4dba-382">Gebruik in plaats daarvan de `Connect-PSSession` cmdlet om verbinding te maken met de sessie en gebruik vervolgens de `Invoke-Command` cmdlet om een `Receive-Job` opdracht uit te voeren in de sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-382">Instead, use the `Connect-PSSession` cmdlet to connect to the session and then use the `Invoke-Command` cmdlet to run a `Receive-Job` command in the session.</span></span>

<span data-ttu-id="f4dba-383">Wanneer een sessie die een actieve taak bevat losgekoppeld en vervolgens opnieuw verbinding maakt, wordt het oorspronkelijke taak object opnieuw gebruikt als de verbinding met de taak is verbroken en opnieuw verbinding met dezelfde sessie wordt gemaakt en de opdracht om opnieuw verbinding te maken geen nieuwe taak naam opgeeft.</span><span class="sxs-lookup"><span data-stu-id="f4dba-383">When a session that contains a running job is disconnected and then reconnected, the original job object is reused only if the job is disconnected and reconnected to the same session, and the command to reconnect doesn't specify a new job name.</span></span> <span data-ttu-id="f4dba-384">Als de sessie opnieuw wordt verbonden met een andere client sessie of als er een nieuwe taak naam is opgegeven, maakt Power shell een nieuw taak object voor de nieuwe sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-384">If the session is reconnected to a different client session or a new job name is specified, PowerShell creates a new job object for the new session.</span></span>

<span data-ttu-id="f4dba-385">Wanneer u een **PSSession** verbreekt, wordt de sessie status losgekoppeld en is de beschik baarheid geen.</span><span class="sxs-lookup"><span data-stu-id="f4dba-385">When you disconnect a **PSSession** , the session state is Disconnected and the availability is None.</span></span>

- <span data-ttu-id="f4dba-386">De waarde van de eigenschap **State** is relatief ten opzichte van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-386">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="f4dba-387">Als de waarde voor de verbinding is verbroken, betekent dit dat de **PSSession** niet is verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-387">A value of Disconnected means that the **PSSession** isn't connected to the current session.</span></span> <span data-ttu-id="f4dba-388">Dit betekent echter niet dat de **PSSession** van de verbinding met alle sessies is verbroken.</span><span class="sxs-lookup"><span data-stu-id="f4dba-388">However, it doesn't mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="f4dba-389">Deze is mogelijk verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-389">It might be connected to a different session.</span></span>
  <span data-ttu-id="f4dba-390">Gebruik de eigenschap **Beschik baarheid** om te bepalen of u verbinding kunt maken met de sessie of er opnieuw verbinding mee wilt maken.</span><span class="sxs-lookup"><span data-stu-id="f4dba-390">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>
- <span data-ttu-id="f4dba-391">Een **beschikbaarheids** waarde van geen geeft aan dat u verbinding kunt maken met de sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-391">An **Availability** value of None indicates that you can connect to the session.</span></span> <span data-ttu-id="f4dba-392">De waarde bezet geeft aan dat u geen verbinding kunt maken met de **PSSession** , omdat deze is verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="f4dba-392">A value of Busy indicates that you can't connect to the **PSSession** because it's connected to another session.</span></span>
- <span data-ttu-id="f4dba-393">Zie [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate) in de MSDN-bibliotheek voor meer informatie over de waarden van de eigenschap **State** van sessies.</span><span class="sxs-lookup"><span data-stu-id="f4dba-393">For more information about the values of the **State** property of sessions, see [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate) in the MSDN library.</span></span>
- <span data-ttu-id="f4dba-394">Zie [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability)voor meer informatie over de waarden van de eigenschap **Beschik baarheid** van sessies.</span><span class="sxs-lookup"><span data-stu-id="f4dba-394">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="f4dba-395">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f4dba-395">RELATED LINKS</span></span>

[<span data-ttu-id="f4dba-396">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="f4dba-396">about_PSSessions</span></span>](./About/about_PSSessions.md)

[<span data-ttu-id="f4dba-397">about_Remote</span><span class="sxs-lookup"><span data-stu-id="f4dba-397">about_Remote</span></span>](./About/about_Remote.md)

[<span data-ttu-id="f4dba-398">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="f4dba-398">about_Remote_Disconnected_Sessions</span></span>](./About/about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="f4dba-399">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="f4dba-399">about_Session_Configurations</span></span>](./About/about_Session_Configurations.md)

[<span data-ttu-id="f4dba-400">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="f4dba-400">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="f4dba-401">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="f4dba-401">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="f4dba-402">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="f4dba-402">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="f4dba-403">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="f4dba-403">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="f4dba-404">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="f4dba-404">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="f4dba-405">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="f4dba-405">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="f4dba-406">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="f4dba-406">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="f4dba-407">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="f4dba-407">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="f4dba-408">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="f4dba-408">Remove-PSSession</span></span>](Remove-PSSession.md)
