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
# <a name="powershell-remoting-over-ssh"></a>Externe communicatie van PowerShell via SSH

## <a name="overview"></a>Overzicht

Externe communicatie van Power Shell maakt normaal gesp roken gebruik van WinRM voor verbindings onderhandeling en gegevens overdracht. SSH is nu beschikbaar voor Linux-en Windows-platforms en biedt echte externe communicatie van Power shell op meerdere platforms.

WinRM biedt een robuust hosting model voor externe Power shell-sessies. Op SSH gebaseerde externe toegang biedt momenteel geen ondersteuning voor externe eindpunt configuratie en JEA (net genoeg beheer).

Met SSH-externe communicatie kunt u een eenvoudige Power shell-sessie tussen Windows-en Linux-computers uitvoeren. Externe SSH-processen maken een Power shell-hostproces op de doel computer als een SSH-subsysteem. Uiteindelijk implementeren we een algemeen hosting model, vergelijkbaar met WinRM, ter ondersteuning van de eindpunt configuratie en JEA.

De `New-PSSession`cmdlets `Enter-PSSession`, `Invoke-Command` en hebben nu een nieuwe para meter die is ingesteld voor de ondersteuning van deze nieuwe externe verbinding.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Als u een externe sessie wilt maken, geeft u de doel computer `HostName` op met de para meter en geeft `UserName`u de gebruikers naam op bij. Wanneer de cmdlets interactief worden uitgevoerd, wordt u gevraagd een wacht woord op te vragen. U kunt ook SSH-sleutel verificatie gebruiken met behulp van een persoonlijke- `KeyFilePath` sleutel bestand met de para meter.

## <a name="general-setup-information"></a>Algemene informatie over de installatie

SSH moet op alle computers zijn geïnstalleerd. Installeer zowel de SSH-client`ssh.exe`() als de`sshd.exe`server (), zodat u op afstand van en naar de computers kunt. OpenSSH voor Windows is nu beschikbaar in Windows 10 build 1809 en Windows Server 2019. Zie [OpenSSH voor Windows](/windows-server/administration/openssh/openssh_overview)voor meer informatie. Installeer voor Linux SSH (inclusief sshd-server) die geschikt is voor uw platform. U moet ook Power shell Core van GitHub installeren om de externe SSH-functie te krijgen. De SSH-server moet worden geconfigureerd om een SSH-subsysteem te maken voor het hosten van een Power Shell-proces op de externe computer. U moet ook inschakelen van wacht woord of op sleutel gebaseerde verificatie configureren.

## <a name="set-up-on-windows-machine"></a>Instellen op Windows-machine

1. Installeer de nieuwste versie van [Power shell core voor Windows](../../install/installing-powershell-core-on-windows.md#msi)

   - U kunt zien of het de SSH-ondersteuning voor externe toegang heeft door te kijken naar de parameter sets voor`New-PSSession`

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. Installeer de meest recente Win32-OpenSSH. Zie [installatie van OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse)voor installatie-instructies.
3. Bewerk het `sshd_config` bestand dat zich `$env:ProgramData\ssh`bevindt in.

   - Controleer of wachtwoord verificatie is ingeschakeld

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > Er is een fout in OpenSSH voor Windows waarmee wordt voor komen dat ruimten in subsysteem uitvoer bare paden werken. Zie voor meer informatie [Dit github-probleem](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

     Eén oplossing is het maken van een symlink in de Power shell-installatie directory die geen spaties heeft:

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     en voer deze in het subsysteem in:

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - Optioneel sleutel verificatie inschakelen

     ```
     PubkeyAuthentication yes
     ```

4. De sshd-service opnieuw starten

   ```powershell
   Restart-Service sshd
   ```

5. Voeg het pad toe waar OpenSSH wordt geïnstalleerd in uw omgevings variabele PATH. Voorbeeld: `C:\Program Files\OpenSSH\`. Met deze vermelding kan ssh. exe worden gevonden.

## <a name="set-up-on-linux-ubuntu-1604-machine"></a>Instellen op een Linux-machine (Ubuntu 16,04)

1. De nieuwste versie van [Power shell Core for Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) van github installeren
2. Installeer [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) indien nodig

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. Bewerk het sshd_config-bestand op locatie/etc/ssh

   - Controleer of wachtwoord verificatie is ingeschakeld

   ```
   PasswordAuthentication yes
   ```

   - Een vermelding voor een Power shell-subsysteem toevoegen

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - Optioneel sleutel verificatie inschakelen

   ```
   PubkeyAuthentication yes
   ```

4. De sshd-service opnieuw starten

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a>Instellen op MacOS-computer

1. Installeer de nieuwste [Power shell core voor MacOS](../../install/installing-powershell-core-on-macos.md) build

   - Zorg ervoor dat externe SSH-communicatie is ingeschakeld door de volgende stappen te volgen:
     - Staan`System Preferences`
     - Klik op`Sharing`
     - Controleren `Remote Login` -moet zeggen`Remote Login: On`
     - Toegang tot de juiste gebruikers toestaan

2. Het `sshd_config` bestand op locatie bewerken`/private/etc/ssh/sshd_config`

   - Uw favoriete editor gebruiken of

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - Controleer of wachtwoord verificatie is ingeschakeld

     ```
     PasswordAuthentication yes
     ```

   - Een vermelding voor een Power shell-subsysteem toevoegen

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - Optioneel sleutel verificatie inschakelen

     ```
     PubkeyAuthentication yes
     ```

3. De sshd-service opnieuw starten

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Verificatie

Externe communicatie van Power shell is afhankelijk van de verificatie uitwisseling tussen de SSH-client en de SSH-service en implementeert geen verificatie schema's zelf. Dit betekent dat alle geconfigureerde verificatie schema's, waaronder multi-factor Authentication, worden verwerkt door SSH en onafhankelijk van Power shell. U kunt bijvoorbeeld de SSH-service zo configureren dat de verificatie van de open bare sleutel is vereist, evenals een eenmalig wacht woord voor extra beveiliging. Configuratie van multi-factor Authentication valt buiten het bereik van deze documentatie. Raadpleeg de documentatie voor SSH over het correct configureren van multi-factor Authentication en het valideren van de oplossing werkt buiten Power shell voordat u deze probeert te gebruiken met externe communicatie met Power shell.

## <a name="powershell-remoting-example"></a>Externe Power shell-voor beeld

De eenvoudigste manier om externe communicatie te testen is door deze te proberen op één computer. In dit voor beeld maken we een externe sessie terug naar dezelfde Linux-computer. Power shell-cmdlets worden interactief gebruikt, dus er worden prompts van SSH weer gegeven waarin wordt gevraagd om de hostcomputer te controleren en te vragen om een wacht woord. U kunt hetzelfde doen op een Windows-computer om ervoor te zorgen dat externe toegang werkt. Vervolgens op afstand tussen computers door de naam van de host te wijzigen.

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

### <a name="known-issues"></a>Bekende problemen

De opdracht sudo werkt niet in de externe sessie met de Linux-machine.

## <a name="see-also"></a>Zie ook

[Power shell core voor Windows](../../install/installing-powershell-core-on-windows.md#msi)

[Power shell core voor Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[Power shell core voor MacOS](../../install/installing-powershell-core-on-macos.md)

[OpenSSH voor Windows](/windows-server/administration/openssh/openssh_overview)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
