---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Delen van objecten selecteren object selecteren
ms.openlocfilehash: 4d4c89f0b5103e4701a3af3cd07fcd7c8f1c697f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030119"
---
# <a name="selecting-parts-of-objects-select-object"></a>Delen van objecten selecteren (select-object)

U kunt de **Select-object-** cmdlet gebruiken om nieuwe aangepaste Windows Power shell-objecten te maken die eigenschappen bevatten die zijn geselecteerd in de objecten die u gebruikt om ze te maken. Typ de volgende opdracht om een nieuw object te maken dat alleen de naam en de eigenschappen van de beschik bare ruimte van de Win32_LogicalDisk WMI-klasse bevat:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

U kunt het type gegevens niet zien nadat u die opdracht hebt uitgevoerd, maar als u het resultaat naar Get-member na het Select-object Pipet, weet u dat u een nieuw type object hebt, een PSCustomObject:

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

Select-object heeft veel toepassingen. Een daarvan repliceert gegevens die u vervolgens kunt wijzigen. We kunnen nu het probleem afhandelen dat in de vorige sectie is uitgevoerd. De waarde van vrije ruimte in de zojuist gemaakte objecten kan worden bijgewerkt. de uitvoer bevat de beschrijvende naam:

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```
