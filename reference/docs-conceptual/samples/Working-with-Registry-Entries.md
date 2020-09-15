---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Met registervermeldingen werken
ms.openlocfilehash: 7f8ee87cebb8b220570bcb969445071a72a68526
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/04/2020
ms.locfileid: "87758479"
---
# <a name="working-with-registry-entries"></a>Met registervermeldingen werken

Omdat Register vermeldingen eigenschappen van sleutels zijn en, als zodanig, niet rechtstreeks kunnen worden doorzocht, moeten we een iets andere benadering nemen wanneer ze ermee werken.

## <a name="listing-registry-entries"></a>Register vermeldingen weer geven

Er zijn veel verschillende manieren om Register vermeldingen te controleren. De eenvoudigste manier is om de namen van de eigenschappen van een sleutel op te halen. Als u bijvoorbeeld de namen van de vermeldingen in de register sleutel wilt weer geven `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion` , gebruikt u `Get-Item` . Register sleutels hebben een eigenschap met de algemene naam ' Property ' die een lijst met Register vermeldingen in de sleutel is.
Met de volgende opdracht wordt de eigenschap Property geselecteerd en worden de items uitgevouwen zodat deze in een lijst worden weer gegeven:

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Als u de Register vermeldingen in een meer Lees bare vorm wilt weer geven, gebruikt u `Get-ItemProperty` :

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
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

De Windows Power shell-gerelateerde eigenschappen voor de sleutel worden allemaal voorafgegaan door "PS", zoals **PSPath**, **PSParentPath**, **PSChildName**en **PSProvider**.

U kunt de `*.*` notatie gebruiken voor het verwijzen naar de huidige locatie. U kunt gebruiken `Set-Location` om eerst naar de **CurrentVersion** -register container te overschakelen:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

U kunt ook het ingebouwde HKLM-PSDrive gebruiken met `Set-Location` :

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

U kunt vervolgens de `*.*` notatie voor de huidige locatie gebruiken om de eigenschappen weer te geven zonder een volledig pad op te gave:

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

Pad-uitbrei ding werkt op dezelfde manier als in het bestands systeem, dus vanaf deze locatie kunt u de **item Property** -vermelding voor `HKLM:\SOFTWARE\Microsoft\Windows\Help` gebruiken met behulp van `Get-ItemProperty -Path ..\Help` .

## <a name="getting-a-single-registry-entry"></a>Eén register vermelding ophalen

Als u een specifieke vermelding in een register sleutel wilt ophalen, kunt u een van de verschillende mogelijke benaderingen gebruiken. In dit voor beeld wordt gezocht naar de waarde van **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion` .

`Get-ItemProperty`Gebruik met de para meter **Path** om de naam van de sleutel op te geven en de para meter **name** om de naam van het item **DevicePath** op te geven.

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

Met deze opdracht worden de standaard eigenschappen van Windows Power shell en de eigenschap **DevicePath** geretourneerd.

> [!NOTE]
> Hoewel de `Get-ItemProperty` para meters **filter**, **include**en **exclude** zijn, kunnen ze niet worden gebruikt om te filteren op naam van eigenschap. Deze para meters verwijzen naar register sleutels, die item paden zijn en geen register vermeldingen, die item eigenschappen zijn.

Een andere optie is het gebruik van het Reg.exe opdracht regel programma. Voor hulp bij reg.exe, typt u `reg.exe /?` bij een opdracht prompt. Als u de vermelding DevicePath wilt vinden, gebruikt u reg.exe zoals weer gegeven in de volgende opdracht:

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

U kunt ook het COM-object **WshShell** gebruiken om enkele register vermeldingen te vinden, hoewel deze methode niet werkt met grote binaire gegevens of met namen van Register vermeldingen die tekens bevatten zoals " \\ "). Voeg de naam van de eigenschap toe aan het pad van het item met een \\ scheidings teken:

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a>Eén register vermelding instellen

Als u een specifieke vermelding in een register sleutel wilt wijzigen, kunt u een van de verschillende mogelijke benaderingen gebruiken. In dit voor beeld wordt de invoer van het **pad** in gewijzigd `HKEY_CURRENT_USER\Environment` . De **pad** -vermelding geeft aan waar uitvoer bare bestanden moeten worden gevonden.

1. Haal de huidige waarde van het **pad** op met behulp van `Get-ItemProperty` .
2. Voeg de nieuwe waarde toe, gescheiden met een `;` .
3. Gebruik `Set-ItemProperty` met de opgegeven sleutel, vermeldings naam en waarde om de register vermelding te wijzigen.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> Hoewel de `Set-ItemProperty` para meters **filter**, **include**en **exclude** zijn, kunnen ze niet worden gebruikt om te filteren op naam van eigenschap. Deze para meters verwijzen naar register sleutels, die item paden zijn, en geen register vermeldingen, die item eigenschappen zijn.

Een andere optie is het gebruik van het Reg.exe opdracht regel programma. Voor hulp bij reg.exe, typt u **reg.exe/?**
bij een opdrachtprompt.

In het volgende voor beeld wordt de invoer van het **pad** gewijzigd door het pad dat in bovenstaand voor beeld is toegevoegd, te verwijderen.
`Get-ItemProperty` wordt nog steeds gebruikt voor het ophalen van de huidige waarde om te voor komen dat de geretourneerde teken reeks moet worden geparseerd `reg query` . De **subtekenreeks** -en **LastIndexOf** -methoden worden gebruikt voor het ophalen van het laatste pad dat is toegevoegd aan het **pad** .

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a>Nieuwe register vermeldingen maken

Als u een nieuwe vermelding met de naam "PowerShellPath" wilt toevoegen aan de **CurrentVersion** -sleutel, gebruikt u `New-ItemProperty` met het pad naar de sleutel, de naam van de vermelding en de waarde van de vermelding. In dit voor beeld nemen we de waarde van de Windows Power shell-variabele op `$PSHome` , waarmee het pad naar de installatiemap voor Windows Power shell wordt opgeslagen.

U kunt de nieuwe vermelding toevoegen aan de sleutel met behulp van de volgende opdracht, en de opdracht retourneert ook informatie over de nieuwe vermelding:

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

De **Property type** moet de naam zijn van een **micro soft. Win32. RegistryValueKind** -opsommings element uit de volgende tabel:

|Waarde Property type|Betekenis|
|----------------------|-----------|
|Binair|Binaire gegevens|
|32|Een getal dat een geldige UInt32 is|
|ExpandString|Een teken reeks die omgevings variabelen kan bevatten die dynamisch worden uitgevouwen|
|Fixedlength|Een teken reeks met meerdere regels|
|Tekenreeks|Elke tekenreekswaarde|
|QWord|8 bytes aan binaire gegevens|

> [!NOTE]
> U kunt een register vermelding toevoegen aan meerdere locaties door een matrix met waarden op te geven voor de para meter **Path** :

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

U kunt ook een vooraf bestaande register vermelding overschrijven door de para meter **Force** toe te voegen aan een `New-ItemProperty` opdracht.

## <a name="renaming-registry-entries"></a>Naam wijzigen van Register vermeldingen

Als u de naam van de **PowerShellPath** -vermelding wilt wijzigen in ' PSHome ', gebruikt u `Rename-ItemProperty` :

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Als u de hernoemde waarde wilt weer geven, voegt u de para meter **PassThru** toe aan de opdracht.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a>Register vermeldingen verwijderen

Als u de Register vermeldingen PSHome en PowerShellPath wilt verwijderen, gebruikt u `Remove-ItemProperty` :

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
