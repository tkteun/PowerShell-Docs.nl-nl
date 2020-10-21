---
title: Externe communicatie van PowerShell via SSH
description: Externe communicatie in Power shell core via SSH
ms.date: 10/19/2020
ms.openlocfilehash: 23c5dc9c1ff6427cc718114bd58dc7c568e697bc
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "92298285"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="a78b8-103">Externe communicatie van PowerShell via SSH</span><span class="sxs-lookup"><span data-stu-id="a78b8-103">PowerShell remoting over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="a78b8-104">Overzicht</span><span class="sxs-lookup"><span data-stu-id="a78b8-104">Overview</span></span>

<span data-ttu-id="a78b8-105">Externe communicatie van Power Shell maakt normaal gesp roken gebruik van WinRM voor verbindings onderhandeling en gegevens overdracht.</span><span class="sxs-lookup"><span data-stu-id="a78b8-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="a78b8-106">SSH is nu beschikbaar voor Linux-en Windows-platforms en biedt echte externe communicatie van Power shell op meerdere platforms.</span><span class="sxs-lookup"><span data-stu-id="a78b8-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="a78b8-107">WinRM biedt een robuust hosting model voor externe Power shell-sessies.</span><span class="sxs-lookup"><span data-stu-id="a78b8-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="a78b8-108">Op SSH gebaseerde externe toegang biedt momenteel geen ondersteuning voor externe eindpunt configuratie en voldoende beheer (JEA).</span><span class="sxs-lookup"><span data-stu-id="a78b8-108">SSH-based remoting doesn't currently support remote endpoint configuration and Just Enough Administration (JEA).</span></span>

<span data-ttu-id="a78b8-109">Met SSH-externe communicatie kunt u een eenvoudige Power shell-sessie tussen Windows-en Linux-computers uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="a78b8-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux computers.</span></span> <span data-ttu-id="a78b8-110">Externe SSH-processen maken een Power shell-hostproces op de doel computer als een SSH-subsysteem.</span><span class="sxs-lookup"><span data-stu-id="a78b8-110">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="a78b8-111">Uiteindelijk implementeren we een algemeen hosting model, vergelijkbaar met WinRM, ter ondersteuning van de eindpunt configuratie en JEA.</span><span class="sxs-lookup"><span data-stu-id="a78b8-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="a78b8-112">De `New-PSSession` `Enter-PSSession` `Invoke-Command` cmdlets, en hebben nu een nieuwe para meter die is ingesteld voor de ondersteuning van deze nieuwe externe verbinding.</span><span class="sxs-lookup"><span data-stu-id="a78b8-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="a78b8-113">Als u een externe sessie wilt maken, geeft u de doel computer op met de para meter **hostname** en geeft u de gebruikers naam met de **naam**van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a78b8-113">To create a remote session, you specify the target computer with the **HostName** parameter and provide the user name with **UserName**.</span></span> <span data-ttu-id="a78b8-114">Wanneer de cmdlets interactief worden uitgevoerd, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="a78b8-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="a78b8-115">U kunt ook SSH-sleutel verificatie gebruiken met behulp van een persoonlijke-sleutel bestand met de para meter/ **filepath** .</span><span class="sxs-lookup"><span data-stu-id="a78b8-115">You can also use SSH key authentication using a private key file with the **KeyFilePath** parameter.</span></span> <span data-ttu-id="a78b8-116">Het maken van sleutels voor SSH-verificatie varieert per platform.</span><span class="sxs-lookup"><span data-stu-id="a78b8-116">Creating keys for SSH authentication varies by platform.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="a78b8-117">Algemene informatie over de installatie</span><span class="sxs-lookup"><span data-stu-id="a78b8-117">General setup information</span></span>

