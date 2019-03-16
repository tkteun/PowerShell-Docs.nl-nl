---
title: Externe communicatie van PowerShell via SSH
description: Externe communicatie in PowerShell Core met behulp van SSH
ms.date: 08/14/2018
ms.openlocfilehash: 1d7bcb69c7e784bf745cb5c2633106ea53f6226a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056529"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="e6ca8-103">Externe communicatie van PowerShell via SSH</span><span class="sxs-lookup"><span data-stu-id="e6ca8-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="e6ca8-104">Overzicht</span><span class="sxs-lookup"><span data-stu-id="e6ca8-104">Overview</span></span>

<span data-ttu-id="e6ca8-105">PowerShell voor externe toegang gebruikt normaal gesproken WinRM verbinding-onderhandeling en gegevenstransport.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="e6ca8-106">SSH is nu beschikbaar voor Linux en Windows-platform en kunt waar meerdere platforms externe communicatie van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="e6ca8-107">WinRM biedt een robuuste hostingmodel voor de externe PowerShell-sessies.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="e6ca8-108">Externe toegang op basis van SSH ondersteunt momenteel geen configuratie van externe eindpunten en JEA (Just Enough Administration).</span><span class="sxs-lookup"><span data-stu-id="e6ca8-108">SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="e6ca8-109">Externe communicatie met SSH kunt u eenvoudige PowerShell-sessie voor externe toegang tussen Windows en Linux-machines.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="e6ca8-110">SSH voor externe toegang maakt een hostproces PowerShell op de doel-VM als een SSH-subsysteem.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="e6ca8-111">Uiteindelijk zult we een algemene hostingmodel, vergelijkbaar met WinRM, ter ondersteuning van configuratie van eindpunten en JEA implementeren.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="e6ca8-112">De `New-PSSession`, `Enter-PSSession`, en `Invoke-Command` cmdlets hebben nu een nieuwe parameterset voor de ondersteuning van deze nieuwe verbinding voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="e6ca8-113">Voor het maken van een externe sessie die u opgeeft de doel-VM met de `HostName` parameter en geeft u de gebruikersnaam van de met `UserName`.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="e6ca8-114">Als de cmdlets interactief wordt uitgevoerd, wordt u gevraagd om een wachtwoord.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="e6ca8-115">U kunt ook gebruiken met behulp van een persoonlijk sleutelbestand met SSH-sleutelverificatie de `KeyFilePath` parameter.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="e6ca8-116">Algemene instellingen</span><span class="sxs-lookup"><span data-stu-id="e6ca8-116">General setup information</span></span>

<span data-ttu-id="e6ca8-117">SSH moet worden geïnstalleerd op alle virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="e6ca8-118">Zowel de SSH-client installeren (`ssh.exe`) en de server (`sshd.exe`) zodat u externe naar en van de machines kunt.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="e6ca8-119">OpenSSH voor Windows is nu beschikbaar in Windows 10 build 1809 en Windows Server 2019.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-119">OpenSSH for Windows is now availabe in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="e6ca8-120">Zie voor meer informatie, [OpenSSH voor Windows](/windows-server/administration/openssh/openssh_overview).</span><span class="sxs-lookup"><span data-stu-id="e6ca8-120">For more information, see [OpenSSH for Windows](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="e6ca8-121">Voor Linux installeren SSH (inclusief sshd-server) geschikt is voor uw platform.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-121">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="e6ca8-122">U moet ook PowerShell Core installeren vanuit GitHub om op te halen van de SSH-functie voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-122">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="e6ca8-123">De SSH-server moet worden geconfigureerd voor het maken van een SSH-subsysteem voor het hosten van een PowerShell-proces op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="e6ca8-124">Ook moet u inschakelen wachtwoord of sleutel gebaseerde verificatie configureren.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-124">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="e6ca8-125">Op Windows-Machine instellen</span><span class="sxs-lookup"><span data-stu-id="e6ca8-125">Set up on Windows Machine</span></span>

