---
title: PowerShell installeren in Windows
description: Informatie over het installeren van PowerShell in Windows
ms.date: 04/27/2021
ms.openlocfilehash: 24f5687411004ebc6f84a76493ded46b7b30b0d2
ms.sourcegitcommit: afbcc8675107ad9ec6afff91ef4a42b2953121cc
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/28/2021
ms.locfileid: "108121642"
---
# <a name="installing-powershell-on-windows"></a>PowerShell installeren in Windows

Er zijn meerdere manieren om PowerShell in Windows te installeren.

## <a name="prerequisites"></a>Vereisten

De nieuwste versie van PowerShell wordt ondersteund in Windows 7 SP1, Server 2008 R2 en latere versies.

Aan de volgende vereisten moet worden voldaan om powershell voor remoting via WSMan in te kunnenschakelen:

- Installeer universal [C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) in Windows-versies die voorafgaan aan Windows 10. Deze is beschikbaar via direct downloaden of Windows Update. Dit pakket is al geïnstalleerd op volledig gepatchte systemen.
- Installeer de Windows Management Framework (WMF) 4.0 of hoger op Windows 7 en Windows Server 2008 R2. Zie WMF-overzicht voor meer informatie [over WMF.](/powershell/scripting/wmf/overview)

## <a name="download-the-installer-package"></a>Het installatiepakket downloaden

Als u PowerShell in Windows wilt installeren, downloadt u [het meest][] recente installatiepakket van GitHub. U kunt ook de nieuwste [preview-versie][] vinden. Schuif omlaag naar de **sectie Assets** van de pagina Release. De **sectie** Assets is mogelijk samengevouwen, dus mogelijk moet u erop klikken om deze uit te vouwen.

## <a name="installing-the-msi-package"></a><a id="msi" />Het MSI-pakket installeren

Het MSI-bestand ziet er als `PowerShell-<version>-win-<os-arch>.msi` uit. Bijvoorbeeld:

- `PowerShell-7.1.3-win-x64.msi`
- `PowerShell-7.1.3-win-x86.msi`

Dubbelklik na het downloaden op het installatieprogramma en volg de aanwijzingen.

Het installatieprogramma maakt een snelkoppeling in het menu Start van Windows.

- Het pakket is standaard geïnstalleerd op `$env:ProgramFiles\PowerShell\<version>`
- U kunt PowerShell starten via het startmenu of `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

> [!NOTE]
> PowerShell 7.1 wordt geïnstalleerd in een nieuwe map en wordt naast elkaar uitgevoerd met Windows PowerShell 5.1.
> PowerShell 7.1 is een in-place upgrade powershell 6.x vervangt. of PowerShell 7.0.
>
> - PowerShell 7.1 is geïnstalleerd op `$env:ProgramFiles\PowerShell\7`
> - De `$env:ProgramFiles\PowerShell\7` map wordt toegevoegd aan `$env:PATH`
> - De `$env:ProgramFiles\PowerShell\6` map is verwijderd
>
> Als u PowerShell 7.1 naast andere versies moet uitvoeren, [](#zip) gebruikt u de zip-installatiemethode om de andere versie in een andere map te installeren.

### <a name="administrative-install-from-the-command-line"></a>Beheer installeren vanaf de opdrachtregel

MSI-pakketten kunnen worden geïnstalleerd vanaf de opdrachtregel, zodat beheerders pakketten kunnen implementeren zonder tussenkomst van de gebruiker. Het MSI-pakket bevat de volgende eigenschappen om de installatieopties te bepalen:

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL:** met deze eigenschap bepaalt u de optie voor het toevoegen van het **open PowerShell-item** aan het contextmenu in Windows Verkenner.
- **ADD_FILE_CONTEXT_MENU_RUNPOWERSHELL:** met deze eigenschap bepaalt u de optie voor het toevoegen van het item Uitvoeren met **PowerShell** aan het contextmenu in Windows Verkenner.
- **ENABLE_PSREMOTING:** met deze eigenschap bepaalt u de optie voor het inschakelen van de toegang tot powershell tijdens de installatie.
- **REGISTER_MANIFEST:** met deze eigenschap bepaalt u de optie voor het registreren van het Windows Event Logging-manifest.

In het volgende voorbeeld ziet u hoe u PowerShell op de stille manier installeert met alle installatieopties ingeschakeld.

```powershell
msiexec.exe /package PowerShell-7.1.3-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

