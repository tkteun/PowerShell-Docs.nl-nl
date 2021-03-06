---
title: Externe communicatie van PowerShell via SSH
ms.date: 10/19/2020
description: In dit artikel wordt uitgelegd hoe u het SSH-protocol instelt voor externe communicatie met Power shell.
ms.openlocfilehash: c3373ac30fd915d42e8c9fb7f1eae348a2aee7f1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501334"
---
# <a name="powershell-remoting-over-ssh"></a>Externe communicatie van PowerShell via SSH

## <a name="overview"></a>Overzicht

Externe communicatie van Power Shell maakt normaal gesp roken gebruik van WinRM voor verbindings onderhandeling en gegevens overdracht. SSH is nu beschikbaar voor Linux-en Windows-platforms en biedt echte externe communicatie van Power shell op meerdere platforms.

WinRM biedt een robuust hosting model voor externe Power shell-sessies. Op SSH gebaseerde externe toegang biedt momenteel geen ondersteuning voor externe eindpunt configuratie en voldoende beheer (JEA).

Met SSH-externe communicatie kunt u een eenvoudige Power shell-sessie tussen Windows-en Linux-computers uitvoeren. Externe SSH-processen maken een Power shell-hostproces op de doel computer als een SSH-subsysteem. Uiteindelijk implementeren we een algemeen hosting model, vergelijkbaar met WinRM, ter ondersteuning van de eindpunt configuratie en JEA.

De `New-PSSession` `Enter-PSSession` `Invoke-Command` cmdlets, en hebben nu een nieuwe para meter die is ingesteld voor de ondersteuning van deze nieuwe externe verbinding.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Als u een externe sessie wilt maken, geeft u de doel computer op met de para meter **hostname** en geeft u de gebruikers naam met de **naam** van de gebruiker. Wanneer de cmdlets interactief worden uitgevoerd, wordt u gevraagd een wacht woord op te vragen. U kunt ook SSH-sleutel verificatie gebruiken met behulp van een persoonlijke-sleutel bestand met de para meter/ **filepath** . Het maken van sleutels voor SSH-verificatie varieert per platform.

## <a name="general-setup-information"></a>Algemene informatie over de installatie

Power shell 6 of hoger en SSH moet op alle computers zijn ge??nstalleerd. Installeer zowel de SSH-client ( `ssh.exe` ) als de server ( `sshd.exe` ), zodat u op afstand van en naar de computers kunt. OpenSSH voor Windows is nu beschikbaar in Windows 10 build 1809 en Windows Server 2019. Zie [Manage Windows with OpenSSH](/windows-server/administration/openssh/openssh_overview)(Engelstalig) voor meer informatie. Voor Linux installeert u SSH, met inbegrip van de sshd-server, die geschikt is voor uw platform. U moet Power shell ook installeren vanaf GitHub om de externe SSH-functie te krijgen. De SSH-server moet worden geconfigureerd om een SSH-subsysteem te maken voor het hosten van een Power Shell-proces op de externe computer. En u moet verificatie **op basis van** **wacht woord** of sleutel inschakelen.

## <a name="set-up-on-a-windows-computer"></a>Instellen op een Windows-computer

