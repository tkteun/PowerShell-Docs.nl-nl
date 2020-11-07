---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/connect-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-PSSession
ms.openlocfilehash: 8aff8a2b3962b3bf09d158247c06b36f99eaf527
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342515"
---
# <span data-ttu-id="bb851-103">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="bb851-103">Connect-PSSession</span></span>

## <span data-ttu-id="bb851-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="bb851-104">SYNOPSIS</span></span>
<span data-ttu-id="bb851-105">Opnieuw verbinding maken met verbroken sessies.</span><span class="sxs-lookup"><span data-stu-id="bb851-105">Reconnects to disconnected sessions.</span></span>

## <span data-ttu-id="bb851-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="bb851-106">SYNTAX</span></span>

### <span data-ttu-id="bb851-107">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="bb851-107">Name (Default)</span></span>

```
Connect-PSSession -Name <String[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bb851-108">Sessie</span><span class="sxs-lookup"><span data-stu-id="bb851-108">Session</span></span>

```
Connect-PSSession [-Session] <PSSession[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bb851-109">ComputerName</span><span class="sxs-lookup"><span data-stu-id="bb851-109">ComputerName</span></span>

```
Connect-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bb851-110">ComputerNameGuid</span><span class="sxs-lookup"><span data-stu-id="bb851-110">ComputerNameGuid</span></span>

```
Connect-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bb851-111">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="bb851-111">ConnectionUri</span></span>

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bb851-112">ConnectionUriGuid</span><span class="sxs-lookup"><span data-stu-id="bb851-112">ConnectionUriGuid</span></span>

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bb851-113">InstanceId</span><span class="sxs-lookup"><span data-stu-id="bb851-113">InstanceId</span></span>

```
Connect-PSSession -InstanceId <Guid[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bb851-114">Id</span><span class="sxs-lookup"><span data-stu-id="bb851-114">Id</span></span>

```
Connect-PSSession [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bb851-115">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="bb851-115">DESCRIPTION</span></span>

<span data-ttu-id="bb851-116">De `Connect-PSSession` cmdlet maakt opnieuw verbinding met door gebruikers beheerde Power shell-sessies ( **PSSessions** ) die zijn losgekoppeld.</span><span class="sxs-lookup"><span data-stu-id="bb851-116">The `Connect-PSSession` cmdlet reconnects to user-managed PowerShell sessions ( **PSSessions** ) that were disconnected.</span></span> <span data-ttu-id="bb851-117">Het werkt op sessies die opzettelijk worden losgekoppeld, zoals met de `Disconnect-PSSession` cmdlet of de **InDisconnectedSession** -para meter van de `Invoke-Command` cmdlet, en die onbedoeld zijn losgekoppeld, bijvoorbeeld door een tijdelijke netwerk storing.</span><span class="sxs-lookup"><span data-stu-id="bb851-117">It works on sessions that are disconnected intentionally, such as by using the `Disconnect-PSSession` cmdlet or the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet, and those that were disconnected unintentionally, such as by a temporary network outage.</span></span>

<span data-ttu-id="bb851-118">`Connect-PSSession` kan verbinding maken met elke verbroken sessie die is gestart door dezelfde gebruiker.</span><span class="sxs-lookup"><span data-stu-id="bb851-118">`Connect-PSSession` can connect to any disconnected session that was started by the same user.</span></span> <span data-ttu-id="bb851-119">Dit zijn onder andere de verbindingen die zijn gestart door of losgekoppeld van andere sessies op andere computers.</span><span class="sxs-lookup"><span data-stu-id="bb851-119">These include those that were started by or disconnected from other sessions on other computers.</span></span>

<span data-ttu-id="bb851-120">Er `Connect-PSSession` kan echter geen verbinding worden gemaakt met verbroken of gesloten sessies, of interactieve sessies die zijn gestart met behulp van de `Enter-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bb851-120">However, `Connect-PSSession` cannot connect to broken or closed sessions, or interactive sessions started by using the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="bb851-121">Het is ook niet mogelijk om sessies te verbinden met sessies die zijn gestart door andere gebruikers, tenzij u de referenties kunt opgeven van de gebruiker die de sessie heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bb851-121">Also you cannot connect sessions to sessions started by other users, unless you can provide the credentials of the user who created the session.</span></span>

<span data-ttu-id="bb851-122">Zie [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md)voor meer informatie over de functie voor verbroken sessies.</span><span class="sxs-lookup"><span data-stu-id="bb851-122">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="bb851-123">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bb851-123">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="bb851-124">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="bb851-124">EXAMPLES</span></span>

### <span data-ttu-id="bb851-125">Voor beeld 1: opnieuw verbinding maken met een sessie</span><span class="sxs-lookup"><span data-stu-id="bb851-125">Example 1: Reconnect to a session</span></span>

```
PS C:\> Connect-PSSession -ComputerName Server01 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Opened        ITTasks                  Available
```

<span data-ttu-id="bb851-126">Met deze opdracht wordt opnieuw verbinding gemaakt met de ITTask-sessie op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="bb851-126">This command reconnects to the ITTask session on the Server01 computer.</span></span>

<span data-ttu-id="bb851-127">In de uitvoer ziet u dat de opdracht is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="bb851-127">The output shows that the command was successful.</span></span> <span data-ttu-id="bb851-128">De **status** van de sessie wordt geopend en de **Beschik baarheid** is beschikbaar. Dit geeft aan dat u opdrachten in de sessie kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="bb851-128">The **State** of the session is Opened and the **Availability** is Available, which indicates that you can run commands in the session.</span></span>

### <span data-ttu-id="bb851-129">Voor beeld 2: gevolgen van het verbreken van de verbinding en opnieuw verbinden</span><span class="sxs-lookup"><span data-stu-id="bb851-129">Example 2: Effect of disconnecting and reconnecting</span></span>

```
PS C:\> Get-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available


PS C:\> Get-PSSession | Disconnect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Disconnected  Microsoft.PowerShell          None


PS C:\> Get-PSSession | Connect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available
```

<span data-ttu-id="bb851-130">In dit voor beeld ziet u het effect van het verbreken van de verbinding en vervolgens de verbinding met een sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-130">This example shows the effect of disconnecting and then reconnecting to a session.</span></span>

<span data-ttu-id="bb851-131">De eerste opdracht maakt gebruik van de `Get-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bb851-131">The first command uses the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="bb851-132">Zonder de para meter **ComputerName** worden met de opdracht alleen sessies opgehaald die in de huidige sessie zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bb851-132">Without the **ComputerName** parameter, the command gets only sessions that were created in the current session.</span></span>

<span data-ttu-id="bb851-133">In de uitvoer ziet u dat met de opdracht de back-upsessie wordt opgehaald op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bb851-133">The output shows that the command gets the Backups session on the local computer.</span></span> <span data-ttu-id="bb851-134">De **status** van de sessie wordt geopend en de **Beschik baarheid** is beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="bb851-134">The **State** of the session is Opened and the **Availability** is Available.</span></span>

<span data-ttu-id="bb851-135">Met de tweede opdracht wordt de `Get-PSSession` cmdlet gebruikt om de **PSSession** -objecten op te halen die zijn gemaakt in de huidige sessie en de `Disconnect-PSSession` cmdlet om de sessie te verbreken.</span><span class="sxs-lookup"><span data-stu-id="bb851-135">The second command uses the `Get-PSSession` cmdlet to get the **PSSession** objects that were created in the current session and the `Disconnect-PSSession` cmdlet to disconnect the sessions.</span></span> <span data-ttu-id="bb851-136">In de uitvoer ziet u dat de verbinding met de back-upsessie is verbroken.</span><span class="sxs-lookup"><span data-stu-id="bb851-136">The output shows that the Backups session was disconnected.</span></span> <span data-ttu-id="bb851-137">De **status** van de sessie wordt verbroken en de **Beschik baarheid** is geen.</span><span class="sxs-lookup"><span data-stu-id="bb851-137">The **State** of the session is Disconnected and the **Availability** is None.</span></span>

<span data-ttu-id="bb851-138">De derde opdracht gebruikt de `Get-PSSession` cmdlet om de **PSSession** -objecten op te halen die zijn gemaakt in de huidige sessie en de `Connect-PSSession` cmdlet om de sessies opnieuw te verbinden.</span><span class="sxs-lookup"><span data-stu-id="bb851-138">The third command uses the `Get-PSSession` cmdlet to get the **PSSession** objects that were created in the current session and the `Connect-PSSession` cmdlet to reconnect the sessions.</span></span> <span data-ttu-id="bb851-139">In de uitvoer ziet u dat er opnieuw verbinding is gemaakt met de back-up van de sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-139">The output shows that the Backups session was reconnected.</span></span> <span data-ttu-id="bb851-140">De **status** van de sessie wordt geopend en de **Beschik baarheid** is beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="bb851-140">The **State** of the session is Opened and the **Availability** is Available.</span></span>

<span data-ttu-id="bb851-141">Als u de `Connect-PSSession` cmdlet gebruikt voor een sessie die niet wordt losgekoppeld, is de opdracht niet van invloed op de sessie en worden er geen fouten gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="bb851-141">If you use the `Connect-PSSession` cmdlet on a session that is not disconnected, the command does not affect the session and it does not generate any errors.</span></span>

### <span data-ttu-id="bb851-142">Voor beeld 3: reeks opdrachten in een bedrijfs scenario</span><span class="sxs-lookup"><span data-stu-id="bb851-142">Example 3: Series of commands in an enterprise scenario</span></span>

<span data-ttu-id="bb851-143">In deze reeks opdrachten ziet u hoe de `Connect-PSSession` cmdlet kan worden gebruikt in een bedrijfs scenario.</span><span class="sxs-lookup"><span data-stu-id="bb851-143">This series of commands shows how the `Connect-PSSession` cmdlet might be used in an enterprise scenario.</span></span> <span data-ttu-id="bb851-144">In dit geval start een systeem beheerder een langlopende taak in een sessie op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="bb851-144">In this case, a system administrator starts a long-running job in a session on a remote computer.</span></span> <span data-ttu-id="bb851-145">Nadat de taak is gestart, wordt de verbinding met de sessie verbroken en gaat de beheerder naar thuis.</span><span class="sxs-lookup"><span data-stu-id="bb851-145">After starting the job, the administrator disconnects from the session and goes home.</span></span>
<span data-ttu-id="bb851-146">Later die avond meldt de beheerder zich aan bij haar computer thuis en wordt gecontroleerd of de taak is uitgevoerd totdat deze is voltooid.</span><span class="sxs-lookup"><span data-stu-id="bb851-146">Later that evening, the administrator logs on to her home computer and verifies that the job ran until it is completed.</span></span>

<span data-ttu-id="bb851-147">De beheerder begint met het maken van een sessie op een externe computer en het uitvoeren van een script in de sessie. De eerste opdracht gebruikt de `New-PSSession` cmdlet om de ITTask-sessie te maken op de externe computer met Server01.</span><span class="sxs-lookup"><span data-stu-id="bb851-147">The administrator starts by creating a sessions on a remote computer and running a script in the session.The first command uses the `New-PSSession` cmdlet to create the ITTask session on the Server01 remote computer.</span></span> <span data-ttu-id="bb851-148">De opdracht maakt gebruik van de para meter **configuratiepad** om de ITTasks-sessie configuratie op te geven.</span><span class="sxs-lookup"><span data-stu-id="bb851-148">The command uses the **ConfigurationName** parameter to specify the ITTasks session configuration.</span></span> <span data-ttu-id="bb851-149">Met de opdracht worden de sessies in de `$s` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="bb851-149">The command saves the sessions in the `$s` variable.</span></span>

<span data-ttu-id="bb851-150">De tweede opdracht- `Invoke-Command` cmdlet voor het starten van een achtergrond taak in de sessie in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="bb851-150">The second command `Invoke-Command` cmdlet to start a background job in the session in the `$s` variable.</span></span> <span data-ttu-id="bb851-151">Hierbij wordt de **filepath** -para meter gebruikt voor het uitvoeren van het script in de achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="bb851-151">It uses the **FilePath** parameter to run the script in the background job.</span></span>

<span data-ttu-id="bb851-152">De derde opdracht gebruikt de `Disconnect-PSSession` cmdlet om de verbinding met de sessie in de variabele te verbreken `$s` .</span><span class="sxs-lookup"><span data-stu-id="bb851-152">The third command uses the `Disconnect-PSSession` cmdlet to disconnect from the session in the `$s` variable.</span></span> <span data-ttu-id="bb851-153">De opdracht gebruikt de para meter **OutputBufferingMode** met de waarde drop om te voor komen dat het script wordt geblokkeerd door uitvoer naar de sessie te leveren.</span><span class="sxs-lookup"><span data-stu-id="bb851-153">The command uses the **OutputBufferingMode** parameter with a value of Drop to prevent the script from being blocked by having to deliver output to the session.</span></span> <span data-ttu-id="bb851-154">De para meter **IdleTimeoutSec** wordt gebruikt om de sessietime-out uit te breiden tot 15 uur.</span><span class="sxs-lookup"><span data-stu-id="bb851-154">It uses the **IdleTimeoutSec** parameter to extend the session time-out to 15 hours.</span></span> <span data-ttu-id="bb851-155">Wanneer de opdracht is voltooid, wordt de computer door de beheerder vergrendeld en blijft de eind avond thuis.</span><span class="sxs-lookup"><span data-stu-id="bb851-155">When the command is completed, the administrator locks her computer and goes home for the evening.</span></span>

<span data-ttu-id="bb851-156">Later die avond start de beheerder haar thuis computer, meldt zich aan bij het bedrijfs netwerk en start Power shell.</span><span class="sxs-lookup"><span data-stu-id="bb851-156">Later that evening, the administrator starts her home computer, logs on to the corporate network, and starts PowerShell.</span></span> <span data-ttu-id="bb851-157">De vierde opdracht gebruikt de `Get-PSSession` cmdlet om de sessies op de Server01-computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="bb851-157">The fourth command uses the `Get-PSSession` cmdlet to get the sessions on the Server01 computer.</span></span> <span data-ttu-id="bb851-158">De opdracht vindt de ITTask-sessie. De vijfde opdracht maakt gebruik van de `Connect-PSSession` cmdlet om verbinding te maken met de ITTask-sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-158">The command finds the ITTask session.The fifth command uses the `Connect-PSSession` cmdlet to connect to the ITTask session.</span></span> <span data-ttu-id="bb851-159">Met de opdracht wordt de sessie opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="bb851-159">The command saves the session in the `$s` variable.</span></span>

<span data-ttu-id="bb851-160">De zesde opdracht gebruikt de `Invoke-Command` cmdlet om een opdracht uit te voeren `Get-Job` in de sessie in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="bb851-160">The sixth command uses the `Invoke-Command` cmdlet to run a `Get-Job` command in the session in the `$s` variable.</span></span> <span data-ttu-id="bb851-161">In de uitvoer ziet u dat de taak is voltooid. De zevende opdracht gebruikt de `Invoke-Command` cmdlet om een opdracht uit te voeren `Receive-Job` in de sessie in de `$s` variabele in de sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-161">The output shows that the job finished successfully.The seventh command uses the `Invoke-Command` cmdlet to run a `Receive-Job` command in the session in the `$s` variable in the session.</span></span> <span data-ttu-id="bb851-162">Met de opdracht worden de resultaten opgeslagen in de `$BackupSpecs` variabele. De achtste opdracht gebruikt de `Invoke-Command` cmdlet om een ander script uit te voeren in de sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-162">The command saves the results in the `$BackupSpecs` variable.The eighth command uses the `Invoke-Command` cmdlet to runs another script in the session.</span></span> <span data-ttu-id="bb851-163">De opdracht gebruikt de waarde van de `$BackupSpecs` variabele in de sessie als invoer voor het script.</span><span class="sxs-lookup"><span data-stu-id="bb851-163">The command uses the value of the `$BackupSpecs` variable in the session as input to the script.</span></span>

```
PS C:\> $s = New-PSSession -ComputerName Server01 -Name ITTask -ConfigurationName ITTasks
PS C:\> Invoke-Command -Session $s {Start-Job -FilePath \\Server30\Scripts\Backup-SQLDatabase.ps1}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Running       True            Server01             \\Server30\Scripts\Backup...

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None

PS C:\> Get-PSSession -ComputerName Server01 -Name ITTask

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None


PS C:\> $s = Connect-PSSession -ComputerName Server01 -Name ITTask


Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Opened        ITTasks               Available

PS C:\> Invoke-Command -Session $s {Get-Job}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Completed     True            Server01             \\Server30\Scripts\Backup...

PS C:\> Invoke-Command -Session $s {$BackupSpecs = Receive-Job -JobName Job2}

PS C:\> Invoke-Command -Session $s {\\Server30\Scripts\New-SQLDatabase.ps1 -InitData $BackupSpecs.Initialization}

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None
```

<span data-ttu-id="bb851-164">De negende opdracht verbreekt de verbinding met de sessie in de `$s` variabele. De beheerder sluit Power shell en sluit de computer.</span><span class="sxs-lookup"><span data-stu-id="bb851-164">The ninth command disconnects from the session in the `$s` variable.The administrator closes PowerShell and closes the computer.</span></span> <span data-ttu-id="bb851-165">Ze kan de volgende dag opnieuw verbinding maken met de sessie en de script status van haar werk computer controleren.</span><span class="sxs-lookup"><span data-stu-id="bb851-165">She can reconnect to the session on the next day and check the script status from her work computer.</span></span>

## <span data-ttu-id="bb851-166">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bb851-166">PARAMETERS</span></span>

### <span data-ttu-id="bb851-167">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="bb851-167">-AllowRedirection</span></span>

<span data-ttu-id="bb851-168">Geeft aan dat deze cmdlet omleiding van deze verbinding met een alternatieve URI toestaat.</span><span class="sxs-lookup"><span data-stu-id="bb851-168">Indicates that this cmdlet allows redirection of this connection to an alternate URI.</span></span>

<span data-ttu-id="bb851-169">Wanneer u de para meter **ConnectionURI** gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI.</span><span class="sxs-lookup"><span data-stu-id="bb851-169">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="bb851-170">Standaard worden verbindingen niet door Power shell omgeleid, maar u kunt deze para meter gebruiken om de verbinding te omleiden.</span><span class="sxs-lookup"><span data-stu-id="bb851-170">By default, PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="bb851-171">U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de waarde van de **MaximumConnectionRedirectionCount** -sessie optie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="bb851-171">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="bb851-172">Gebruik de para meter **MaximumRedirection** van de `New-PSSessionOption` cmdlet of stel de eigenschap **MaximumConnectionRedirectionCount** van de voorkeurs variabele **$PSSessionOption** in.</span><span class="sxs-lookup"><span data-stu-id="bb851-172">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span> <span data-ttu-id="bb851-173">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="bb851-173">The default value is 5.</span></span>
<span data-ttu-id="bb851-174">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="bb851-174">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb851-175">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="bb851-175">-ApplicationName</span></span>

<span data-ttu-id="bb851-176">Hiermee geeft u de naam van een toepassing op.</span><span class="sxs-lookup"><span data-stu-id="bb851-176">Specifies the name of an application.</span></span> <span data-ttu-id="bb851-177">Deze cmdlet maakt alleen verbinding met sessies die gebruikmaken van de opgegeven toepassing.</span><span class="sxs-lookup"><span data-stu-id="bb851-177">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="bb851-178">Voer het segment van de toepassings naam van de verbindings-URI in.</span><span class="sxs-lookup"><span data-stu-id="bb851-178">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="bb851-179">In de volgende verbindings-URI is de naam van de toepassing bijvoorbeeld WSMan: `http://localhost:5985/WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="bb851-179">For example, in the following connection URI, the application name is WSMan: `http://localhost:5985/WSMAN`.</span></span> <span data-ttu-id="bb851-180">De toepassings naam van een sessie wordt opgeslagen in de eigenschap **runs Pace. Connection info. appName** van de sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-180">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="bb851-181">De waarde van deze para meter wordt gebruikt voor het selecteren en filteren van sessies.</span><span class="sxs-lookup"><span data-stu-id="bb851-181">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="bb851-182">De toepassing die door de sessie wordt gebruikt, wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="bb851-182">It does not change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, ComputerNameGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bb851-183">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="bb851-183">-Authentication</span></span>

<span data-ttu-id="bb851-184">Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van gebruikers referenties in de opdracht om opnieuw verbinding te maken met de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-184">Specifies the mechanism that is used to authenticate user credentials in the command to reconnect to the disconnected session.</span></span> <span data-ttu-id="bb851-185">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="bb851-185">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bb851-186">Standaard</span><span class="sxs-lookup"><span data-stu-id="bb851-186">Default</span></span>
- <span data-ttu-id="bb851-187">Basic</span><span class="sxs-lookup"><span data-stu-id="bb851-187">Basic</span></span>
- <span data-ttu-id="bb851-188">CredSSP</span><span class="sxs-lookup"><span data-stu-id="bb851-188">Credssp</span></span>
- <span data-ttu-id="bb851-189">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="bb851-189">Digest</span></span>
- <span data-ttu-id="bb851-190">Kerberos</span><span class="sxs-lookup"><span data-stu-id="bb851-190">Kerberos</span></span>
- <span data-ttu-id="bb851-191">Negotiate</span><span class="sxs-lookup"><span data-stu-id="bb851-191">Negotiate</span></span>
- <span data-ttu-id="bb851-192">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="bb851-192">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="bb851-193">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="bb851-193">The default value is Default.</span></span>

<span data-ttu-id="bb851-194">Zie [AuthenticationMechanism Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) in de MSDN-bibliotheek voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="bb851-194">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) in the MSDN library.</span></span>

> [!CAUTION]
> <span data-ttu-id="bb851-195">De verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="bb851-195">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="bb851-196">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="bb851-196">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="bb851-197">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="bb851-197">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, ComputerNameGuid, ConnectionUri, ConnectionUriGuid
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb851-198">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="bb851-198">-CertificateThumbprint</span></span>

<span data-ttu-id="bb851-199">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om verbinding te maken met de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-199">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="bb851-200">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="bb851-200">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="bb851-201">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="bb851-201">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="bb851-202">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts.</span><span class="sxs-lookup"><span data-stu-id="bb851-202">They can be mapped only to local user accounts.</span></span> <span data-ttu-id="bb851-203">Ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="bb851-203">They do not work with domain accounts.</span></span>

<span data-ttu-id="bb851-204">Als u een certificaat vingerafdruk wilt ophalen, gebruikt u een `Get-Item` of- `Get-ChildItem` opdracht in het Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="bb851-204">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, ComputerNameGuid, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb851-205">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="bb851-205">-ComputerName</span></span>

<span data-ttu-id="bb851-206">Hiermee geeft u de computers op waarop de niet-verbonden sessies worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="bb851-206">Specifies the computers on which the disconnected sessions are stored.</span></span> <span data-ttu-id="bb851-207">Sessies worden opgeslagen op de computer die zich aan de server zijde bevindt of het einde van een verbinding ontvangt.</span><span class="sxs-lookup"><span data-stu-id="bb851-207">Sessions are stored on the computer that is at the server-side or receiving end of a connection.</span></span> <span data-ttu-id="bb851-208">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bb851-208">The default is the local computer.</span></span>

<span data-ttu-id="bb851-209">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een computer.</span><span class="sxs-lookup"><span data-stu-id="bb851-209">Type the NetBIOS name, an IP address, or a fully qualified domain name of one computer.</span></span> <span data-ttu-id="bb851-210">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="bb851-210">Wildcard characters are not permitted.</span></span> <span data-ttu-id="bb851-211">Typ de computer naam, localhost of een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="bb851-211">To specify the local computer, type the computer name, localhost, or a dot (.)</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName, ComputerNameGuid
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb851-212">-Configuratiepad</span><span class="sxs-lookup"><span data-stu-id="bb851-212">-ConfigurationName</span></span>

<span data-ttu-id="bb851-213">Maakt alleen verbinding met sessies die gebruikmaken van de opgegeven sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="bb851-213">Connects only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="bb851-214">Voer een configuratie naam of de volledig gekwalificeerde resource-URI in voor een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="bb851-214">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="bb851-215">Als u alleen de configuratie naam opgeeft, wordt de volgende schema-URI voor voegsel: `http://schemas.microsoft.com/powershell` .</span><span class="sxs-lookup"><span data-stu-id="bb851-215">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span> <span data-ttu-id="bb851-216">De configuratie naam van een sessie wordt opgeslagen in de eigenschap **configuratiepad** van de sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-216">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="bb851-217">De waarde van deze para meter wordt gebruikt voor het selecteren en filteren van sessies.</span><span class="sxs-lookup"><span data-stu-id="bb851-217">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="bb851-218">De sessie configuratie die door de sessie wordt gebruikt, wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="bb851-218">It does not change the session configuration that the session uses.</span></span>

<span data-ttu-id="bb851-219">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="bb851-219">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, ComputerNameGuid, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bb851-220">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="bb851-220">-ConnectionUri</span></span>

<span data-ttu-id="bb851-221">Hiermee geeft u de Uri's van de verbindings eindpunten voor de niet-verbonden sessies.</span><span class="sxs-lookup"><span data-stu-id="bb851-221">Specifies the URIs of the connection endpoints for the disconnected sessions.</span></span>

<span data-ttu-id="bb851-222">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="bb851-222">The URI must be fully qualified.</span></span> <span data-ttu-id="bb851-223">De indeling van deze teken reeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="bb851-223">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="bb851-224">De standaard waarde is als volgt:</span><span class="sxs-lookup"><span data-stu-id="bb851-224">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="bb851-225">Als u geen verbindings-URI opgeeft, kunt u de para meters **UseSSL** en **Port** gebruiken om de verbindings-URI-waarden op te geven.</span><span class="sxs-lookup"><span data-stu-id="bb851-225">If you do not specify a connection URI, you can use the **UseSSL** and **Port** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="bb851-226">Geldige waarden voor het **transport** segment van de URI zijn http en HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bb851-226">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="bb851-227">Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met standaard poorten: 80 voor HTTP en 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bb851-227">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="bb851-228">Als u de standaard poorten voor externe communicatie van Power shell wilt gebruiken, geeft u poort 5985 voor HTTP of 5986 op voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bb851-228">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="bb851-229">Als de doel computer de verbinding omleidt naar een andere URI, wordt de omleiding door Power shell voor komen, tenzij u de para meter **AllowRedirection** in de opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bb851-229">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUri, ConnectionUriGuid
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bb851-230">-Credential</span><span class="sxs-lookup"><span data-stu-id="bb851-230">-Credential</span></span>

<span data-ttu-id="bb851-231">Hiermee geeft u een gebruikers account op dat is gemachtigd om verbinding te maken met de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-231">Specifies a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="bb851-232">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="bb851-232">The default is the current user.</span></span>

<span data-ttu-id="bb851-233">Typ een gebruikers naam, zoals `User01` of `Domain01\User01` , of voer een `PSCredential` object in dat door de `Get-Credential` cmdlet wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="bb851-233">Type a user name, such as `User01` or `Domain01\User01`, or enter a `PSCredential` object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="bb851-234">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="bb851-234">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="bb851-235">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="bb851-235">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="bb851-236">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="bb851-236">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, ComputerNameGuid, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb851-237">-Id</span><span class="sxs-lookup"><span data-stu-id="bb851-237">-Id</span></span>

<span data-ttu-id="bb851-238">Hiermee geeft u de Id's van de niet-verbonden sessies.</span><span class="sxs-lookup"><span data-stu-id="bb851-238">Specifies the IDs of the disconnected sessions.</span></span> <span data-ttu-id="bb851-239">De **id-** para meter werkt alleen wanneer de verbroken sessie eerder is verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-239">The **Id** parameter works only when the disconnected session was previously connected to the current session.</span></span>

<span data-ttu-id="bb851-240">Deze para meter is geldig, maar niet effectief, wanneer de sessie wordt opgeslagen op de lokale computer, maar niet is verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-240">This parameter is valid, but not effective, when the session is stored on the local computer, but was not connected to the current session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bb851-241">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="bb851-241">-InstanceId</span></span>

<span data-ttu-id="bb851-242">Hiermee geeft u de exemplaar-Id's van de niet-verbonden sessies.</span><span class="sxs-lookup"><span data-stu-id="bb851-242">Specifies the instance IDs of the disconnected sessions.</span></span>

<span data-ttu-id="bb851-243">De exemplaar-ID is een unieke aanduiding voor een **PSSession** op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="bb851-243">The instance ID is a GUID that uniquely identifies a **PSSession** on a local or remote computer.</span></span>

<span data-ttu-id="bb851-244">De exemplaar-ID wordt opgeslagen in de eigenschap **InstanceId** van de **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="bb851-244">The instance ID is stored in the **InstanceID** property of the **PSSession**.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: ComputerNameGuid, ConnectionUriGuid, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb851-245">-Name</span><span class="sxs-lookup"><span data-stu-id="bb851-245">-Name</span></span>

<span data-ttu-id="bb851-246">Hiermee geeft u de beschrijvende namen van de niet-verbonden sessies.</span><span class="sxs-lookup"><span data-stu-id="bb851-246">Specifies the friendly names of the disconnected sessions.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri
Aliases:

Required: True (Name), False (ComputerName, ConnectionUri)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb851-247">-Port</span><span class="sxs-lookup"><span data-stu-id="bb851-247">-Port</span></span>

<span data-ttu-id="bb851-248">Hiermee geeft u de netwerk poort op de externe computer op die wordt gebruikt om opnieuw verbinding te maken met de sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-248">Specifies the network port on the remote computer that is used to reconnect to the session.</span></span> <span data-ttu-id="bb851-249">Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bb851-249">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="bb851-250">De standaard poorten zijn 5985, de WinRM-poort voor HTTP en 5986, de WinRM-poort voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bb851-250">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="bb851-251">Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren.</span><span class="sxs-lookup"><span data-stu-id="bb851-251">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="bb851-252">Als u de listener wilt configureren, typt u de volgende twee opdrachten bij de Power shell-prompt:</span><span class="sxs-lookup"><span data-stu-id="bb851-252">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="bb851-253">Gebruik de para meter **poort** alleen als dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="bb851-253">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="bb851-254">De poort die in de opdracht is ingesteld, is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bb851-254">The port that is set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="bb851-255">Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.</span><span class="sxs-lookup"><span data-stu-id="bb851-255">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, ComputerNameGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb851-256">-Sessie</span><span class="sxs-lookup"><span data-stu-id="bb851-256">-Session</span></span>

<span data-ttu-id="bb851-257">Hiermee geeft u de verbroken sessies.</span><span class="sxs-lookup"><span data-stu-id="bb851-257">Specifies the disconnected sessions.</span></span> <span data-ttu-id="bb851-258">Voer een variabele in die de **PSSession** -objecten bevat of een opdracht waarmee de **PSSession** -objecten, zoals een opdracht, worden gemaakt of opgehaald `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="bb851-258">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bb851-259">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="bb851-259">-SessionOption</span></span>

<span data-ttu-id="bb851-260">Hiermee geeft u geavanceerde opties voor de sessie op.</span><span class="sxs-lookup"><span data-stu-id="bb851-260">Specifies advanced options for the session.</span></span> <span data-ttu-id="bb851-261">Voer een **SessionOption** -object in, zoals het, dat u maakt met behulp van de `New-PSSessionOption` cmdlet of een hash-tabel waarin de sleutels de naam van de sessie optie zijn en de waarden voor de waarden van de sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-261">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="bb851-262">De standaard waarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="bb851-262">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="bb851-263">Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="bb851-263">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="bb851-264">De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="bb851-264">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="bb851-265">Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="bb851-265">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="bb851-266">Zie voor een beschrijving van de sessie opties die de standaard waarden bevatten `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="bb851-266">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="bb851-267">Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie over de **$PSSessionOption** voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="bb851-267">For information about the **$PSSessionOption** preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="bb851-268">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="bb851-268">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, ComputerNameGuid, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb851-269">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="bb851-269">-ThrottleLimit</span></span>

<span data-ttu-id="bb851-270">Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="bb851-270">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="bb851-271">Als u deze para meter weglaat of een waarde van 0 invoert, wordt de standaard waarde 32 gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bb851-271">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="bb851-272">De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="bb851-272">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb851-273">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="bb851-273">-UseSSL</span></span>

<span data-ttu-id="bb851-274">Geeft aan dat deze cmdlet het Secure Sockets Layer-Protocol (SSL) gebruikt om verbinding te maken met de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-274">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to connect to the disconnected session.</span></span> <span data-ttu-id="bb851-275">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bb851-275">By default, SSL is not used.</span></span>

<span data-ttu-id="bb851-276">WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="bb851-276">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="bb851-277">De para meter **UseSSL** is een extra beveiliging waarmee de gegevens worden verzonden via een HTTPS-verbinding in plaats van via een http-verbinding.</span><span class="sxs-lookup"><span data-stu-id="bb851-277">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="bb851-278">Als u deze para meter gebruikt, maar SSL is niet beschikbaar op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="bb851-278">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, ComputerNameGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb851-279">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bb851-279">-Confirm</span></span>

<span data-ttu-id="bb851-280">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="bb851-280">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="bb851-281">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bb851-281">-WhatIf</span></span>

<span data-ttu-id="bb851-282">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="bb851-282">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="bb851-283">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bb851-283">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="bb851-284">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bb851-284">CommonParameters</span></span>

<span data-ttu-id="bb851-285">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bb851-285">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bb851-286">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bb851-286">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bb851-287">INVOER</span><span class="sxs-lookup"><span data-stu-id="bb851-287">INPUTS</span></span>

### <span data-ttu-id="bb851-288">System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="bb851-288">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="bb851-289">U kunt een sessie ( **PSSession** ) door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bb851-289">You can pipe a session ( **PSSession** ) to this cmdlet.</span></span>

## <span data-ttu-id="bb851-290">UITVOER</span><span class="sxs-lookup"><span data-stu-id="bb851-290">OUTPUTS</span></span>

### <span data-ttu-id="bb851-291">System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="bb851-291">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="bb851-292">Met deze cmdlet wordt een object geretourneerd dat de sessie vertegenwoordigt waarmee de verbinding is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bb851-292">This cmdlet returns an object that represents the session to which it reconnected.</span></span>

## <span data-ttu-id="bb851-293">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="bb851-293">NOTES</span></span>

- <span data-ttu-id="bb851-294">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="bb851-294">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="bb851-295">`Connect-PSSession` opnieuw verbinding maken met sessies die niet zijn verbonden, dat wil zeggen, sessies waarvan de waarde voor de eigenschap **State** is verbroken.</span><span class="sxs-lookup"><span data-stu-id="bb851-295">`Connect-PSSession` reconnects only to sessions that are disconnected, that is, sessions that have a value of Disconnected for the **State** property.</span></span> <span data-ttu-id="bb851-296">Alleen sessies die zijn verbonden met of eindigen op computers waarop Windows Power Shell 3,0 of hoger wordt uitgevoerd, kunnen worden losgekoppeld en opnieuw worden aangesloten.</span><span class="sxs-lookup"><span data-stu-id="bb851-296">Only sessions that are connected to, or end at, computers that run Windows PowerShell 3.0 or later versions can be disconnected and reconnected.</span></span>

- <span data-ttu-id="bb851-297">Als u gebruikt `Connect-PSSession` voor een sessie die niet wordt losgekoppeld, is de opdracht niet van invloed op de sessie en worden er geen fouten gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="bb851-297">If you use `Connect-PSSession` on a session that is not disconnected, the command does not affect the session and it does not generate errors.</span></span>

- <span data-ttu-id="bb851-298">Verbroken loop Back-sessies met interactieve tokens, die worden gemaakt met behulp van de para meter **EnableNetworkAccess** , kunnen alleen opnieuw worden verbonden vanaf de computer waarop de sessie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bb851-298">Disconnected loopback sessions with interactive tokens, which are created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="bb851-299">Met deze beperking wordt de computer beschermd tegen kwaadwillende toegang.</span><span class="sxs-lookup"><span data-stu-id="bb851-299">This restriction protects the computer from malicious access.</span></span>

- <span data-ttu-id="bb851-300">De waarde van de eigenschap **State** van een **PSSession** is relatief ten opzichte van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-300">The value of the **State** property of a **PSSession** is relative to the current session.</span></span>
  <span data-ttu-id="bb851-301">Als de waarde voor de **verbinding is verbroken** , betekent dit daarom dat de **PSSession** niet is verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-301">Therefore, a value of **Disconnected** means that the **PSSession** is not connected to the current session.</span></span> <span data-ttu-id="bb851-302">Het betekent echter niet dat de **PSSession** -verbinding met alle sessies is verbroken.</span><span class="sxs-lookup"><span data-stu-id="bb851-302">However, it does not mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="bb851-303">Deze is mogelijk verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-303">It might be connected to a different session.</span></span> <span data-ttu-id="bb851-304">Gebruik de eigenschap **Beschik baarheid** om te bepalen of u verbinding kunt maken met de sessie of er opnieuw verbinding mee wilt maken.</span><span class="sxs-lookup"><span data-stu-id="bb851-304">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

  <span data-ttu-id="bb851-305">Een **beschikbaarheids** waarde van geen geeft aan dat u verbinding kunt maken met de sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-305">An **Availability** value of None indicates that you can connect to the session.</span></span> <span data-ttu-id="bb851-306">De waarde bezet geeft aan dat u geen verbinding kunt maken met de **PSSession** omdat deze is verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-306">A value of Busy indicates that you cannot connect to the **PSSession** because it is connected to another session.</span></span>

  <span data-ttu-id="bb851-307">Zie [RunspaceState Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspacestate) in de MSDN-bibliotheek voor meer informatie over de waarden van de eigenschap **State** van sessies.</span><span class="sxs-lookup"><span data-stu-id="bb851-307">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspacestate) in the MSDN library.</span></span>

  <span data-ttu-id="bb851-308">Zie [RunspaceAvailability Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspaceavailability) in de MSDN-bibliotheek voor meer informatie over de waarden van de eigenschap **Availability** van sessies.</span><span class="sxs-lookup"><span data-stu-id="bb851-308">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspaceavailability) in the MSDN library.</span></span>