<span data-ttu-id="a78b8-118">Power shell 6 of hoger en SSH moet op alle computers zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="a78b8-118">PowerShell 6 or higher, and SSH must be installed on all computers.</span></span> <span data-ttu-id="a78b8-119">Installeer zowel de SSH-client ( `ssh.exe` ) als de server ( `sshd.exe` ), zodat u op afstand van en naar de computers kunt.</span><span class="sxs-lookup"><span data-stu-id="a78b8-119">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the computers.</span></span> <span data-ttu-id="a78b8-120">OpenSSH voor Windows is nu beschikbaar in Windows 10 build 1809 en Windows Server 2019.</span><span class="sxs-lookup"><span data-stu-id="a78b8-120">OpenSSH for Windows is now available in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="a78b8-121">Zie [Manage Windows with OpenSSH](/windows-server/administration/openssh/openssh_overview)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a78b8-121">For more information, see [Manage Windows with OpenSSH](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="a78b8-122">Voor Linux installeert u SSH, met inbegrip van de sshd-server, die geschikt is voor uw platform.</span><span class="sxs-lookup"><span data-stu-id="a78b8-122">For Linux, install SSH, including sshd server, that's appropriate for your platform.</span></span> <span data-ttu-id="a78b8-123">U moet Power shell ook installeren vanaf GitHub om de externe SSH-functie te krijgen.</span><span class="sxs-lookup"><span data-stu-id="a78b8-123">You also need to install PowerShell from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="a78b8-124">De SSH-server moet worden geconfigureerd om een SSH-subsysteem te maken voor het hosten van een Power Shell-proces op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="a78b8-124">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote computer.</span></span> <span data-ttu-id="a78b8-125">En u moet verificatie **op basis van** **wacht woord** of sleutel inschakelen.</span><span class="sxs-lookup"><span data-stu-id="a78b8-125">And, you must enable **password** or **key-based** authentication.</span></span>

## <a name="set-up-on-a-windows-computer"></a><span data-ttu-id="a78b8-126">Instellen op een Windows-computer</span><span class="sxs-lookup"><span data-stu-id="a78b8-126">Set up on a Windows computer</span></span>