1. <span data-ttu-id="e6ca8-126">Installeer de nieuwste versie van [PowerShell Core voor Windows](../../install/installing-powershell-core-on-windows.md#msi)</span><span class="sxs-lookup"><span data-stu-id="e6ca8-126">Install the latest version of [PowerShell Core for Windows](../../install/installing-powershell-core-on-windows.md#msi)</span></span>

   - <span data-ttu-id="e6ca8-127">U kunt zien dat als dat zo de SSH-ondersteuning voor externe communicatie is door te kijken naar de parameter wordt ingesteld voor `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="e6ca8-127">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="e6ca8-128">Installeer de meest recente Win32-OpenSSH.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-128">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="e6ca8-129">Zie voor installatie-instructies [installatie van OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span><span class="sxs-lookup"><span data-stu-id="e6ca8-129">For installation instructions, see [Installation of OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>
3. <span data-ttu-id="e6ca8-130">Bewerk de `sshd_config` bestand dat zich bevindt in `$env:ProgramData\ssh`.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-130">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   - <span data-ttu-id="e6ca8-131">Zorg ervoor dat de wachtwoordverificatie is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="e6ca8-131">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="e6ca8-132">Er is een fout in OpenSSH voor Windows waarmee wordt voorkomen dat spaties in subsysteem uitvoerbare paden werkt.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-132">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="e6ca8-133">Zie voor meer informatie, [deze GitHub-probleem](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="e6ca8-133">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="e6ca8-134">Eén oplossing is het maken van een symlink naar de PowerShell-installatiemap die geen spaties:</span><span class="sxs-lookup"><span data-stu-id="e6ca8-134">One solution is to create a symlink to the PowerShell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     <span data-ttu-id="e6ca8-135">en geef de code in het subsysteem:</span><span class="sxs-lookup"><span data-stu-id="e6ca8-135">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="e6ca8-136">Verificatie met sleutel (optioneel) inschakelen</span><span class="sxs-lookup"><span data-stu-id="e6ca8-136">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="e6ca8-137">De sshd-service opnieuw starten</span><span class="sxs-lookup"><span data-stu-id="e6ca8-137">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="e6ca8-138">Voeg het pad waar OpenSSH wordt geïnstalleerd in uw padomgevingsvariabele bevindt.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-138">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="e6ca8-139">Voorbeeld: `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-139">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="e6ca8-140">Deze vermelding kunt u de ssh.exe worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-140">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="e6ca8-141">Op Linux (Ubuntu 14.04) Machine instellen</span><span class="sxs-lookup"><span data-stu-id="e6ca8-141">Set up on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="e6ca8-142">Installeer de meest recente [PowerShell Core voor Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1404) samengesteld op basis van GitHub</span><span class="sxs-lookup"><span data-stu-id="e6ca8-142">Install the latest [PowerShell Core for Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1404) build from GitHub</span></span>
2. <span data-ttu-id="e6ca8-143">Installeer [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) indien nodig</span><span class="sxs-lookup"><span data-stu-id="e6ca8-143">Install [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="e6ca8-144">Bewerk het bestand sshd_config op locatie /etc/ssh</span><span class="sxs-lookup"><span data-stu-id="e6ca8-144">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="e6ca8-145">Zorg ervoor dat de wachtwoordverificatie is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="e6ca8-145">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="e6ca8-146">Een PowerShell-subsysteem-item toevoegen</span><span class="sxs-lookup"><span data-stu-id="e6ca8-146">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="e6ca8-147">Verificatie met sleutel (optioneel) inschakelen</span><span class="sxs-lookup"><span data-stu-id="e6ca8-147">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="e6ca8-148">De sshd-service opnieuw starten</span><span class="sxs-lookup"><span data-stu-id="e6ca8-148">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="e6ca8-149">Ingesteld op MacOS-computer</span><span class="sxs-lookup"><span data-stu-id="e6ca8-149">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="e6ca8-150">Installeer de meest recente [PowerShell Core voor MacOS](../../install/installing-powershell-core-on-macos.md) bouwen</span><span class="sxs-lookup"><span data-stu-id="e6ca8-150">Install the latest [PowerShell Core for MacOS](../../install/installing-powershell-core-on-macos.md) build</span></span>

   - <span data-ttu-id="e6ca8-151">Zorg ervoor dat SSH voor externe toegang is ingeschakeld door de volgende stappen:</span><span class="sxs-lookup"><span data-stu-id="e6ca8-151">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="e6ca8-152">Open `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="e6ca8-152">Open `System Preferences`</span></span>
     - <span data-ttu-id="e6ca8-153">Klik op `Sharing`</span><span class="sxs-lookup"><span data-stu-id="e6ca8-153">Click on `Sharing`</span></span>
     - <span data-ttu-id="e6ca8-154">Controleer `Remote Login` -melding `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="e6ca8-154">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="e6ca8-155">Toegang tot de juiste gebruikers toestaan</span><span class="sxs-lookup"><span data-stu-id="e6ca8-155">Allow access to appropriate users</span></span>

2. <span data-ttu-id="e6ca8-156">Bewerk de `sshd_config` -bestand op locatie `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="e6ca8-156">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="e6ca8-157">Uw favoriete editor gebruiken of</span><span class="sxs-lookup"><span data-stu-id="e6ca8-157">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="e6ca8-158">Zorg ervoor dat de wachtwoordverificatie is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="e6ca8-158">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="e6ca8-159">Een PowerShell-subsysteem-item toevoegen</span><span class="sxs-lookup"><span data-stu-id="e6ca8-159">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="e6ca8-160">Verificatie met sleutel (optioneel) inschakelen</span><span class="sxs-lookup"><span data-stu-id="e6ca8-160">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="e6ca8-161">De sshd-service opnieuw starten</span><span class="sxs-lookup"><span data-stu-id="e6ca8-161">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="e6ca8-162">Verificatie</span><span class="sxs-lookup"><span data-stu-id="e6ca8-162">Authentication</span></span>

<span data-ttu-id="e6ca8-163">PowerShell voor externe toegang via SSH is afhankelijk van de authenticatie-uitwisseling tussen de SSH-client en de SSH-service en implementeert niet alle verificatiemethoden zelf.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-163">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span>
<span data-ttu-id="e6ca8-164">Dit betekent dat alle geconfigureerde verificatiemethoden, waaronder multi-factor authentication wordt verwerkt door de SSH- en onafhankelijk van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-164">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span>
<span data-ttu-id="e6ca8-165">U kunt bijvoorbeeld de SSH-service om te vereisen dat verificatie van de openbare sleutel, evenals een eenmalig wachtwoord voor extra beveiliging configureren.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-165">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span>
<span data-ttu-id="e6ca8-166">Configuratie van multi-factor authentication is buiten het bereik van deze documentatie.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-166">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span>
<span data-ttu-id="e6ca8-167">Raadpleeg de documentatie voor SSH over het correct multi-factor authentication configureren en te werken buiten PowerShell valideren voordat u probeert te gebruiken met PowerShell voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-167">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="e6ca8-168">Voorbeeld van PowerShell voor externe toegang</span><span class="sxs-lookup"><span data-stu-id="e6ca8-168">PowerShell Remoting Example</span></span>

<span data-ttu-id="e6ca8-169">De eenvoudigste manier om te testen voor externe toegang is om het te proberen op één computer.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-169">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="e6ca8-170">In dit voorbeeld maken we een externe sessie terug naar de dezelfde Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-170">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="e6ca8-171">We zijn met behulp van PowerShell cmdlets interactief zodat we zien uit in SSH waarin wordt gevraagd om te controleren of de computer en dat u wordt gevraagd om een wachtwoord gevraagd.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-171">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="e6ca8-172">U kunt hetzelfde doen op een Windows-machine om ervoor te zorgen voor externe toegang werkt.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-172">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="e6ca8-173">Klik vervolgens op afstand tussen machines door de hostnaam te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-173">Then remote between machines by changing the host name.</span></span>

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
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

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

### <a name="known-issues"></a><span data-ttu-id="e6ca8-174">Bekende problemen</span><span class="sxs-lookup"><span data-stu-id="e6ca8-174">Known Issues</span></span>

<span data-ttu-id="e6ca8-175">De sudo-opdracht werkt niet in de externe sessie op Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="e6ca8-175">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6ca8-176">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e6ca8-176">See Also</span></span>

[<span data-ttu-id="e6ca8-177">PowerShell Core voor Windows</span><span class="sxs-lookup"><span data-stu-id="e6ca8-177">PowerShell Core for Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="e6ca8-178">PowerShell Core voor Linux</span><span class="sxs-lookup"><span data-stu-id="e6ca8-178">PowerShell Core for Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="e6ca8-179">PowerShell Core voor MacOS</span><span class="sxs-lookup"><span data-stu-id="e6ca8-179">PowerShell Core for MacOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="e6ca8-180">OpenSSH voor Windows</span><span class="sxs-lookup"><span data-stu-id="e6ca8-180">OpenSSH for Windows</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="e6ca8-181">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="e6ca8-181">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
