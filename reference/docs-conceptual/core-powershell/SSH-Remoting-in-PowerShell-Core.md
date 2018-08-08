---
title: Externe communicatie van PowerShell via SSH
description: Externe communicatie in PowerShell Core met behulp van SSH
ms.date: 08/06/2018
ms.openlocfilehash: 27a8fc5623796a270a2ea67aa550c9a0998e766b
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587496"
---
# <a name="powershell-remoting-over-ssh"></a>Externe communicatie van PowerShell via SSH

## <a name="overview"></a>Overzicht

PowerShell voor externe toegang gebruikt normaal gesproken WinRM verbinding-onderhandeling en gegevenstransport. SSH is gekozen voor deze implementatie voor externe toegang, omdat deze nu beschikbaar voor zowel Windows als Linux-platforms is en waar meerdere platforms PowerShell voor externe toegang kunt. WinRM biedt een robuuste hostingmodel echter ook voor externe PowerShell-sessies die deze implementatie wordt nog niet. En dit betekent dat PowerShell externe eindpunt-configuratie en JEA (Just Enough Administration) wordt nog niet ondersteund in deze implementatie.

PowerShell SSH voor externe toegang kunt u eenvoudige PowerShell-sessie voor externe toegang tussen Windows en Linux-machines. Dit wordt gedaan door het maken van een PowerShell-proces op de doel-VM als een SSH-subsysteem te hosten. Dit wordt uiteindelijk worden gewijzigd naar een meer algemene hostingmodel die vergelijkbaar is met de werking van WinRM ter ondersteuning van de configuratie van eindpunten en JEA.

De `New-PSSession`, `Enter-PSSession` en `Invoke-Command` cmdlets hebben nu een nieuwe parameterset om deze nieuwe verbinding voor externe toegang mogelijk te maken

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Deze nieuwe parameterset waarschijnlijk zullen veranderen, maar voor nu kunt u maken van SSH PSSessions kunt u communiceren met vanaf de opdrachtregel of opdrachten en scripts aanroepen op. U opgeven van de doel-VM met de parameter hostnaam en gebruikersnaam van de naam van de gebruiker voorzien. Als de cmdlets interactief wordt uitgevoerd op de PowerShell-opdrachtregel wordt u gevraagd om een wachtwoord. Maar u hebt ook de optie voor het gebruik van verificatie van SSH-sleutel en geef het pad van een bestand met persoonlijke sleutel met de parameter KeyFilePath.

## <a name="general-setup-information"></a>Algemene instellingen

SSH is vereist om te worden geïnstalleerd op alle virtuele machines. U moet zowel client installeren (`ssh.exe`) en de server (`sshd.exe`) zodat u met externe toegang naar en van de machines experimenteren kunt. Voor Windows moet u voor het installeren van [Win32-OpenSSH vanuit GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
Voor Linux moet u SSH (inclusief sshd-server) geschikt is voor uw platform installeren. U moet ook een recente PowerShell-build of een pakket van de SSH-functie voor externe communicatie met GitHub.
SSH-subsystemen tot stand brengen van een PowerShell-proces op de externe computer wordt gebruikt en de SSH-server moet worden geconfigureerd voor die. Bovendien moet u wachtwoordverificatie en eventueel sleutel gebaseerde verificatie inschakelen.

## <a name="setup-on-windows-machine"></a>Instellen op Windows-Machine

1. Installeer de nieuwste versie van [PowerShell Core voor Windows]

   - U kunt zien dat als dat zo de SSH-ondersteuning voor externe communicatie is door te kijken naar de parameter wordt ingesteld voor `New-PSSession`

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. De meest recente [Win32 OpenSSH]-build installeren vanuit GitHub met behulp van de [installatie]-instructies
3. Bewerk het bestand sshd_config op de locatie waar u Win32 OpenSSH geïnstalleerd

   - Zorg ervoor dat de wachtwoordverificatie is ingeschakeld

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > Er is een fout in OpenSSH voor Windows waarmee wordt voorkomen dat spaties in subsysteem uitvoerbare paden werkt.
     > Zie [dit probleem op GitHub voor meer informatie](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

     Eén oplossing is het maken van een symlink naar de Powershell-installatiemap die geen spaties bevatten:

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
     ```

     en geef de code in het subsysteem:

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - Verificatie met sleutel (optioneel) inschakelen

     ```
     PubkeyAuthentication yes
     ```

4. De sshd-service opnieuw starten

   ```powershell
   Restart-Service sshd
   ```

5. Het pad waar OpenSSH is geïnstalleerd op uw pad Env variabele toevoegen

   - Dit moet zijn aan de regels van `C:\Program Files\OpenSSH\`
   - Hiermee kunt u de ssh.exe worden gevonden

## <a name="setup-on-linux-ubuntu-1404-machine"></a>Installatie op de Machine voor Linux (Ubuntu 14.04)

1. De meest recente [PowerShell Core voor Linux]-build installeren vanuit GitHub
2. [Ubuntu SSH] indien nodig geïnstalleerd

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. Bewerk het bestand sshd_config op locatie /etc/ssh

   - Zorg ervoor dat de wachtwoordverificatie is ingeschakeld

   ```
   PasswordAuthentication yes
   ```

   - Een PowerShell-subsysteem-item toevoegen

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - Verificatie met sleutel (optioneel) inschakelen

   ```
   PubkeyAuthentication yes
   ```

4. De sshd-service opnieuw starten

   ```bash
   sudo service sshd restart
   ```

## <a name="setup-on-macos-machine"></a>Instellen op MacOS-computer

1. Installeer de nieuwste build van de [PowerShell Core voor MacOS]

   - Zorg ervoor dat SSH voor externe toegang is ingeschakeld door de volgende stappen:
     - Open `System Preferences`
     - Klik op `Sharing`
     - Controleer `Remote Login` -melding `Remote Login: On`
     - Toegang tot de juiste gebruikers toestaan

2. Bewerk de `sshd_config` -bestand op locatie `/private/etc/ssh/sshd_config`

   - Uw favoriete editor gebruiken of

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - Zorg ervoor dat de wachtwoordverificatie is ingeschakeld

     ```
     PasswordAuthentication yes
     ```

   - Een PowerShell-subsysteem-item toevoegen

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - Verificatie met sleutel (optioneel) inschakelen

     ```
     PubkeyAuthentication yes
     ```

3. De sshd-service opnieuw starten

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a>Voorbeeld van PowerShell voor externe toegang

De eenvoudigste manier om te testen voor externe toegang is om te proberen deze slechts op één computer. Ik zal hier een externe sessie naar dezelfde computer op een Linux-vak maken. U ziet dat ik ben met behulp van PowerShell-cmdlets vanaf een opdrachtprompt, zodat we ziet u aanwijzingen uit in SSH waarin wordt gevraagd om te controleren of de hostcomputer, evenals een wachtwoord wordt gevraagd. U kunt hetzelfde doen op een Windows-machine om ervoor te zorgen voor externe toegang werkt er en vervolgens extern tussen machines wijzig gewoon de naam van de host.

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

### <a name="known-issues"></a>Bekende problemen

De sudo-opdracht werkt niet in de externe sessie op Linux-machine.

## <a name="see-also"></a>Zie ook

[PowerShell Core voor Windows](../setup/installing-powershell-core-on-windows.md#msi)

[PowerShell Core voor Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[PowerShell Core voor MacOS](../setup/installing-powershell-core-on-macos.md)

[Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)

[installatie](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)