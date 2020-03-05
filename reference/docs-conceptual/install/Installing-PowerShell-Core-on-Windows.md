---
title: PowerShell Core in Windows installeren
description: Informatie over het installeren van Power shell core in Windows
ms.date: 08/06/2018
ms.openlocfilehash: e9e78e3ab182099caf3dbf74b033168f1f2927d5
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78280269"
---
# <a name="installing-powershell-core-on-windows"></a>PowerShell Core in Windows installeren

Er zijn meerdere manieren om Power shell core in Windows te installeren.

## <a name="prerequisites"></a>Vereisten

Als u externe communicatie van Power shell wilt inschakelen via WSMan, moeten aan de volgende vereisten worden voldaan:

- Installeer de [Universal C runtime](https://www.microsoft.com/download/details.aspx?id=50410) op Windows-versies ouder dan Windows 10. Het is beschikbaar via direct downloaden of Windows Update. Volledige patches (inclusief optionele pakketten), de ondersteunde systemen hebben dit al geïnstalleerd.
- Installeer Windows Management Framework (WMF) 4,0 of nieuwer op Windows 7 en Windows Server 2008 R2. Zie [overzicht van WMF](/powershell/scripting/wmf/overview)voor meer informatie over WMF.

## <a name="a-idmsi-installing-the-msi-package"></a><a id="msi" />het MSI-pakket niet installeren

Als u Power shell wilt installeren op een Windows-client of Windows-Server (werkt met Windows 7 SP1, Server 2008 R2 en hoger), downloadt u het MSI-pakket van onze pagina met GitHub- [releases][releases] . Schuif omlaag naar de sectie **assets** van de release die u wilt installeren. De sectie assets kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.

Het MSI-bestand ziet er als volgt uit: `PowerShell-<version>-win-<os-arch>.msi`

Na het downloaden dubbelklikt u op het installatie programma en volgt u de aanwijzingen.

Het installatie programma maakt een snelkoppeling in het menu Start van Windows.

- Standaard wordt het pakket geïnstalleerd op `$env:ProgramFiles\PowerShell\<version>`
- U kunt Power shell starten via het menu Start of `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

> [!NOTE]
> Power shell 7 wordt geïnstalleerd in een nieuwe map en wordt naast elkaar uitgevoerd met Windows Power shell 5,1. Voor Power shell Core 6. x is Power shell 7 een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.
>
> - Power shell 7 is geïnstalleerd op `%programfiles%\PowerShell\7`
> - De map `%programfiles%\PowerShell\7` wordt toegevoegd aan `$env:PATH`
> - De map `%programfiles%\PowerShell\6` wordt verwijderd
>
> Als u Power shell 6 side-by-side wilt uitvoeren met Power shell 7, installeert u Power shell 6 opnieuw met de methode [zip-installatie](#zip) .

### <a name="administrative-install-from-the-command-line"></a>Beheerders installatie vanaf de opdracht regel

MSI-pakketten kunnen worden geïnstalleerd vanaf de opdracht regel. Hiermee kunnen beheerders pakketten implementeren zonder tussen komst van de gebruiker. Het MSI-pakket voor Power shell bevat de volgende eigenschappen voor het beheren van de installatie opties:

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** : met deze eigenschap bepaalt u de optie voor het toevoegen van het **geopende Power shell** -item aan het context menu in Windows Verkenner.
- **ENABLE_PSREMOTING** : deze eigenschap bepaalt de optie voor het inschakelen van externe communicatie van Power shell tijdens de installatie.
- **REGISTER_MANIFEST** -met deze eigenschap bepaalt u de optie voor het registreren van het Windows-logboek voor gebeurtenis logboek registratie.

In de volgende voor beelden ziet u hoe u Power shell Core op de achtergrond installeert met alle installatie opties ingeschakeld.

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

Zie [opdracht regel opties](/windows/desktop/Msi/command-line-options)voor een volledige lijst met opdracht regel opties voor Msiexec. exe.

## <a name="a-idmsix-installing-the-msix-package"></a><a id="msix" />het MSIX-pakket niet installeren

Als u het MSIX-pakket hand matig wilt installeren op een Windows 10-client, downloadt u het MSIX-pakket van de pagina met GitHub- [releases][releases] . Schuif omlaag naar de sectie **assets** van de release die u wilt installeren. De sectie assets kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.

Het MSI-bestand ziet er als volgt uit: `PowerShell-<version>-win-<os-arch>.msix`

Nadat u het installatie programma hebt gedownload, kunt u het niet gewoon dubbel klikken. dit pakket vereist het gebruik van niet-gevirtualiseerde resources.  Als u wilt installeren, moet u de cmdlet `Add-AppxPackage` gebruiken:

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="a-idzip-installing-the-zip-package"></a><a id="zip" />het ZIP-pakket niet installeren

Binaire ZIP-archieven van Power shell zijn beschikbaar om geavanceerde implementatie scenario's mogelijk te maken. Wanneer u het ZIP-archief gebruikt, wordt de controle van vereisten niet weer gegeven als in het MSI-pakket. Zorg ervoor dat u aan de [vereisten](#prerequisites)hebt voldaan voor externe communicatie via WSMan.

## <a name="deploying-on-windows-iot"></a>Implementeren op Windows IoT

Windows IoT wordt al geleverd met Windows Power shell en wordt gebruikt voor het implementeren van Power shell Core 6.

1. `PSSession` maken op doel apparaat

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. Het ZIP-pakket kopiëren naar het apparaat

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Verbinding maken met het apparaat en het archief uitvouwen

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. Externe toegang tot Power shell Core 6 instellen

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Verbinding maken met het Power shell Core 6-eind punt op het apparaat

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a>Implementeren op nano server

Bij deze instructies wordt ervan uitgegaan dat er al een versie van Power shell wordt uitgevoerd op de nano server-installatie kopie en dat deze is gegenereerd door de [Image Builder-installatie kopie van nano server](/windows-server/get-started/deploy-nano-server).
Nano server is een ' headless ' besturings systeem. Kern-binaire bestanden kunnen worden geïmplementeerd met twee verschillende methoden.

1. De nano server-VHD offline koppelen en de inhoud van het zip-bestand uitpakken naar de gekozen locatie in de gekoppelde installatie kopie.
2. Online: zet het zip-bestand over een Power shell-sessie over en pak het uit op uw gekozen locatie.

In beide gevallen hebt u het Windows 10 x64 ZIP-release pakket nodig en moet u de opdrachten uitvoeren in het Power shell-exemplaar ' Administrator '.

### <a name="offline-deployment-of-powershell-core"></a>Offline-implementatie van Power shell core

1. Gebruik uw favoriete zip-hulp programma om het pakket uit te pakken naar een map in de gekoppelde nano server-installatie kopie.
2. Ontkoppel de installatie kopie en start deze op.
3. Verbinding maken met het postvak in van Windows Power shell.
4. Volg de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Online implementatie van Power shell core

De volgende stappen begeleiden u bij de implementatie van Power shell core naar een actief exemplaar van nano server en de configuratie van het externe eind punt.

- Verbinding maken met het postvak in van Windows Power shell

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
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- Als u externe toegang op basis van WSMan wilt gebruiken, volgt u de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="install-as-a-net-global-tool"></a>Installeren als een Global .NET-hulp programma

Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).

```
dotnet tool install --global PowerShell
```

## <a name="how-to-create-a-remoting-endpoint"></a>Een extern eind punt maken

Power shell core ondersteunt het PSRP (Power shell Remoting Protocol) voor zowel WSMan als SSH. Zie voor meer informatie:

- [Externe SSH-communicatie in Power shell core][ssh-remoting]
- [Externe WSMan-communicatie in Power shell core][wsman-remoting]

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
