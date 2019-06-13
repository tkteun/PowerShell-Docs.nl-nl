---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Delen van objecten selecteren selecteren Object
ms.openlocfilehash: 4d4c89f0b5103e4701a3af3cd07fcd7c8f1c697f
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030119"
---
# <a name="selecting-parts-of-objects-select-object"></a>Delen van objecten (Select-Object) selecteren

U kunt de **Select-Object** cmdlet voor het maken van nieuwe, aangepaste Windows PowerShell-objecten die u hebt geselecteerd in de objecten die u gebruikt om ze te maken, eigenschappen bevatten. Typ de volgende opdracht om te maken van een nieuw object met alleen de naam en FreeSpace eigenschappen van de Win32_LogicalDisk WMI-klasse:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

Kunt u het type gegevens na uitgifte van deze opdracht niet zien, maar als u het resultaat dat Get-Member na de Select-Object doorgeven, kunt u zien dat er een nieuw type object, een PSCustomObject:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace| Get-Member

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       System.Boolean Equals(Object obj)
GetHashCode Method       System.Int32 GetHashCode()
GetType     Method       System.Type GetType()
ToString    Method       System.String ToString()
FreeSpace   NoteProperty  FreeSpace=...
Name        NoteProperty System.String Name=C:
```

Select-Object heeft vele toepassingen. Een van beide is repliceren van gegevens die u kunt wijzigen. We kunnen nu worden het probleem dat er op in de vorige sectie is verwerkt. We kunnen de waarde van de vrije ruimte in de zojuist gemaakte objecten bijwerken en de uitvoer bevat de beschrijvende naam:

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```
