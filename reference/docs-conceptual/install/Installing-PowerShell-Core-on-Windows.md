---
title: PowerShell installeren in Windows
description: Informatie over het installeren van Power shell in Windows
ms.date: 02/02/2021
ms.openlocfilehash: bd3643c1ca6beb60a8727478a1ae612dcb34c7fb
ms.sourcegitcommit: 080c8b05a1242348c365fe1684457e873325f11e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2021
ms.locfileid: "103483433"
---
# <a name="installing-powershell-on-windows"></a>PowerShell installeren in Windows

Er zijn meerdere manieren om Power shell in Windows te installeren.

## <a name="prerequisites"></a>Vereisten

De meest recente versie van Power shell wordt ondersteund op Windows 7 SP1, Server 2008 R2 en latere versies.

Als u externe communicatie van Power shell wilt inschakelen via WSMan, moeten aan de volgende vereisten worden voldaan:

- Installeer de [universele C-runtime](https://www.microsoft.com/download/details.aspx?id=50410) op Windows-versies predating Windows 10. Het is beschikbaar via direct downloaden of Windows Update. Dit pakket is al geïnstalleerd op systemen met volledige patches.
- Installeer Windows Management Framework (WMF) 4,0 of nieuwer op Windows 7 en Windows Server 2008 R2. Zie [overzicht van WMF](/powershell/scripting/wmf/overview)voor meer informatie over WMF.

## <a name="download-the-installer-package"></a>Het installatie pakket downloaden

Als u Power shell in Windows wilt installeren, downloadt u het [meest recente][] installatie pakket van github. U kunt ook de nieuwste [Preview][] -versie vinden. Schuif omlaag naar de sectie **assets** van de pagina release. De sectie **assets** kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.

## <a name="installing-the-msi-package"></a><a id="msi" />Het MSI-pakket installeren

Het MSI-bestand ziet er als volgt uit `PowerShell-<version>-win-<os-arch>.msi` . Bijvoorbeeld:

- `PowerShell-7.1.3-win-x64.msi`
- `PowerShell-7.1.3-win-x86.msi`

Na het downloaden dubbelklikt u op het installatie programma en volgt u de aanwijzingen.

Het installatie programma maakt een snelkoppeling in het menu Start van Windows.

- Het pakket is standaard geïnstalleerd voor `$env:ProgramFiles\PowerShell\<version>`
- U kunt Power shell starten via het menu Start of `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

> [!NOTE]
> Power shell 7,1 wordt geïnstalleerd in een nieuwe map en kan naast Windows Power shell 5,1 worden uitgevoerd.
> Power shell 7,1 is een in-place upgrade waarmee Power shell 6. x wordt vervangen. of Power shell 7,0.
>
> - Power shell 7,1 is geïnstalleerd voor `$env:ProgramFiles\PowerShell\7`
> - De `$env:ProgramFiles\PowerShell\7` map wordt toegevoegd aan `$env:PATH`
> - De `$env:ProgramFiles\PowerShell\6` map wordt verwijderd
>
> Als u Power shell 7,1 naast andere versies moet uitvoeren, gebruikt u de methode [zip-installatie](#zip) om de andere versie te installeren in een andere map.

### <a name="administrative-install-from-the-command-line"></a>Beheerders installatie vanaf de opdracht regel

MSI-pakketten kunnen worden geïnstalleerd vanaf de opdracht regel zodat beheerders pakketten kunnen implementeren zonder tussen komst van de gebruiker. Het MSI-pakket bevat de volgende eigenschappen om de installatie opties te beheren:

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** : met deze eigenschap bepaalt u de optie voor het toevoegen van het **geopende Power shell** -item aan het context menu in Windows Verkenner.
- **ADD_FILE_CONTEXT_MENU_RUNPOWERSHELL** : deze eigenschap bepaalt de optie voor het toevoegen van het item **uitvoeren met Power shell** in het context menu in Windows Verkenner.
- **ENABLE_PSREMOTING** : deze eigenschap bepaalt de optie voor het inschakelen van externe communicatie van Power shell tijdens de installatie.
- **REGISTER_MANIFEST** -met deze eigenschap bepaalt u de optie voor het registreren van het Windows-logboek voor gebeurtenis logboek registratie.

In het volgende voor beeld ziet u hoe u Power shell op de achtergrond installeert met alle installatie opties ingeschakeld.

```powershell
msiexec.exe /package PowerShell-7.1.3-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

`Msiexec.exe`Zie [opdracht regel opties](/windows/desktop/Msi/command-line-options)voor een volledige lijst met opdracht regel opties voor.

### <a name="registry-keys-created-during-installation"></a>Register sleutels die tijdens de installatie zijn gemaakt

Vanaf Power shell 7,1 maakt het MSI-pakket register sleutels waarin de installatie locatie en de versie van Power shell worden opgeslagen. Deze waarden bevinden zich in `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>` . De waarde van `<GUID>` is uniek voor elk type Build (release of preview), de primaire versie en de architectuur.

|    Release    | Architectuur |                                          Registersleutel                                           |
| ------------- | :----------: | ----------------------------------------------------------------------------------------------- |
| Versie 7.1. x |     x86      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\1d00683b-0f84-4db8-a64f-2f98ad42fe06` |
| Versie 7.1. x |     x64      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\31ab5147-9a97-4452-8443-d9709f0516e1` |
| 7.1. x preview |     x86      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\86abcfbd-1ccc-4a88-b8b2-0facfde29094` |
| 7.1. x preview |     x64      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\39243d76-adaf-42b1-94fb-16ecf83237c8` |

Dit kan worden gebruikt door beheerders en ontwikkel aars om het pad naar Power shell te vinden. De `<GUID>` waarden zijn hetzelfde voor alle versies van de preview-versie en secundaire versies. De `<GUID>` waarden voor elke grote release worden gewijzigd.

## <a name="installing-the-zip-package"></a><a id="zip" />Het ZIP-pakket installeren

Binaire ZIP-archieven van Power shell zijn beschikbaar om geavanceerde implementatie scenario's mogelijk te maken. Down load een van de volgende ZIP-archieven van de pagina [releases] [releases].

- PowerShell-7.1.3-win-x64.zip
- PowerShell-7.1.3-win-x86.zip
- PowerShell-7.1.3-win-arm64.zip
- PowerShell-7.1.3-win-arm32.zip

Afhankelijk van hoe u het bestand downloadt, moet u het bestand mogelijk deblokkeren met de `Unblock-File` cmdlet. Pak de inhoud uit naar de gewenste locatie en voer deze `pwsh.exe` uit. In tegens telling tot de installatie van de MSI-pakketten controleert de installatie van het ZIP-archief niet op vereisten. Zorg ervoor dat u aan de [vereisten](#prerequisites)voldoet om externe toegang tot WSMan goed te laten werken.

Gebruik deze methode om de ARM-gebaseerde versie van Power shell te installeren op computers zoals micro soft Surface Pro X. Voor de beste resultaten installeert u Power shell op de `$env:ProgramFiles\PowerShell\7` map aan.

> [!NOTE]
> U kunt deze methode gebruiken om een wille keurige versie van Power shell te installeren, met inbegrip van de nieuwste:
> - Stabiele release: [https://aka.ms/powershell-release?tag=stable](https://aka.ms/powershell-release?tag=stable)
> - Preview-versie: [https://aka.ms/powershell-release?tag=preview](https://aka.ms/powershell-release?tag=preview)
> - LTS release: [https://aka.ms/powershell-release?tag=lts](https://aka.ms/powershell-release?tag=lts)

## <a name="deploying-on-windows-10-iot-enterprise"></a>Implementeren in Windows 10 IoT Enter prise

Windows 10 IoT Enter prise wordt geleverd met Windows Power shell en kan worden gebruikt voor het implementeren van Power shell 7.

1. Maken `PSSession` op doel apparaat

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

1. Het ZIP-pakket kopiëren naar het apparaat

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

1. Verbinding maken met het apparaat en het archief uitvouwen

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

1. Externe toegang instellen met Power shell 7

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because
   # it has to restart WinRM
   ```

1. Verbinding maken met het Power shell 7-eind punt op het apparaat

   ```powershell
   # Be sure to use the -Configuration parameter. If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a>Implementeren in Windows 10 IoT core

Windows 10 IoT core voegt Windows Power shell toe wanneer u _IOT_POWERSHELL_ -functie opneemt, die we kunnen gebruiken om Power shell 7 te implementeren. De stappen die hierboven voor Windows 10 IoT Enter prise zijn gedefinieerd, kunnen ook worden gevolgd voor IoT core.

Voor het toevoegen van de meest recente Power shell in de verzend installatie kopie gebruikt u de opdracht [import-PSCoreRelease][] om het pakket op te zetten in de workarea en voegt u _OPENSRC_POWERSHELL_ functie toe aan uw installatie kopie.

> [!NOTE]
> Voor ARM64-architectuur wordt Windows Power shell niet toegevoegd wanneer u _IOT_POWERSHELL_ opneemt. De op ZIP gebaseerde installatie werkt dus niet. U moet `Import-PSCoreRelease` de opdracht gebruiken om deze toe te voegen aan de installatie kopie.

## <a name="deploying-on-nano-server"></a>Implementeren op nano server

Bij deze instructies wordt ervan uitgegaan dat de nano server een ' headless ' besturings systeem is waarop al een versie van Power shell wordt uitgevoerd. Zie de documentatie van [nano server Image Builder](/windows-server/get-started/deploy-nano-server) voor meer informatie.

Binaire Power Shell-bestanden kunnen met twee verschillende methoden worden geïmplementeerd.

1. De nano server-VHD offline koppelen en de inhoud van het zip-bestand uitpakken naar de gekozen locatie in de gekoppelde installatie kopie.
1. Online: zet het zip-bestand over een Power shell-sessie over en pak het uit op uw gekozen locatie.

In beide gevallen hebt u het Windows 10 x64 ZIP-release pakket nodig. Voer de opdrachten uit in een ' beheerder ' exemplaar van Power shell.

### <a name="offline-deployment-of-powershell"></a>Offline-implementatie van Power shell

1. Gebruik uw favoriete zip-hulp programma om het pakket uit te pakken naar een map in de gekoppelde nano server-installatie kopie.
1. Ontkoppel de installatie kopie en start deze op.
1. Maak verbinding met het ingebouwde exemplaar van Windows Power shell.
1. Volg de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"][].

### <a name="online-deployment-of-powershell"></a>Online implementatie van Power shell

Implementeer Power shell naar nano server met behulp van de volgende stappen.

- Verbinding maken met het ingebouwde exemplaar van Windows Power shell

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- Kopieer het bestand naar het Nano Server-exemplaar

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- De sessie invoeren

  ```powershell
  Enter-PSSession $session
  ```

- Het ZIP-bestand uitpakken

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- Als u externe toegang op basis van WSMan wilt gebruiken, volgt u de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"][].

## <a name="install-as-a-net-global-tool"></a>Installeren als een Global .NET-hulp programma

Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).

```
dotnet tool install --global PowerShell
```

Het hulp programma DotNet tool wordt toegevoegd `$env:USERPROFILE\dotnet\tools` aan de `$env:PATH` omgevings variabele. De momenteel actieve shell beschikt echter niet over de bijgewerkte versie `$env:PATH` . U kunt Power shell starten vanuit een nieuwe shell door te typen `pwsh` .

## <a name="install-powershell-via-winget"></a>Power Shell installeren via Winget

`winget`Met het opdracht regel programma kunnen ontwikkel aars toepassingen op Windows 10-computers detecteren, installeren, upgraden, verwijderen en configureren. Dit hulp programma is de client interface voor de Windows Package Manager-service.

> [!NOTE]
> Het `winget` hulp programma is momenteel een preview-versie. Niet alle geplande functionaliteit is op dit moment beschikbaar.
> U moet deze methode niet gebruiken in een scenario voor productie-implementatie. Raadpleeg de [Winget] -documentatie voor een lijst met systeem vereisten en installatie-instructies.

De volgende opdrachten kunnen worden gebruikt om Power shell te installeren met behulp van de gepubliceerde `winget` pakketten:

1. Zoeken naar de meest recente versie van Power shell

   ```powershell
   winget search Microsoft.PowerShell
   ```

   ```Output
   Name                      Id                                Version
   ---------------------------------------------------------------------------
   PowerShell                Microsoft.PowerShell              7.1.3
   PowerShell Preview (MSIX) Microsoft.PowerShell-Preview-MSIX 7.0.2
   PowerShell-Preview        Microsoft.PowerShell-Preview      7.2.0-preview.3
   ```

1. Een versie van Power Shell installeren met behulp van de `--exact` para meter

   ```powershell
   winget install --name PowerShell --exact
   winget install --name PowerShell-Preview --exact
   ```

## <a name="installing-from-the-microsoft-store"></a><a id="msix" />Installeren vanuit de Microsoft Store

Power shell 7,1 is gepubliceerd op de Microsoft Store. U kunt de Power shell-release vinden op de [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website of in de Store-toepassing in Windows.

Voor delen van het Microsoft Store-pakket:

- Automatische updates zijn direct in Windows 10 ingebouwd
- Kan worden geïntegreerd met andere software distributie mechanismen, zoals intune en SCCM

Beperkingen:

MSIX-pakketten worden uitgevoerd in een sandbox voor toepassingen waarmee de toegang tot bepaalde bestands systeem-en register locaties wordt gevirtualeerd.

- Alle register wijzigingen onder HKEY_CURRENT_USER worden bij het schrijven naar een persoonlijke, per gebruiker per app-locatie gekopieerd. Daarom zijn deze waarden niet beschikbaar voor andere toepassingen.
- Alle configuratie-instellingen op systeem niveau die zijn opgeslagen in, `$PSHOME` kunnen niet worden gewijzigd. Dit omvat de WSMAN-configuratie. Hiermee voor komt u dat externe sessies verbinding maken met op opslag gebaseerde installaties van Power shell. Configuraties op gebruikers niveau en externe SSH-communicatie worden ondersteund.

Zie [hoe verpakte bureau blad-apps worden uitgevoerd in Windows](/windows/msix/desktop/desktop-to-uwp-behind-the-scenes)voor meer informatie.

### <a name="using-the-msix-package"></a>Het MSIX-pakket gebruiken

> [!NOTE]
> De preview-builds van Power shell bevatten een MSIX-pakket. Het MSIX-pakket wordt niet officieel ondersteund. Het pakket is gebouwd voor test doeleinden tijdens de preview-periode.

Als u het MSIX-pakket hand matig wilt installeren op een Windows 10-client, downloadt u het MSIX-pakket van de pagina GitHub [releases] [releases]. Schuif omlaag naar de sectie **assets** van de release die u wilt installeren. De sectie assets kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.

Het MSIX-bestand ziet er als volgt uit: `PowerShell-<version>-win-<os-arch>.msix`

Als u het pakket wilt installeren, moet u de `Add-AppxPackage` cmdlet gebruiken.

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="how-to-create-a-remoting-endpoint"></a>Een extern eind punt maken

Power shell ondersteunt het Power shell Remoting Protocol (PSRP) voor zowel WSMan als SSH. Zie voor meer informatie:

- [Externe SSH-communicatie in Power shell core][ssh-remoting]
- [Externe WSMan-communicatie in Power shell core][wsman-remoting]

## <a name="upgrading-an-existing-installation"></a>Een bestaande installatie upgraden

Voor de beste resultaten bij het uitvoeren van een upgrade moet u dezelfde installatie methode gebruiken die u hebt gebruikt toen u Power shell voor het eerst installeerde. Elke installatie methode installeert Power shell op een andere locatie. Als u niet zeker weet hoe Power shell is geïnstalleerd, kunt u de geïnstalleerde locatie vergelijken met de pakket gegevens in dit artikel. Als u via het MSI-pakket hebt geïnstalleerd, wordt die informatie weer gegeven in het onderdeel **Program ma's en onderdelen** van het configuratie scherm.

## <a name="installation-support"></a>Ondersteuning voor installatie

Micro soft ondersteunt de installatie methoden in dit document. Er zijn mogelijk andere methoden van installatie beschikbaar van andere bronnen. Deze hulpprogram ma's en methoden kunnen werken, maar deze methoden kunnen niet door micro soft worden ondersteund.

<!-- link references -->

[Voorbeeld]: https://aka.ms/powershell-release?tag=preview
[meest recente]: https://aka.ms/powershell-release?tag=stable
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[winget]: /windows/package-manager/winget
["een andere instantie-techniek"]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
[Import-PSCoreRelease]: https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease
