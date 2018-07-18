
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="6f20e-101">Externe communicatie van PowerShell via SSH</span><span class="sxs-lookup"><span data-stu-id="6f20e-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="6f20e-102">Overzicht</span><span class="sxs-lookup"><span data-stu-id="6f20e-102">Overview</span></span>

<span data-ttu-id="6f20e-103">PowerShell voor externe toegang gebruikt normaal gesproken WinRM verbinding-onderhandeling en gegevenstransport.</span><span class="sxs-lookup"><span data-stu-id="6f20e-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="6f20e-104">SSH is gekozen voor deze implementatie voor externe toegang, omdat deze nu beschikbaar voor zowel Windows als Linux-platforms is en waar meerdere platforms PowerShell voor externe toegang kunt.</span><span class="sxs-lookup"><span data-stu-id="6f20e-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="6f20e-105">WinRM biedt een robuuste hostingmodel echter ook voor externe PowerShell-sessies die deze implementatie wordt nog niet.</span><span class="sxs-lookup"><span data-stu-id="6f20e-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="6f20e-106">En dit betekent dat PowerShell externe eindpunt-configuratie en JEA (Just Enough Administration) wordt nog niet ondersteund in deze implementatie.</span><span class="sxs-lookup"><span data-stu-id="6f20e-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="6f20e-107">PowerShell SSH voor externe toegang kunt u eenvoudige PowerShell-sessie voor externe toegang tussen Windows en Linux-machines.</span><span class="sxs-lookup"><span data-stu-id="6f20e-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="6f20e-108">Dit wordt gedaan door het maken van een PowerShell-proces op de doel-VM als een SSH-subsysteem te hosten.</span><span class="sxs-lookup"><span data-stu-id="6f20e-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="6f20e-109">Dit wordt uiteindelijk worden gewijzigd naar een meer algemene hostingmodel die vergelijkbaar is met de werking van WinRM ter ondersteuning van de configuratie van eindpunten en JEA.</span><span class="sxs-lookup"><span data-stu-id="6f20e-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="6f20e-110">De `New-PSSession`, `Enter-PSSession` en `Invoke-Command` cmdlets hebben nu een nieuwe parameterset om deze nieuwe verbinding voor externe toegang mogelijk te maken</span><span class="sxs-lookup"><span data-stu-id="6f20e-110">The `New-PSSession`, `Enter-PSSession` and `Invoke-Command` cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="6f20e-111">Deze nieuwe parameterset waarschijnlijk zullen veranderen, maar voor nu kunt u maken van SSH PSSessions kunt u communiceren met vanaf de opdrachtregel of opdrachten en scripts aanroepen op.</span><span class="sxs-lookup"><span data-stu-id="6f20e-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="6f20e-112">U opgeven van de doel-VM met de parameter hostnaam en gebruikersnaam van de naam van de gebruiker voorzien.</span><span class="sxs-lookup"><span data-stu-id="6f20e-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="6f20e-113">Als de cmdlets interactief wordt uitgevoerd op de PowerShell-opdrachtregel wordt u gevraagd om een wachtwoord.</span><span class="sxs-lookup"><span data-stu-id="6f20e-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="6f20e-114">Maar u hebt ook de optie voor het gebruik van verificatie van SSH-sleutel en geef het pad van een bestand met persoonlijke sleutel met de parameter KeyFilePath.</span><span class="sxs-lookup"><span data-stu-id="6f20e-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="6f20e-115">Algemene instellingen</span><span class="sxs-lookup"><span data-stu-id="6f20e-115">General setup information</span></span>