- <span data-ttu-id="bb851-309">U kunt de time-outwaarde voor inactiviteit van een **PSSession** niet wijzigen wanneer u verbinding maakt met de **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="bb851-309">You cannot change the idle time-out value of a **PSSession** when you connect to the **PSSession**.</span></span> <span data-ttu-id="bb851-310">De para meter **SessionOption** van `Connect-PSSession` maakt een **SessionOption** -object met een **IdleTimeout** -waarde.</span><span class="sxs-lookup"><span data-stu-id="bb851-310">The **SessionOption** parameter of `Connect-PSSession` takes a **SessionOption** object that has an **IdleTimeout** value.</span></span> <span data-ttu-id="bb851-311">De waarde **IdleTimeout** van het object **SessionOption** en de waarde **IdleTimeout** van de `$PSSessionOption` variabele wordt echter genegeerd wanneer er verbinding wordt gemaakt met een **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="bb851-311">However, the **IdleTimeout** value of the **SessionOption** object and the **IdleTimeout** value of the `$PSSessionOption` variable are ignored when connecting to a **PSSession**.</span></span>

  <span data-ttu-id="bb851-312">U kunt de time-out voor inactiviteit van een **PSSession** instellen en wijzigen wanneer u de **PSSession** maakt met behulp van de- `New-PSSession` of `Invoke-Command` -cmdlets en wanneer u de verbinding met de **PSSession** verbreekt.</span><span class="sxs-lookup"><span data-stu-id="bb851-312">You can set and change the idle time-out of a **PSSession** when you create the **PSSession** , by using the `New-PSSession` or `Invoke-Command` cmdlets, and when you disconnect from the **PSSession**.</span></span>

  <span data-ttu-id="bb851-313">De eigenschap **IdleTimeout** van een **PSSession** is essentieel voor verbroken sessies, omdat deze bepaalt hoe lang een verbroken sessie op de externe computer wordt onderhouden.</span><span class="sxs-lookup"><span data-stu-id="bb851-313">The **IdleTimeout** property of a **PSSession** is critical to disconnected sessions, because it determines how long a disconnected session is maintained on the remote computer.</span></span> <span data-ttu-id="bb851-314">Verbroken sessies worden beschouwd als niet-actief vanaf het moment dat ze worden losgekoppeld, zelfs als opdrachten worden uitgevoerd in de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="bb851-314">Disconnected sessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

## <span data-ttu-id="bb851-315">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="bb851-315">RELATED LINKS</span></span>

[<span data-ttu-id="bb851-316">Verbinding verbreken-PSSession</span><span class="sxs-lookup"><span data-stu-id="bb851-316">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="bb851-317">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="bb851-317">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="bb851-318">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="bb851-318">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="bb851-319">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="bb851-319">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="bb851-320">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bb851-320">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="bb851-321">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="bb851-321">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="bb851-322">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="bb851-322">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="bb851-323">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="bb851-323">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="bb851-324">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="bb851-324">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="bb851-325">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bb851-325">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="bb851-326">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="bb851-326">Remove-PSSession</span></span>](Remove-PSSession.md)
