# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="348e0-101">Externe communicatie van PowerShell via SSH</span><span class="sxs-lookup"><span data-stu-id="348e0-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="348e0-102">Overzicht</span><span class="sxs-lookup"><span data-stu-id="348e0-102">Overview</span></span>

<span data-ttu-id="348e0-103">Externe communicatie van PowerShell gebruikt normaal gesproken WinRM voor verbinding onderhandeling en data-transport.</span><span class="sxs-lookup"><span data-stu-id="348e0-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="348e0-104">SSH is gekozen voor deze implementatie van externe toegang, omdat deze nu beschikbaar voor Linux- en Windows-platforms is en waar meerdere platforms PowerShell voor externe toegang kunt.</span><span class="sxs-lookup"><span data-stu-id="348e0-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="348e0-105">WinRM bevat echter ook een robuuste hostingmodel voor externe PowerShell-sessies die deze implementatie wordt nog niet.</span><span class="sxs-lookup"><span data-stu-id="348e0-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="348e0-106">En dit betekent dat externe PowerShell-eindpuntconfiguratie en JEA (net genoeg beheer) wordt nog niet ondersteund in deze implementatie.</span><span class="sxs-lookup"><span data-stu-id="348e0-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="348e0-107">PowerShell SSH remoting kunt u doen basic PowerShell-sessie op afstand tussen Windows en Linux-machines.</span><span class="sxs-lookup"><span data-stu-id="348e0-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="348e0-108">Dit wordt gedaan door het maken van een PowerShell-proces op de doelcomputer als een SSH-subsysteem hosten.</span><span class="sxs-lookup"><span data-stu-id="348e0-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="348e0-109">Dit wordt uiteindelijk gewijzigd in een meer algemene hostingmodel die vergelijkbaar is met de werking van WinRM ter ondersteuning van endpoint-configuratie en JEA.</span><span class="sxs-lookup"><span data-stu-id="348e0-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="348e0-110">De cmdlets New-PSSession, Enter-PSSession en Invoke-Command hebt nu een nieuwe parameterset ter bevordering van deze nieuwe verbinding voor externe toegang</span><span class="sxs-lookup"><span data-stu-id="348e0-110">The New-PSSession, Enter-PSSession and Invoke-Command cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="348e0-111">Deze nieuwe parameterset zullen waarschijnlijk veranderen, maar nu kunt u voor het maken van SSH PSSessions communiceren met vanaf de opdrachtregel of opdrachten en scripts op worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="348e0-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="348e0-112">U de doelmachine opgeven met de parameter hostnaam en geef de gebruikersnaam op die met gebruikersnaam.</span><span class="sxs-lookup"><span data-stu-id="348e0-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="348e0-113">Wanneer de cmdlets interactief wordt uitgevoerd op de PowerShell-opdrachtregel wordt u gevraagd om een wachtwoord.</span><span class="sxs-lookup"><span data-stu-id="348e0-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="348e0-114">Maar u hebt ook de optie voor het gebruik van SSH-sleutelverificatie en geef een pad op persoonlijke sleutelbestand met de parameter KeyFilePath.</span><span class="sxs-lookup"><span data-stu-id="348e0-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="348e0-115">Informatie over algemene instellingen</span><span class="sxs-lookup"><span data-stu-id="348e0-115">General setup information</span></span>

<span data-ttu-id="348e0-116">SSH is vereist om te worden geïnstalleerd op alle machines.</span><span class="sxs-lookup"><span data-stu-id="348e0-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="348e0-117">U moet zowel de client (ssh.exe) als de server (sshd.exe) installeren zodat u met externe toegang naar en van de machines experimenteren kunt.</span><span class="sxs-lookup"><span data-stu-id="348e0-117">You should install both client (ssh.exe) and server (sshd.exe) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="348e0-118">Voor Windows moet u installeren [Win32 OpenSSH vanuit GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="348e0-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="348e0-119">Voor Linux moet u geschikt is voor uw platform SSH (inclusief sshd server) installeren.</span><span class="sxs-lookup"><span data-stu-id="348e0-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="348e0-120">U moet ook een recente PowerShell build of een pakket vanuit de externecommunicatiefunctie van SSH met GitHub.</span><span class="sxs-lookup"><span data-stu-id="348e0-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="348e0-121">SSH subsystemen wordt gebruikt voor het opzetten van een PowerShell-proces op de externe computer en de SSH-server moet worden geconfigureerd voor die.</span><span class="sxs-lookup"><span data-stu-id="348e0-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="348e0-122">Bovendien moet u wachtwoordverificatie en eventueel sleutel gebaseerde authenticatie inschakelen.</span><span class="sxs-lookup"><span data-stu-id="348e0-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="348e0-123">Setup op Windows-computer</span><span class="sxs-lookup"><span data-stu-id="348e0-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="348e0-124">Installeer de nieuwste versie van [Core voor Windows PowerShell]</span><span class="sxs-lookup"><span data-stu-id="348e0-124">Install the latest version of [PowerShell Core for Windows]</span></span>
    - <span data-ttu-id="348e0-125">U kunt zien dat als de SSH-ondersteuning voor externe communicatie door te kijken heeft de parameter wordt ingesteld voor New-PSSession</span><span class="sxs-lookup"><span data-stu-id="348e0-125">You can tell if it has the SSH remoting support by looking at the parameter sets for New-PSSession</span></span>

    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```

1. <span data-ttu-id="348e0-126">Installeer de meest recente [Win32-OpenSSH] opbouwen vanuit GitHub met de [installatie] instructies</span><span class="sxs-lookup"><span data-stu-id="348e0-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
1. <span data-ttu-id="348e0-127">Bewerk het bestand sshd_config op de locatie waar u de Win32-OpenSSH geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="348e0-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
    - <span data-ttu-id="348e0-128">Zorg ervoor dat de wachtwoordverificatie is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="348e0-128">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="348e0-129">De vermelding voor een PowerShell-subsysteem toevoegen, vervangen door `c:/program files/powershell/6.0.0/pwsh.exe` met het juiste pad naar de versie die u wilt gebruiken</span><span class="sxs-lookup"><span data-stu-id="348e0-129">Add a PowerShell subsystem entry, replace `c:/program files/powershell/6.0.0/pwsh.exe` with the correct path to the version you want to use</span></span>

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="348e0-130">Verificatie met sleutel (optioneel) inschakelen</span><span class="sxs-lookup"><span data-stu-id="348e0-130">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="348e0-131">Start de service sshd</span><span class="sxs-lookup"><span data-stu-id="348e0-131">Restart the sshd service</span></span>

    ```powershell
    Restart-Service sshd
    ```

1. <span data-ttu-id="348e0-132">Het pad waar OpenSSH is geïnstalleerd op uw pad Env variabele toevoegen</span><span class="sxs-lookup"><span data-stu-id="348e0-132">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
    - <span data-ttu-id="348e0-133">Dit moet langs de lijnen van `C:\Program Files\OpenSSH\`</span><span class="sxs-lookup"><span data-stu-id="348e0-133">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
    - <span data-ttu-id="348e0-134">Hiermee kunt u de ssh.exe die u wilt zoeken</span><span class="sxs-lookup"><span data-stu-id="348e0-134">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="348e0-135">Setup op de Machine met Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="348e0-135">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="348e0-136">Installeer de meest recente [PowerShell voor Linux] opbouwen vanuit GitHub</span><span class="sxs-lookup"><span data-stu-id="348e0-136">Install the latest [PowerShell for Linux] build from GitHub</span></span>
1. <span data-ttu-id="348e0-137">Installeer [Ubuntu SSH] indien nodig</span><span class="sxs-lookup"><span data-stu-id="348e0-137">Install [Ubuntu SSH] as needed</span></span>

    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```

