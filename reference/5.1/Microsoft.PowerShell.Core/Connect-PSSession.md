---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/connect-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-PSSession
ms.openlocfilehash: d4f071b4c106735e622281f728b8632c211a813d
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251495"
---
# <span data-ttu-id="46bda-103">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="46bda-103">Connect-PSSession</span></span>

## <span data-ttu-id="46bda-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="46bda-104">SYNOPSIS</span></span>
<span data-ttu-id="46bda-105">Opnieuw verbinding maken met verbroken sessies.</span><span class="sxs-lookup"><span data-stu-id="46bda-105">Reconnects to disconnected sessions.</span></span>

## <span data-ttu-id="46bda-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="46bda-106">SYNTAX</span></span>

### <span data-ttu-id="46bda-107">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="46bda-107">Name (Default)</span></span>

```
Connect-PSSession -Name <String[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="46bda-108">Sessie</span><span class="sxs-lookup"><span data-stu-id="46bda-108">Session</span></span>

```
Connect-PSSession [-Session] <PSSession[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="46bda-109">ComputerName</span><span class="sxs-lookup"><span data-stu-id="46bda-109">ComputerName</span></span>

```
Connect-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="46bda-110">ComputerNameGuid</span><span class="sxs-lookup"><span data-stu-id="46bda-110">ComputerNameGuid</span></span>

```
Connect-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="46bda-111">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="46bda-111">ConnectionUri</span></span>

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="46bda-112">ConnectionUriGuid</span><span class="sxs-lookup"><span data-stu-id="46bda-112">ConnectionUriGuid</span></span>

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="46bda-113">InstanceId</span><span class="sxs-lookup"><span data-stu-id="46bda-113">InstanceId</span></span>

```
Connect-PSSession -InstanceId <Guid[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="46bda-114">Id</span><span class="sxs-lookup"><span data-stu-id="46bda-114">Id</span></span>

```
Connect-PSSession [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="46bda-115">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="46bda-115">DESCRIPTION</span></span>

<span data-ttu-id="46bda-116">De cmdlet **Connect-PSSession** maakt opnieuw verbinding met door gebruikers beheerde Windows Power shell-sessies ( **PSSessions** ) die zijn losgekoppeld.</span><span class="sxs-lookup"><span data-stu-id="46bda-116">The **Connect-PSSession** cmdlet reconnects to user-managed Windows PowerShell sessions ( **PSSessions** ) that were disconnected.</span></span>
<span data-ttu-id="46bda-117">Het werkt op sessies die opzettelijk worden verbroken, zoals met behulp van de Disconnect-PSSession cmdlet of de para meter *InDisconnectedSession* van de cmdlet Invoke-Command, en die onbedoeld zijn losgekoppeld, bijvoorbeeld door een tijdelijke netwerk storing.</span><span class="sxs-lookup"><span data-stu-id="46bda-117">It works on sessions that are disconnected intentionally, such as by using the Disconnect-PSSession cmdlet or the *InDisconnectedSession* parameter of the Invoke-Command cmdlet, and those that were disconnected unintentionally, such as by a temporary network outage.</span></span>

<span data-ttu-id="46bda-118">**Connect-PSSession** kan verbinding maken met elke verbroken sessie die is gestart door dezelfde gebruiker.</span><span class="sxs-lookup"><span data-stu-id="46bda-118">**Connect-PSSession** can connect to any disconnected session that was started by the same user.</span></span>
<span data-ttu-id="46bda-119">Dit zijn onder andere de verbindingen die zijn gestart door of losgekoppeld van andere sessies op andere computers.</span><span class="sxs-lookup"><span data-stu-id="46bda-119">These include those that were started by or disconnected from other sessions on other computers.</span></span>

<span data-ttu-id="46bda-120">**Connect-PSSession** kan echter geen verbinding maken met verbroken of gesloten sessies of interactieve sessies die zijn gestart met behulp van de cmdlet Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="46bda-120">However, **Connect-PSSession** cannot connect to broken or closed sessions, or interactive sessions started by using the Enter-PSSession cmdlet.</span></span>
<span data-ttu-id="46bda-121">Het is ook niet mogelijk om sessies te verbinden met sessies die zijn gestart door andere gebruikers, tenzij u de referenties kunt opgeven van de gebruiker die de sessie heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="46bda-121">Also you cannot connect sessions to sessions started by other users, unless you can provide the credentials of the user who created the session.</span></span>

<span data-ttu-id="46bda-122">Zie [about_Remote_Disconnected_Sessions](About/about_Remote_Disconnected_Sessions.md)voor meer informatie over de functie voor verbroken sessies.</span><span class="sxs-lookup"><span data-stu-id="46bda-122">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](About/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="46bda-123">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="46bda-123">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="46bda-124">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="46bda-124">EXAMPLES</span></span>

### <span data-ttu-id="46bda-125">Voor beeld 1: opnieuw verbinding maken met een sessie</span><span class="sxs-lookup"><span data-stu-id="46bda-125">Example 1: Reconnect to a session</span></span>

```
PS C:\> Connect-PSSession -ComputerName Server01 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Opened        ITTasks                  Available
```

<span data-ttu-id="46bda-126">Met deze opdracht wordt opnieuw verbinding gemaakt met de ITTask-sessie op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="46bda-126">This command reconnects to the ITTask session on the Server01 computer.</span></span>

<span data-ttu-id="46bda-127">In de uitvoer ziet u dat de opdracht is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="46bda-127">The output shows that the command was successful.</span></span>
<span data-ttu-id="46bda-128">De **status** van de sessie wordt geopend en de **Beschik baarheid** is beschikbaar. Dit geeft aan dat u opdrachten in de sessie kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="46bda-128">The **State** of the session is Opened and the **Availability** is Available, which indicates that you can run commands in the session.</span></span>

### <span data-ttu-id="46bda-129">Voor beeld 2: gevolgen van het verbreken van de verbinding en opnieuw verbinden</span><span class="sxs-lookup"><span data-stu-id="46bda-129">Example 2: Effect of disconnecting and reconnecting</span></span>

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

<span data-ttu-id="46bda-130">In dit voor beeld ziet u het effect van het verbreken van de verbinding en vervolgens de verbinding met een sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-130">This example shows the effect of disconnecting and then reconnecting to a session.</span></span>

<span data-ttu-id="46bda-131">De eerste opdracht maakt gebruik van de cmdlet Get-PSSession.</span><span class="sxs-lookup"><span data-stu-id="46bda-131">The first command uses the Get-PSSession cmdlet.</span></span>
<span data-ttu-id="46bda-132">Zonder de para meter *ComputerName* worden met de opdracht alleen sessies opgehaald die in de huidige sessie zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="46bda-132">Without the *ComputerName* parameter, the command gets only sessions that were created in the current session.</span></span>

<span data-ttu-id="46bda-133">In de uitvoer ziet u dat met de opdracht de back-upsessie wordt opgehaald op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="46bda-133">The output shows that the command gets the Backups session on the local computer.</span></span>
<span data-ttu-id="46bda-134">De **status** van de sessie wordt geopend en de **Beschik baarheid** is beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="46bda-134">The **State** of the session is Opened and the **Availability** is Available.</span></span>

<span data-ttu-id="46bda-135">De tweede opdracht maakt gebruik van de cmdlet **Get-PSSession** om de **PSSession** -objecten op te halen die zijn gemaakt in de huidige sessie en de cmdlet **Disconnect-PSSession** om de sessie te verbreken.</span><span class="sxs-lookup"><span data-stu-id="46bda-135">The second command uses the **Get-PSSession** cmdlet to get the **PSSession** objects that were created in the current session and the **Disconnect-PSSession** cmdlet to disconnect the sessions.</span></span>
<span data-ttu-id="46bda-136">In de uitvoer ziet u dat de verbinding met de back-upsessie is verbroken.</span><span class="sxs-lookup"><span data-stu-id="46bda-136">The output shows that the Backups session was disconnected.</span></span>
<span data-ttu-id="46bda-137">De **status** van de sessie wordt verbroken en de **Beschik baarheid** is geen.</span><span class="sxs-lookup"><span data-stu-id="46bda-137">The **State** of the session is Disconnected and the **Availability** is None.</span></span>

<span data-ttu-id="46bda-138">De derde opdracht maakt gebruik van de cmdlet **Get-PSSession** om de **PSSession** -objecten op te halen die zijn gemaakt in de huidige sessie en de cmdlet **Connect-PSSession** om de sessies opnieuw te verbinden.</span><span class="sxs-lookup"><span data-stu-id="46bda-138">The third command uses the **Get-PSSession** cmdlet to get the **PSSession** objects that were created in the current session and the **Connect-PSSession** cmdlet to reconnect the sessions.</span></span>
<span data-ttu-id="46bda-139">In de uitvoer ziet u dat er opnieuw verbinding is gemaakt met de back-up van de sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-139">The output shows that the Backups session was reconnected.</span></span>
<span data-ttu-id="46bda-140">De **status** van de sessie wordt geopend en de **Beschik baarheid** is beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="46bda-140">The **State** of the session is Opened and the **Availability** is Available.</span></span>

<span data-ttu-id="46bda-141">Als u de cmdlet **Connect-PSSession** gebruikt voor een sessie die niet wordt losgekoppeld, is de opdracht niet van invloed op de sessie en worden er geen fouten gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="46bda-141">If you use the **Connect-PSSession** cmdlet on a session that is not disconnected, the command does not affect the session and it does not generate any errors.</span></span>

### <span data-ttu-id="46bda-142">Voor beeld 3: reeks opdrachten in een bedrijfs scenario</span><span class="sxs-lookup"><span data-stu-id="46bda-142">Example 3: Series of commands in an enterprise scenario</span></span>

```
The administrator starts by creating a sessions on a remote computer and running a script in the session.The first command uses the **New-PSSession** cmdlet to create the ITTask session on the Server01 remote computer. The command uses the *ConfigurationName* parameter to specify the ITTasks session configuration. The command saves the sessions in the $s variable.
PS C:\> $s = New-PSSession -ComputerName Server01 -Name ITTask -ConfigurationName ITTasks

 The second command **Invoke-Command** cmdlet to start a background job in the session in the $s variable. It uses the *FilePath* parameter to run the script in the background job.
PS C:\> Invoke-Command -Session $s {Start-Job -FilePath \\Server30\Scripts\Backup-SQLDatabase.ps1}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Running       True            Server01             \\Server30\Scripts\Backup...

The third command uses the Disconnect-PSSession cmdlet to disconnect from the session in the $s variable. The command uses the *OutputBufferingMode* parameter with a value of Drop to prevent the script from being blocked by having to deliver output to the session. It uses the *IdleTimeoutSec* parameter to extend the session time-out to 15 hours.When the command is completed, the administrator locks her computer and goes home for the evening.
PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None

Later that evening, the administrator starts her home computer, logs on to the corporate network, and starts Windows PowerShell. The fourth command uses the Get-PSSession cmdlet to get the sessions on the Server01 computer. The command finds the ITTask session.The fifth command uses the **Connect-PSSession** cmdlet to connect to the ITTask session. The command saves the session in the $s variable.
PS C:\> Get-PSSession -ComputerName Server01 -Name ITTask

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None


PS C:\> $s = Connect-PSSession -ComputerName Server01 -Name ITTask


Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Opened        ITTasks               Available

The sixth command uses the **Invoke-Command** cmdlet to run a Get-Job command in the session in the $s variable. The output shows that the job finished successfully.The seventh command uses the **Invoke-Command** cmdlet to run a Receive-Job command in the session in the $s variable in the session. The command saves the results in the $BackupSpecs variable.The eighth command uses the **Invoke-Command** cmdlet to runs another script in the session. The command uses the value of the $BackupSpecs variable in the session as input to the script.


PS C:\> Invoke-Command -Session $s {Get-Job}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Completed     True            Server01             \\Server30\Scripts\Backup...

PS C:\> Invoke-Command -Session $s {$BackupSpecs = Receive-Job -JobName Job2}

PS C:\> Invoke-Command -Session $s {\\Server30\Scripts\New-SQLDatabase.ps1 -InitData $BackupSpecs.Initialization}

The ninth command disconnects from the session in the $s variable.The administrator closes Windows PowerShell and closes the computer. She can reconnect to the session on the next day and check the script status from her work computer.
PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None
```

<span data-ttu-id="46bda-143">In deze reeks opdrachten ziet u hoe de cmdlet **Connect-PSSession** kan worden gebruikt in een bedrijfs scenario.</span><span class="sxs-lookup"><span data-stu-id="46bda-143">This series of commands shows how the **Connect-PSSession** cmdlet might be used in an enterprise scenario.</span></span>
<span data-ttu-id="46bda-144">In dit geval start een systeem beheerder een langlopende taak in een sessie op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="46bda-144">In this case, a system administrator starts a long-running job in a session on a remote computer.</span></span>
<span data-ttu-id="46bda-145">Nadat de taak is gestart, wordt de verbinding met de sessie verbroken en gaat de beheerder naar thuis.</span><span class="sxs-lookup"><span data-stu-id="46bda-145">After starting the job, the administrator disconnects from the session and goes home.</span></span>
<span data-ttu-id="46bda-146">Later die avond meldt de beheerder zich aan bij haar computer thuis en wordt gecontroleerd of de taak is uitgevoerd totdat deze is voltooid.</span><span class="sxs-lookup"><span data-stu-id="46bda-146">Later that evening, the administrator logs on to her home computer and verifies that the job ran until it is completed.</span></span>

## <span data-ttu-id="46bda-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="46bda-147">PARAMETERS</span></span>

### <span data-ttu-id="46bda-148">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="46bda-148">-AllowRedirection</span></span>

<span data-ttu-id="46bda-149">Geeft aan dat deze cmdlet omleiding van deze verbinding met een alternatieve URI toestaat.</span><span class="sxs-lookup"><span data-stu-id="46bda-149">Indicates that this cmdlet allows redirection of this connection to an alternate URI.</span></span>

<span data-ttu-id="46bda-150">Wanneer u de para meter *ConnectionURI* gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI.</span><span class="sxs-lookup"><span data-stu-id="46bda-150">When you use the *ConnectionURI* parameter, the remote destination can return an instruction to redirect to a different URI.</span></span>
<span data-ttu-id="46bda-151">Standaard worden verbindingen niet door Windows Power shell omgeleid, maar u kunt deze para meter gebruiken om de verbinding door te sturen.</span><span class="sxs-lookup"><span data-stu-id="46bda-151">By default, Windows PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="46bda-152">U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de waarde van de **MaximumConnectionRedirectionCount** -sessie optie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="46bda-152">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span>
<span data-ttu-id="46bda-153">Gebruik de para meter *MaximumRedirection* van de cmdlet New-PSSessionOption of stel de eigenschap **MaximumConnectionRedirectionCount** van de voorkeurs variabele **$PSSessionOption** in.</span><span class="sxs-lookup"><span data-stu-id="46bda-153">Use the *MaximumRedirection* parameter of the New-PSSessionOption cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span>
<span data-ttu-id="46bda-154">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="46bda-154">The default value is 5.</span></span>

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

### <span data-ttu-id="46bda-155">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="46bda-155">-ApplicationName</span></span>

<span data-ttu-id="46bda-156">Hiermee geeft u de naam van een toepassing op.</span><span class="sxs-lookup"><span data-stu-id="46bda-156">Specifies the name of an application.</span></span>
<span data-ttu-id="46bda-157">Deze cmdlet maakt alleen verbinding met sessies die gebruikmaken van de opgegeven toepassing.</span><span class="sxs-lookup"><span data-stu-id="46bda-157">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="46bda-158">Voer het segment van de toepassings naam van de verbindings-URI in.</span><span class="sxs-lookup"><span data-stu-id="46bda-158">Enter the application name segment of the connection URI.</span></span>
<span data-ttu-id="46bda-159">In de volgende verbindings-URI is de naam van de toepassing bijvoorbeeld WSMan: `http://localhost:5985/WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="46bda-159">For example, in the following connection URI, the application name is WSMan: `http://localhost:5985/WSMAN`.</span></span>
<span data-ttu-id="46bda-160">De toepassings naam van een sessie wordt opgeslagen in de eigenschap **runs Pace. Connection info. appName** van de sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-160">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="46bda-161">De waarde van deze para meter wordt gebruikt voor het selecteren en filteren van sessies.</span><span class="sxs-lookup"><span data-stu-id="46bda-161">The value of this parameter is used to select and filter sessions.</span></span>
<span data-ttu-id="46bda-162">De toepassing die door de sessie wordt gebruikt, wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="46bda-162">It does not change the application that the session uses.</span></span>

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

### <span data-ttu-id="46bda-163">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="46bda-163">-Authentication</span></span>

<span data-ttu-id="46bda-164">Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van gebruikers referenties in de opdracht om opnieuw verbinding te maken met de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-164">Specifies the mechanism that is used to authenticate user credentials in the command to reconnect to the disconnected session.</span></span> <span data-ttu-id="46bda-165">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="46bda-165">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="46bda-166">Standaard</span><span class="sxs-lookup"><span data-stu-id="46bda-166">Default</span></span>
- <span data-ttu-id="46bda-167">Basic</span><span class="sxs-lookup"><span data-stu-id="46bda-167">Basic</span></span>
- <span data-ttu-id="46bda-168">CredSSP</span><span class="sxs-lookup"><span data-stu-id="46bda-168">Credssp</span></span>
- <span data-ttu-id="46bda-169">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="46bda-169">Digest</span></span>
- <span data-ttu-id="46bda-170">Kerberos</span><span class="sxs-lookup"><span data-stu-id="46bda-170">Kerberos</span></span>
- <span data-ttu-id="46bda-171">Negotiate</span><span class="sxs-lookup"><span data-stu-id="46bda-171">Negotiate</span></span>
- <span data-ttu-id="46bda-172">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="46bda-172">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="46bda-173">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="46bda-173">The default value is Default.</span></span>

<span data-ttu-id="46bda-174">Zie [AuthenticationMechanism Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) in de MSDN-bibliotheek voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="46bda-174">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) in the MSDN library.</span></span>

<span data-ttu-id="46bda-175">Let op: de verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten die verificatie vereisen voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="46bda-175">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
<span data-ttu-id="46bda-176">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="46bda-176">This mechanism increases the security risk of the remote operation.</span></span>
<span data-ttu-id="46bda-177">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="46bda-177">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

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

### <span data-ttu-id="46bda-178">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="46bda-178">-CertificateThumbprint</span></span>

<span data-ttu-id="46bda-179">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om verbinding te maken met de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-179">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="46bda-180">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="46bda-180">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="46bda-181">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="46bda-181">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="46bda-182">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts.</span><span class="sxs-lookup"><span data-stu-id="46bda-182">They can be mapped only to local user accounts.</span></span>
<span data-ttu-id="46bda-183">Ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="46bda-183">They do not work with domain accounts.</span></span>

<span data-ttu-id="46bda-184">Als u een certificaat vingerafdruk wilt krijgen, gebruikt u een Get-Item-of Get-ChildItem opdracht in het Windows Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="46bda-184">To get a certificate thumbprint, use a Get-Item or Get-ChildItem command in the Windows PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="46bda-185">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="46bda-185">-ComputerName</span></span>

<span data-ttu-id="46bda-186">Hiermee geeft u de computers op waarop de niet-verbonden sessies worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="46bda-186">Specifies the computers on which the disconnected sessions are stored.</span></span>
<span data-ttu-id="46bda-187">Sessies worden opgeslagen op de computer die zich aan de server zijde bevindt of het einde van een verbinding ontvangt.</span><span class="sxs-lookup"><span data-stu-id="46bda-187">Sessions are stored on the computer that is at the server-side or receiving end of a connection.</span></span>
<span data-ttu-id="46bda-188">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="46bda-188">The default is the local computer.</span></span>

<span data-ttu-id="46bda-189">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een computer.</span><span class="sxs-lookup"><span data-stu-id="46bda-189">Type the NetBIOS name, an IP address, or a fully qualified domain name of one computer.</span></span>
<span data-ttu-id="46bda-190">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="46bda-190">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="46bda-191">Typ de computer naam, localhost of een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="46bda-191">To specify the local computer, type the computer name, localhost, or a dot (.)</span></span>

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

### <span data-ttu-id="46bda-192">-Configuratiepad</span><span class="sxs-lookup"><span data-stu-id="46bda-192">-ConfigurationName</span></span>

<span data-ttu-id="46bda-193">Maakt alleen verbinding met sessies die gebruikmaken van de opgegeven sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="46bda-193">Connects only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="46bda-194">Voer een configuratie naam of de volledig gekwalificeerde resource-URI in voor een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="46bda-194">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span>
<span data-ttu-id="46bda-195">Als u alleen de configuratie naam opgeeft, wordt de volgende schema-URI voor voegsel: `http://schemas.microsoft.com/powershell` .</span><span class="sxs-lookup"><span data-stu-id="46bda-195">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span>
<span data-ttu-id="46bda-196">De configuratie naam van een sessie wordt opgeslagen in de eigenschap **configuratiepad** van de sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-196">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="46bda-197">De waarde van deze para meter wordt gebruikt voor het selecteren en filteren van sessies.</span><span class="sxs-lookup"><span data-stu-id="46bda-197">The value of this parameter is used to select and filter sessions.</span></span>
<span data-ttu-id="46bda-198">De sessie configuratie die door de sessie wordt gebruikt, wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="46bda-198">It does not change the session configuration that the session uses.</span></span>

<span data-ttu-id="46bda-199">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="46bda-199">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

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

### <span data-ttu-id="46bda-200">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="46bda-200">-ConnectionUri</span></span>

<span data-ttu-id="46bda-201">Hiermee geeft u de Uri's van de verbindings eindpunten voor de niet-verbonden sessies.</span><span class="sxs-lookup"><span data-stu-id="46bda-201">Specifies the URIs of the connection endpoints for the disconnected sessions.</span></span>

<span data-ttu-id="46bda-202">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="46bda-202">The URI must be fully qualified.</span></span>
<span data-ttu-id="46bda-203">De indeling van deze teken reeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="46bda-203">The format of this string is as follows:</span></span>

`\<Transport\>://\<ComputerName\>:\<Port\>/\<ApplicationName\>`

<span data-ttu-id="46bda-204">De standaard waarde is als volgt:</span><span class="sxs-lookup"><span data-stu-id="46bda-204">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="46bda-205">Als u geen verbindings-URI opgeeft, kunt u de para meters *UseSSL* en *Port* gebruiken om de verbindings-URI-waarden op te geven.</span><span class="sxs-lookup"><span data-stu-id="46bda-205">If you do not specify a connection URI, you can use the *UseSSL* and *Port* parameters to specify the connection URI values.</span></span>

<span data-ttu-id="46bda-206">Geldige waarden voor het **transport** segment van de URI zijn http en HTTPS.</span><span class="sxs-lookup"><span data-stu-id="46bda-206">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span>
<span data-ttu-id="46bda-207">Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met standaard poorten: 80 voor HTTP en 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="46bda-207">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span>
<span data-ttu-id="46bda-208">Als u de standaard poorten voor externe communicatie van Windows Power shell wilt gebruiken, geeft u poort 5985 op voor HTTP of 5986 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="46bda-208">To use the default ports for Windows PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="46bda-209">Als de doel computer de verbinding omleidt naar een andere URI, verhindert Windows Power shell de omleiding tenzij u de para meter *AllowRedirection* in de opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="46bda-209">If the destination computer redirects the connection to a different URI, Windows PowerShell prevents the redirection unless you use the *AllowRedirection* parameter in the command.</span></span>

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

### <span data-ttu-id="46bda-210">-Credential</span><span class="sxs-lookup"><span data-stu-id="46bda-210">-Credential</span></span>

<span data-ttu-id="46bda-211">Hiermee geeft u een gebruikers account op dat is gemachtigd om verbinding te maken met de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-211">Specifies a user account that has permission to connect to the disconnected session.</span></span>
<span data-ttu-id="46bda-212">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="46bda-212">The default is the current user.</span></span>

<span data-ttu-id="46bda-213">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="46bda-213">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="46bda-214">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="46bda-214">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="46bda-215">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="46bda-215">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="46bda-216">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="46bda-216">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="46bda-217">-Id</span><span class="sxs-lookup"><span data-stu-id="46bda-217">-Id</span></span>

<span data-ttu-id="46bda-218">Hiermee geeft u de Id's van de niet-verbonden sessies.</span><span class="sxs-lookup"><span data-stu-id="46bda-218">Specifies the IDs of the disconnected sessions.</span></span>
<span data-ttu-id="46bda-219">De *id-* para meter werkt alleen wanneer de verbroken sessie eerder is verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-219">The *Id* parameter works only when the disconnected session was previously connected to the current session.</span></span>

<span data-ttu-id="46bda-220">Deze para meter is geldig, maar niet effectief, wanneer de sessie wordt opgeslagen op de lokale computer, maar niet is verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-220">This parameter is valid, but not effective, when the session is stored on the local computer, but was not connected to the current session.</span></span>

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

### <span data-ttu-id="46bda-221">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="46bda-221">-InstanceId</span></span>

<span data-ttu-id="46bda-222">Hiermee geeft u de exemplaar-Id's van de niet-verbonden sessies.</span><span class="sxs-lookup"><span data-stu-id="46bda-222">Specifies the instance IDs of the disconnected sessions.</span></span>

<span data-ttu-id="46bda-223">De exemplaar-ID is een unieke aanduiding voor een **PSSession** op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="46bda-223">The instance ID is a GUID that uniquely identifies a **PSSession** on a local or remote computer.</span></span>

<span data-ttu-id="46bda-224">De exemplaar-ID wordt opgeslagen in de eigenschap **InstanceId** van de **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="46bda-224">The instance ID is stored in the **InstanceID** property of the **PSSession**.</span></span>

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

### <span data-ttu-id="46bda-225">-Name</span><span class="sxs-lookup"><span data-stu-id="46bda-225">-Name</span></span>

<span data-ttu-id="46bda-226">Hiermee geeft u de beschrijvende namen van de niet-verbonden sessies.</span><span class="sxs-lookup"><span data-stu-id="46bda-226">Specifies the friendly names of the disconnected sessions.</span></span>

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

### <span data-ttu-id="46bda-227">-Port</span><span class="sxs-lookup"><span data-stu-id="46bda-227">-Port</span></span>

<span data-ttu-id="46bda-228">Hiermee geeft u de netwerk poort op de externe computer op die wordt gebruikt om opnieuw verbinding te maken met de sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-228">Specifies the network port on the remote computer that is used to reconnect to the session.</span></span>
<span data-ttu-id="46bda-229">Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="46bda-229">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span>
<span data-ttu-id="46bda-230">De standaard poorten zijn 5985, de WinRM-poort voor HTTP en 5986, de WinRM-poort voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="46bda-230">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="46bda-231">Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren.</span><span class="sxs-lookup"><span data-stu-id="46bda-231">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span>
<span data-ttu-id="46bda-232">Als u de listener wilt configureren, typt u de volgende twee opdrachten bij de Windows Power shell-prompt:</span><span class="sxs-lookup"><span data-stu-id="46bda-232">To configure the listener, type the following two commands at the Windows PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="46bda-233">Gebruik de para meter *poort* alleen als dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="46bda-233">Do not use the *Port* parameter unless you must.</span></span>
<span data-ttu-id="46bda-234">De poort die in de opdracht is ingesteld, is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="46bda-234">The port that is set in the command applies to all computers or sessions on which the command runs.</span></span>
<span data-ttu-id="46bda-235">Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.</span><span class="sxs-lookup"><span data-stu-id="46bda-235">An alternate port setting might prevent the command from running on all computers.</span></span>

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

### <span data-ttu-id="46bda-236">-Sessie</span><span class="sxs-lookup"><span data-stu-id="46bda-236">-Session</span></span>

<span data-ttu-id="46bda-237">Hiermee geeft u de verbroken sessies.</span><span class="sxs-lookup"><span data-stu-id="46bda-237">Specifies the disconnected sessions.</span></span>
<span data-ttu-id="46bda-238">Voer een variabele in die de **PSSession** -objecten bevat of een opdracht waarmee de **PSSession** -objecten worden gemaakt of opgehaald, zoals een Get-PSSession opdracht.</span><span class="sxs-lookup"><span data-stu-id="46bda-238">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a Get-PSSession command.</span></span>

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

### <span data-ttu-id="46bda-239">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="46bda-239">-SessionOption</span></span>

<span data-ttu-id="46bda-240">Hiermee geeft u geavanceerde opties voor de sessie op.</span><span class="sxs-lookup"><span data-stu-id="46bda-240">Specifies advanced options for the session.</span></span>
<span data-ttu-id="46bda-241">Voer een **SessionOption** -object in, zoals het, dat u maakt met behulp van de cmdlet New-PSSessionOption, of een hash-tabel waarin de sleutels de naam van de sessie optie zijn en de waarden zijn de waarden van de sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-241">Enter a **SessionOption** object, such as one that you create by using the New-PSSessionOption cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="46bda-242">De standaard waarden voor de opties worden bepaald door de waarde van de $PSSessionOption voorkeurs variabele, als deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="46bda-242">The default values for the options are determined by the value of the $PSSessionOption preference variable, if it is set.</span></span>
<span data-ttu-id="46bda-243">Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="46bda-243">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="46bda-244">De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de $PSSessionOption voorkeurs variabele en in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="46bda-244">The session option values take precedence over default values for sessions set in the $PSSessionOption preference variable and in the session configuration.</span></span>
<span data-ttu-id="46bda-245">Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="46bda-245">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="46bda-246">Zie New-PSSessionOption voor een beschrijving van de sessie opties die de standaard waarden bevatten.</span><span class="sxs-lookup"><span data-stu-id="46bda-246">For a description of the session options that includes the default values, see New-PSSessionOption.</span></span>
<span data-ttu-id="46bda-247">Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie over de **$PSSessionOption** voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="46bda-247">For information about the **$PSSessionOption** preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>
<span data-ttu-id="46bda-248">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="46bda-248">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

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

### <span data-ttu-id="46bda-249">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="46bda-249">-ThrottleLimit</span></span>

<span data-ttu-id="46bda-250">Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="46bda-250">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="46bda-251">Als u deze para meter weglaat of een waarde van 0 invoert, wordt de standaard waarde 32 gebruikt.</span><span class="sxs-lookup"><span data-stu-id="46bda-251">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="46bda-252">De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="46bda-252">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="46bda-253">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="46bda-253">-UseSSL</span></span>

<span data-ttu-id="46bda-254">Geeft aan dat deze cmdlet het Secure Sockets Layer-Protocol (SSL) gebruikt om verbinding te maken met de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-254">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to connect to the disconnected session.</span></span> <span data-ttu-id="46bda-255">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="46bda-255">By default, SSL is not used.</span></span>

<span data-ttu-id="46bda-256">WS-Management versleutelt alle Windows Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="46bda-256">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span>
<span data-ttu-id="46bda-257">De para meter *UseSSL* is een extra beveiliging waarmee de gegevens worden verzonden via een HTTPS-verbinding in plaats van via een http-verbinding.</span><span class="sxs-lookup"><span data-stu-id="46bda-257">The *UseSSL* parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="46bda-258">Als u deze para meter gebruikt, maar SSL is niet beschikbaar op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="46bda-258">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="46bda-259">-Confirm</span><span class="sxs-lookup"><span data-stu-id="46bda-259">-Confirm</span></span>

<span data-ttu-id="46bda-260">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="46bda-260">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="46bda-261">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="46bda-261">-WhatIf</span></span>

<span data-ttu-id="46bda-262">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="46bda-262">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="46bda-263">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="46bda-263">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="46bda-264">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="46bda-264">CommonParameters</span></span>

<span data-ttu-id="46bda-265">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="46bda-265">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="46bda-266">Zie about_CommonParameters (voor meer informatie https://go.microsoft.com/fwlink/?LinkID=113216) .</span><span class="sxs-lookup"><span data-stu-id="46bda-266">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="46bda-267">INVOER</span><span class="sxs-lookup"><span data-stu-id="46bda-267">INPUTS</span></span>

### <span data-ttu-id="46bda-268">System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="46bda-268">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="46bda-269">U kunt een sessie ( **PSSession** ) door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="46bda-269">You can pipe a session ( **PSSession** ) to this cmdlet.</span></span>

## <span data-ttu-id="46bda-270">UITVOER</span><span class="sxs-lookup"><span data-stu-id="46bda-270">OUTPUTS</span></span>

### <span data-ttu-id="46bda-271">System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="46bda-271">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="46bda-272">Met deze cmdlet wordt een object geretourneerd dat de sessie vertegenwoordigt waarmee de verbinding is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="46bda-272">This cmdlet returns an object that represents the session to which it reconnected.</span></span>

## <span data-ttu-id="46bda-273">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="46bda-273">NOTES</span></span>

* <span data-ttu-id="46bda-274">**Connect-PSSession** opnieuw verbinding maken met sessies die niet zijn verbonden, dat wil zeggen, sessies waarvan de waarde voor de eigenschap **State** is verbroken.</span><span class="sxs-lookup"><span data-stu-id="46bda-274">**Connect-PSSession** reconnects only to sessions that are disconnected, that is, sessions that have a value of Disconnected for the **State** property.</span></span> <span data-ttu-id="46bda-275">Alleen sessies die zijn verbonden met of eindigen op computers waarop Windows Power Shell 3,0 of hoger wordt uitgevoerd, kunnen worden losgekoppeld en opnieuw worden aangesloten.</span><span class="sxs-lookup"><span data-stu-id="46bda-275">Only sessions that are connected to, or end at, computers that run Windows PowerShell 3.0 or later versions can be disconnected and reconnected.</span></span>
* <span data-ttu-id="46bda-276">Als u **Connect-PSSession** gebruikt voor een sessie die niet wordt losgekoppeld, is de opdracht niet van invloed op de sessie en worden er geen fouten gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="46bda-276">If you use **Connect-PSSession** on a session that is not disconnected, the command does not affect the session and it does not generate errors.</span></span>
* <span data-ttu-id="46bda-277">Verbroken loop Back-sessies met interactieve tokens, die worden gemaakt met behulp van de para meter *EnableNetworkAccess* , kunnen alleen opnieuw worden verbonden vanaf de computer waarop de sessie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="46bda-277">Disconnected loopback sessions with interactive tokens, which are created by using the *EnableNetworkAccess* parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="46bda-278">Met deze beperking wordt de computer beschermd tegen kwaadwillende toegang.</span><span class="sxs-lookup"><span data-stu-id="46bda-278">This restriction protects the computer from malicious access.</span></span>
* <span data-ttu-id="46bda-279">De waarde van de eigenschap **State** van een **PSSession** is relatief ten opzichte van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-279">The value of the **State** property of a **PSSession** is relative to the current session.</span></span>
<span data-ttu-id="46bda-280">Als de waarde voor de **verbinding is verbroken** , betekent dit daarom dat de **PSSession** niet is verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-280">Therefore, a value of **Disconnected** means that the **PSSession** is not connected to the current session.</span></span> <span data-ttu-id="46bda-281">Het betekent echter niet dat de **PSSession** -verbinding met alle sessies is verbroken.</span><span class="sxs-lookup"><span data-stu-id="46bda-281">However, it does not mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="46bda-282">Deze is mogelijk verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-282">It might be connected to a different session.</span></span> <span data-ttu-id="46bda-283">Gebruik de eigenschap **Beschik baarheid** om te bepalen of u verbinding kunt maken met de sessie of er opnieuw verbinding mee wilt maken.</span><span class="sxs-lookup"><span data-stu-id="46bda-283">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

  <span data-ttu-id="46bda-284">Een **beschikbaarheids** waarde van geen geeft aan dat u verbinding kunt maken met de sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-284">An **Availability** value of None indicates that you can connect to the session.</span></span>
<span data-ttu-id="46bda-285">De waarde bezet geeft aan dat u geen verbinding kunt maken met de **PSSession** omdat deze is verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-285">A value of Busy indicates that you cannot connect to the **PSSession** because it is connected to another session.</span></span>

  <span data-ttu-id="46bda-286">Zie [RunspaceState Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspacestate) in de MSDN-bibliotheek voor meer informatie over de waarden van de eigenschap **State** van sessies.</span><span class="sxs-lookup"><span data-stu-id="46bda-286">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspacestate) in the MSDN library.</span></span>

  <span data-ttu-id="46bda-287">Zie [RunspaceAvailability Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspaceavailability) in de MSDN-bibliotheek voor meer informatie over de waarden van de eigenschap **Availability** van sessies.</span><span class="sxs-lookup"><span data-stu-id="46bda-287">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspaceavailability) in the MSDN library.</span></span>

