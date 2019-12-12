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
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="0a603-103">Delen van objecten selecteren (select-object)</span><span class="sxs-lookup"><span data-stu-id="0a603-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="0a603-104">U kunt de **Select-object-** cmdlet gebruiken om nieuwe aangepaste Windows Power shell-objecten te maken die eigenschappen bevatten die zijn geselecteerd in de objecten die u gebruikt om ze te maken.</span><span class="sxs-lookup"><span data-stu-id="0a603-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="0a603-105">Typ de volgende opdracht om een nieuw object te maken dat alleen de naam en de eigenschappen van de beschik bare ruimte van de Win32_LogicalDisk WMI-klasse bevat:</span><span class="sxs-lookup"><span data-stu-id="0a603-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="0a603-106">U kunt het type gegevens niet zien nadat u die opdracht hebt uitgevoerd, maar als u het resultaat naar Get-member na het Select-object Pipet, weet u dat u een nieuw type object hebt, een PSCustomObject:</span><span class="sxs-lookup"><span data-stu-id="0a603-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

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

<span data-ttu-id="0a603-107">Select-object heeft veel toepassingen.</span><span class="sxs-lookup"><span data-stu-id="0a603-107">Select-Object has many uses.</span></span> <span data-ttu-id="0a603-108">Een daarvan repliceert gegevens die u vervolgens kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="0a603-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="0a603-109">We kunnen nu het probleem afhandelen dat in de vorige sectie is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0a603-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="0a603-110">De waarde van vrije ruimte in de zojuist gemaakte objecten kan worden bijgewerkt. de uitvoer bevat de beschrijvende naam:</span><span class="sxs-lookup"><span data-stu-id="0a603-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```
