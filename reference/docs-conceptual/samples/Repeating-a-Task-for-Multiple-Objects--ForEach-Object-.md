---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Een taak herhalen voor meerdere objecten-ForEach-Object
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 64d85edad4a6931b2376b95b6d1f5b4d5194399f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404565"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Een taak herhalen voor meerdere objecten (ForEach-Object)

De **ForEach-Object** cmdlet scriptblokken gebruikt en de `$_` descriptor voor de huidige pijplijn-object dat u een opdracht uitvoeren op elk object in de pijplijn. Dit kan worden gebruikt om uit te voeren sommige complexe taken.

Een situatie waarin dit kan nuttig zijn met het bewerken van de gegevens zodat deze nuttiger zijn. De WMI-klasse Win32_LogicalDisk kunt bijvoorbeeld worden gebruikt om gegevens van de vrije ruimte voor elke lokale schijf te retourneren. De gegevens worden geretourneerd in termen van bytes, waardoor het moeilijk te lezen:

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

We kunnen de waarde FreeSpace omzetten naar megabytes door elke waarde te delen door 1024 tweemaal te gebruiken. na de eerste afdeling, de gegevens zich in kilobytes en na het tweede getal is in megabytes. U kunt dat doen in een scriptblok ForEach-Object door te typen:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

De uitvoer is nu gegevens met geen bijbehorende label. Omdat WMI-eigenschappen zoals deze alleen-lezen zijn, kunt u niet rechtstreeks FreeSpace converteren. Als u deze typt:

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Krijgt u een foutbericht weergegeven:

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

U kunt de gegevens opnieuw indelen met behulp van sommige geavanceerde technieken, maar het eenvoudiger is een nieuw object maken met behulp van **Select-Object**.