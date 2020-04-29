---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Windows PowerShell-stations beheren
ms.openlocfilehash: 5d1aba459caeaab2542e17e74534da6713b0faa9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "70215506"
---
# <a name="managing-windows-powershell-drives"></a>Windows PowerShell-stations beheren

Een *Windows Power Shell-station* is een gegevens opslag locatie die u kunt openen als een bestandssysteem station in Windows Power shell. De Windows Power shell-providers maken enkele stations voor u, zoals de bestandssysteem stations (inclusief C: en D:), de register stations (HKCU: en HKLM:) en het certificaat station (CERT:), en u kunt uw eigen Windows Power Shell-stations maken. Deze stations zijn erg nuttig, maar ze zijn alleen beschikbaar in Windows Power shell. U kunt ze niet openen met andere Windows-hulpprogram ma's, zoals bestanden Verkenner of Cmd. exe.

Windows Power Shell maakt gebruik van het zelfstandige naam woord, **PSDrive**, voor opdrachten die werken met Windows Power Shell-stations. Voor een lijst met Windows Power Shell-stations in uw Windows Power shell-sessie gebruikt u de cmdlet **Get-PSDrive** .

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

Hoewel de stations in de weer gave afhankelijk zijn van de stations op het systeem, ziet de vermelding er ongeveer uit als de uitvoer van de opdracht **Get-PSDrive** die hierboven wordt weer gegeven.

Bestandssysteem stations zijn een subset van de Windows Power Shell-stations. U kunt de bestandssysteem stations identificeren met de vermelding bestands systeem in de kolom provider. (De bestandssysteem stations in Windows Power shell worden ondersteund door de Windows Power shell-systeem provider.)

Als u de syntaxis van de cmdlet **Get-PSDrive** wilt weer geven, typt u een **Get-opdracht** opdracht met de **syntaxis** parameter:

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

Met de para meter **PSProvider** kunt u alleen de Windows Power Shell-stations weer geven die door een bepaalde provider worden ondersteund. Als u bijvoorbeeld alleen de Windows Power Shell-stations wilt weer geven die worden ondersteund door de Windows Power shell-bestandssysteem provider, typt u de opdracht **Get-PSDrive** met de para meter **PSProvider** en de waarde van het **Bestands systeem** :

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Als u de Windows Power Shell-stations wilt weer geven die register onderdelen vertegenwoordigen, gebruikt u de para meter **PSProvider** om alleen de Windows Power Shell-stations weer te geven die worden ondersteund door de Windows Power shell-register provider:

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

U kunt ook de standaard locatie-cmdlets gebruiken met de Windows Power Shell-stations:

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Nieuwe Windows Power Shell-stations toevoegen (New-PSDrive)

U kunt uw eigen Windows Power Shell-stations toevoegen met behulp van de opdracht **New-PSDrive** . Als u de syntaxis voor de opdracht **New-PSDrive** wilt ophalen, voert u de opdracht **Get-opdracht** in met de **syntaxis** parameter:

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Als u een nieuw Windows Power Shell-station wilt maken, moet u drie para meters opgeven:

- Een naam voor het station (u kunt elke geldige Windows Power shell-naam gebruiken)

- De PSProvider (gebruik ' File System ' voor bestandssysteem locaties en ' Registry ' voor register locaties)

- De basis, dat wil zeggen, het pad naar de hoofdmap van het nieuwe station

U kunt bijvoorbeeld een station met de naam ' Office ' maken dat is toegewezen aan de map die de Microsoft Office toepassingen op uw computer bevat, zoals **C:\\Program\\Files Microsoft Office\\Office11**. Typ de volgende opdracht om het station te maken:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Microsoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> In het algemeen zijn paden niet hoofdletter gevoelig.

U verwijst naar het nieuwe Windows Power Shell-station, net zoals u alle Windows Power Shell-stations gebruikt, door de naam gevolgd door een dubbele punt (**:**).

Een Windows Power Shell-station kan veel taken veel eenvoudiger maken. Enkele van de belangrijkste sleutels in het Windows-REGI ster hebben bijvoorbeeld extreem lange paden, waardoor ze lastig toegankelijk zijn en moeilijk te onthouden zijn. Essentiële configuratie-informatie bevindt zich onder **HKEY_LOCAL_MACHINE\\-software\\micro soft\\Windows\\CurrentVersion**. Als u items in de sleutel CurrentVersion wilt bekijken en wijzigen, kunt u een Windows Power Shell-station maken dat in die sleutel is geroot door het volgende te typen:

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\Windows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

U kunt de locatie wijzigen in de **cvkey:** station, net zoals u dat zou doen met een ander station:

```
PS> cd cvkey:
```

of:

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

Met de cmdlet New-PsDrive wordt het nieuwe station alleen toegevoegd aan de huidige Windows Power shell-sessie. Als u het Windows Power shell-venster sluit, gaat het nieuwe station verloren. Als u een Windows Power Shell-station wilt opslaan, gebruikt u de cmdlet Export-console om de huidige Windows Power shell-sessie te exporteren. vervolgens gebruikt u de para meter **PSConsoleFile** van Power shell. exe om deze te importeren. U kunt ook het nieuwe station toevoegen aan uw Windows Power shell-profiel.

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Windows Power Shell-stations verwijderen (Remove-PSDrive)

U kunt stations verwijderen uit Windows Power shell met behulp van de cmdlet **Remove-PSDrive** . De cmdlet **Remove-PSDrive** is eenvoudig te gebruiken. Als u een specifiek Windows Power Shell-station wilt verwijderen, geeft u gewoon de naam van het Windows Power Shell-station op.

Als u bijvoorbeeld het **Office:** Windows Power Shell-station hebt toegevoegd, zoals wordt weer gegeven in het onderwerp **New-PSDrive** , kunt u het verwijderen door het volgende te typen:

```powershell
Remove-PSDrive -Name Office
```

Als u het **cvkey:** Windows Power Shell-station, dat ook wordt weer gegeven in het onderwerp **New-PSDrive** , wilt verwijderen, gebruikt u de volgende opdracht:

```powershell
Remove-PSDrive -Name cvkey
```

Het is eenvoudig om een Windows Power Shell-station te verwijderen, maar u kunt het niet verwijderen terwijl u zich in het station bevindt. Bijvoorbeeld:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a>Stations toevoegen en verwijderen buiten Windows Power shell

Windows Power shell detecteert bestandssysteem stations die worden toegevoegd of verwijderd in Windows, met inbegrip van netwerk stations die zijn toegewezen, USB-stations die zijn aangesloten en stations die worden verwijderd met behulp van de opdracht **net use** of de methoden **WScript. NetworkMapNetworkDrive** en **RemoveNetworkDrive** van een Windows Script Host (WSH)-script.
