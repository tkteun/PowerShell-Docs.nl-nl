---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met bestanden en mappen werken
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: 393e886a4945222198d9b81019250c5d5b905ad3
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984388"
---
# <a name="working-with-files-and-folders"></a>Met bestanden en mappen werken

Navigeren door Windows PowerShell-stations en de items op deze bewerken is vergelijkbaar met het bewerken van bestanden en mappen op de fysieke schijven Windows. Deze sectie wordt beschreven hoe u omgaat met specifieke bestanden en mappen manipulatie taken-met behulp van PowerShell.

## <a name="listing-all-the-files-and-folders-within-a-folder"></a>Lijst van alle bestanden en mappen in een map

U kunt alle items rechtstreeks in een map ophalen met behulp van **Get-ChildItem**. Voeg de optionele **Force** parameter verborgen weergeven of items van system. Deze opdracht geeft bijvoorbeeld de directe inhoud van Windows PowerShell-station C (dit is hetzelfde als de fysieke Windows-station C):

```powershell
Get-ChildItem -Path C:\ -Force
```

De opdracht bevat alleen de rechtstreeks opgenomen items, net als met behulp van Cmd.exe **DIR** opdracht of **ls** in een UNIX-shell. Als u wilt de opgenomen items weergeven, moet u opgeven de **-Recurse** ook de parameter. (Dit kan een extreem lange tijd in beslag nemen.) Overzicht van alles op de C-station:

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

**Get-ChildItem** items kunt filteren op de **pad**, **Filter**, **opnemen**, en **uitsluiten** parameters, maar deze zijn Normaal gesproken alleen gebaseerd op de naam. U kunt uitvoeren met het complex filteren op basis van andere eigenschappen van items met behulp van **Where-Object**.

De volgende opdracht wordt gezocht naar alle uitvoerbare bestanden in de map Program Files die het laatst zijn gewijzigd na 1 oktober 2005 die wel en niet kleiner zijn dan 1 MB of groter is dan 10 MB:

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a>Kopiëren van bestanden en mappen

Kopiëren is klaar met **Copy-Item**. De volgende opdracht uit back-ups van C:\\boot.ini naar C:\\boot.bak:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

Als het doelbestand al bestaat, mislukt die poging kopiëren. Als u wilt overschrijven van een reeds bestaande bestemming, gebruikt u de **Force** parameter:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

Met deze opdracht werkt zelfs als de bestemming alleen-lezen is.

Map kopiëren werkt op dezelfde manier. Deze opdracht wordt de map C:\\temp\\test1 naar de nieuwe map C:\\temp\\DeleteMe recursief:

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

U kunt ook een selectie van items kopiëren. De volgende opdracht kopieert alle txt-bestanden die deel uitmaken van een willekeurige plaats c:\\gegevens naar c:\\temp\\tekst:

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

U kunt nog steeds andere hulpprogramma's gebruiken om uit te voeren bestandskopie van het systeem. XCOPY en ROBOCOPY COM-objecten, zoals de **Scripting.FileSystemObject,** alle werken in Windows PowerShell. Bijvoorbeeld, kunt u de Windows Script Host **Scripting.FileSystem COM** klasse back-up C:\\boot.ini naar C:\\boot.bak:

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a>Het maken van bestanden en mappen

Het maken van nieuwe items werkt hetzelfde voor alle Windows PowerShell-providers. Als een Windows PowerShell-provider meer dan één type item heeft, bijvoorbeeld, het bestandssysteem Windows PowerShell-provider wordt onderscheid gemaakt tussen de mappen en bestanden, moet u het itemtype opgeven.

Deze opdracht maakt u een nieuwe map C:\\temp\\nieuwe map:

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

Deze opdracht maakt u een nieuwe lege bestand C:\\temp\\nieuwe map\\bestand.txt

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a>Alle bestanden en mappen in een map verwijderen

Kunt u de opgenomen items met **Remove-Item**, maar u wordt gevraagd om te bevestigen van de verwijzing wordt verwijderd als het item iets anders bevat. Bijvoorbeeld, als u probeert te verwijderen van de map C:\\temp\\DeleteMe met andere items, Windows PowerShell wordt u gevraagd om bevestiging voordat u verwijdert de map:

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Als u niet elk ingesloten item worden gevraagd wilt, geeft u de **Recurse** parameter:

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a>Toewijzing van een lokale map als een toegankelijke Windows-station

U kunt ook een lokale map toewijzen met behulp van de **subst** opdracht. De volgende opdracht maakt een lokaal station die p: geroot in de lokale map Program Files:

```powershell
subst p: $env:programfiles
```

Net als bij stations, de stations die zijn toegewezen in met behulp van Windows PowerShell **subst** zijn direct zichtbaar zijn voor de Windows PowerShell-shell.

## <a name="reading-a-text-file-into-an-array"></a>Een tekstbestand lezen in een matrix

Een van de meest voorkomende opslagindelingen voor tekstgegevens zich in een bestand met afzonderlijke regels behandeld als afzonderlijke gegevenselementen. De **Get-inhoud** cmdlet kan worden gebruikt om een volledige bestand in één stap te lezen, zoals hier wordt weergegeven:

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

**Get-inhoud** al behandelt de gegevens lezen uit het bestand als een matrix, met één element per regel van de inhoud van bestand. U kunt dit bevestigen door het controleren van de **lengte** van de geretourneerde inhoud:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Met deze opdracht is vooral nuttig zijn voor het ophalen van lijsten met gegevens in Windows PowerShell direct. U kunt bijvoorbeeld een lijst van computernamen of IP-adressen opslaan in een bestand C:\\temp\\domainMembers.txt, met een naam op elke regel van het bestand. U kunt **Get-inhoud** voor het ophalen van inhoud van het bestand en plaats u ze in de variabele **$Computers**:

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** is nu een matrix met de naam van een computer in elk element.