Zie Opdrachtregelopties voor een volledige lijst met `Msiexec.exe` [opdrachtregelopties voor](/windows/desktop/Msi/command-line-options).

### <a name="registry-keys-created-during-installation"></a>Registersleutels die tijdens de installatie zijn gemaakt

Vanaf PowerShell 7.1 maakt het MSI-pakket registersleutels waarin de installatielocatie en versie van PowerShell worden opgeslagen. Deze waarden bevinden zich in `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>` . De waarde van `<GUID>` is uniek voor elk buildtype (release of preview), de belangrijkste versie en architectuur.

|    Release    | Architectuur |                                          Registersleutel                                           |
| ------------- | :----------: | ----------------------------------------------------------------------------------------------- |
| 7.1.x Release |     x86      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\1d00683b-0f84-4db8-a64f-2f98ad42fe06` |
| 7.1.x Release |     x64      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\31ab5147-9a97-4452-8443-d9709f0516e1` |
| 7.1.x Preview |     x86      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\86abcfbd-1ccc-4a88-b8b2-0facfde29094` |
| 7.1.x Preview |     x64      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\39243d76-adaf-42b1-94fb-16ecf83237c8` |

Dit kan worden gebruikt door beheerders en ontwikkelaars om het pad naar PowerShell te vinden. De waarden zijn hetzelfde voor alle preview- en `<GUID>` secundaire versiereleases. De `<GUID>` waarden worden voor elke belangrijke release gewijzigd.

## <a name="installing-the-zip-package"></a><a id="zip" />Het ZIP-pakket installeren

Binaire ZIP-archieven van PowerShell worden geleverd om geavanceerde implementatiescenario's mogelijk te maken. Download een van de volgende ZIP-archieven op de pagina [releases][releases].

- PowerShell-7.1.3-win-x64.zip
- PowerShell-7.1.3-win-x86.zip
- PowerShell-7.1.3-win-arm64.zip
- PowerShell-7.1.3-win-arm32.zip

Afhankelijk van hoe u het bestand downloadt, moet u het bestand mogelijk deblokkeren met behulp van de `Unblock-File` cmdlet . Voer de inhoud uit op de locatie van uw keuze en voer `pwsh.exe` deze uit. In tegenstelling tot het installeren van de MSI-pakketten, wordt bij het installeren van het ZIP-archief niet op vereisten gecontroleerd. Voor een goede werking van remoting via WSMan moet u ervoor zorgen dat u aan de [vereisten hebt voldaan.](#prerequisites)

Gebruik deze methode om de op ARM gebaseerde versie van PowerShell te installeren op computers zoals de Microsoft Surface Pro X. Voor het beste resultaat installeert u PowerShell in de map `$env:ProgramFiles\PowerShell\7` to.

> [!NOTE]
> U kunt deze methode gebruiken om elke versie van PowerShell te installeren, inclusief de nieuwste versie:
> - Stabiele release: [https://aka.ms/powershell-release?tag=stable](https://aka.ms/powershell-release?tag=stable)
> - Preview-versie: [https://aka.ms/powershell-release?tag=preview](https://aka.ms/powershell-release?tag=preview)
> - LTS-release: [https://aka.ms/powershell-release?tag=lts](https://aka.ms/powershell-release?tag=lts)

## <a name="deploying-on-windows-10-iot-enterprise"></a>Implementeren op Windows 10 IoT Enterprise

Windows 10 IoT Enterprise wordt geleverd met Windows PowerShell, die we kunnen gebruiken om PowerShell 7 te implementeren.

1. Maken `PSSession` om het doelapparaat te maken

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

1. Het ZIP-pakket naar het apparaat kopiëren

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

1. Verbinding maken met het apparaat en het archief uitbreiden

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

1. Moting instellen voor PowerShell 7

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because
   # it has to restart WinRM
   ```

1. Verbinding maken met het PowerShell 7-eindpunt op het apparaat

   ```powershell
   # Be sure to use the -Configuration parameter. If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a>Implementeren op Windows 10 IoT Core

Windows 10 IoT Core voegt Windows PowerShell toe wanneer u de _functie IOT_POWERSHELL,_ die we kunnen gebruiken om PowerShell 7 te implementeren. De bovenstaande stappen voor Windows 10 IoT Enterprise kunnen ook worden gevolgd voor IoT Core.

Als u de nieuwste versie van PowerShell wilt toevoegen aan de verzendafbeelding, gebruikt u de opdracht [Import-PSCoreRelease][] om het pakket op te nemen in de workarea en voegt u OPENSRC_POWERSHELL-functie _toe_ aan uw afbeelding.

> [!NOTE]
> Voor arm64-architectuur wordt Windows PowerShell niet toegevoegd wanneer u de _IOT_POWERSHELL._ De zip-installatie werkt dus niet. U moet de opdracht gebruiken `Import-PSCoreRelease` om deze toe te voegen aan de afbeelding.

## <a name="deploying-on-nano-server"></a>Implementeren op Nano Server

In deze instructies wordt ervan uitgenomen dat de Nano Server een 'headless' besturingssysteem is met een versie van PowerShell die al wordt uitgevoerd. Zie de Documentatie over [nanoserver-Image Builder](/windows-server/get-started/deploy-nano-server) voor meer informatie.

Binaire PowerShell-bestanden kunnen op twee verschillende manieren worden geïmplementeerd.

1. Offline: bevestig de Nano Server-VHD en los de inhoud van het zip-bestand uit op de locatie die u hebt gekozen in de bevestigingsafbeelding.
1. Online: breng het ZIP-bestand over via een PowerShell-sessie en pakken het uit op de door u gekozen locatie.

In beide gevallen hebt u het Windows 10 x64 ZIP-releasepakket nodig. Voer de opdrachten uit in een administrator-exemplaar van PowerShell.

### <a name="offline-deployment-of-powershell"></a>Offlineimplementatie van PowerShell

1. Gebruik uw favoriete zip-hulpprogramma om het pakket uit te pak in een map in de bevestigd Nano Server-afbeelding.
1. Ontkoppel de afbeelding en start deze op.
1. Maak verbinding met het ingebouwde exemplaar van Windows PowerShell.
1. Volg de instructies voor het maken van een eindpunt voor remoting met behulp van [de 'techniek van een ander exemplaar'.][]

### <a name="online-deployment-of-powershell"></a>Onlineimplementatie van PowerShell

Implementeer PowerShell in Nano Server met behulp van de volgende stappen.

- Verbinding maken met het ingebouwde exemplaar van Windows PowerShell

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- Het bestand kopiëren naar het Nano Server-exemplaar

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- Voer de sessie in

  ```powershell
  Enter-PSSession $session
  ```

- Het ZIP-bestand uitpakken

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- Als u op WSMan gebaseerde remoting wilt, volgt u de instructies voor het maken van een remoting-eindpunt met behulp van [de 'andere instantietechniek'.][]

## <a name="install-as-a-net-global-tool"></a>Installeren als een .NET Global-hulpprogramma

Als u de .NET Core SDK [hebt](/dotnet/core/sdk) geïnstalleerd, kunt u PowerShell eenvoudig installeren als [een .NET Global-hulpprogramma.](/dotnet/core/tools/global-tools)

```
dotnet tool install --global PowerShell
```

Het installatieprogramma dotnet voegt toe `$env:USERPROFILE\.dotnet\tools` aan uw `$env:PATH` omgevingsvariabele. De momenteel lopende shell heeft echter niet de bijgewerkte `$env:PATH` . U kunt PowerShell starten vanuit een nieuwe shell door te `pwsh` typen.

## <a name="install-powershell-via-the-windows-package-manager"></a>Installeer PowerShell via de Windows-pakketbeheerder

Het `winget` opdrachtregelprogramma stelt ontwikkelaars in staat om toepassingen te ontdekken, installeren, upgraden, verwijderen en configureren op Windows 10 computers. Dit hulpprogramma is de clientinterface voor de Windows-pakketbeheerder service.

> [!NOTE]
> Windows-pakketbeheerder en het hulpprogramma zijn in openbare preview en kunnen aanzienlijk worden `winget` gewijzigd voordat ze algemeen beschikbaar zijn. Zie de [documentatie voor][winget] een lijst met systeemvereisten en installatie-instructies.

De volgende opdrachten kunnen worden gebruikt om PowerShell te installeren met behulp van de `winget` gepubliceerde pakketten:

1. Zoek naar de nieuwste versie van PowerShell

   ```powershell
   winget search Microsoft.PowerShell
   ```

   ```Output
   Name                      Id                                Version
   ---------------------------------------------------------------------------
   PowerShell                Microsoft.PowerShell              7.1.3
   PowerShell Preview (MSIX) Microsoft.PowerShell-Preview-MSIX 7.0.2
   PowerShell-Preview        Microsoft.PowerShell-Preview      7.2.0-preview.5
   ```

1. Een versie van PowerShell installeren met behulp van de `--exact` parameter

   ```powershell
   winget install --name PowerShell --exact
   winget install --name PowerShell-Preview --exact
   ```

## <a name="installing-from-the-microsoft-store"></a><a id="msix" />Installeren vanaf de Microsoft Store

PowerShell 7.1 is gepubliceerd op de Microsoft Store. U vindt de PowerShell-release op de [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website of in de Store-toepassing in Windows.

Voordelen van het Microsoft Store pakket:

- Automatische updates ingebouwd in Windows 10
- Kan worden geïntegreerd met andere softwaredistributiemechanismen, zoals Intune en SCCM

Beperkingen:

MSIX-pakketten worden uitgevoerd in een toepassings-sandbox die de toegang tot sommige bestandssysteem- en registerlocaties virtualiseert.

- Alle registerwijzigingen onder HKEY_CURRENT_USER worden gekopieerd bij schrijven naar een privélocatie per gebruiker, per app. Deze waarden zijn daarom niet beschikbaar voor andere toepassingen.
- Configuratie-instellingen op systeemniveau die zijn opgeslagen in `$PSHOME` , kunnen niet worden gewijzigd. Dit omvat de WSMAN-configuratie. Dit voorkomt dat externe sessies verbinding maken met op de Store gebaseerde installaties van PowerShell. Configuraties op gebruikersniveau en SSH-remoting worden ondersteund.

Zie Understanding [how packaged desktop apps run on Windows (Begrijpen hoe verpakte bureaublad-apps worden uitgevoerd in Windows) voor meer informatie.](/windows/msix/desktop/desktop-to-uwp-behind-the-scenes)

### <a name="using-the-msix-package"></a>Het MSIX-pakket gebruiken

> [!NOTE]
> De preview-builds van PowerShell bevatten een MSIX-pakket. Het MSIX-pakket wordt niet officieel ondersteund. Het pakket is gebouwd voor testdoeleinden tijdens de preview-periode.

Als u het MSIX-pakket handmatig wilt installeren op een Windows 10-client, downloadt u het MSIX-pakket op onze pagina GitHub [releases][releases]. Schuif omlaag naar de **sectie Assets** van de release die u wilt installeren. De sectie Assets kan worden samengevouwen, dus mogelijk moet u erop klikken om deze uit te vouwen.

Het MSIX-bestand ziet er als deze uit: `PowerShell-<version>-win-<os-arch>.msix`

Als u het pakket wilt installeren, moet u de `Add-AppxPackage` cmdlet gebruiken.

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="how-to-create-a-remoting-endpoint"></a>Een eindpunt voor remoting maken

PowerShell ondersteunt het PowerShell Remoting Protocol (PSRP) via zowel WSMan als SSH. Zie voor meer informatie:

- [SSH-remoting in PowerShell Core][ssh-remoting]
- [WSMan Remoting in PowerShell Core][wsman-remoting]

## <a name="upgrading-an-existing-installation"></a>Een bestaande installatie upgraden

Voor de beste resultaten bij het upgraden moet u dezelfde installatiemethode gebruiken die u hebt gebruikt toen u PowerShell voor het eerst installeerde. Elke installatiemethode installeert PowerShell op een andere locatie. Als u niet zeker weet hoe PowerShell is geïnstalleerd, kunt u de geïnstalleerde locatie vergelijken met de pakketgegevens in dit artikel. Als u hebt geïnstalleerd via het MSI-pakket, wordt die informatie weergegeven in **de** Configuratiescherm.

## <a name="installation-support"></a>Ondersteuning voor installatie

Microsoft ondersteunt de installatiemethoden in dit document. Er zijn mogelijk andere installatiemethoden beschikbaar vanuit andere bronnen. Hoewel deze hulpprogramma's en methoden kunnen werken, biedt Microsoft geen ondersteuning voor deze methoden.

<!-- link references -->

[Voorbeeld]: https://aka.ms/powershell-release?tag=preview
[meest recente]: https://aka.ms/powershell-release?tag=stable
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[winget]: /windows/package-manager/winget
['een andere instantietechniek']: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
[Import-PSCoreRelease]: https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease
