# <a name="powershell-remoting-over-ssh"></a>Externe communicatie van PowerShell via SSH

## <a name="overview"></a>Overzicht

Externe communicatie van PowerShell gebruikt normaal gesproken WinRM voor verbinding onderhandeling en data-transport.
SSH is gekozen voor deze implementatie van externe toegang, omdat deze nu beschikbaar voor Linux- en Windows-platforms is en waar meerdere platforms PowerShell voor externe toegang kunt.
WinRM bevat echter ook een robuuste hostingmodel voor externe PowerShell-sessies die deze implementatie wordt nog niet.
En dit betekent dat externe PowerShell-eindpuntconfiguratie en JEA (net genoeg beheer) wordt nog niet ondersteund in deze implementatie.

PowerShell SSH remoting kunt u doen basic PowerShell-sessie op afstand tussen Windows en Linux-machines.
Dit wordt gedaan door het maken van een PowerShell-proces op de doelcomputer als een SSH-subsysteem hosten.
Dit wordt uiteindelijk gewijzigd in een meer algemene hostingmodel die vergelijkbaar is met de werking van WinRM ter ondersteuning van endpoint-configuratie en JEA.

De cmdlets New-PSSession, Enter-PSSession en Invoke-Command hebt nu een nieuwe parameterset ter bevordering van deze nieuwe verbinding voor externe toegang

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Deze nieuwe parameterset zullen waarschijnlijk veranderen, maar nu kunt u voor het maken van SSH PSSessions communiceren met vanaf de opdrachtregel of opdrachten en scripts op worden aangeroepen.
U de doelmachine opgeven met de parameter hostnaam en geef de gebruikersnaam op die met gebruikersnaam.
Wanneer de cmdlets interactief wordt uitgevoerd op de PowerShell-opdrachtregel wordt u gevraagd om een wachtwoord.
Maar u hebt ook de optie voor het gebruik van SSH-sleutelverificatie en geef een pad op persoonlijke sleutelbestand met de parameter KeyFilePath.

## <a name="general-setup-information"></a>Informatie over algemene instellingen

SSH is vereist om te worden geïnstalleerd op alle machines.
U moet zowel de client (ssh.exe) als de server (sshd.exe) installeren zodat u met externe toegang naar en van de machines experimenteren kunt.
Voor Windows moet u installeren [Win32 OpenSSH vanuit GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
Voor Linux moet u geschikt is voor uw platform SSH (inclusief sshd server) installeren.
U moet ook een recente PowerShell build of een pakket vanuit de externecommunicatiefunctie van SSH met GitHub.
SSH subsystemen wordt gebruikt voor het opzetten van een PowerShell-proces op de externe computer en de SSH-server moet worden geconfigureerd voor die.
Bovendien moet u wachtwoordverificatie en eventueel sleutel gebaseerde authenticatie inschakelen.

## <a name="setup-on-windows-machine"></a>Setup op Windows-computer

1. Installeer de nieuwste versie van [Core voor Windows PowerShell]
    - U kunt zien dat als de SSH-ondersteuning voor externe communicatie door te kijken heeft de parameter wordt ingesteld voor New-PSSession

    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```

1. Installeer de meest recente [Win32 OpenSSH] opbouwen vanuit GitHub met de [installatie] instructies
1. Bewerk het bestand sshd_config op de locatie waar u de Win32-OpenSSH geïnstalleerd
    - Zorg ervoor dat de wachtwoordverificatie is ingeschakeld

    ```
    PasswordAuthentication yes
    ```

    - De vermelding voor een PowerShell-subsysteem toevoegen, vervangen door `c:/program files/powershell/6.0.0/pwsh.exe` met het juiste pad naar de versie die u wilt gebruiken

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```
    
    > [!NOTE]
    Er is een fout in OpenSSH voor Windows waarmee wordt voorkomen dat spaties in subsysteem uitvoerbare paden werkt.
    Zie [dit probleem op GitHub voor meer informatie](https://github.com/PowerShell/Win32-OpenSSH/issues/784).
    
    Eén oplossing is voor het maken van een symlink naar de Powershell-installatiemap op die geen spaties bevatten:
    
    ```powershell
    mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
    ```

    en voer vervolgens in het subsysteem:
 
    ```
    Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
    ```

    - Verificatie met sleutel (optioneel) inschakelen

    ```
    PubkeyAuthentication yes
    ```

1. Start de service sshd

    ```powershell
    Restart-Service sshd
    ```

1. Het pad waar OpenSSH is geïnstalleerd op uw pad Env variabele toevoegen
    - Dit moet langs de lijnen van `C:\Program Files\OpenSSH\`
    - Hiermee kunt u de ssh.exe die u wilt zoeken

## <a name="setup-on-linux-ubuntu-1404-machine"></a>Setup op de Machine met Linux (Ubuntu 14.04)

1. Installeer de meest recente [PowerShell Core voor Linux] opbouwen vanuit GitHub
1. Installeer [Ubuntu SSH] indien nodig

    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```

1. Bewerk het bestand sshd_config op locatie /etc/ssh
    - Zorg ervoor dat de wachtwoordverificatie is ingeschakeld

    ```
    PasswordAuthentication yes
    ```

    - Een PowerShell-subsysteem vermelding toevoegen

    ```
    Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - Verificatie met sleutel (optioneel) inschakelen

    ```
    PubkeyAuthentication yes
    ```

1. Start de service sshd

    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a>Setup op Mac OS-Machine

1. Installeer de meest recente [PowerShell-kern voor Mac OS] bouwen
    - Controleer of dat de SSH-externe toegang is ingeschakeld met de volgende stappen:
      - openen `System Preferences`
      - Klik op `Sharing`
      - Controleer `Remote Login` -melding `Remote Login: On`
      - Toegang tot de juiste gebruikers toestaan
1. Bewerk de `sshd_config` bestand op locatie `/private/etc/ssh/sshd_config`
    - Uw favoriete editor gebruiken of

    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```

    - Zorg ervoor dat de wachtwoordverificatie is ingeschakeld

    ```
    PasswordAuthentication yes
    ```

    - Een PowerShell-subsysteem vermelding toevoegen

    ```
    Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - Verificatie met sleutel (optioneel) inschakelen

    ```
    PubkeyAuthentication yes
    ```

1. Start de service sshd

    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a>Voorbeeld van een externe communicatie van PowerShell

De eenvoudigste manier om te testen voor externe toegang is zojuist probeer op een enkele computer.
Ik maak hier een externe sessie naar dezelfde machine op een Linux-vak.
U ziet dat ik gebruik PowerShell-cmdlets uit vanaf de opdrachtprompt zodat we zien prompts van SSH waarin wordt gevraagd om te controleren of de hostcomputer evenals een wachtwoord wordt gevraagd.
Hetzelfde geldt voor een Windows-computer om ervoor te zorgen voor externe toegang er werkt en vervolgens de afstand tussen machines door gewoon de hostnaam van de te wijzigen, kunt u doen.

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

### <a name="known-issues"></a>Bekende problemen

1. sudo-opdracht werkt niet in de externe sessie op Linux-machine.

[Core voor Windows PowerShell]: ../setup/installing-powershell-core-on-windows.md#msi
[PowerShell Core voor Linux]: ../setup/installing-powershell-core-on-linux.md#ubuntu-1404
[PowerShell-kern voor Mac OS]: ../setup/installing-powershell-core-on-macos.md
[Win32 OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH/releases
[Installatie]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