1. <span data-ttu-id="a78b8-127">Installeer de meest recente versie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="a78b8-127">Install the latest version of PowerShell.</span></span> <span data-ttu-id="a78b8-128">Zie [Power shell Core installeren op Windows](../../install/installing-powershell-core-on-windows.md#msi)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a78b8-128">For more information, see [Installing PowerShell Core on Windows](../../install/installing-powershell-core-on-windows.md#msi).</span></span>

   <span data-ttu-id="a78b8-129">U kunt controleren of Power Shell ondersteuning biedt voor externe SSH door de `New-PSSession` parameter sets op te geven.</span><span class="sxs-lookup"><span data-stu-id="a78b8-129">You can confirm that PowerShell has SSH remoting support by listing the `New-PSSession` parameter sets.</span></span> <span data-ttu-id="a78b8-130">U ziet dat er namen van parameter sets zijn die beginnen met **SSH**.</span><span class="sxs-lookup"><span data-stu-id="a78b8-130">You'll notice there are parameter set names that begin with **SSH**.</span></span> <span data-ttu-id="a78b8-131">Deze parameter sets bevatten **SSH** -para meters.</span><span class="sxs-lookup"><span data-stu-id="a78b8-131">Those parameter sets include **SSH** parameters.</span></span>

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. <span data-ttu-id="a78b8-132">Installeer de meest recente Win32-OpenSSH.</span><span class="sxs-lookup"><span data-stu-id="a78b8-132">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="a78b8-133">Zie aan de slag [met OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse)voor installatie-instructies.</span><span class="sxs-lookup"><span data-stu-id="a78b8-133">For installation instructions, see [Getting started with OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>

   > [!NOTE]
   > <span data-ttu-id="a78b8-134">Als u Power shell wilt instellen als de standaard shell voor OpenSSH, raadpleegt u [Windows configureren voor OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).</span><span class="sxs-lookup"><span data-stu-id="a78b8-134">If you want to set PowerShell as the default shell for OpenSSH, see [Configuring Windows for OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).</span></span>

1. <span data-ttu-id="a78b8-135">Bewerk het `sshd_config` bestand dat zich bevindt in `$env:ProgramData\ssh` .</span><span class="sxs-lookup"><span data-stu-id="a78b8-135">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   <span data-ttu-id="a78b8-136">Controleer of wachtwoord verificatie is ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="a78b8-136">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="a78b8-137">Maak het SSH-subsysteem dat als host fungeert voor een Power Shell-proces op de externe computer:</span><span class="sxs-lookup"><span data-stu-id="a78b8-137">Create the SSH subsystem that hosts a PowerShell process on the remote computer:</span></span>

   ```
   Subsystem powershell c:/progra~1/powershell/7/pwsh.exe -sshs -NoLogo
   ```

   > [!NOTE]
   > <span data-ttu-id="a78b8-138">De standaard locatie van het uitvoer bare Power shell-bestand is `c:/progra~1/powershell/7/pwsh.exe` .</span><span class="sxs-lookup"><span data-stu-id="a78b8-138">The default location of the PowerShell executable is `c:/progra~1/powershell/7/pwsh.exe`.</span></span> <span data-ttu-id="a78b8-139">De locatie kan variëren, afhankelijk van de manier waarop u Power shell hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="a78b8-139">The location can vary depending on how you installed PowerShell.</span></span>
   >
   > <span data-ttu-id="a78b8-140">U moet de korte naam van 8,3 gebruiken voor bestands paden die spaties bevatten.</span><span class="sxs-lookup"><span data-stu-id="a78b8-140">You must use the 8.3 short name for any file paths that contain spaces.</span></span> <span data-ttu-id="a78b8-141">Er is een fout in OpenSSH voor Windows waarmee wordt voor komen dat ruimten in subsysteem uitvoer bare paden werken.</span><span class="sxs-lookup"><span data-stu-id="a78b8-141">There's a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="a78b8-142">Zie voor meer informatie dit [github-probleem](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="a78b8-142">For more information, see this [GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>
   >
   > <span data-ttu-id="a78b8-143">De korte naam van 8,3 voor de `Program Files` map in Windows is doorgaans `Progra~1` .</span><span class="sxs-lookup"><span data-stu-id="a78b8-143">The 8.3 short name for the `Program Files` folder in Windows is usually `Progra~1`.</span></span> <span data-ttu-id="a78b8-144">U kunt echter de volgende opdracht gebruiken om ervoor te zorgen:</span><span class="sxs-lookup"><span data-stu-id="a78b8-144">However, you can use the following command to make sure:</span></span>
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

   <span data-ttu-id="a78b8-145">Schakel eventueel sleutel verificatie in:</span><span class="sxs-lookup"><span data-stu-id="a78b8-145">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

   <span data-ttu-id="a78b8-146">Zie [Managing OpenSSH Keys](/windows-server/administration/openssh/openssh_keymanagement)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a78b8-146">For more information, see [Managing OpenSSH Keys](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

1. <span data-ttu-id="a78b8-147">Start de service **sshd** opnieuw.</span><span class="sxs-lookup"><span data-stu-id="a78b8-147">Restart the **sshd** service.</span></span>

   ```powershell
   Restart-Service sshd
   ```

1. <span data-ttu-id="a78b8-148">Voeg het pad toe waar OpenSSH wordt geïnstalleerd in uw omgevings variabele PATH.</span><span class="sxs-lookup"><span data-stu-id="a78b8-148">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="a78b8-149">Bijvoorbeeld `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="a78b8-149">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="a78b8-150">Met deze vermelding kan de worden `ssh.exe` gevonden.</span><span class="sxs-lookup"><span data-stu-id="a78b8-150">This entry allows for the `ssh.exe` to be found.</span></span>

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a><span data-ttu-id="a78b8-151">Instellen op een Ubuntu 16,04 Linux-computer</span><span class="sxs-lookup"><span data-stu-id="a78b8-151">Set up on an Ubuntu 16.04 Linux computer</span></span>

1. <span data-ttu-id="a78b8-152">Installeer de meest recente versie van Power shell, Zie [Power shell Core installeren op Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).</span><span class="sxs-lookup"><span data-stu-id="a78b8-152">Install the latest version of PowerShell, see [Installing PowerShell Core on Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).</span></span>
1. <span data-ttu-id="a78b8-153">Installeer de [Ubuntu openssh-server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span><span class="sxs-lookup"><span data-stu-id="a78b8-153">Install [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. <span data-ttu-id="a78b8-154">Bewerk het `sshd_config` bestand op locatie `/etc/ssh` .</span><span class="sxs-lookup"><span data-stu-id="a78b8-154">Edit the `sshd_config` file at location `/etc/ssh`.</span></span>

   <span data-ttu-id="a78b8-155">Controleer of wachtwoord verificatie is ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="a78b8-155">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="a78b8-156">Schakel eventueel sleutel verificatie in:</span><span class="sxs-lookup"><span data-stu-id="a78b8-156">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

   <span data-ttu-id="a78b8-157">Zie de manpage voor [ssh-keygen](http://manpages.ubuntu.com/manpages/xenial/man1/ssh-keygen.1.html)voor meer informatie over het maken van SSH-sleutels op Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="a78b8-157">For more information about creating SSH keys on Ubuntu, see the manpage for [ssh-keygen](http://manpages.ubuntu.com/manpages/xenial/man1/ssh-keygen.1.html).</span></span>

   <span data-ttu-id="a78b8-158">Een vermelding voor een Power shell-subsysteem toevoegen:</span><span class="sxs-lookup"><span data-stu-id="a78b8-158">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo
   ```

   > [!NOTE]
   > <span data-ttu-id="a78b8-159">De standaard locatie van het uitvoer bare Power shell-bestand is `/usr/bin/pwsh` .</span><span class="sxs-lookup"><span data-stu-id="a78b8-159">The default location of the PowerShell executable is `/usr/bin/pwsh`.</span></span> <span data-ttu-id="a78b8-160">De locatie kan variëren, afhankelijk van de manier waarop u Power shell hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="a78b8-160">The location can vary depending on how you installed PowerShell.</span></span>

   <span data-ttu-id="a78b8-161">Schakel eventueel sleutel verificatie in:</span><span class="sxs-lookup"><span data-stu-id="a78b8-161">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="a78b8-162">Start de **SSH** -service opnieuw.</span><span class="sxs-lookup"><span data-stu-id="a78b8-162">Restart the **ssh** service.</span></span>

   ```bash
   sudo service ssh restart
   ```

## <a name="set-up-on-a-macos-computer"></a><span data-ttu-id="a78b8-163">Instellen op een macOS-computer</span><span class="sxs-lookup"><span data-stu-id="a78b8-163">Set up on a macOS computer</span></span>

1. <span data-ttu-id="a78b8-164">Installeer de meest recente versie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="a78b8-164">Install the latest version of PowerShell.</span></span> <span data-ttu-id="a78b8-165">Voor meer informatie [installeert u Power shell core in macOS](../../install/installing-powershell-core-on-macos.md).</span><span class="sxs-lookup"><span data-stu-id="a78b8-165">For more information, [Installing PowerShell Core on macOS](../../install/installing-powershell-core-on-macos.md).</span></span>

   <span data-ttu-id="a78b8-166">Zorg ervoor dat externe SSH-communicatie is ingeschakeld door de volgende stappen te volgen:</span><span class="sxs-lookup"><span data-stu-id="a78b8-166">Make sure SSH Remoting is enabled by following these steps:</span></span>

   1. <span data-ttu-id="a78b8-167">Open `System Preferences`.</span><span class="sxs-lookup"><span data-stu-id="a78b8-167">Open `System Preferences`.</span></span>
   1. <span data-ttu-id="a78b8-168">Klik op `Sharing`.</span><span class="sxs-lookup"><span data-stu-id="a78b8-168">Click on `Sharing`.</span></span>
   1. <span data-ttu-id="a78b8-169">Selecteer deze optie `Remote Login` `Remote Login: On` .</span><span class="sxs-lookup"><span data-stu-id="a78b8-169">Check `Remote Login` to set `Remote Login: On`.</span></span>
   1. <span data-ttu-id="a78b8-170">Toegang tot de juiste gebruikers toestaan.</span><span class="sxs-lookup"><span data-stu-id="a78b8-170">Allow access to the appropriate users.</span></span>

1. <span data-ttu-id="a78b8-171">Bewerk het `sshd_config` bestand op locatie `/private/etc/ssh/sshd_config` .</span><span class="sxs-lookup"><span data-stu-id="a78b8-171">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`.</span></span>

   <span data-ttu-id="a78b8-172">Gebruik een tekst editor zoals **nano**:</span><span class="sxs-lookup"><span data-stu-id="a78b8-172">Use a text editor such as **nano**:</span></span>

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   <span data-ttu-id="a78b8-173">Controleer of wachtwoord verificatie is ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="a78b8-173">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="a78b8-174">Een vermelding voor een Power shell-subsysteem toevoegen:</span><span class="sxs-lookup"><span data-stu-id="a78b8-174">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo
   ```

   > [!NOTE]
   > <span data-ttu-id="a78b8-175">De standaard locatie van het uitvoer bare Power shell-bestand is `/usr/local/bin/pwsh` .</span><span class="sxs-lookup"><span data-stu-id="a78b8-175">The default location of the PowerShell executable is `/usr/local/bin/pwsh`.</span></span> <span data-ttu-id="a78b8-176">De locatie kan variëren, afhankelijk van de manier waarop u Power shell hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="a78b8-176">The location can vary depending on how you installed PowerShell.</span></span>

   <span data-ttu-id="a78b8-177">Schakel eventueel sleutel verificatie in:</span><span class="sxs-lookup"><span data-stu-id="a78b8-177">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="a78b8-178">Start de service **sshd** opnieuw.</span><span class="sxs-lookup"><span data-stu-id="a78b8-178">Restart the **sshd** service.</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="a78b8-179">Verificatie</span><span class="sxs-lookup"><span data-stu-id="a78b8-179">Authentication</span></span>

<span data-ttu-id="a78b8-180">Externe communicatie van Power shell is afhankelijk van de verificatie uitwisseling tussen de SSH-client en de SSH-service en implementeert geen verificatie schema's zelf.</span><span class="sxs-lookup"><span data-stu-id="a78b8-180">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and doesn't implement any authentication schemes itself.</span></span> <span data-ttu-id="a78b8-181">Het resultaat is dat alle geconfigureerde verificatie schema's, waaronder multi-factor Authentication, worden afgehandeld door SSH en onafhankelijk van Power shell.</span><span class="sxs-lookup"><span data-stu-id="a78b8-181">The result is that any configured authentication schemes including multi-factor authentication are handled by SSH and independent of PowerShell.</span></span> <span data-ttu-id="a78b8-182">U kunt bijvoorbeeld de SSH-service zo configureren dat verificatie met een open bare sleutel en een eenmalig wacht woord voor extra beveiliging zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="a78b8-182">For example, you can configure the SSH service to require public key authentication and a one-time password for added security.</span></span> <span data-ttu-id="a78b8-183">Configuratie van multi-factor Authentication valt buiten het bereik van deze documentatie.</span><span class="sxs-lookup"><span data-stu-id="a78b8-183">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span> <span data-ttu-id="a78b8-184">Raadpleeg de documentatie voor SSH over het correct configureren van multi-factor Authentication en het valideren van de oplossing werkt buiten Power shell voordat u deze probeert te gebruiken met externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="a78b8-184">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

> [!NOTE]
> <span data-ttu-id="a78b8-185">Gebruikers behouden dezelfde bevoegdheden in externe sessies.</span><span class="sxs-lookup"><span data-stu-id="a78b8-185">Users retain the same privileges in remote sessions.</span></span> <span data-ttu-id="a78b8-186">Dat wil zeggen dat beheerders toegang hebben tot een verhoogde shell en dat gewone gebruikers dat niet doen.</span><span class="sxs-lookup"><span data-stu-id="a78b8-186">Meaning, Administrators have access to an elevated shell, and normal users will not.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="a78b8-187">Externe Power shell-voor beeld</span><span class="sxs-lookup"><span data-stu-id="a78b8-187">PowerShell remoting example</span></span>

<span data-ttu-id="a78b8-188">De eenvoudigste manier om externe communicatie te testen is door deze te proberen op één computer.</span><span class="sxs-lookup"><span data-stu-id="a78b8-188">The easiest way to test remoting is to try it on a single computer.</span></span> <span data-ttu-id="a78b8-189">In dit voor beeld maken we een externe sessie terug naar dezelfde Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="a78b8-189">In this example, we create a remote session back to the same Linux computer.</span></span> <span data-ttu-id="a78b8-190">Power shell-cmdlets worden interactief gebruikt, dus er worden prompts van SSH weer gegeven waarin wordt gevraagd om de hostcomputer te controleren en te vragen om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="a78b8-190">We're using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="a78b8-191">U kunt hetzelfde doen op een Windows-computer om ervoor te zorgen dat externe toegang werkt.</span><span class="sxs-lookup"><span data-stu-id="a78b8-191">You can do the same thing on a Windows computer to ensure remoting is working.</span></span> <span data-ttu-id="a78b8-192">Vervolgens op afstand tussen computers door de hostnaam te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a78b8-192">Then, remote between computers by changing the host name.</span></span>

```powershell
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

```
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

### <a name="limitations"></a><span data-ttu-id="a78b8-193">Beperkingen</span><span class="sxs-lookup"><span data-stu-id="a78b8-193">Limitations</span></span>

- <span data-ttu-id="a78b8-194">De opdracht **sudo** werkt niet in een externe sessie met een Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="a78b8-194">The **sudo** command doesn't work in a remote session to a Linux computer.</span></span>

- <span data-ttu-id="a78b8-195">PSRemoting via SSH ondersteunt geen profielen en heeft geen toegang tot `$PROFILE` .</span><span class="sxs-lookup"><span data-stu-id="a78b8-195">PSRemoting over SSH does not support Profiles and does not have access to `$PROFILE`.</span></span> <span data-ttu-id="a78b8-196">Eenmaal in een sessie kunt u een profiel laden met punt op het profiel met het volledige bestandspad.</span><span class="sxs-lookup"><span data-stu-id="a78b8-196">Once in a session, you can load a profile by dot sourcing the profile with the full filepath.</span></span> <span data-ttu-id="a78b8-197">Dit is niet gerelateerd aan SSH-profielen.</span><span class="sxs-lookup"><span data-stu-id="a78b8-197">This is not related to SSH profiles.</span></span> <span data-ttu-id="a78b8-198">U kunt de SSH-server configureren voor het gebruik van Power shell als de standaard shell en een profiel laden via SSH.</span><span class="sxs-lookup"><span data-stu-id="a78b8-198">You can configure the SSH server to use PowerShell as the default shell and to load a profile through SSH.</span></span> <span data-ttu-id="a78b8-199">Raadpleeg de SSH-documentatie voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a78b8-199">See the SSH documentation for more information.</span></span>

- <span data-ttu-id="a78b8-200">Voorafgaand aan Power shell 7,1 heeft externe toegang via SSH geen ondersteuning voor externe sessies van de tweede hop.</span><span class="sxs-lookup"><span data-stu-id="a78b8-200">Prior to PowerShell 7.1, remoting over SSH did not support second-hop remote sessions.</span></span> <span data-ttu-id="a78b8-201">Deze mogelijkheid is beperkt tot sessies met WinRM.</span><span class="sxs-lookup"><span data-stu-id="a78b8-201">This capability was limited to sessions using WinRM.</span></span> <span data-ttu-id="a78b8-202">Met Power shell 7,1 kunt `Enter-PSSession` `Enter-PSHostProcess` u binnen elke interactieve externe sessie werken.</span><span class="sxs-lookup"><span data-stu-id="a78b8-202">PowerShell 7.1 allows `Enter-PSSession` and `Enter-PSHostProcess` to work from within any interactive remote session.</span></span>

## <a name="see-also"></a><span data-ttu-id="a78b8-203">Zie tevens</span><span class="sxs-lookup"><span data-stu-id="a78b8-203">See also</span></span>

<span data-ttu-id="a78b8-204">[Installing PowerShell Core on Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) (PowerShell Core installeren in Linux)</span><span class="sxs-lookup"><span data-stu-id="a78b8-204">[Installing PowerShell Core on Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)</span></span>

<span data-ttu-id="a78b8-205">[Installing PowerShell Core on macOS](../../install/installing-powershell-core-on-macos.md) (PowerShell Core installeren in macOS)</span><span class="sxs-lookup"><span data-stu-id="a78b8-205">[Installing PowerShell Core on macOS](../../install/installing-powershell-core-on-macos.md)</span></span>

[<span data-ttu-id="a78b8-206">PowerShell Core in Windows installeren</span><span class="sxs-lookup"><span data-stu-id="a78b8-206">Installing PowerShell Core on Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="a78b8-207">Windows beheren met OpenSSH</span><span class="sxs-lookup"><span data-stu-id="a78b8-207">Manage Windows with OpenSSH</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="a78b8-208">OpenSSH-sleutels beheren</span><span class="sxs-lookup"><span data-stu-id="a78b8-208">Managing OpenSSH Keys</span></span>](/windows-server/administration/openssh/openssh_keymanagement)

[<span data-ttu-id="a78b8-209">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="a78b8-209">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
