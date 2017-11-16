---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Object selecteren selecteren delen van objecten
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 8c9633e80f63e1d474c46fa772108aee4f79751d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="2656f-103">Delen van objecten (Select-Object) selecteren</span><span class="sxs-lookup"><span data-stu-id="2656f-103">Selecting Parts of Objects (Select-Object)</span></span>
<span data-ttu-id="2656f-104">U kunt de **Select-Object** cmdlet voor het maken van nieuwe, aangepaste Windows PowerShell-objecten die u hebt geselecteerd in de objecten die u gebruikt om ze te maken, eigenschappen bevatten.</span><span class="sxs-lookup"><span data-stu-id="2656f-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="2656f-105">Typ de volgende opdracht voor het maken van een nieuw object met alleen de naam en FreeSpace eigenschappen van de Win32_LogicalDisk WMI-klasse:</span><span class="sxs-lookup"><span data-stu-id="2656f-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="2656f-106">Het type gegevens na het uitgeven van deze opdracht niet wordt weergegeven, maar als u het resultaat dat Get-lid na de Select-Object doorsluizen, kunt u zien dat er een nieuw type object, een PSCustomObject:</span><span class="sxs-lookup"><span data-stu-id="2656f-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

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

<span data-ttu-id="2656f-107">Select-Object heeft veel gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2656f-107">Select-Object has many uses.</span></span> <span data-ttu-id="2656f-108">Een van beide is bezig met het repliceren van gegevens die u kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="2656f-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="2656f-109">We kan het probleem dat er op in de vorige sectie is nu verwerken.</span><span class="sxs-lookup"><span data-stu-id="2656f-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="2656f-110">We kunnen de waarde van FreeSpace bijwerken in onze zojuist gemaakte objecten en de uitvoer bevat de beschrijvende label:</span><span class="sxs-lookup"><span data-stu-id="2656f-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```