1. <span data-ttu-id="348e0-138">Bewerk het bestand sshd_config op locatie /etc/ssh</span><span class="sxs-lookup"><span data-stu-id="348e0-138">Edit the sshd_config file at location /etc/ssh</span></span>
    - <span data-ttu-id="348e0-139">Zorg ervoor dat de wachtwoordverificatie is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="348e0-139">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="348e0-140">Een PowerShell-subsysteem vermelding toevoegen</span><span class="sxs-lookup"><span data-stu-id="348e0-140">Add a PowerShell subsystem entry</span></span>

    ```
    Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="348e0-141">Verificatie met sleutel (optioneel) inschakelen</span><span class="sxs-lookup"><span data-stu-id="348e0-141">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="348e0-142">Start de service sshd</span><span class="sxs-lookup"><span data-stu-id="348e0-142">Restart the sshd service</span></span>

    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="348e0-143">Setup op Mac OS-Machine</span><span class="sxs-lookup"><span data-stu-id="348e0-143">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="348e0-144">Installeer de meest recente [PowerShell voor Mac OS] bouwen</span><span class="sxs-lookup"><span data-stu-id="348e0-144">Install the latest [PowerShell for MacOS] build</span></span>
    - <span data-ttu-id="348e0-145">Controleer of dat de SSH-externe toegang is ingeschakeld met de volgende stappen:</span><span class="sxs-lookup"><span data-stu-id="348e0-145">Make sure SSH Remoting is enabled by following these steps:</span></span>
      - <span data-ttu-id="348e0-146">openen `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="348e0-146">Open `System Preferences`</span></span>
      - <span data-ttu-id="348e0-147">Klik op `Sharing`</span><span class="sxs-lookup"><span data-stu-id="348e0-147">Click on `Sharing`</span></span>
      - <span data-ttu-id="348e0-148">Controleer `Remote Login` -melding `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="348e0-148">Check `Remote Login` - Should say `Remote Login: On`</span></span>
      - <span data-ttu-id="348e0-149">Toegang tot de juiste gebruikers toestaan</span><span class="sxs-lookup"><span data-stu-id="348e0-149">Allow access to appropriate users</span></span>
1. <span data-ttu-id="348e0-150">Bewerk de `sshd_config` bestand op locatie `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="348e0-150">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
    - <span data-ttu-id="348e0-151">Uw favoriete editor gebruiken of</span><span class="sxs-lookup"><span data-stu-id="348e0-151">Use your favorite editor or</span></span>

    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```

    - <span data-ttu-id="348e0-152">Zorg ervoor dat de wachtwoordverificatie is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="348e0-152">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="348e0-153">Een PowerShell-subsysteem vermelding toevoegen</span><span class="sxs-lookup"><span data-stu-id="348e0-153">Add a PowerShell subsystem entry</span></span>

    ```
    Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="348e0-154">Verificatie met sleutel (optioneel) inschakelen</span><span class="sxs-lookup"><span data-stu-id="348e0-154">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="348e0-155">Start de service sshd</span><span class="sxs-lookup"><span data-stu-id="348e0-155">Restart the sshd service</span></span>

    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="348e0-156">Voorbeeld van een externe communicatie van PowerShell</span><span class="sxs-lookup"><span data-stu-id="348e0-156">PowerShell Remoting Example</span></span>

<span data-ttu-id="348e0-157">De eenvoudigste manier om te testen voor externe toegang is zojuist probeer op een enkele computer.</span><span class="sxs-lookup"><span data-stu-id="348e0-157">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="348e0-158">Ik maak hier een externe sessie naar dezelfde machine op een Linux-vak.</span><span class="sxs-lookup"><span data-stu-id="348e0-158">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="348e0-159">U ziet dat ik gebruik PowerShell-cmdlets uit vanaf de opdrachtprompt zodat we zien prompts van SSH waarin wordt gevraagd om te controleren of de hostcomputer evenals een wachtwoord wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="348e0-159">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="348e0-160">Hetzelfde geldt voor een Windows-computer om ervoor te zorgen voor externe toegang er werkt en vervolgens de afstand tussen machines door gewoon de hostnaam van de te wijzigen, kunt u doen.</span><span class="sxs-lookup"><span data-stu-id="348e0-160">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
PS /home/TestUser> $session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:

PS /home/TestUser> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available

PS /home/TestUser> Enter-PSSession $session

[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession

PS /home/TestUser> Invoke-Command $session -ScriptBlock { Get-Process powershell }

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1


#
# Linux to Windows
#
PS /home/TestUser> Enter-PSSession -HostName WinVM1 -UserName PTestName
PTestName@WinVM1s password:

[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver

Microsoft Windows [Version 10.0.10586]

[WinVM1]: PS C:\Users\PTestName\Documents>

#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.

PS C:\Users\PSUser\Documents> $session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
PS C:\Users\PSUser\Documents> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available


PS C:\Users\PSUser\Documents> Enter-PSSession -Session $session
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

### <a name="known-issues"></a><span data-ttu-id="348e0-161">Bekende problemen</span><span class="sxs-lookup"><span data-stu-id="348e0-161">Known Issues</span></span>

1. <span data-ttu-id="348e0-162">sudo-opdracht werkt niet in de externe sessie op Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="348e0-162">sudo command does not work in remote session to Linux machine.</span></span>

[Core voor Windows PowerShell]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[PowerShell Core for Windows]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[Win32-OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH/releases
[Win32 OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH/releases
[Installatie]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[installation]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[PowerShell voor Linux]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[PowerShell for Linux]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
[PowerShell voor Mac OS]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md#macos-1012
[PowerShell for MacOS]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md#macos-1012