<span data-ttu-id="6f20e-116">SSH is vereist om te worden geïnstalleerd op alle virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="6f20e-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="6f20e-117">U moet zowel client installeren (`ssh.exe`) en de server (`sshd.exe`) zodat u met externe toegang naar en van de machines experimenteren kunt.</span><span class="sxs-lookup"><span data-stu-id="6f20e-117">You should install both client (`ssh.exe`) and server (`sshd.exe`) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="6f20e-118">Voor Windows moet u voor het installeren van [Win32-OpenSSH vanuit GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="6f20e-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="6f20e-119">Voor Linux moet u SSH (inclusief sshd-server) geschikt is voor uw platform installeren.</span><span class="sxs-lookup"><span data-stu-id="6f20e-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="6f20e-120">U moet ook een recente PowerShell-build of een pakket van de SSH-functie voor externe communicatie met GitHub.</span><span class="sxs-lookup"><span data-stu-id="6f20e-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="6f20e-121">SSH-subsystemen tot stand brengen van een PowerShell-proces op de externe computer wordt gebruikt en de SSH-server moet worden geconfigureerd voor die.</span><span class="sxs-lookup"><span data-stu-id="6f20e-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="6f20e-122">Bovendien moet u wachtwoordverificatie en eventueel sleutel gebaseerde verificatie inschakelen.</span><span class="sxs-lookup"><span data-stu-id="6f20e-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="6f20e-123">Instellen op Windows-Machine</span><span class="sxs-lookup"><span data-stu-id="6f20e-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="6f20e-124">Installeer de nieuwste versie van [PowerShell Core voor Windows]</span><span class="sxs-lookup"><span data-stu-id="6f20e-124">Install the latest version of [PowerShell Core for Windows]</span></span>
   - <span data-ttu-id="6f20e-125">U kunt zien dat als dat zo de SSH-ondersteuning voor externe communicatie is door te kijken naar de parameter wordt ingesteld voor `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="6f20e-125">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

1. <span data-ttu-id="6f20e-126">De meest recente [Win32 OpenSSH]-build installeren vanuit GitHub met behulp van de [installatie]-instructies</span><span class="sxs-lookup"><span data-stu-id="6f20e-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
1. <span data-ttu-id="6f20e-127">Bewerk het bestand sshd_config op de locatie waar u Win32 OpenSSH geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="6f20e-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
   - <span data-ttu-id="6f20e-128">Zorg ervoor dat de wachtwoordverificatie is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="6f20e-128">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    > [!NOTE]
    > <span data-ttu-id="6f20e-129">Er is een fout in OpenSSH voor Windows waarmee wordt voorkomen dat spaties in subsysteem uitvoerbare paden werkt.</span><span class="sxs-lookup"><span data-stu-id="6f20e-129">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span>
    > <span data-ttu-id="6f20e-130">Zie [dit probleem op GitHub voor meer informatie](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="6f20e-130">See [this issue on GitHub for more information](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

    <span data-ttu-id="6f20e-131">Eén oplossing is het maken van een symlink naar de Powershell-installatiemap die geen spaties bevatten:</span><span class="sxs-lookup"><span data-stu-id="6f20e-131">One solution is to create a symlink to the Powershell installation directory that does not contain spaces:</span></span>

    ```powershell
    mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
    ```

    <span data-ttu-id="6f20e-132">en geef de code in het subsysteem:</span><span class="sxs-lookup"><span data-stu-id="6f20e-132">and then enter it in the subsystem:</span></span>

    ```
    Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
    ```

   ```
   Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="6f20e-133">Verificatie met sleutel (optioneel) inschakelen</span><span class="sxs-lookup"><span data-stu-id="6f20e-133">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="6f20e-134">De sshd-service opnieuw starten</span><span class="sxs-lookup"><span data-stu-id="6f20e-134">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

