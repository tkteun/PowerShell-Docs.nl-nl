# <a name="installing-powershell-core-on-windows"></a>PowerShell Core in Windows installeren

## <a name="msi"></a>MSI

PowerShell installeren op een Windows-client of Windows Server (werkt op Windows 7 SP1 Server 2008 R2 en hoger), het downloaden van het MSI-pakket van onze GitHub [releases][] pagina.

Het MSI-bestand ziet er zo- `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Zodra u hebt gedownload, dubbelklikt u op het installatieprogramma en volg de aanwijzingen.

Er is een snelkoppeling geplaatst in het Menu Start na de installatie.

- Het pakket wordt standaard geïnstalleerd op `$env:ProgramFiles\PowerShell\`
- U kunt PowerShell via het Menu Start starten of `$env:ProgramFiles\PowerShell\pwsh.exe`

### <a name="prerequisites"></a>Vereisten

Voor meer informatie over het inschakelen van PowerShell voor externe toegang via WSMan moeten de volgende vereisten worden voldaan:

- Installeer de [universeel C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) op Windows-versies voor Windows 10.
  Het is beschikbaar via de directe download of Windows Update.
  Volledig hersteld (inclusief optionele pakketten), ondersteunde systemen beschikt al over deze software al geïnstalleerd.
- Installeer de Windows Management Framework (WMF) 4.0 of hoger op Windows 7 en Windows Server 2008 R2.

## <a name="zip"></a>POSTCODE

PowerShell binaire ZIP-archief zijn bedoeld om geavanceerde implementatiescenario's inschakelen.
Worden opgemerkt dat de controle van vereisten zoals in het MSI-pakket bij gebruik van het ZIP-archief krijgen Won't.
Dus voor externe toegang via WSMan goed werken op Windows-versies voor Windows 10, u moet controleren of de [vereisten](#prerequisites) wordt voldaan.

## <a name="deploying-on-windows-iot"></a>Op Windows IoT is geïmplementeerd

Windows IoT is al wordt geleverd met Windows PowerShell die zullen worden gebruikt voor het implementeren van PowerShell Core 6.

1. Maak `PSSession` doelapparaat

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. Het ZIP-pakket kopiëren naar het apparaat

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.0.2-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Verbinding met het apparaat en vouw het archief

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.0.2-win-arm32.zip
   ```

4. Instellingen voor externe toegang tot en met PowerShell Core 6

   ```powershell
   cd .\PowerShell-6.0.2-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Verbinding maken met PowerShell Core 6-eindpunt op apparaat

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.0.2
   ```

## <a name="deploying-on-nano-server"></a>Op Nano Server implementeren

Deze instructies wordt ervan uitgegaan dat een versie van PowerShell al wordt uitgevoerd op de installatiekopie van het Nano Server en dat deze is gegenereerd door de [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).
Nano Server is een 'headless' besturingssysteem. Kan de binaire bestanden Core kunt implementeren met behulp van twee verschillende methoden.

1. Offline - de Nano Server-VHD koppelen en pak de inhoud van het zip-bestand naar uw gekozen locatie binnen de gekoppelde installatiekopie.
2. Online - zet het zip-bestand via een PowerShell-sessie en pak deze in uw gekozen locatie.

In beide gevallen moet u de Windows 10 x64 ZIP-release van het pakket en moet de opdrachten binnen een exemplaar van 'Administrator' PowerShell uit te voeren.

### <a name="offline-deployment-of-powershell-core"></a>Offline implementatie van PowerShell Core

1. Uw favoriete zip-hulpprogramma gebruiken voor het uitpakken van het pakket naar een map in de gekoppelde installatiekopie van de Nano Server.
2. Ontkoppelen van de installatiekopie en het opstarten.
3. Verbinding maken met het postvak in-exemplaar van Windows PowerShell.
4. Volg de instructies voor het maken van een externe eindpunt met de ['een ander exemplaar techniek'](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Online implementatie van PowerShell Core

De volgende stappen helpen u bij de implementatie van PowerShell Core naar een actief exemplaar van de Nano Server en de configuratie van het externe eindpunt.

- Verbinding met het postvak in-exemplaar van Windows PowerShell

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- Kopieer het bestand naar de Nano Server-exemplaar

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- Voer de sessie

  ```powershell
  Enter-PSSession $session
  ```

- Pak het ZIP-bestand

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- Als u externe toegang op basis van WSMan wilt, volg de instructies voor het maken van een externe eindpunt met de ['een ander exemplaar techniek'](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instructies voor het maken van een eindpunt voor externe toegang

PowerShell Core ondersteunt de PowerShell Remoting Protocol (PSRP) via WSMan- en SSH.
Zie voor meer informatie

- [SSH Remoting in PowerShell-kern][ssh-remoting]
- [Externe communicatie van WSMan in PowerShell-kern][wsman-remoting]

## <a name="artifact-installation-instructions"></a>Artefacten installatie-instructies

We een archief met CoreCLR bits elke CI-versie met publiceren [AppVeyor][].

PowerShell-kern van het artefact CoreCLR installeren:

1. Download ZIP-pakket van **artefacten** tabblad van de bepaalde build.
2. Opheffen van blokkeringen ZIP-bestand: klik met de rechtermuisknop in Verkenner -> Eigenschappen -> selectievakje blokkering vak -> toepassen
3. Pak het zipbestand naar `bin` directory
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell