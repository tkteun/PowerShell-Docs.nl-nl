---
title: PowerShell installeren in Windows
description: Informatie over het installeren van Power shell in Windows
ms.date: 07/30/2020
ms.openlocfilehash: 21dc032afd61b628f2c43912ed6673875479ebff
ms.sourcegitcommit: 79d430fe48ad77a058f42b6bc9955d21b657987e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/30/2020
ms.locfileid: "87441756"
---
# <a name="installing-powershell-on-windows"></a>PowerShell installeren in Windows

Er zijn meerdere manieren om Power shell in Windows te installeren.

## <a name="prerequisites"></a>Vereisten

De meest recente versie van Power shell wordt ondersteund op Windows 7 SP1, Server 2008 R2 en latere versies.

Als u externe communicatie van Power shell wilt inschakelen via WSMan, moeten aan de volgende vereisten worden voldaan:

- Installeer de [universele C-runtime](https://www.microsoft.com/download/details.aspx?id=50410) op Windows-versies predating Windows 10. Het is beschikbaar via direct downloaden of Windows Update. Dit pakket is al geïnstalleerd op systemen met volledige patches.
- Installeer Windows Management Framework (WMF) 4,0 of nieuwer op Windows 7 en Windows Server 2008 R2. Zie [overzicht van WMF](/powershell/scripting/wmf/overview)voor meer informatie over WMF.

## <a name="download-the-installer-package"></a>Het installatie pakket downloaden

Als u Power shell in Windows wilt installeren, downloadt u het installatie pakket van onze pagina met GitHub- [releases][releases] . Schuif omlaag naar de sectie **assets** van de pagina release. De sectie **assets** kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.

## <a name="installing-the-msi-package"></a><a id="msi" />Het MSI-pakket installeren

Het MSI-bestand ziet er als volgt uit `PowerShell-<version>-win-<os-arch>.msi` . Bijvoorbeeld:

- `PowerShell-7.0.3-win-x64.msi`
- `PowerShell-7.0.3-win-x86.msi`

Na het downloaden dubbelklikt u op het installatie programma en volgt u de aanwijzingen.

Het installatie programma maakt een snelkoppeling in het menu Start van Windows.

- Het pakket is standaard geïnstalleerd voor `$env:ProgramFiles\PowerShell\<version>`
- U kunt Power shell starten via het menu Start of `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

> [!NOTE]
> Power shell 7 wordt geïnstalleerd in een nieuwe map en wordt naast elkaar uitgevoerd met Windows Power shell 5,1. Voor Power shell Core 6. x is Power shell 7 een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.
>
> - Power shell 7 is geïnstalleerd op `$env:ProgramFiles\PowerShell\7`
> - De `$env:ProgramFiles\PowerShell\7` map wordt toegevoegd aan `$env:PATH`
> - De `$env:ProgramFiles\PowerShell\6` map wordt verwijderd
>
> Als u Power shell 6 side-by-side wilt uitvoeren met Power shell 7, installeert u Power shell 6 opnieuw met de methode [zip-installatie](#zip) .

### <a name="administrative-install-from-the-command-line"></a>Beheerders installatie vanaf de opdracht regel

MSI-pakketten kunnen worden geïnstalleerd vanaf de opdracht regel zodat beheerders pakketten kunnen implementeren zonder tussen komst van de gebruiker. Het MSI-pakket bevat de volgende eigenschappen om de installatie opties te beheren:

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** : met deze eigenschap bepaalt u de optie voor het toevoegen van het **geopende Power shell** -item aan het context menu in Windows Verkenner.
- **ENABLE_PSREMOTING** : deze eigenschap bepaalt de optie voor het inschakelen van externe communicatie van Power shell tijdens de installatie.
- **REGISTER_MANIFEST** -met deze eigenschap bepaalt u de optie voor het registreren van het Windows-logboek voor gebeurtenis logboek registratie.

In het volgende voor beeld ziet u hoe u Power shell op de achtergrond installeert met alle installatie opties ingeschakeld.

```powershell
msiexec.exe /package PowerShell-7.0.3-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

`Msiexec.exe`Zie [opdracht regel opties](/windows/desktop/Msi/command-line-options)voor een volledige lijst met opdracht regel opties voor.

## <a name="installing-the-msix-package"></a><a id="msix" />Het MSIX-pakket installeren

> [!NOTE]
> Het MSIX-pakket wordt op dit moment niet officieel ondersteund. We blijven het pakket alleen voor interne test doeleinden bouwen.

Als u het MSIX-pakket hand matig wilt installeren op een Windows 10-client, downloadt u het MSIX-pakket van de pagina met GitHub- [releases][releases] . Schuif omlaag naar de sectie **assets** van de release die u wilt installeren. De sectie assets kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.

Het MSIX-bestand ziet er als volgt uit: `PowerShell-<version>-win-<os-arch>.msix`

Als u het pakket wilt installeren, moet u de `Add-AppxPackage` cmdlet gebruiken.

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="installing-the-zip-package"></a><a id="zip" />Het ZIP-pakket installeren

Binaire ZIP-archieven van Power shell zijn beschikbaar om geavanceerde implementatie scenario's mogelijk te maken. Het installeren van het ZIP-archief controleert niet de vereisten zoals de MSI-pakketten. Down load het ZIP-archief vanaf de pagina [releases][releases] . Afhankelijk van hoe u het bestand downloadt, moet u het bestand mogelijk deblokkeren met de `Unblock-File` cmdlet. Pak de inhoud uit naar de gewenste locatie en voer deze `pwsh.exe` uit. Zorg ervoor dat u aan de [vereisten](#prerequisites)voldoet om externe toegang tot WSMan goed te laten werken.

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
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

1. Verbinding maken met het Power shell 7-eind punt op het apparaat

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a>Implementeren in Windows 10 IoT core

Windows 10 IoT core voegt Windows Power shell toe wanneer u *IOT_POWERSHELL* -functie opneemt, die we kunnen gebruiken om Power shell 7 te implementeren.
De stappen die hierboven voor Windows 10 IoT Enter prise zijn gedefinieerd, kunnen ook worden gevolgd voor IoT core.

Voor het toevoegen van de meest recente Power shell in de verzend installatie kopie gebruikt u de opdracht [import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease) om het pakket op te zetten in de workarea en voegt u *OPENSRC_POWERSHELL* functie toe aan uw installatie kopie.

> [!NOTE]
> Voor ARM64-architectuur wordt Windows Power shell niet toegevoegd wanneer u *IOT_POWERSHELL*opneemt. De op ZIP gebaseerde installatie werkt dus niet.
> U moet de opdracht import-PSCoreRelease gebruiken om deze toe te voegen aan de installatie kopie.

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
1. Volg de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

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

- Als u externe toegang op basis van WSMan wilt gebruiken, volgt u de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

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
> De opties en functies van het hulp programma zijn onderhevig aan wijzigingen. U moet deze methode niet gebruiken in een scenario voor productie-implementatie. Raadpleeg de [Winget] -documentatie voor een lijst met systeem vereisten en installatie-instructies.

De volgende opdrachten kunnen worden gebruikt om Power shell te installeren met behulp van de gepubliceerde `winget` pakketten:

1. Zoeken naar de meest recente versie van Power shell

   ```powershell
   winget search Microsoft.PowerShell
   ```

   ```Output
   Name               Id                           Version
   ---------------------------------------------------------------
   PowerShell         Microsoft.PowerShell         7.0.3
   PowerShell-Preview Microsoft.PowerShell-Preview 7.1.0-preview.5
   ```

1. Een versie van Power Shell installeren met behulp van de `--exact` para meter

   ```powershell
   winget install --name PowerShell --exact
   winget install --name PowerShell-Preview --exact
   ```

## <a name="how-to-create-a-remoting-endpoint"></a>Een extern eind punt maken

Power shell ondersteunt het Power shell Remoting Protocol (PSRP) voor zowel WSMan als SSH. Zie voor meer informatie:

- [Externe SSH-communicatie in Power shell core][ssh-remoting]
- [Externe WSMan-communicatie in Power shell core][wsman-remoting]

## <a name="installation-support"></a>Ondersteuning voor installatie

Micro soft ondersteunt de installatie methoden in dit document. Er zijn mogelijk andere methoden van installatie beschikbaar van andere bronnen. Deze hulpprogram ma's en methoden kunnen werken, maar deze methoden kunnen niet door micro soft worden ondersteund.

<!-- link references -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[winget]: /windows/package-manager/winget
