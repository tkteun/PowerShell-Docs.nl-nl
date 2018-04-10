---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met registervermeldingen werken
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-registry-entries"></a>Met registervermeldingen werken

Omdat registervermeldingen eigenschappen van sleutels zijn en als zodanig kunnen niet worden rechtstreeks gebladerd, moeten we een lichtjes andere benadering rekening te houden wanneer u ze.

### <a name="listing-registry-entries"></a>Registervermeldingen van aanbieding

Er zijn veel verschillende manieren om te onderzoeken registervermeldingen. De eenvoudigste manier is om op te halen van de namen van de eigenschappen die zijn gekoppeld aan een sleutel. Bijvoorbeeld, om te zien van de namen van de vermeldingen in de registersleutel **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, gebruik **Get-Item** . Registersleutels hebben een eigenschap met de algemene naam van 'Eigenschap' die een lijst met registervermeldingen in de sleutel is. De volgende opdracht de eigenschap selecteert en de items wordt uitgebreid zodat ze in een lijst worden weergegeven:

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

U kunt de registervermeldingen weergeven in een beter leesbare vorm, met **Get ItemProperty**:

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

De Windows PowerShell-gerelateerde eigenschappen voor de sleutel, worden alle voorafgegaan door 'PS', zoals **PSPath**, **PSParentPath**, **PSChildName**, en **PSProvider** .

U kunt de '**.**' notatie voor het verwijzen naar de huidige locatie. U kunt **Set-Location** te wijzigen in de **CurrentVersion** register container eerste:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

U kunt ook kunt u de ingebouwde HKLM PSDrive met **locatie instellen**:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Vervolgens kunt u de '**.**' notatie voor de huidige locatie voor het weergeven van de eigenschappen zonder op te geven van een volledig pad:

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

Pad uitbreiding werkt hetzelfde als binnen het bestandssysteem, zodat u vanaf deze locatie downloaden kunt de **ItemProperty** weergeven voor **HKLM:\\SOFTWARE\\Microsoft\\Windows \\Help** met behulp van **Get ItemProperty-pad... \\Help**.

### <a name="getting-a-single-registry-entry"></a>Ophalen van een enkele registervermelding

Als u ophalen van een bepaald item in een registersleutel wilt, kunt u een van de verschillende mogelijke manieren. In dit voorbeeld wordt de waarde van **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.

Met behulp van **Get ItemProperty**, gebruiken de **pad** parameter om de naam van de sleutel en de **naam** parameter om de naam van de **DevicePath** vermelding.

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

Met deze opdracht retourneert de standaardeigenschappen in de Windows PowerShell, evenals de **DevicePath** eigenschap.

> [!NOTE]
> Hoewel **Get ItemProperty** heeft **Filter**, **opnemen**, en **uitsluiten** parameters, ze filteren op naam van eigenschap kunnen niet worden gebruikt. Deze parameters verwijzen naar registersleutels: die item paden zijn, en niet de registervermeldingen: welke eigenschappen van het item zijn.

Er is een andere optie het Reg.exe vanaf de opdrachtregel-hulpprogramma te gebruiken. Typ voor help met reg.exe **reg.exe /?** bij een opdrachtprompt. Ga voor de vermelding DevicePath reg.exe te gebruiken zoals wordt weergegeven in de volgende opdracht:

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

U kunt ook de **WshShell COM** object ook te vinden van sommige registervermeldingen, hoewel deze methode niet werkt met grote binaire gegevens of met de namen van de Register-vermeldingen die tekens zoals bevatten '\\'). Naam van de eigenschap toevoegen aan het pad van het item met een \\ scheidingsteken:

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a>Maken van nieuwe registervermeldingen

Een nieuwe vermelding met de naam 'PowerShellPath' toevoegen aan de **CurrentVersion** , sleutelgebruik **nieuw ItemProperty** met het pad naar de sleutel, naam van de vermelding en de waarde van het item. In dit voorbeeld wordt de waarde van de Windows PowerShell-variabele duurt **$PSHome**, waarin het pad naar de installatiemap voor Windows PowerShell wordt opgeslagen.

U kunt de nieuwe invoer toevoegen aan de sleutel met behulp van de volgende opdracht en de opdracht ook retourneert informatie over de nieuwe invoer:

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

De **PropertyType** moet de naam van een **Microsoft.Win32.RegistryValueKind** opsommingslid uit de volgende tabel:

|Het eigenschapstype waarde|Betekenis|
|----------------------|-----------|
|Binair|Binaire gegevens|
|DWord|Een getal dat een geldig UInt32|
|ExpandString|Een tekenreeks met omgevingsvariabelen die dynamisch worden uitgebreid|
|MultiString|Een tekenreeks met meerdere regels|
|Tekenreeks|Waarde van een tekenreeks|
|QWord|8 bytes met binaire gegevens|

> [!NOTE]
> U kunt een registervermelding naar meerdere locaties toevoegen door te geven van een matrix met waarden voor de **pad** parameter:

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

U kunt ook de waarde van een bestaande registervermelding overschrijven door toe te voegen de **Force** parameter aan een **nieuw ItemProperty** opdracht.

### <a name="renaming-registry-entries"></a>Registervermeldingen wijzigen

Naam wijzigen van de **PowerShellPath** vermelding 'PSHome', gebruik **Rename ItemProperty**:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Voeg de nieuwe naam als waarde wilt weergeven, de **PassThru** -parameter voor de opdracht.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>Registervermeldingen verwijderen

Gebruik voor het verwijderen van de PSHome en de PowerShellPath registervermeldingen **verwijderen ItemProperty**:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```