1. Installeer de meest recente versie van Power shell. Zie [Power shell Core installeren op Windows](../../install/installing-powershell-core-on-windows.md#msi)voor meer informatie.

   U kunt controleren of Power Shell ondersteuning biedt voor externe SSH door de `New-PSSession` parameter sets op te geven. U ziet dat er namen van parameter sets zijn die beginnen met **SSH**. Deze parameter sets bevatten **SSH** -para meters.

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. Installeer de meest recente Win32-OpenSSH. Zie aan de slag [met OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse)voor installatie-instructies.

   > [!NOTE]
   > Als u Power shell wilt instellen als de standaard shell voor OpenSSH, raadpleegt u [Windows configureren voor OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).

1. Bewerk het `sshd_config` bestand dat zich bevindt in `$env:ProgramData\ssh` .

   Controleer of wachtwoord verificatie is ingeschakeld:

   ```
   PasswordAuthentication yes
   ```

   Maak het SSH-subsysteem dat als host fungeert voor een Power Shell-proces op de externe computer:

   ```
   Subsystem powershell c:/progra~1/powershell/7/pwsh.exe -sshs -NoLogo
   ```

   > [!NOTE]
   > De standaard locatie van het uitvoer bare Power shell-bestand is `c:/progra~1/powershell/7/pwsh.exe` . De locatie kan vari??ren, afhankelijk van de manier waarop u Power shell hebt ge??nstalleerd.
   >
   > U moet de korte naam van 8,3 gebruiken voor bestands paden die spaties bevatten. Er is een fout in OpenSSH voor Windows waarmee wordt voor komen dat ruimten in subsysteem uitvoer bare paden werken. Zie voor meer informatie dit [github-probleem](https://github.com/PowerShell/Win32-OpenSSH/issues/784).
   >
   > De korte naam van 8,3 voor de `Program Files` map in Windows is doorgaans `Progra~1` . U kunt echter de volgende opdracht gebruiken om ervoor te zorgen:
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

   Schakel eventueel sleutel verificatie in:

   ```
   PubkeyAuthentication yes
   ```

   Zie [Managing OpenSSH Keys](/windows-server/administration/openssh/openssh_keymanagement)(Engelstalig) voor meer informatie.

1. Start de service **sshd** opnieuw.

   ```powershell
   Restart-Service sshd
   ```

1. Voeg het pad toe waar OpenSSH wordt ge??nstalleerd in uw omgevings variabele PATH. Bijvoorbeeld `C:\Program Files\OpenSSH\`. Met deze vermelding kan de worden `ssh.exe` gevonden.

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a>Instellen op een Ubuntu 16,04 Linux-computer

1. Installeer de meest recente versie van Power shell, Zie [Power shell Core installeren op Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).
1. Installeer de [Ubuntu openssh-server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. Bewerk het `sshd_config` bestand op locatie `/etc/ssh` .

   Controleer of wachtwoord verificatie is ingeschakeld:

   ```
   PasswordAuthentication yes
   ```

   Schakel eventueel sleutel verificatie in:

   ```
   PubkeyAuthentication yes
   ```

   Zie de manpage voor [ssh-keygen](http://manpages.ubuntu.com/manpages/xenial/man1/ssh-keygen.1.html)voor meer informatie over het maken van SSH-sleutels op Ubuntu.

   Een vermelding voor een Power shell-subsysteem toevoegen:

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo
   ```

   > [!NOTE]
   > De standaard locatie van het uitvoer bare Power shell-bestand is `/usr/bin/pwsh` . De locatie kan vari??ren, afhankelijk van de manier waarop u Power shell hebt ge??nstalleerd.

   Schakel eventueel sleutel verificatie in:

   ```
   PubkeyAuthentication yes
   ```

1. Start de **SSH** -service opnieuw.

   ```bash
   sudo service ssh restart
   ```

## <a name="set-up-on-a-macos-computer"></a>Instellen op een macOS-computer

1. Installeer de meest recente versie van Power shell. Voor meer informatie [installeert u Power shell core in macOS](../../install/installing-powershell-core-on-macos.md).

   Zorg ervoor dat externe SSH-communicatie is ingeschakeld door de volgende stappen te volgen:

   1. Open `System Preferences`.
   1. Klik op `Sharing`.
   1. Selecteer deze optie `Remote Login` `Remote Login: On` .
   1. Toegang tot de juiste gebruikers toestaan.

1. Bewerk het `sshd_config` bestand op locatie `/private/etc/ssh/sshd_config` .

   Gebruik een tekst editor zoals **nano**:

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   Controleer of wachtwoord verificatie is ingeschakeld:

   ```
   PasswordAuthentication yes
   ```

   Een vermelding voor een Power shell-subsysteem toevoegen:

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo
   ```

   > [!NOTE]
   > De standaard locatie van het uitvoer bare Power shell-bestand is `/usr/local/bin/pwsh` . De locatie kan vari??ren, afhankelijk van de manier waarop u Power shell hebt ge??nstalleerd.

   Schakel eventueel sleutel verificatie in:

   ```
   PubkeyAuthentication yes
   ```

1. Start de service **sshd** opnieuw.

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Verificatie

Externe communicatie van Power shell is afhankelijk van de verificatie uitwisseling tussen de SSH-client en de SSH-service en implementeert geen verificatie schema's zelf. Het resultaat is dat alle geconfigureerde verificatie schema's, waaronder multi-factor Authentication, worden afgehandeld door SSH en onafhankelijk van Power shell. U kunt bijvoorbeeld de SSH-service zo configureren dat verificatie met een open bare sleutel en een eenmalig wacht woord voor extra beveiliging zijn vereist. Configuratie van multi-factor Authentication valt buiten het bereik van deze documentatie. Raadpleeg de documentatie voor SSH over het correct configureren van multi-factor Authentication en het valideren van de oplossing werkt buiten Power shell voordat u deze probeert te gebruiken met externe communicatie met Power shell.

> [!NOTE]
> Gebruikers behouden dezelfde bevoegdheden in externe sessies. Dat wil zeggen dat beheerders toegang hebben tot een verhoogde shell en dat gewone gebruikers dat niet doen.

## <a name="powershell-remoting-example"></a>Externe Power shell-voor beeld

De eenvoudigste manier om externe communicatie te testen is door deze te proberen op ????n computer. In dit voor beeld maken we een externe sessie terug naar dezelfde Linux-computer. Power shell-cmdlets worden interactief gebruikt, dus er worden prompts van SSH weer gegeven waarin wordt gevraagd om de hostcomputer te controleren en te vragen om een wacht woord. U kunt hetzelfde doen op een Windows-computer om ervoor te zorgen dat externe toegang werkt. Vervolgens op afstand tussen computers door de hostnaam te wijzigen.

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

### <a name="limitations"></a>Beperkingen

- De opdracht **sudo** werkt niet in een externe sessie met een Linux-computer.

- PSRemoting via SSH ondersteunt geen profielen en heeft geen toegang tot `$PROFILE` . Eenmaal in een sessie kunt u een profiel laden met punt op het profiel met het volledige bestandspad. Dit is niet gerelateerd aan SSH-profielen. U kunt de SSH-server configureren voor het gebruik van Power shell als de standaard shell en een profiel laden via SSH. Raadpleeg de SSH-documentatie voor meer informatie.

- Voorafgaand aan Power shell 7,1 heeft externe toegang via SSH geen ondersteuning voor externe sessies van de tweede hop. Deze mogelijkheid is beperkt tot sessies met WinRM. Met Power shell 7,1 kunt `Enter-PSSession` `Enter-PSHostProcess` u binnen elke interactieve externe sessie werken.

## <a name="see-also"></a>Zie ook

[Installing PowerShell Core on Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) (PowerShell Core installeren in Linux)

[Installing PowerShell Core on macOS](../../install/installing-powershell-core-on-macos.md) (PowerShell Core installeren in macOS)

[PowerShell Core in Windows installeren](../../install/installing-powershell-core-on-windows.md#msi)

[Windows beheren met OpenSSH](/windows-server/administration/openssh/openssh_overview)

[OpenSSH-sleutels beheren](/windows-server/administration/openssh/openssh_keymanagement)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