1. <span data-ttu-id="6f20e-135">Het pad waar OpenSSH is geïnstalleerd op uw pad Env variabele toevoegen</span><span class="sxs-lookup"><span data-stu-id="6f20e-135">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
   - <span data-ttu-id="6f20e-136">Dit moet zijn aan de regels van `C:\Program Files\OpenSSH\`</span><span class="sxs-lookup"><span data-stu-id="6f20e-136">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
   - <span data-ttu-id="6f20e-137">Hiermee kunt u de ssh.exe worden gevonden</span><span class="sxs-lookup"><span data-stu-id="6f20e-137">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="6f20e-138">Installatie op de Machine voor Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="6f20e-138">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="6f20e-139">De meest recente [PowerShell Core voor Linux]-build installeren vanuit GitHub</span><span class="sxs-lookup"><span data-stu-id="6f20e-139">Install the latest [PowerShell Core for Linux] build from GitHub</span></span>
1. <span data-ttu-id="6f20e-140">[Ubuntu SSH] indien nodig geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="6f20e-140">Install [Ubuntu SSH] as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. <span data-ttu-id="6f20e-141">Bewerk het bestand sshd_config op locatie /etc/ssh</span><span class="sxs-lookup"><span data-stu-id="6f20e-141">Edit the sshd_config file at location /etc/ssh</span></span>
   - <span data-ttu-id="6f20e-142">Zorg ervoor dat de wachtwoordverificatie is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="6f20e-142">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="6f20e-143">Een PowerShell-subsysteem-item toevoegen</span><span class="sxs-lookup"><span data-stu-id="6f20e-143">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="6f20e-144">Verificatie met sleutel (optioneel) inschakelen</span><span class="sxs-lookup"><span data-stu-id="6f20e-144">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="6f20e-145">De sshd-service opnieuw starten</span><span class="sxs-lookup"><span data-stu-id="6f20e-145">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="6f20e-146">Instellen op MacOS-computer</span><span class="sxs-lookup"><span data-stu-id="6f20e-146">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="6f20e-147">Installeer de nieuwste build van de [PowerShell Core voor MacOS]</span><span class="sxs-lookup"><span data-stu-id="6f20e-147">Install the latest [PowerShell Core for MacOS] build</span></span>
   - <span data-ttu-id="6f20e-148">Zorg ervoor dat SSH voor externe toegang is ingeschakeld door de volgende stappen:</span><span class="sxs-lookup"><span data-stu-id="6f20e-148">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="6f20e-149">Open `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="6f20e-149">Open `System Preferences`</span></span>
     - <span data-ttu-id="6f20e-150">Klik op `Sharing`</span><span class="sxs-lookup"><span data-stu-id="6f20e-150">Click on `Sharing`</span></span>
     - <span data-ttu-id="6f20e-151">Controleer `Remote Login` -melding `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="6f20e-151">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="6f20e-152">Toegang tot de juiste gebruikers toestaan</span><span class="sxs-lookup"><span data-stu-id="6f20e-152">Allow access to appropriate users</span></span>
1. <span data-ttu-id="6f20e-153">Bewerk de `sshd_config` -bestand op locatie `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="6f20e-153">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
   - <span data-ttu-id="6f20e-154">Uw favoriete editor gebruiken of</span><span class="sxs-lookup"><span data-stu-id="6f20e-154">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="6f20e-155">Zorg ervoor dat de wachtwoordverificatie is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="6f20e-155">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="6f20e-156">Een PowerShell-subsysteem-item toevoegen</span><span class="sxs-lookup"><span data-stu-id="6f20e-156">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="6f20e-157">Verificatie met sleutel (optioneel) inschakelen</span><span class="sxs-lookup"><span data-stu-id="6f20e-157">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

1. <span data-ttu-id="6f20e-158">De sshd-service opnieuw starten</span><span class="sxs-lookup"><span data-stu-id="6f20e-158">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="6f20e-159">Voorbeeld van PowerShell voor externe toegang</span><span class="sxs-lookup"><span data-stu-id="6f20e-159">PowerShell Remoting Example</span></span>

<span data-ttu-id="6f20e-160">De eenvoudigste manier om te testen voor externe toegang is om te proberen deze slechts op één computer.</span><span class="sxs-lookup"><span data-stu-id="6f20e-160">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="6f20e-161">Ik zal hier een externe sessie naar dezelfde computer op een Linux-vak maken.</span><span class="sxs-lookup"><span data-stu-id="6f20e-161">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="6f20e-162">U ziet dat ik ben met behulp van PowerShell-cmdlets vanaf een opdrachtprompt, zodat we ziet u aanwijzingen uit in SSH waarin wordt gevraagd om te controleren of de hostcomputer, evenals een wachtwoord wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="6f20e-162">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="6f20e-163">U kunt hetzelfde doen op een Windows-machine om ervoor te zorgen voor externe toegang werkt er en vervolgens extern tussen machines wijzig gewoon de naam van de host.</span><span class="sxs-lookup"><span data-stu-id="6f20e-163">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

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
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available
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

### <a name="known-issues"></a><span data-ttu-id="6f20e-164">Bekende problemen</span><span class="sxs-lookup"><span data-stu-id="6f20e-164">Known Issues</span></span>

- <span data-ttu-id="6f20e-165">sudo-opdracht werkt niet in de externe sessie op Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="6f20e-165">sudo command does not work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f20e-166">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6f20e-166">See Also</span></span>

[<span data-ttu-id="6f20e-167">PowerShell Core voor Windows</span><span class="sxs-lookup"><span data-stu-id="6f20e-167">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="6f20e-168">PowerShell Core voor Linux</span><span class="sxs-lookup"><span data-stu-id="6f20e-168">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="6f20e-169">PowerShell Core voor MacOS</span><span class="sxs-lookup"><span data-stu-id="6f20e-169">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="6f20e-170">Win32-OpenSSH</span><span class="sxs-lookup"><span data-stu-id="6f20e-170">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="6f20e-171">installatie</span><span class="sxs-lookup"><span data-stu-id="6f20e-171">installation</span></span>](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[<span data-ttu-id="6f20e-172">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="6f20e-172">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)