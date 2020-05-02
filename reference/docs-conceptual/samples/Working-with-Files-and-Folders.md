---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Met bestanden en mappen werken
ms.openlocfilehash: 8876ff70adbd10c9019f6d80ce7ad327f2932c74
ms.sourcegitcommit: 08acbea14c69a347f2f46aafcb215a5233c7d830
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/01/2020
ms.locfileid: "82691488"
---
# <a name="working-with-files-and-folders"></a>Met bestanden en mappen werken

Het navigeren door Windows Power Shell-stations en het bewerken van de items hierop is vergelijkbaar met het bewerken van bestanden en mappen op fysieke Windows-schijf stations. In deze sectie wordt beschreven hoe u specifieke bewerkingen voor het bewerken van bestanden en mappen kunt uitvoeren met behulp van Power shell.

## <a name="listing-all-the-files-and-folders-within-a-folder"></a>Alle bestanden en mappen in een map weer geven

U kunt alle items rechtstreeks in een map ophalen met behulp `Get-ChildItem`van. Voeg de optionele **Force** -para meter toe om verborgen of systeem items weer te geven. Met deze opdracht wordt bijvoorbeeld de directe inhoud van Windows Power Shell-station C weer gegeven (dit is hetzelfde als de fysieke schijf met Windows C):

```powershell
Get-ChildItem -Path C:\ -Force
```

Met `Cmd.exe`de opdracht worden alleen de direct opgenomen items weer gegeven, net `DIR` zoals de `ls` opdracht of in een Unix-shell. Als u opgenomen items wilt weer geven, moet u ook de `-Recurse` para meter opgeven. (Dit kan een zeer lange tijd duren.) Alles op station C weer geven:

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

`Get-ChildItem`kan items filteren met de para meters **Path**, **filter**, **include**en **exclude** , maar deze zijn meestal alleen gebaseerd op naam. U kunt complexe filtering uitvoeren op basis van andere eigenschappen van items `Where-Object`met behulp van.

Met de volgende opdracht worden alle uitvoer bare bestanden in de map Program Files gevonden die voor het laatst zijn gewijzigd na 1 oktober 2005 en die kleiner zijn dan 1 MB of groter dan 10 MB:

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a>Kopiëren van bestanden en mappen

Kopiëren is voltooid met `Copy-Item`. Met de volgende opdracht maakt u een back\\-up van c: boot\\. ini naar c: boot. bak:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

Als het doel bestand al bestaat, mislukt de poging tot kopiëren. Als u een bestaande bestemming wilt overschrijven, gebruikt u de para meter **Force** :

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

Deze opdracht werkt zelfs als de bestemming alleen-lezen is.

Kopiëren van mappen werkt op dezelfde manier. Met deze opdracht wordt de `C:\temp\test1` map recursief naar `C:\temp\DeleteMe` de nieuwe map gekopieerd:

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

U kunt ook een selectie van items kopiëren. Met de volgende opdracht kopieert u alle txt-bestanden die `C:\data` zich `C:\temp\text`overal in naar bevinden:

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

U kunt nog steeds andere hulpprogram ma's gebruiken om bestandssysteem kopieën uit te voeren. XCOPY-, ROBOCOPY-en COM-objecten, zoals **Scripting. File System object,** werken allemaal in Windows Power shell. U kunt bijvoorbeeld de Windows Script Host **Scripting. COM-klasse scripts** gebruiken om een back- `C:\boot.ini` up `C:\boot.bak`te maken naar:

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a>Bestanden en mappen maken

Het maken van nieuwe items werkt hetzelfde op alle Windows Power shell-providers. Als een Windows Power shell-provider meer dan één type item heeft, bijvoorbeeld het bestands systeem van de Windows Power shell-provider onderscheidt tussen mappen en bestanden, moet u het item type opgeven.

Met deze opdracht maakt u een `C:\temp\New Folder`nieuwe map:

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

Met deze opdracht maakt u een nieuw leeg bestand`C:\temp\New Folder\file.txt`

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

> [!IMPORTANT]
> Wanneer u de schakel optie **forceert** met de `New-Item` opdracht om een map te maken en de map al bestaat, wordt de map _niet_ overschreven of vervangen. Er wordt gewoon het bestaande map-object geretourneerd. Als u echter gebruikt `New-Item -Force` voor een bestand dat al bestaat, _wordt_ het bestand volledig overschreven.

## <a name="removing-all-files-and-folders-within-a-folder"></a>Alle bestanden en mappen in een map verwijderen

U kunt opgenomen items verwijderen met `Remove-Item`, maar u wordt gevraagd het verwijderen te bevestigen als het item iets anders bevat. Als u bijvoorbeeld probeert de map `C:\temp\DeleteMe` te verwijderen die andere items bevat, vraagt Windows Power shell u om bevestiging voordat de map wordt verwijderd:

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the Recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Als u niet voor elk opgenomen item wilt worden gevraagd, geeft u de para meter **recursief** op:

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a>Een lokale map toewijzen als een station

U kunt ook een lokale map toewijzen met behulp `New-PSDrive` van de opdracht. Met de volgende opdracht maakt u een `P:` lokaal station in de map lokaal programma bestanden, alleen zichtbaar vanuit de Power shell-sessie:

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

Net als bij netwerk stations zijn stations die zijn toegewezen in Windows Power shell, direct zichtbaar voor de Windows Power shell-shell. Als u een toegewezen station zichtbaar wilt maken vanuit Verkenner, is de para `-Persist` meter vereist. Er kunnen echter alleen externe paden worden gebruikt met persistent.

## <a name="reading-a-text-file-into-an-array"></a>Een tekst bestand in een matrix lezen

Een van de meest voorkomende opslag indelingen voor tekst gegevens bevindt zich in een bestand met afzonderlijke regels behandeld als afzonderlijke gegevens elementen. De `Get-Content` cmdlet kan worden gebruikt om een volledig bestand in één stap te lezen, zoals hier wordt weer gegeven:

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

`Get-Content`behandelt de gegevens die uit het bestand zijn gelezen, al als een matrix, met één element per regel bestands inhoud. U kunt dit controleren door de **lengte** van de geretourneerde inhoud te controleren:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Deze opdracht is vooral handig voor het rechtstreeks ophalen van lijsten met gegevens in Windows Power shell. U kunt bijvoorbeeld een lijst met computer namen of IP-adressen opslaan in een bestand `C:\temp\domainMembers.txt`met één naam op elke regel van het bestand. U kunt gebruiken `Get-Content` om de bestands inhoud op te halen en deze in de `$Computers`variabele te plaatsen:

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

`$Computers`is nu een matrix met een computer naam in elk-element.