* <span data-ttu-id="46bda-288">U kunt de time-outwaarde voor inactiviteit van een **PSSession** niet wijzigen wanneer u verbinding maakt met de **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="46bda-288">You cannot change the idle time-out value of a **PSSession** when you connect to the **PSSession**.</span></span> <span data-ttu-id="46bda-289">De *SessionOption* -para meter van **Connect-PSSession** neemt een **SessionOption** -object met een **IdleTimeout** -waarde.</span><span class="sxs-lookup"><span data-stu-id="46bda-289">The *SessionOption* parameter of **Connect-PSSession** takes a **SessionOption** object that has an **IdleTimeout** value.</span></span> <span data-ttu-id="46bda-290">De waarde **IdleTimeout** van het object **SessionOption** en de waarde **IdleTimeout** van de variabele $PSSessionOption worden genegeerd wanneer er verbinding wordt gemaakt met een **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="46bda-290">However, the **IdleTimeout** value of the **SessionOption** object and the **IdleTimeout** value of the $PSSessionOption variable are ignored when connecting to a **PSSession**.</span></span>

  <span data-ttu-id="46bda-291">U kunt de time-out voor inactiviteit van een **PSSession** instellen en wijzigen wanneer u de **PSSession** maakt met behulp van de **nieuwe-PSSession** of **invoke-opdracht-** cmdlets en wanneer u de verbinding met de **PSSession** verbreekt.</span><span class="sxs-lookup"><span data-stu-id="46bda-291">You can set and change the idle time-out of a **PSSession** when you create the **PSSession** , by using the **New-PSSession** or **Invoke-Command** cmdlets, and when you disconnect from the **PSSession**.</span></span>

  <span data-ttu-id="46bda-292">De eigenschap **IdleTimeout** van een **PSSession** is essentieel voor verbroken sessies, omdat deze bepaalt hoe lang een verbroken sessie op de externe computer wordt onderhouden.</span><span class="sxs-lookup"><span data-stu-id="46bda-292">The **IdleTimeout** property of a **PSSession** is critical to disconnected sessions, because it determines how long a disconnected session is maintained on the remote computer.</span></span>
<span data-ttu-id="46bda-293">Verbroken sessies worden beschouwd als niet-actief vanaf het moment dat ze worden losgekoppeld, zelfs als opdrachten worden uitgevoerd in de verbroken sessie.</span><span class="sxs-lookup"><span data-stu-id="46bda-293">Disconnected sessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

## <span data-ttu-id="46bda-294">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="46bda-294">RELATED LINKS</span></span>

[<span data-ttu-id="46bda-295">Verbinding verbreken-PSSession</span><span class="sxs-lookup"><span data-stu-id="46bda-295">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="46bda-296">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="46bda-296">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="46bda-297">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="46bda-297">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="46bda-298">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="46bda-298">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="46bda-299">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="46bda-299">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="46bda-300">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="46bda-300">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="46bda-301">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="46bda-301">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="46bda-302">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="46bda-302">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="46bda-303">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="46bda-303">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="46bda-304">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="46bda-304">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="46bda-305">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="46bda-305">Remove-PSSession</span></span>](Remove-PSSession.md)
