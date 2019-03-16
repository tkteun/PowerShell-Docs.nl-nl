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
# <a name="powershell-remoting-over-ssh"></a>Externe communicatie van PowerShell via SSH

## <a name="overview"></a>Overzicht

PowerShell voor externe toegang gebruikt normaal gesproken WinRM verbinding-onderhandeling en gegevenstransport. SSH is nu beschikbaar voor Linux en Windows-platform en kunt waar meerdere platforms externe communicatie van PowerShell.

WinRM biedt een robuuste hostingmodel voor de externe PowerShell-sessies. Externe toegang op basis van SSH ondersteunt momenteel geen configuratie van externe eindpunten en JEA (Just Enough Administration).

Externe communicatie met SSH kunt u eenvoudige PowerShell-sessie voor externe toegang tussen Windows en Linux-machines. SSH voor externe toegang maakt een hostproces PowerShell op de doel-VM als een SSH-subsysteem.
Uiteindelijk zult we een algemene hostingmodel, vergelijkbaar met WinRM, ter ondersteuning van configuratie van eindpunten en JEA implementeren.

De `New-PSSession`, `Enter-PSSession`, en `Invoke-Command` cmdlets hebben nu een nieuwe parameterset voor de ondersteuning van deze nieuwe verbinding voor externe toegang.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Voor het maken van een externe sessie die u opgeeft de doel-VM met de `HostName` parameter en geeft u de gebruikersnaam van de met `UserName`. Als de cmdlets interactief wordt uitgevoerd, wordt u gevraagd om een wachtwoord. U kunt ook gebruiken met behulp van een persoonlijk sleutelbestand met SSH-sleutelverificatie de `KeyFilePath` parameter.

## <a name="general-setup-information"></a>Algemene instellingen

SSH moet worden geïnstalleerd op alle virtuele machines. Zowel de SSH-client installeren (`ssh.exe`) en de server (`sshd.exe`) zodat u externe naar en van de machines kunt. OpenSSH voor Windows is nu beschikbaar in Windows 10 build 1809 en Windows Server 2019. Zie voor meer informatie, [OpenSSH voor Windows](/windows-server/administration/openssh/openssh_overview). Voor Linux installeren SSH (inclusief sshd-server) geschikt is voor uw platform. U moet ook PowerShell Core installeren vanuit GitHub om op te halen van de SSH-functie voor externe toegang. De SSH-server moet worden geconfigureerd voor het maken van een SSH-subsysteem voor het hosten van een PowerShell-proces op de externe computer. Ook moet u inschakelen wachtwoord of sleutel gebaseerde verificatie configureren.

## <a name="set-up-on-windows-machine"></a>Op Windows-Machine instellen

1. Installeer de nieuwste versie van [PowerShell Core voor Windows](../../install/installing-powershell-core-on-windows.md#msi)

   - U kunt zien dat als dat zo de SSH-ondersteuning voor externe communicatie is door te kijken naar de parameter wordt ingesteld voor `New-PSSession`

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. Installeer de meest recente Win32-OpenSSH. Zie voor installatie-instructies [installatie van OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).
3. Bewerk de `sshd_config` bestand dat zich bevindt in `$env:ProgramData\ssh`.

   - Zorg ervoor dat de wachtwoordverificatie is ingeschakeld

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > Er is een fout in OpenSSH voor Windows waarmee wordt voorkomen dat spaties in subsysteem uitvoerbare paden werkt. Zie voor meer informatie, [deze GitHub-probleem](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

     Eén oplossing is het maken van een symlink naar de PowerShell-installatiemap die geen spaties:

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     en geef de code in het subsysteem:

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - Verificatie met sleutel (optioneel) inschakelen

     ```
     PubkeyAuthentication yes
     ```

4. De sshd-service opnieuw starten

   ```powershell
   Restart-Service sshd
   ```

5. Voeg het pad waar OpenSSH wordt geïnstalleerd in uw padomgevingsvariabele bevindt. Voorbeeld: `C:\Program Files\OpenSSH\`. Deze vermelding kunt u de ssh.exe worden gevonden.

## <a name="set-up-on-linux-ubuntu-1404-machine"></a>Op Linux (Ubuntu 14.04) Machine instellen

1. Installeer de meest recente [PowerShell Core voor Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1404) samengesteld op basis van GitHub
2. Installeer [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) indien nodig

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

## <a name="set-up-on-macos-machine"></a>Ingesteld op MacOS-computer

1. Installeer de meest recente [PowerShell Core voor MacOS](../../install/installing-powershell-core-on-macos.md) bouwen

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

## <a name="authentication"></a>Verificatie

PowerShell voor externe toegang via SSH is afhankelijk van de authenticatie-uitwisseling tussen de SSH-client en de SSH-service en implementeert niet alle verificatiemethoden zelf.
Dit betekent dat alle geconfigureerde verificatiemethoden, waaronder multi-factor authentication wordt verwerkt door de SSH- en onafhankelijk van PowerShell.
U kunt bijvoorbeeld de SSH-service om te vereisen dat verificatie van de openbare sleutel, evenals een eenmalig wachtwoord voor extra beveiliging configureren.
Configuratie van multi-factor authentication is buiten het bereik van deze documentatie.
Raadpleeg de documentatie voor SSH over het correct multi-factor authentication configureren en te werken buiten PowerShell valideren voordat u probeert te gebruiken met PowerShell voor externe toegang.

## <a name="powershell-remoting-example"></a>Voorbeeld van PowerShell voor externe toegang

De eenvoudigste manier om te testen voor externe toegang is om het te proberen op één computer. In dit voorbeeld maken we een externe sessie terug naar de dezelfde Linux-machine. We zijn met behulp van PowerShell cmdlets interactief zodat we zien uit in SSH waarin wordt gevraagd om te controleren of de computer en dat u wordt gevraagd om een wachtwoord gevraagd. U kunt hetzelfde doen op een Windows-machine om ervoor te zorgen voor externe toegang werkt. Klik vervolgens op afstand tussen machines door de hostnaam te wijzigen.

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

### <a name="known-issues"></a>Bekende problemen

De sudo-opdracht werkt niet in de externe sessie op Linux-machine.

## <a name="see-also"></a>Zie ook

[PowerShell Core voor Windows](../../install/installing-powershell-core-on-windows.md#msi)

[PowerShell Core voor Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1404)

[PowerShell Core voor MacOS](../../install/installing-powershell-core-on-macos.md)

[OpenSSH voor Windows](/windows-server/administration/openssh/openssh_overview)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
