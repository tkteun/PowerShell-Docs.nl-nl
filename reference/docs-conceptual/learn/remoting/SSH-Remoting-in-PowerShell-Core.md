---
title: Externe communicatie van PowerShell via SSH
description: Externe communicatie in Power shell core via SSH
ms.date: 09/30/2019
ms.openlocfilehash: 0f2fb13010d62dec5b19b373a24a199bff22665d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "73444378"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="b7ff2-103">Externe communicatie van PowerShell via SSH</span><span class="sxs-lookup"><span data-stu-id="b7ff2-103">PowerShell remoting over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="b7ff2-104">Overzicht</span><span class="sxs-lookup"><span data-stu-id="b7ff2-104">Overview</span></span>

<span data-ttu-id="b7ff2-105">Externe communicatie van Power Shell maakt normaal gesp roken gebruik van WinRM voor verbindings onderhandeling en gegevens overdracht.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="b7ff2-106">SSH is nu beschikbaar voor Linux-en Windows-platforms en biedt echte externe communicatie van Power shell op meerdere platforms.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="b7ff2-107">WinRM biedt een robuust hosting model voor externe Power shell-sessies.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="b7ff2-108">Op SSH gebaseerde externe toegang biedt momenteel geen ondersteuning voor externe eindpunt configuratie en voldoende beheer (JEA).</span><span class="sxs-lookup"><span data-stu-id="b7ff2-108">SSH-based remoting doesn't currently support remote endpoint configuration and Just Enough Administration (JEA).</span></span>

<span data-ttu-id="b7ff2-109">Met SSH-externe communicatie kunt u een eenvoudige Power shell-sessie tussen Windows-en Linux-computers uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux computers.</span></span> <span data-ttu-id="b7ff2-110">Externe SSH-processen maken een Power shell-hostproces op de doel computer als een SSH-subsysteem.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-110">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="b7ff2-111">Uiteindelijk implementeren we een algemeen hosting model, vergelijkbaar met WinRM, ter ondersteuning van de eindpunt configuratie en JEA.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="b7ff2-112">De cmdlets `New-PSSession`, `Enter-PSSession`en `Invoke-Command` hebben nu een nieuwe para meter ingesteld ter ondersteuning van deze nieuwe externe verbinding.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="b7ff2-113">Als u een externe sessie wilt maken, geeft u de doel computer op met de para meter `HostName` en geeft u de gebruikers naam op met `UserName`.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-113">To create a remote session, you specify the target computer with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="b7ff2-114">Wanneer de cmdlets interactief worden uitgevoerd, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="b7ff2-115">U kunt ook SSH-sleutel verificatie gebruiken met behulp van een persoonlijke-sleutel bestand met de para meter `KeyFilePath`.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="b7ff2-116">Algemene informatie over de installatie</span><span class="sxs-lookup"><span data-stu-id="b7ff2-116">General setup information</span></span>

<span data-ttu-id="b7ff2-117">Power shell 6 of hoger en SSH moet op alle computers zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-117">PowerShell 6 or higher, and SSH must be installed on all computers.</span></span> <span data-ttu-id="b7ff2-118">Installeer zowel de SSH-client (`ssh.exe`) als de server (`sshd.exe`) zodat u op afstand van en naar de computers kunt.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the computers.</span></span> <span data-ttu-id="b7ff2-119">OpenSSH voor Windows is nu beschikbaar in Windows 10 build 1809 en Windows Server 2019.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-119">OpenSSH for Windows is now available in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="b7ff2-120">Zie [Manage Windows with OpenSSH](/windows-server/administration/openssh/openssh_overview)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-120">For more information, see [Manage Windows with OpenSSH](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="b7ff2-121">Voor Linux installeert u SSH, met inbegrip van de sshd-server, die geschikt is voor uw platform.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-121">For Linux, install SSH, including sshd server, that's appropriate for your platform.</span></span> <span data-ttu-id="b7ff2-122">U moet Power shell ook installeren vanaf GitHub om de externe SSH-functie te krijgen.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-122">You also need to install PowerShell from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="b7ff2-123">De SSH-server moet worden geconfigureerd om een SSH-subsysteem te maken voor het hosten van een Power Shell-proces op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote computer.</span></span> <span data-ttu-id="b7ff2-124">En u moet verificatie **op basis van** **wacht woord** of sleutel inschakelen.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-124">And, you must enable **password** or **key-based** authentication.</span></span>

