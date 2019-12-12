---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Een taak herhalen voor meerdere objecten ForEach-object
ms.openlocfilehash: 1442507c4213476f65df3401c1021f8d0fc31956
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030816"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Een taak herhalen voor meerdere objecten (ForEach-object)

De **foreach-object-** cmdlet gebruikt script blokken en de `$_` descriptor voor het huidige pijplijn object, zodat u een opdracht kunt uitvoeren op elk object in de pijp lijn. Dit kan worden gebruikt voor het uitvoeren van enkele gecompliceerde taken.

Een situatie waarin dit nuttig kan zijn, is om het handiger te maken om de gegevens te bewerken. Bijvoorbeeld, de klasse Win32_LogicalDisk van WMI kan worden gebruikt om informatie over de beschik bare ruimte voor elke lokale schijf te retour neren. De gegevens worden weer gegeven in termen van bytes, waardoor het moeilijk te lezen is:

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

De vrije ruimte-waarde kan worden geconverteerd naar mega bytes door elke 1024 waarde twee keer te delen. na de eerste deling bevindt de gegevens zich in kilo bytes en na de tweede deling is dit mega bytes. U kunt dit doen in een script blok voor ForEach-objecten door het volgende te typen:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

Helaas is de uitvoer nu gegevens zonder bijbehorend label. Omdat WMI-eigenschappen zoals dit alleen-lezen zijn, kunt u niet rechtstreeks vrije ruimte converteren. Als u dit typt:

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Er wordt een fout bericht weer gegeven:

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

U kunt de gegevens opnieuw indelen met een aantal geavanceerde technieken, maar een eenvoudigere benadering is het maken van een nieuw object met behulp van **Select-object**.
