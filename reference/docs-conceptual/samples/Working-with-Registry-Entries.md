---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met registervermeldingen werken
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 8483b6f98739697b24a13055dfffbc7b5bacc2cc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686808"
---
# <a name="working-with-registry-entries"></a>Met registervermeldingen werken

Omdat de registervermeldingen zijn eigenschappen van sleutels en, als zodanig kunnen niet worden rechtstreeks gebladerd, moet een lichtjes andere benadering nemen bij het werken met hen.

### <a name="listing-registry-entries"></a>Registervermeldingen van aanbieding

Er zijn veel verschillende manieren om te onderzoeken registervermeldingen. De eenvoudigste manier is om op te halen van de namen van eigenschappen die zijn gekoppeld aan een sleutel. Bijvoorbeeld, om te zien van de namen van de vermeldingen in de registersleutel `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, gebruikt u `Get-Item`. Registersleutels hebben een eigenschap met de algemene naam van 'Eigenschap' die een lijst met vermeldingen in de sleutel is.
De volgende opdracht uit de eigenschap selecteert en de items wordt uitgebreid zodat ze worden weergegeven in een lijst:

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

U kunt de registervermeldingen weergeven in een beter leesbare vorm, met `Get-ItemProperty`:

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

De Windows PowerShell-eigenschappen voor de sleutel worden alle voorafgegaan door 'PS', zoals **PSPath**, **PSParentPath**, **PSChildName**, en **PSProvider** .

U kunt de `*.*` notatie voor verwijzen naar de huidige locatie. U kunt `Set-Location` wijzigen in de **CurrentVersion** container registry eerste:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

U kunt ook kunt u de ingebouwde HKLM PSDrive met `Set-Location`:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Vervolgens kunt u de `*.*` notatie voor de huidige locatie om de eigenschappen zonder op te geven van een volledig pad:

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

Pad uitbreiding werkt hetzelfde als in het bestandssysteem, zodat u vanaf deze locatie krijgt u de **ItemProperty** aanbieding voor `HKLM:\SOFTWARE\Microsoft\Windows\Help` met behulp van `Get-ItemProperty -Path ..\Help`.

### <a name="getting-a-single-registry-entry"></a>Een enkel register-item ophalen

Als u ophalen van een bepaalde vermelding in een registersleutel wilt, kunt u een van verschillende mogelijke methoden. In dit voorbeeld wordt gezocht naar de waarde van **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.

Met behulp van `Get-ItemProperty`, gebruikt u de **pad** parameter opgeven voor de naam van de sleutel en de **naam** parameter opgeven voor de naam van de **DevicePath** vermelding.

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

Met deze opdracht retourneert de standaardeigenschappen van Windows PowerShell, evenals de **DevicePath** eigenschap.

> [!NOTE]
> Hoewel `Get-ItemProperty` heeft **Filter**, **opnemen**, en **uitsluiten** parameters, ze om te filteren op naam van de eigenschap kunnen niet worden gebruikt. Deze parameters verwijzen naar registersleutels, item paden en geen vermeldingen in het register. De registervermeldingen die eigenschappen van het item.

Een andere optie is het gebruik van het hulpprogramma Reg.exe vanaf de opdrachtregel. Typ voor help met reg.exe `reg.exe /?` achter de opdrachtprompt. Als u de vermelding DevicePath zoekt, gebruikt u reg.exe zoals wordt weergegeven in de volgende opdracht uit:

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

U kunt ook de **WshShell** COM-object ook te vinden van sommige registervermeldingen, hoewel deze methode niet werkt met grote binaire gegevens of met de namen van de Register-vermeldingen die tekens zoals bevatten '\\'). Naam van de eigenschap toevoegen aan het pad van het item met een \\ scheidingsteken:

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

### <a name="setting-a-single-registry-entry"></a>Instellen van een enkel register-item

Als u wijzigen van een bepaalde vermelding in een registersleutel wilt, kunt u een van verschillende mogelijke methoden gebruiken. In dit voorbeeld wijzigt de **pad** item onder `HKEY_CURRENT_USER\Environment`. De **pad** vermelding wordt opgegeven waar zich uitvoerbare bestanden.

1. Ophalen van de huidige waarde van de **pad** met behulp van vermelding `Get-ItemProperty`.
2. Voeg de nieuwe waarde, scheiden met een `;`.
3. Gebruik `Set-ItemProperty` met de opgegeven sleutel, naam en waarde te wijzigen van het register-item.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> Hoewel `Set-ItemProperty` heeft **Filter**, **opnemen**, en **uitsluiten** parameters, ze om te filteren op naam van de eigenschap kunnen niet worden gebruikt. Deze parameters verwijzen naar registersleutels: item paden zijn, en niet de registervermeldingen: welke eigenschappen van het item zijn.

Een andere optie is het gebruik van het hulpprogramma Reg.exe vanaf de opdrachtregel. Typ voor help met reg.exe **reg.exe /?**
bij een opdrachtprompt.

Het volgende voorbeeld van de wijzigingen de **pad** vermelding door het verwijderen van het pad dat is toegevoegd in het bovenstaande voorbeeld.
`Get-ItemProperty` nog steeds wordt gebruikt om op te halen van de huidige waarde om te voorkomen dat de tekenreeks die is geretourneerd door parseren `reg query`. De **subtekenreeks** en **LastIndexOf** methoden worden gebruikt voor het ophalen van het laatste pad toegevoegd aan de **pad** vermelding.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

### <a name="creating-new-registry-entries"></a>Het maken van nieuwe registervermeldingen

Een nieuwe vermelding met de naam 'PowerShellPath' toevoegen aan de **CurrentVersion** , sleutelgebruik `New-ItemProperty` met het pad naar de sleutel, naam van de vermelding en de waarde van het item. In dit voorbeeld wordt de waarde van de Windows PowerShell-variabele duurt `$PSHome`, waarin het pad naar de installatiemap voor Windows PowerShell wordt opgeslagen.

U kunt het nieuwe item toevoegen aan de sleutel met behulp van de volgende opdracht en de opdracht retourneert ook informatie over het nieuwe item:

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

De **%d{PropertyType/** moet de naam van een **Microsoft.Win32.RegistryValueKind** lid van de opsomming van de volgende tabel:

|%D{PropertyType/ waarde|Betekenis|
|----------------------|-----------|
|Binair|Binaire gegevens|
|DWord|Een getal dat is een geldige UInt32|
|ExpandString|Een tekenreeks is die u kunt omgevingsvariabelen die dynamisch worden uitgebreid bevatten|
|MultiString|Een tekenreeks met meerdere regels|
|Tekenreeks|Een string-waarde|
|QWord|8 bytes van binaire gegevens|

> [!NOTE]
> U kunt een registervermelding toevoegen aan meerdere locaties door te geven van een matrix met waarden voor de **pad** parameter:

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

U kunt ook een bestaande vermelding registerwaarde overschrijven door toe te voegen de **Force** parameter aan een `New-ItemProperty` opdracht.

### <a name="renaming-registry-entries"></a>Naam van de registervermeldingen

Naam wijzigen van de **PowerShellPath** vermelding "PSHome," Gebruik `Rename-ItemProperty`:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

De nieuwe naam als waarde wilt weergeven, toevoegen de **PassThru** parameter aan de opdracht.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>Registervermeldingen verwijderen

Als u wilt de PSHome en PowerShellPath registervermeldingen verwijderen, gebruikt u `Remove-ItemProperty`:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