## <a name="set-up-on-a-windows-computer"></a><span data-ttu-id="b7ff2-125">Instellen op een Windows-computer</span><span class="sxs-lookup"><span data-stu-id="b7ff2-125">Set up on a Windows computer</span></span>

1. <span data-ttu-id="b7ff2-126">Installeer de meest recente versie van Power shell, Zie [Power shell Core installeren in Windows](../../install/installing-powershell-core-on-windows.md#msi).</span><span class="sxs-lookup"><span data-stu-id="b7ff2-126">Install the latest version of PowerShell, see [Installing PowerShell Core on Windows](../../install/installing-powershell-core-on-windows.md#msi).</span></span>

   <span data-ttu-id="b7ff2-127">U kunt controleren of Power Shell ondersteuning biedt voor externe SSH door de `New-PSSession` parameter sets op te geven.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-127">You can confirm that PowerShell has SSH remoting support by listing the `New-PSSession` parameter sets.</span></span> <span data-ttu-id="b7ff2-128">U ziet dat er namen van parameter sets zijn die beginnen met **SSH**.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-128">You'll notice there are parameter set names that begin with **SSH**.</span></span> <span data-ttu-id="b7ff2-129">Deze parameter sets bevatten **SSH** -para meters.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-129">Those parameter sets include **SSH** parameters.</span></span>

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. <span data-ttu-id="b7ff2-130">Installeer de meest recente Win32-OpenSSH.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-130">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="b7ff2-131">Zie aan de slag [met OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse)voor installatie-instructies.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-131">For installation instructions, see [Getting started with OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>

   > [!NOTE]
   > <span data-ttu-id="b7ff2-132">Als u Power shell wilt instellen als de standaard shell voor OpenSSH, raadpleegt u [Windows configureren voor OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).</span><span class="sxs-lookup"><span data-stu-id="b7ff2-132">If you want to set PowerShell as the default shell for OpenSSH, see [Configuring Windows for OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).</span></span>

1. <span data-ttu-id="b7ff2-133">Bewerk het `sshd_config`-bestand dat zich op `$env:ProgramData\ssh`bevindt.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-133">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   <span data-ttu-id="b7ff2-134">Controleer of wachtwoord verificatie is ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="b7ff2-134">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="b7ff2-135">Maak het SSH-subsysteem dat als host fungeert voor een Power Shell-proces op de externe computer:</span><span class="sxs-lookup"><span data-stu-id="b7ff2-135">Create the SSH subsystem that hosts a PowerShell process on the remote computer:</span></span>

   ```
   Subsystem powershell c:/progra~1/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   > [!NOTE]
   > <span data-ttu-id="b7ff2-136">U moet de korte naam van 8,3 gebruiken voor bestands paden die spaties bevatten.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-136">You must use the 8.3 short name for any file paths that contain spaces.</span></span> <span data-ttu-id="b7ff2-137">Er is een fout in OpenSSH voor Windows waarmee wordt voor komen dat ruimten in subsysteem uitvoer bare paden werken.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-137">There's a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="b7ff2-138">Zie voor meer informatie dit [github-probleem](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="b7ff2-138">For more information, see this [GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>
   >
   > <span data-ttu-id="b7ff2-139">De korte naam van 8,3 voor de map `Program Files` in Windows is doorgaans `Progra~1`.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-139">The 8.3 short name for the `Program Files` folder in Windows is usually `Progra~1`.</span></span> <span data-ttu-id="b7ff2-140">U kunt echter de volgende opdracht gebruiken om ervoor te zorgen:</span><span class="sxs-lookup"><span data-stu-id="b7ff2-140">However, you can use the following command to make sure:</span></span>
   >
   > ```powershell
   > Get-CimInstance Win32_Directory -Filter 'Name="C:\\Program Files"' |
   >   Select-Object EightDotThreeFileName
   > ```
   >
   > ```Output
   > EightDotThreeFileName
   > ---------------------
   > c:\progra~1
   > ```

   <span data-ttu-id="b7ff2-141">Schakel eventueel sleutel verificatie in:</span><span class="sxs-lookup"><span data-stu-id="b7ff2-141">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

   <span data-ttu-id="b7ff2-142">Zie [Managing OpenSSH Keys](/windows-server/administration/openssh/openssh_keymanagement)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-142">For more information, see [Managing OpenSSH Keys](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

1. <span data-ttu-id="b7ff2-143">Start de service **sshd** opnieuw.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-143">Restart the **sshd** service.</span></span>

   ```powershell
   Restart-Service sshd
   ```

1. <span data-ttu-id="b7ff2-144">Voeg het pad toe waar OpenSSH wordt geïnstalleerd in uw omgevings variabele PATH.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-144">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="b7ff2-145">Voorbeeld: `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-145">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="b7ff2-146">Met deze vermelding kan de `ssh.exe` worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-146">This entry allows for the `ssh.exe` to be found.</span></span>

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a><span data-ttu-id="b7ff2-147">Instellen op een Ubuntu 16,04 Linux-computer</span><span class="sxs-lookup"><span data-stu-id="b7ff2-147">Set up on an Ubuntu 16.04 Linux computer</span></span>

1. <span data-ttu-id="b7ff2-148">Installeer de meest recente versie van Power shell, Zie [Power shell Core installeren op Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).</span><span class="sxs-lookup"><span data-stu-id="b7ff2-148">Install the latest version of PowerShell, see [Installing PowerShell Core on Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).</span></span>
1. <span data-ttu-id="b7ff2-149">Installeer de [Ubuntu openssh-server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span><span class="sxs-lookup"><span data-stu-id="b7ff2-149">Install [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. <span data-ttu-id="b7ff2-150">Bewerk het `sshd_config` bestand op locatie `/etc/ssh`.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-150">Edit the `sshd_config` file at location `/etc/ssh`.</span></span>

   <span data-ttu-id="b7ff2-151">Controleer of wachtwoord verificatie is ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="b7ff2-151">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="b7ff2-152">Een vermelding voor een Power shell-subsysteem toevoegen:</span><span class="sxs-lookup"><span data-stu-id="b7ff2-152">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   <span data-ttu-id="b7ff2-153">Schakel eventueel sleutel verificatie in:</span><span class="sxs-lookup"><span data-stu-id="b7ff2-153">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="b7ff2-154">Start de service **sshd** opnieuw.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-154">Restart the **sshd** service.</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-a-macos-computer"></a><span data-ttu-id="b7ff2-155">Instellen op een macOS-computer</span><span class="sxs-lookup"><span data-stu-id="b7ff2-155">Set up on a macOS computer</span></span>

1. <span data-ttu-id="b7ff2-156">Installeer de meest recente versie van Power shell, Zie [Power shell Core installeren op macOS](../../install/installing-powershell-core-on-macos.md).</span><span class="sxs-lookup"><span data-stu-id="b7ff2-156">Install the latest version of PowerShell, see [Installing PowerShell Core on macOS](../../install/installing-powershell-core-on-macos.md).</span></span>

   <span data-ttu-id="b7ff2-157">Zorg ervoor dat externe SSH-communicatie is ingeschakeld door de volgende stappen te volgen:</span><span class="sxs-lookup"><span data-stu-id="b7ff2-157">Make sure SSH Remoting is enabled by following these steps:</span></span>

   1. <span data-ttu-id="b7ff2-158">Open `System Preferences`.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-158">Open `System Preferences`.</span></span>
   1. <span data-ttu-id="b7ff2-159">Klik op `Sharing`.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-159">Click on `Sharing`.</span></span>
   1. <span data-ttu-id="b7ff2-160">Controleer `Remote Login` om `Remote Login: On`in te stellen.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-160">Check `Remote Login` to set `Remote Login: On`.</span></span>
   1. <span data-ttu-id="b7ff2-161">Toegang tot de juiste gebruikers toestaan.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-161">Allow access to the appropriate users.</span></span>

1. <span data-ttu-id="b7ff2-162">Bewerk het `sshd_config` bestand op locatie `/private/etc/ssh/sshd_config`.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-162">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`.</span></span>

   <span data-ttu-id="b7ff2-163">Gebruik een tekst editor zoals **nano**:</span><span class="sxs-lookup"><span data-stu-id="b7ff2-163">Use a text editor such as **nano**:</span></span>

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   <span data-ttu-id="b7ff2-164">Controleer of wachtwoord verificatie is ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="b7ff2-164">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="b7ff2-165">Een vermelding voor een Power shell-subsysteem toevoegen:</span><span class="sxs-lookup"><span data-stu-id="b7ff2-165">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   <span data-ttu-id="b7ff2-166">Schakel eventueel sleutel verificatie in:</span><span class="sxs-lookup"><span data-stu-id="b7ff2-166">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="b7ff2-167">Start de service **sshd** opnieuw.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-167">Restart the **sshd** service.</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="b7ff2-168">Verificatie</span><span class="sxs-lookup"><span data-stu-id="b7ff2-168">Authentication</span></span>

<span data-ttu-id="b7ff2-169">Externe communicatie van Power shell is afhankelijk van de verificatie uitwisseling tussen de SSH-client en de SSH-service en implementeert geen verificatie schema's zelf.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-169">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and doesn't implement any authentication schemes itself.</span></span> <span data-ttu-id="b7ff2-170">Het resultaat is dat alle geconfigureerde verificatie schema's, waaronder multi-factor Authentication, worden afgehandeld door SSH en onafhankelijk van Power shell.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-170">The result is that any configured authentication schemes including multi-factor authentication are handled by SSH and independent of PowerShell.</span></span> <span data-ttu-id="b7ff2-171">U kunt bijvoorbeeld de SSH-service zo configureren dat verificatie met een open bare sleutel en een eenmalig wacht woord voor extra beveiliging zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-171">For example, you can configure the SSH service to require public key authentication and a one-time password for added security.</span></span> <span data-ttu-id="b7ff2-172">Configuratie van multi-factor Authentication valt buiten het bereik van deze documentatie.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-172">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span> <span data-ttu-id="b7ff2-173">Raadpleeg de documentatie voor SSH over het correct configureren van multi-factor Authentication en het valideren van de oplossing werkt buiten Power shell voordat u deze probeert te gebruiken met externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-173">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="b7ff2-174">Externe Power shell-voor beeld</span><span class="sxs-lookup"><span data-stu-id="b7ff2-174">PowerShell remoting example</span></span>

<span data-ttu-id="b7ff2-175">De eenvoudigste manier om externe communicatie te testen is door deze te proberen op één computer.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-175">The easiest way to test remoting is to try it on a single computer.</span></span> <span data-ttu-id="b7ff2-176">In dit voor beeld maken we een externe sessie terug naar dezelfde Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-176">In this example, we create a remote session back to the same Linux computer.</span></span> <span data-ttu-id="b7ff2-177">Power shell-cmdlets worden interactief gebruikt, dus er worden prompts van SSH weer gegeven waarin wordt gevraagd om de hostcomputer te controleren en te vragen om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-177">We're using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="b7ff2-178">U kunt hetzelfde doen op een Windows-computer om ervoor te zorgen dat externe toegang werkt.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-178">You can do the same thing on a Windows computer to ensure remoting is working.</span></span> <span data-ttu-id="b7ff2-179">Vervolgens op afstand tussen computers door de hostnaam te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-179">Then, remote between computers by changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```Output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```Output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```Output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```Output
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

```Output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```Output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```Output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```Output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```Output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```Output
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

### <a name="known-issues"></a><span data-ttu-id="b7ff2-180">Bekende problemen</span><span class="sxs-lookup"><span data-stu-id="b7ff2-180">Known issues</span></span>

<span data-ttu-id="b7ff2-181">De opdracht **sudo** werkt niet in een externe sessie met een Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="b7ff2-181">The **sudo** command doesn't work in a remote session to a Linux computer.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7ff2-182">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b7ff2-182">See also</span></span>

<span data-ttu-id="b7ff2-183">[Installing PowerShell Core on Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) (PowerShell Core installeren in Linux)</span><span class="sxs-lookup"><span data-stu-id="b7ff2-183">[Installing PowerShell Core on Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)</span></span>

<span data-ttu-id="b7ff2-184">[Installing PowerShell Core on macOS](../../install/installing-powershell-core-on-macos.md) (PowerShell Core installeren in macOS)</span><span class="sxs-lookup"><span data-stu-id="b7ff2-184">[Installing PowerShell Core on macOS](../../install/installing-powershell-core-on-macos.md)</span></span>

[<span data-ttu-id="b7ff2-185">Power shell Core installeren in Windows</span><span class="sxs-lookup"><span data-stu-id="b7ff2-185">Installing PowerShell Core on Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="b7ff2-186">Windows beheren met OpenSSH</span><span class="sxs-lookup"><span data-stu-id="b7ff2-186">Manage Windows with OpenSSH</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="b7ff2-187">OpenSSH-sleutels beheren</span><span class="sxs-lookup"><span data-stu-id="b7ff2-187">Managing OpenSSH Keys</span></span>](/windows-server/administration/openssh/openssh_keymanagement)

[<span data-ttu-id="b7ff2-188">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="b7ff2-188">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
