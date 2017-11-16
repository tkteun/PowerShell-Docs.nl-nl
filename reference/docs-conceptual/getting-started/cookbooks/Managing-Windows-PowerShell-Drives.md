---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het beheren van Windows PowerShell-stations
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: e2908246bb584291f04b67dc8635caec93d3b72e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="managing-windows-powershell-drives"></a>Het beheren van Windows PowerShell-stations
Een *Windows PowerShell-station* is een locatie voor het opslaan van gegevens waartoe u toegang hebt, zoals een station file system in Windows PowerShell. De Windows PowerShell-providers stations voor u te maken, zoals het bestandssysteem stations (inclusief C: en D:), het register stations (HKCU: en HKLM:), en het station van het certificaat (Cert:), en u uw eigen Windows PowerShell-schijven kunt maken. Deze stations zeer nuttig zijn, maar ze zijn alleen beschikbaar in Windows PowerShell. U kunt ze niet openen met behulp van andere Windows-hulpprogramma's, zoals Windows Verkenner of Cmd.exe.

Windows PowerShell maakt gebruik van het zelfstandig naamwoord, **PSDrive**, voor opdrachten die met Windows PowerShell werken-stations. Voor een lijst van de Windows PowerShell-stations in uw Windows PowerShell-sessie, kunt u via de **Get-PSDrive** cmdlet.

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

Hoewel de stations in de weergave naargelang de schijven op uw systeem verschillen, de vermelding ziet er ongeveer als de uitvoer van de **Get-PSDrive** opdracht hierboven weergegeven.

Bestand systeemstations zijn een subset van de Windows PowerShell-stations. U kunt het bestand systeemstations door het bestandssysteem item in de kolom Provider identificeren. (De stations file system in Windows PowerShell worden ondersteund door het bestandssysteem van Windows PowerShell-provider.)

Om te zien van de syntaxis van de **Get-PSDrive** cmdlet, typ een **Get-Command** opdracht met de **syntaxis** parameter:

```
PS> Get-Command -Name Get-PSDrive -Syntax
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

De **PSProvider** parameter kunt u alleen de Windows PowerShell-stations die worden weergegeven door een bepaalde provider worden ondersteund. Bijvoorbeeld, als u wilt weergeven in de Windows PowerShell-stations die worden ondersteund door het bestandssysteem van Windows PowerShell-provider, typ een **Get-PSDrive** opdracht met de **PSProvider** parameter en de  **Bestandssysteem** waarde:

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Als u wilt weergeven in de Windows PowerShell-stations die registeronderdelen vertegenwoordigen, gebruiken de **PSProvider** parameter zodat alleen de Windows PowerShell-stations die worden weergegeven door het register van Windows PowerShell-provider worden ondersteund:

<pre>PS> Get-PSDrive -PSProvider Registry
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE</pre>

U kunt ook de standaard locatie cmdlets met de Windows PowerShell-stations gebruiken:

<pre>PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location
Path
----
HKLM:\SOFTWARE\Microsoft</pre>

### <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Toevoegen van nieuwe Windows PowerShell-schijven (nieuwe PSDrive)
U kunt uw eigen Windows PowerShell-stations toevoegen met behulp van de **nieuw PSDrive** opdracht. Ophalen van de syntaxis voor de **nieuw PSDrive** opdracht, voert u de **Get-Command** opdracht met de **syntaxis** parameter:

```
PS> Get-Command -Name New-PSDrive -Syntax
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Een nieuwe Windows PowerShell-station wilt maken, moet u drie parameters opgeven:

- Een naam voor station (u kunt geldige naam voor de Windows PowerShell gebruiken)

- De PSProvider (gebruik 'Bestandssysteem' voor de locaties van systeem en 'Register' voor registerlocaties)

- De hoofdmap, dat wil zeggen, het pad naar de hoofdmap van het nieuwe station

Bijvoorbeeld, kunt u een station met de naam 'Office' die is toegewezen aan de map met de Microsoft Office-toepassingen op uw computer, zoals **C:\\Program Files\\Microsoft Office\\OFFICE11**. Het station wilt maken, typ de volgende opdracht:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> In het algemeen zijn paden niet hoofdlettergevoelig.

U verwijzen naar de nieuwe Windows PowerShell-station als u alle stations van Windows PowerShell: door de naam gevolgd door een dubbele punt (**:**).

Een Windows PowerShell-station kunt vele taken die veel eenvoudiger maken. Sommige van de belangrijkste sleutels in het Windows-register hebben bijvoorbeeld extreem lange paden, waardoor ze omslachtige voor toegang en moeilijk te onthouden. Essentiële configuratie-informatie zich bevindt onder **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**. Als u wilt weergeven en wijzigen van items in de registersleutel CurrentVersion, kunt u een Windows PowerShell-station dat is geroot in deze sleutel door te typen:

<pre>PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...</pre>

U kunt vervolgens de locatie waar u wilt wijzigen de **cvkey:** station net als elk ander station:''

`PS> cd cvkey:`

of:

<pre>PS> Set-Location cvkey: -PassThru
Path
----
cvkey:\</pre>

De cmdlet New-PsDrive voegt het nieuwe station alleen aan de huidige Windows PowerShell-sessie. Als u de Windows PowerShell-venster sluit, wordt het nieuwe station verloren. Als u wilt opslaan op een Windows PowerShell-station, gebruikt u de cmdlet Export-Console voor het exporteren van de huidige Windows PowerShell-sessie en gebruik vervolgens de PowerShell.exe **PSConsoleFile** parameter te importeren. Of het nieuwe station toevoegen aan uw Windows PowerShell-profiel.

### <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Verwijderen van Windows PowerShell-schijven (Remove-PSDrive)
U kunt schijven uit de Windows PowerShell verwijderen met behulp van de **verwijderen PSDrive** cmdlet. De **verwijderen PSDrive** cmdlet is eenvoudig te gebruiken; voor het verwijderen van een specifieke Windows PowerShell-station u gewoon de naam van de Windows PowerShell-station.

Bijvoorbeeld, als u hebt toegevoegd de **Office:** Windows PowerShell-station, zoals wordt weergegeven in de **nieuw PSDrive** onderwerp, kunt u deze verwijderen door te typen:

```
PS> Remove-PSDrive -Name Office
```

Verwijderen van de **cvkey:** Windows PowerShell-station, ook weergegeven in de **nieuw PSDrive** onderwerp, gebruik de volgende opdracht:

```
PS> Remove-PSDrive -Name cvkey
```

Het is gemakkelijk om te verwijderen van een Windows PowerShell-station, maar u kunt deze niet verwijderen terwijl u in het station bent. Bijvoorbeeld:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

### <a name="adding-and-removing-drives-outside-windows-powershell"></a>Toevoegen en verwijderen van schijven buiten Windows PowerShell
Windows PowerShell detecteert bestand systeemstations die worden toegevoegd of verwijderd in Windows, inclusief stations die zijn toegewezen, USB-stations die zijn gekoppeld en stations die zijn verwijderd met behulp van de **gebruik net** opdracht of het  **WScript.NetworkMapNetworkDrive** en **RemoveNetworkDrive** methoden van een script dat Windows Script Host (WSH).

