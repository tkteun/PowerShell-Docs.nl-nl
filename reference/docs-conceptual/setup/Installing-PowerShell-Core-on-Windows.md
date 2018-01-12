# <a name="installing-powershell-core-on-windows"></a>PowerShell Core installeren in Windows

## <a name="msi"></a>MSI

PowerShell installeren op een Windows-client of Windows Server (werkt op Windows 7 SP1 Server 2008 R2 en hoger), het downloaden van het MSI-pakket van onze GitHub [releases][] pagina.

Het MSI-bestand ziet er zo-`PowerShell-6.0.0.<buildversion>.<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Zodra u hebt gedownload, dubbelklikt u op het installatieprogramma en volg de aanwijzingen.

Er is een snelkoppeling geplaatst in het Menu Start na de installatie.

* Het pakket wordt standaard geïnstalleerd op`$env:ProgramFiles\PowerShell\`
* U kunt PowerShell via het Menu Start starten of`$env:ProgramFiles\PowerShell\pwsh.exe`

### <a name="prerequisites"></a>Vereisten

Voor meer informatie over het inschakelen van PowerShell voor externe toegang via WSMan moeten de volgende vereisten worden voldaan:

* Installeer de [universeel C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) op Windows-versies voor Windows 10.
  Het is beschikbaar via de directe download of Windows Update.
  Volledig hersteld (inclusief optionele pakketten), ondersteunde systemen beschikt al over deze software al geïnstalleerd.
* Windows Management Framework (WMF) installeren [4.0](https://www.microsoft.com/download/details.aspx?id=40855) of hoger ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) in Windows 7 en Windows Server 2008 R2.

## <a name="zip"></a>POSTCODE

PowerShell binaire ZIP-archief zijn bedoeld om geavanceerde implementatiescenario's inschakelen.
Worden opgemerkt dat de controle van vereisten zoals in het MSI-pakket bij gebruik van het ZIP-archief krijgen Won't.
Dus voor externe toegang via WSMan goed werken op Windows-versies voor Windows 10, u moet controleren of de [vereisten](#prerequisites) wordt voldaan.

## <a name="deploying-on-nano-server"></a>Op Nano Server implementeren

Deze instructies wordt ervan uitgegaan dat een versie van PowerShell al wordt uitgevoerd op de installatiekopie van het Nano Server en dat deze is gegenereerd door de [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).
Nano Server is een 'headless' besturingssysteem en de implementatie van de binaire bestanden PowerShell Core kan op twee verschillende manieren gebeuren:

1. Offline - de Nano Server-VHD koppelen en pak de inhoud van het zip-bestand naar uw gekozen locatie binnen de gekoppelde installatiekopie.
1. Online - zet het zip-bestand via een PowerShell-sessie en pak deze in uw gekozen locatie.

In beide gevallen moet u de Windows 10 x64 Zip-release van het pakket en moet de opdrachten binnen een exemplaar van 'Administrator' PowerShell uit te voeren.

### <a name="offline-deployment-of-powershell-core"></a>Offline implementatie van PowerShell Core

1. Uw favoriete zip-hulpprogramma gebruiken voor het uitpakken van het pakket naar een map in de gekoppelde installatiekopie van de Nano Server.
1. Ontkoppelen van de installatiekopie en het opstarten.
1. Verbinding maken met het postvak in-exemplaar van Windows PowerShell.
1. Volg de instructies voor het maken van een externe eindpunt met de [een ander exemplaar techniek](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Online implementatie van PowerShell Core

De volgende stappen leidt u door de implementatie van PowerShell Core naar een actief exemplaar van de Nano Server en de configuratie van het externe eindpunt.

* Verbinding met het postvak in-exemplaar van Windows PowerShell

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* Kopieer het bestand naar de Nano Server-exemplaar

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* Voer de sessie

```powershell
Enter-PSSession $session
```

* Pak het Zip-bestand

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* Als u externe toegang op basis van WSMan wilt, volg de instructies voor het maken van een externe eindpunt met de [een ander exemplaar techniek](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instructies voor het maken van een eindpunt voor externe toegang

PowerShell Core ondersteunt de PowerShell Remoting Protocol (PSRP) via WSMan- en SSH. Zie voor meer informatie

* [SSH Remoting in PowerShell-kern][ssh-remoting]
* [Externe communicatie van WSMan in PowerShell-kern][wsman-remoting]

## <a name="artifact-installation-instructions"></a>Artefacten installatie-instructies

We een archief met CoreCLR bits elke CI-versie met publiceren [AppVeyor][].

## <a name="coreclr-artifacts"></a>CoreCLR artefacten

* Download zip-pakket van **artefacten** tabblad van de bepaalde build.
* Opheffen van blokkeringen zip-bestand: klik met de rechtermuisknop in Verkenner -> Eigenschappen -> selectievakje blokkering vak -> toepassen
* Pak het zipbestand naar `bin` directory
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[releases]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
