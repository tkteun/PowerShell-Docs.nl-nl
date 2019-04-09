---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Windows PowerShell-stations beheren
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: 9ac5136fb28b450ea6397cab2f36082c50f22e1f
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293245"
---
# <a name="managing-windows-powershell-drives"></a>Windows PowerShell-stations beheren

Een *Windows PowerShell-station* is een locatie voor het opslaan van gegevens waartoe u toegang hebt, zoals een station bestand system in Windows PowerShell. De Windows PowerShell-providers maken bepaalde stations, zoals het bestandssysteem stations (inclusief C: en D:), het register stations (HKCU: en HKLM:), en het station van het certificaat (Cert:), en kunt u uw eigen Windows PowerShell-stations. Deze stations zijn zeer nuttig, maar ze zijn alleen beschikbaar in Windows PowerShell. U geen toegang tot deze met behulp van andere Windows-hulpprogramma's, zoals Verkenner of Cmd.exe.

Windows PowerShell maakt gebruik van het zelfstandig naamwoord, **PSDrive**, voor de opdrachten die met Windows PowerShell werken-stations. Voor een lijst van de Windows PowerShell-stations in uw Windows PowerShell-sessie, gebruikt u de **Get-PSDrive** cmdlet.

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

Hoewel de stations in de weergave met de stations op uw systeem variëren, de aanbieding zal er ongeveer als volgt de uitvoer van de **Get-PSDrive** opdracht hierboven wordt weergegeven.

Bestand systeemstations vormen een subset van de Windows PowerShell-stations. U kunt de systeemstations bestand door het bestandssysteem item in de kolom Provider kunt identificeren. (De stations bestand system in Windows PowerShell worden ondersteund door het bestandssysteem van Windows PowerShell-provider.)

Om te zien van de syntaxis van de **Get-PSDrive** cmdlet, typ een **Get-Command** opdracht met de **syntaxis** parameter:

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

De **PSProvider** parameter kunt u alleen de Windows PowerShell-stations die worden weergegeven door een bepaalde provider worden ondersteund. Bijvoorbeeld, als de Windows PowerShell-stations die worden ondersteund door het bestandssysteem van Windows PowerShell-provider, typt u een **Get-PSDrive** opdracht met de **PSProvider** parameter en de  **Bestandssysteem** waarde:

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Als u de Windows PowerShell-stations die registeronderdelen vertegenwoordigen, gebruikt u de **PSProvider** parameter om weer te geven alleen de Windows PowerShell-stations die worden ondersteund door het register van Windows PowerShell-provider:

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

U kunt ook de standaard locatie-cmdlets gebruiken met de Windows PowerShell-stations:

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Toevoegen van nieuwe Windows PowerShell-stations (nieuwe PSDrive)

U kunt uw eigen Windows PowerShell-stations toevoegen met behulp van de **New-PSDrive** opdracht. Om op te halen van de syntaxis voor de **New-PSDrive** opdracht, voer de **Get-Command** opdracht met de **syntaxis** parameter:

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Een nieuwe Windows PowerShell-station wilt maken, moet u drie parameters opgeven:

- Een naam op voor het station (u kunt een geldige naam voor de Windows PowerShell)

- De PSProvider (gebruik "Bestandssysteem" voor bestand systeemlocaties en '-register voor registerlocaties)

- De hoofdmap, dat wil zeggen, het pad naar de hoofdmap van het nieuwe station

Bijvoorbeeld, kunt u een station met de naam 'Office' die is gekoppeld aan de map met de Microsoft Office-toepassingen op uw computer, zoals **C:\\Program Files\\Microsoft Office\\OFFICE11**. Het station wilt maken, typt u de volgende opdracht:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> In het algemeen zijn paden niet hoofdlettergevoelig.

U verwijst naar het nieuwe Windows PowerShell-station, zoals u dat wel alle Windows PowerShell-stations: door de naam gevolgd door een dubbele punt doet (**:**).

Een Windows PowerShell-station kunt vele taken die veel eenvoudiger maken. Sommige van de belangrijkste sleutels in het Windows-register hebben bijvoorbeeld extreem lange paden, zodat ze toegang krijgen tot omslachtig en moeilijk te onthouden. Essentiële configuratie-informatie zich bevindt onder **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**. Als u wilt weergeven en wijzigen van items in de registersleutel CurrentVersion, kunt u een Windows PowerShell-station die verankerd ligt in deze sleutel maken door te typen:

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

U kunt vervolgens Wijzig de locatie in de **cvkey:** station net als elk ander station:''

`PS> cd cvkey:`

of:

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

De cmdlet New-PsDrive voegt het nieuwe station alleen voor de huidige Windows PowerShell-sessie. Als u de Windows PowerShell-venster sluit, wordt het nieuwe station verloren gaan. Als u wilt opslaan op een Windows PowerShell-station, gebruikt u de cmdlet Export-Console voor het exporteren van de huidige Windows PowerShell-sessie en gebruik vervolgens de PowerShell.exe **PSConsoleFile** parameter om het te importeren. Of het nieuwe station toevoegen aan uw Windows PowerShell-profiel.

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Verwijderen van Windows PowerShell-stations (Remove-PSDrive)

U kunt stations uit de Windows PowerShell verwijderen met behulp van de **Remove-PSDrive** cmdlet. De **Remove-PSDrive** cmdlet is eenvoudig te gebruiken; als u wilt verwijderen van een specifieke Windows PowerShell-station, u gewoon de naam van de Windows PowerShell-station.

Bijvoorbeeld, als u hebt toegevoegd de **Office:** Windows PowerShell-station, zoals wordt weergegeven in de **New-PSDrive** onderwerp, kunt u deze verwijderen door te typen:

```powershell
Remove-PSDrive -Name Office
```

Verwijderen van de **cvkey:** Windows PowerShell station, ook weergegeven in de **New-PSDrive** onderwerp, gebruikt u de volgende opdracht:

```powershell
Remove-PSDrive -Name cvkey
```

Het is eenvoudig te verwijderen van een Windows PowerShell-station, maar u kunt deze niet verwijderen wanneer u zich in het station. Bijvoorbeeld:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a>Externe Windows PowerShell-stations toevoegen en verwijderen

Windows PowerShell detecteert bestand systeemstations die worden toegevoegd of verwijderd in Windows, inclusief stations die zijn toegewezen, USB-stations die zijn gekoppeld en stations die zijn verwijderd met behulp van de **netgebruik** opdracht of het  **WScript.NetworkMapNetworkDrive** en **RemoveNetworkDrive** methoden van een script Windows Script Host (WSH).