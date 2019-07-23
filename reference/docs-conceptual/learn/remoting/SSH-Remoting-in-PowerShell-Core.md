---
title: Externe communicatie van PowerShell via SSH
description: Externe communicatie in Power shell core via SSH
ms.date: 08/14/2018
ms.openlocfilehash: d994a3888b9a372b803a65666634775a8905d63a
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372149"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="d3ca8-103">Externe communicatie van PowerShell via SSH</span><span class="sxs-lookup"><span data-stu-id="d3ca8-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="d3ca8-104">Overzicht</span><span class="sxs-lookup"><span data-stu-id="d3ca8-104">Overview</span></span>

<span data-ttu-id="d3ca8-105">Externe communicatie van Power Shell maakt normaal gesp roken gebruik van WinRM voor verbindings onderhandeling en gegevens overdracht.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="d3ca8-106">SSH is nu beschikbaar voor Linux-en Windows-platforms en biedt echte externe communicatie van Power shell op meerdere platforms.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="d3ca8-107">WinRM biedt een robuust hosting model voor externe Power shell-sessies.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="d3ca8-108">Op SSH gebaseerde externe toegang biedt momenteel geen ondersteuning voor externe eindpunt configuratie en JEA (net genoeg beheer).</span><span class="sxs-lookup"><span data-stu-id="d3ca8-108">SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="d3ca8-109">Met SSH-externe communicatie kunt u een eenvoudige Power shell-sessie tussen Windows-en Linux-computers uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="d3ca8-110">Externe SSH-processen maken een Power shell-hostproces op de doel computer als een SSH-subsysteem.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span> <span data-ttu-id="d3ca8-111">Uiteindelijk implementeren we een algemeen hosting model, vergelijkbaar met WinRM, ter ondersteuning van de eindpunt configuratie en JEA.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="d3ca8-112">De `New-PSSession`cmdlets `Enter-PSSession`, `Invoke-Command` en hebben nu een nieuwe para meter die is ingesteld voor de ondersteuning van deze nieuwe externe verbinding.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="d3ca8-113">Als u een externe sessie wilt maken, geeft u de doel computer `HostName` op met de para meter en geeft `UserName`u de gebruikers naam op bij.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="d3ca8-114">Wanneer de cmdlets interactief worden uitgevoerd, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="d3ca8-115">U kunt ook SSH-sleutel verificatie gebruiken met behulp van een persoonlijke- `KeyFilePath` sleutel bestand met de para meter.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="d3ca8-116">Algemene informatie over de installatie</span><span class="sxs-lookup"><span data-stu-id="d3ca8-116">General setup information</span></span>

<span data-ttu-id="d3ca8-117">SSH moet op alle computers zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="d3ca8-118">Installeer zowel de SSH-client`ssh.exe`() als de`sshd.exe`server (), zodat u op afstand van en naar de computers kunt.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="d3ca8-119">OpenSSH voor Windows is nu beschikbaar in Windows 10 build 1809 en Windows Server 2019.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-119">OpenSSH for Windows is now available in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="d3ca8-120">Zie [OpenSSH voor Windows](/windows-server/administration/openssh/openssh_overview)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-120">For more information, see [OpenSSH for Windows](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="d3ca8-121">Installeer voor Linux SSH (inclusief sshd-server) die geschikt is voor uw platform.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-121">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="d3ca8-122">U moet ook Power shell Core van GitHub installeren om de externe SSH-functie te krijgen.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-122">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="d3ca8-123">De SSH-server moet worden geconfigureerd om een SSH-subsysteem te maken voor het hosten van een Power Shell-proces op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="d3ca8-124">U moet ook inschakelen van wacht woord of op sleutel gebaseerde verificatie configureren.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-124">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="d3ca8-125">Instellen op Windows-machine</span><span class="sxs-lookup"><span data-stu-id="d3ca8-125">Set up on Windows Machine</span></span>

1. <span data-ttu-id="d3ca8-126">Installeer de nieuwste versie van [Power shell core voor Windows](../../install/installing-powershell-core-on-windows.md#msi)</span><span class="sxs-lookup"><span data-stu-id="d3ca8-126">Install the latest version of [PowerShell Core for Windows](../../install/installing-powershell-core-on-windows.md#msi)</span></span>

   - <span data-ttu-id="d3ca8-127">U kunt zien of het de SSH-ondersteuning voor externe toegang heeft door te kijken naar de parameter sets voor`New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="d3ca8-127">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="d3ca8-128">Installeer de meest recente Win32-OpenSSH.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-128">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="d3ca8-129">Zie [installatie van OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse)voor installatie-instructies.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-129">For installation instructions, see [Installation of OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>
3. <span data-ttu-id="d3ca8-130">Bewerk het `sshd_config` bestand dat zich `$env:ProgramData\ssh`bevindt in.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-130">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   - <span data-ttu-id="d3ca8-131">Controleer of wachtwoord verificatie is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="d3ca8-131">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="d3ca8-132">Er is een fout in OpenSSH voor Windows waarmee wordt voor komen dat ruimten in subsysteem uitvoer bare paden werken.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-132">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="d3ca8-133">Zie voor meer informatie [Dit github-probleem](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="d3ca8-133">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="d3ca8-134">Eén oplossing is het maken van een symlink in de Power shell-installatie directory die geen spaties heeft:</span><span class="sxs-lookup"><span data-stu-id="d3ca8-134">One solution is to create a symlink to the PowerShell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     <span data-ttu-id="d3ca8-135">en voer deze in het subsysteem in:</span><span class="sxs-lookup"><span data-stu-id="d3ca8-135">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="d3ca8-136">Optioneel sleutel verificatie inschakelen</span><span class="sxs-lookup"><span data-stu-id="d3ca8-136">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="d3ca8-137">De sshd-service opnieuw starten</span><span class="sxs-lookup"><span data-stu-id="d3ca8-137">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="d3ca8-138">Voeg het pad toe waar OpenSSH wordt geïnstalleerd in uw omgevings variabele PATH.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-138">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="d3ca8-139">Voorbeeld: `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-139">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="d3ca8-140">Met deze vermelding kan ssh. exe worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-140">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1604-machine"></a><span data-ttu-id="d3ca8-141">Instellen op een Linux-machine (Ubuntu 16,04)</span><span class="sxs-lookup"><span data-stu-id="d3ca8-141">Set up on Linux (Ubuntu 16.04) Machine</span></span>

1. <span data-ttu-id="d3ca8-142">De nieuwste versie van [Power shell Core for Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) van github installeren</span><span class="sxs-lookup"><span data-stu-id="d3ca8-142">Install the latest [PowerShell Core for Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) build from GitHub</span></span>
2. <span data-ttu-id="d3ca8-143">Installeer [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) indien nodig</span><span class="sxs-lookup"><span data-stu-id="d3ca8-143">Install [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="d3ca8-144">Bewerk het sshd_config-bestand op locatie/etc/ssh</span><span class="sxs-lookup"><span data-stu-id="d3ca8-144">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="d3ca8-145">Controleer of wachtwoord verificatie is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="d3ca8-145">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="d3ca8-146">Een vermelding voor een Power shell-subsysteem toevoegen</span><span class="sxs-lookup"><span data-stu-id="d3ca8-146">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="d3ca8-147">Optioneel sleutel verificatie inschakelen</span><span class="sxs-lookup"><span data-stu-id="d3ca8-147">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="d3ca8-148">De sshd-service opnieuw starten</span><span class="sxs-lookup"><span data-stu-id="d3ca8-148">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="d3ca8-149">Instellen op MacOS-computer</span><span class="sxs-lookup"><span data-stu-id="d3ca8-149">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="d3ca8-150">Installeer de nieuwste [Power shell core voor MacOS](../../install/installing-powershell-core-on-macos.md) build</span><span class="sxs-lookup"><span data-stu-id="d3ca8-150">Install the latest [PowerShell Core for MacOS](../../install/installing-powershell-core-on-macos.md) build</span></span>

   - <span data-ttu-id="d3ca8-151">Zorg ervoor dat externe SSH-communicatie is ingeschakeld door de volgende stappen te volgen:</span><span class="sxs-lookup"><span data-stu-id="d3ca8-151">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="d3ca8-152">Staan`System Preferences`</span><span class="sxs-lookup"><span data-stu-id="d3ca8-152">Open `System Preferences`</span></span>
     - <span data-ttu-id="d3ca8-153">Klik op`Sharing`</span><span class="sxs-lookup"><span data-stu-id="d3ca8-153">Click on `Sharing`</span></span>
     - <span data-ttu-id="d3ca8-154">Controleren `Remote Login` -moet zeggen`Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="d3ca8-154">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="d3ca8-155">Toegang tot de juiste gebruikers toestaan</span><span class="sxs-lookup"><span data-stu-id="d3ca8-155">Allow access to appropriate users</span></span>

2. <span data-ttu-id="d3ca8-156">Het `sshd_config` bestand op locatie bewerken`/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="d3ca8-156">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="d3ca8-157">Uw favoriete editor gebruiken of</span><span class="sxs-lookup"><span data-stu-id="d3ca8-157">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="d3ca8-158">Controleer of wachtwoord verificatie is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="d3ca8-158">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="d3ca8-159">Een vermelding voor een Power shell-subsysteem toevoegen</span><span class="sxs-lookup"><span data-stu-id="d3ca8-159">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="d3ca8-160">Optioneel sleutel verificatie inschakelen</span><span class="sxs-lookup"><span data-stu-id="d3ca8-160">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="d3ca8-161">De sshd-service opnieuw starten</span><span class="sxs-lookup"><span data-stu-id="d3ca8-161">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="d3ca8-162">Verificatie</span><span class="sxs-lookup"><span data-stu-id="d3ca8-162">Authentication</span></span>

<span data-ttu-id="d3ca8-163">Externe communicatie van Power shell is afhankelijk van de verificatie uitwisseling tussen de SSH-client en de SSH-service en implementeert geen verificatie schema's zelf.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-163">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span> <span data-ttu-id="d3ca8-164">Dit betekent dat alle geconfigureerde verificatie schema's, waaronder multi-factor Authentication, worden verwerkt door SSH en onafhankelijk van Power shell.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-164">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span> <span data-ttu-id="d3ca8-165">U kunt bijvoorbeeld de SSH-service zo configureren dat de verificatie van de open bare sleutel is vereist, evenals een eenmalig wacht woord voor extra beveiliging.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-165">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span> <span data-ttu-id="d3ca8-166">Configuratie van multi-factor Authentication valt buiten het bereik van deze documentatie.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-166">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span> <span data-ttu-id="d3ca8-167">Raadpleeg de documentatie voor SSH over het correct configureren van multi-factor Authentication en het valideren van de oplossing werkt buiten Power shell voordat u deze probeert te gebruiken met externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-167">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="d3ca8-168">Externe Power shell-voor beeld</span><span class="sxs-lookup"><span data-stu-id="d3ca8-168">PowerShell Remoting Example</span></span>

<span data-ttu-id="d3ca8-169">De eenvoudigste manier om externe communicatie te testen is door deze te proberen op één computer.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-169">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="d3ca8-170">In dit voor beeld maken we een externe sessie terug naar dezelfde Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-170">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="d3ca8-171">Power shell-cmdlets worden interactief gebruikt, dus er worden prompts van SSH weer gegeven waarin wordt gevraagd om de hostcomputer te controleren en te vragen om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-171">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="d3ca8-172">U kunt hetzelfde doen op een Windows-computer om ervoor te zorgen dat externe toegang werkt.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-172">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="d3ca8-173">Vervolgens op afstand tussen computers door de naam van de host te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-173">Then remote between machines by changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1
```

```powershell
#
# Linux to Windows
#
Enter-PSSession -HostName WinVM1 -UserName PTestName
```

```output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```output
[WinVM2]: PS C:\Users\PSRemoteUser\Documents> $PSVersionTable

Name                           Value
----                           -----
PSEdition                      Core
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
SerializationVersion           1.1.0.1
BuildVersion                   3.0.0.0
CLRVersion
PSVersion                      6.0.0-alpha
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
GitCommitId                    v6.0.0-alpha.17


[WinVM2]: PS C:\Users\PSRemoteUser\Documents>
```

### <a name="known-issues"></a><span data-ttu-id="d3ca8-174">Bekende problemen</span><span class="sxs-lookup"><span data-stu-id="d3ca8-174">Known Issues</span></span>

<span data-ttu-id="d3ca8-175">De opdracht sudo werkt niet in de externe sessie met de Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="d3ca8-175">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3ca8-176">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d3ca8-176">See Also</span></span>

[<span data-ttu-id="d3ca8-177">Power shell core voor Windows</span><span class="sxs-lookup"><span data-stu-id="d3ca8-177">PowerShell Core for Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="d3ca8-178">Power shell core voor Linux</span><span class="sxs-lookup"><span data-stu-id="d3ca8-178">PowerShell Core for Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[<span data-ttu-id="d3ca8-179">Power shell core voor MacOS</span><span class="sxs-lookup"><span data-stu-id="d3ca8-179">PowerShell Core for MacOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="d3ca8-180">OpenSSH voor Windows</span><span class="sxs-lookup"><span data-stu-id="d3ca8-180">OpenSSH for Windows</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="d3ca8-181">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="d3ca8-181">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
