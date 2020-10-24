---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Een taak herhalen voor meerdere objecten ForEach-object
description: Met de ForEach-Object kunt u een reeks opdrachten herhalen voor elk object dat via de pijp lijn wordt door gegeven.
ms.openlocfilehash: 7353be833dc8bf77dd18b7fc45bdd97e092ff6ef
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499954"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Een taak herhalen voor meerdere objecten (ForEach-Object)

De `ForEach-Object` cmdlet gebruikt script blokken en de `$_` descriptor voor het huidige pijplijn object, zodat u een opdracht kunt uitvoeren op elk object in de pijp lijn. Dit kan worden gebruikt voor het uitvoeren van enkele gecompliceerde taken.

Een situatie waarin dit nuttig kan zijn, is om het handiger te maken om de gegevens te bewerken. Bijvoorbeeld, de klasse **Win32_LogicalDisk** van WMI kan worden gebruikt om informatie over de beschik bare ruimte voor elke lokale schijf te retour neren. De gegevens worden weer gegeven in termen van bytes, waardoor het moeilijk te lezen is:

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

De **vrije ruimte** -waarde kan worden geconverteerd naar mega bytes door elke waarde te delen door 1 MB. U kunt dit doen in een `ForEach-Object` script blok door het volgende te typen:

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

Helaas is de uitvoer nu gegevens zonder bijbehorend label. Omdat WMI-eigenschappen zoals dit alleen-lezen zijn, kunt u niet rechtstreeks **vrije ruimte**converteren. Als u dit typt:

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

Er wordt een fout bericht weer gegeven:

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

U kunt de gegevens opnieuw indelen met een aantal geavanceerde technieken, maar een eenvoudigere benadering is het maken van een nieuw object met behulp van `Select-Object` .
