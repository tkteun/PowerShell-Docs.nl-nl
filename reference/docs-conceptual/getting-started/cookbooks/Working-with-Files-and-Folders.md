---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met bestanden en mappen werken
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: e47ea00c9d90d7e04a7af0cb1348849410a6e357
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-files-and-folders"></a>Met bestanden en mappen werken

Navigeren door Windows PowerShell-stations en bewerken van de items op deze lijkt op het manipuleren van bestanden en mappen op de fysieke schijven Windows. Het omgaan met specifieke bestanden en mappen manipulatie taken in deze sectie worden besproken.

### <a name="listing-all-the-files-and-folders-within-a-folder"></a>Lijst van alle bestanden en mappen in een map

U kunt alle items rechtstreeks in een map verkrijgen door middel van **Get-ChildItem**. Voeg de optionele **Force** parameter worden verborgen items van system. Deze opdracht geeft bijvoorbeeld de inhoud direct van Windows PowerShell-station C (dit is hetzelfde als het fysieke Windows-station C):

```powershell
Get-ChildItem -Force C:\
```

De opdracht bevat alleen de rechtstreeks opgenomen items, vergelijkbaar met behulp van Cmd.exe **DIR** opdracht of **ls** in een UNIX-shell. Om te geven opgenomen items, moet u opgeven de **-Recurse** ook de parameter. (Dit kan een zeer lange tijd in beslag nemen.) Overzicht van alles op het station C:

```powershell
Get-ChildItem -Force C:\ -Recurse
```

**Get-ChildItem** kunt items filteren met de **pad**, **Filter**, **opnemen**, en **uitsluiten** parameters, maar deze zijn Normaal gesproken alleen gebaseerd op naam. U kunt uitvoeren complexe filteren op basis van andere eigenschappen van items door **Where-Object**.

De volgende opdracht wordt gezocht naar alle uitvoerbare bestanden in de map Program Files die het laatst zijn gewijzigd na 1 oktober 2005 en die niet kleiner is dan 1 MB noch groter dan 10 MB zijn:

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

### <a name="copying-files-and-folders"></a>Kopiëren van bestanden en mappen

Kopiëren is klaar met **Copy-Item**. De volgende opdracht maakt een back-up C:\\boot.ini naar C:\\boot.bak:

```powershell
Copy-Item -Path c:\boot.ini -Destination c:\boot.bak
```

Als het doelbestand al bestaat, mislukt die poging kopiëren. Om een bestaande bestemming overschrijven, gebruikt u de parameter Force:

```powershell
Copy-Item -Path c:\boot.ini -Destination c:\boot.bak -Force
```

Met deze opdracht werkt zelfs wanneer het doel alleen-lezen is.

Werkt op dezelfde manier map kopiëren. Deze opdracht kopieert u de map C:\\temp\\test1 naar de nieuwe map c:\\temp\\DeleteMe recursief:

```powershell
Copy-Item C:\temp\test1 -Recurse c:\temp\DeleteMe
```

U kunt ook een selectie van items kopiëren. De volgende opdracht kopieert alle txt-bestanden die zich ergens in c:\\gegevens naar c:\\temp\\tekst:

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination c:\temp\text
```

U kunt nog steeds andere hulpprogramma's gebruiken om systeem te bestand kopiëren. XCOPY en ROBOCOPY COM-objecten, zoals de **Scripting.FileSystemObject,** werkt met alle in Windows PowerShell. Bijvoorbeeld, kunt u Windows Script Host **Scripting.FileSystem COM** klasse back-up C:\\boot.ini naar C:\\boot.bak:

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('c:\boot.ini', 'c:\boot.bak')
```

### <a name="creating-files-and-folders"></a>Bestanden en mappen maken

Maken van nieuwe items werkt op dezelfde op alle Windows PowerShell-providers. Als een Windows PowerShell-provider meer dan één type item heeft, bijvoorbeeld, het bestandssysteem Windows PowerShell-provider wordt onderscheid gemaakt tussen de mappen en bestanden, moet u het itemtype opgeven.

Deze opdracht maakt u een nieuwe map C:\\temp\\nieuwe map:

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

Deze opdracht maakt u een nieuwe lege bestand C:\\temp\\nieuwe map\\bestand.txt

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

### <a name="removing-all-files-and-folders-within-a-folder"></a>Alle bestanden en mappen in een map verwijderen

U kunt verwijderen opgenomen items met **Item verwijderen**, maar u wordt gevraagd om te bevestigen dat de verwijzing wordt verwijderd als het item iets anders bevat. Bijvoorbeeld, als u probeert te verwijderen van de map C:\\temp\\DeleteMe die andere items bevat, Windows PowerShell wordt u gevraagd om bevestiging voordat u de map te verwijderen:

```
Remove-Item C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Als u niet worden gevraagd om elk item opgenomen wilt, geeft u de **Recurse** parameter:

```powershell
Remove-Item C:\temp\DeleteMe -Recurse
```

### <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a>Toewijzing van een lokale map als Windows toegankelijk station

U kunt ook een lokale map toewijzen met behulp van de **subst** opdracht. De volgende opdracht maakt een lokaal station die p: geroot in de lokale map Program Files:

```powershell
subst p: $env:programfiles
```

Net als bij netwerkstations, de stations die zijn toegewezen binnen met behulp van Windows PowerShell **subst** zijn direct zichtbaar voor de Windows PowerShell-shell.

### <a name="reading-a-text-file-into-an-array"></a>Een tekstbestand lezen in een matrix

Een van de meest voorkomende opslagindelingen voor tekstgegevens is in een bestand met afzonderlijke regels behandeld als verschillende gegevenselementen. De **Get-inhoud** cmdlet kan worden gebruikt om te lezen van een volledig bestand mogelijk in één stap, zoals hier wordt weergegeven:

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

**Get-inhoud** al behandelt de gegevens lezen uit het bestand als een matrix met één element per regel van de inhoud van bestand. U kunt dit bevestigen door het controleren van de **lengte** van de geretourneerde inhoud:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Met deze opdracht is vooral handig voor het rechtstreeks ophalen van de lijsten met gegevens in Windows PowerShell. Bijvoorbeeld, u een lijst met computernamen of IP-adressen mogelijk opslaan in een bestand C:\\temp\\domainMembers.txt met een naam op elke regel van het bestand. U kunt **Get-inhoud** inhoud van het bestand ophalen en plaatsen in de variabele **$Computers**:

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** is nu een matrix met de naam van een computer in elk element.