---
title: PowerShell Core in Windows installeren
description: Informatie over PowerShell Core in Windows installeren
ms.date: 08/06/2018
ms.openlocfilehash: 2b21908c38796117308f2ac1219db00ff9086408
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850976"
---
# <a name="installing-powershell-core-on-windows"></a>PowerShell Core in Windows installeren

## <a name="msi"></a>MSI-BESTAND

PowerShell installeren op een Windows-client of Windows Server (werkt op Windows 7 SP1, Server 2008 R2 en hoger), het MSI-pakket downloaden in onze GitHub [releases][] pagina.

Het MSI-bestand er als volgt uitzien: `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Nadat u hebt gedownload, dubbelklikt u op het installatieprogramma en volg de aanwijzingen.

Er is een snelkoppeling geplaatst in het Menu Start na de installatie.

- Het pakket wordt standaard geïnstalleerd op `$env:ProgramFiles\PowerShell\<version>`
- U kunt PowerShell via het Menu Start starten of `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="prerequisites"></a>Vereisten

Om in te schakelen PowerShell voor externe toegang via WSMan, moeten de volgende vereisten worden voldaan:

- Installeer de [universeel C-Runtime](https://www.microsoft.com/download/details.aspx?id=50410) op Windows-versies voorafgaand aan Windows 10.
  Het is beschikbaar via de directe download of Windows Update.
  Volledig hersteld (inclusief optionele pakketten), heeft ondersteunde systemen al dit geïnstalleerd.
- Installeer de Windows Management Framework (WMF) 4.0 of hoger op Windows 7 en Windows Server 2008 R2.

## <a name="zip"></a>POSTCODE

PowerShell binaire ZIP-archieven zijn opgegeven voor het inschakelen van geavanceerde implementatiescenario's.
Worden opgemerkt bij het gebruik van het ZIP-archief, kunt u de controle van vereisten zoals in het MSI-pakket wordt niet ophalen.
In de volgorde voor externe toegang via WSMan goed werken op Windows-versies voorafgaand aan Windows 10, moet u om te controleren of de [vereisten](#prerequisites) wordt voldaan.

## <a name="deploying-on-windows-iot"></a>Implementeren op Windows IoT

Windows IoT is al wordt geleverd met Windows PowerShell die zullen worden gebruikt voor het implementeren van PowerShell Core 6.

1. Maak `PSSession` doelapparaat

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. Kopieer het ZIP-pakket naar het apparaat

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.1.0-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Verbinding maken met het apparaat en vouw het archief

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.1.0-win-arm32.zip
   ```

4. Instellingen voor externe toegang tot en met 6 voor PowerShell Core

   ```powershell
   Set-Location .\PowerShell-6.1.0-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Verbinding maken met PowerShell Core 6-eindpunt op apparaat

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.1.0
   ```

## <a name="deploying-on-nano-server"></a>Implementatie van op Nano Server

Deze instructies wordt ervan uitgegaan dat een versie van PowerShell al wordt uitgevoerd op de Nano Server-installatiekopie en dat deze is gegenereerd door de [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).
Nano Server is een 'headless' besturingssysteem. Kan de belangrijke binaire kunt implementeren met behulp van twee verschillende methoden.

1. Offline - de Nano Server-VHD koppelen en pak deze uit de inhoud van het zip-bestand naar uw gekozen locatie binnen de gekoppelde installatiekopie.
2. Online - overdragen van het zip-bestand via een PowerShell-sessie en pak het uit in uw gekozen locatie.

In beide gevallen moet u de versie van Windows 10 x64 ZIP verpakt en moet de opdrachten binnen een exemplaar 'Beheerder' PowerShell uitvoeren.

### <a name="offline-deployment-of-powershell-core"></a>Offline implementatie van PowerShell Core

1. Gebruik uw favoriete zip-hulpprogramma voor het uitpakken van het pakket naar een map in de gekoppelde Nano Server-installatiekopie.
2. Ontkoppelen van de installatiekopie en het opstarten.
3. Verbinding maken met het exemplaar van het postvak in van Windows PowerShell.
4. Volg de instructies voor het maken van een externe toegang-eindpunt met de ["een ander exemplaar techniek"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Online implementatie van PowerShell Core

De volgende stappen begeleiden u bij de implementatie van PowerShell Core een exemplaar van de Nano Server en de configuratie van het externe eindpunt.

- Verbinding maken met het exemplaar van het postvak in van Windows PowerShell

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- Kopieer het bestand naar de Nano Server-exemplaar

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- De sessie

  ```powershell
  Enter-PSSession $session
  ```

- Pak het ZIP-bestand

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- Als u externe toegang op basis van WSMan wilt, volg de instructies voor het maken van een externe toegang-eindpunt met de ["een ander exemplaar techniek"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instructies voor het maken van een eindpunt voor externe toegang

PowerShell Core biedt ondersteuning voor de PowerShell Remoting Protocol (PSRP) via WSMan- en SSH.
Zie voor meer informatie

- [SSH in PowerShell Core voor externe toegang][ssh-remoting]
- [Externe communicatie van WSMan in PowerShell Core][wsman-remoting]

## <a name="artifact-installation-instructions"></a>Artefact installatie-instructies

We een archief met CoreCLR bits op elke CI-build met publiceren [AppVeyor][].

PowerShell Core installeren van het artefact CoreCLR:

1. Download ZIP-pakket van **artefacten** tabblad van de specifieke build.
2. Opheffen van blokkeringen ZIP-bestand: klik met de rechtermuisknop in Verkenner -> Eigenschappen selectievakje deblokkeren box -> toepassen ->
3. Zip-bestand uitpakken `bin` directory
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
