---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Delen van objecten selecteren selecteren Object
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 323c57ba4462e20d9713fb74732989584f5a993f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057888"
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="959fc-103">Delen van objecten (Select-Object) selecteren</span><span class="sxs-lookup"><span data-stu-id="959fc-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="959fc-104">U kunt de **Select-Object** cmdlet voor het maken van nieuwe, aangepaste Windows PowerShell-objecten die u hebt geselecteerd in de objecten die u gebruikt om ze te maken, eigenschappen bevatten.</span><span class="sxs-lookup"><span data-stu-id="959fc-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="959fc-105">Typ de volgende opdracht om te maken van een nieuw object met alleen de naam en FreeSpace eigenschappen van de Win32_LogicalDisk WMI-klasse:</span><span class="sxs-lookup"><span data-stu-id="959fc-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="959fc-106">Kunt u het type gegevens na uitgifte van deze opdracht niet zien, maar als u het resultaat dat Get-Member na de Select-Object doorgeven, kunt u zien dat er een nieuw type object, een PSCustomObject:</span><span class="sxs-lookup"><span data-stu-id="959fc-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

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

<span data-ttu-id="959fc-107">Select-Object heeft vele toepassingen.</span><span class="sxs-lookup"><span data-stu-id="959fc-107">Select-Object has many uses.</span></span> <span data-ttu-id="959fc-108">Een van beide is repliceren van gegevens die u kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="959fc-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="959fc-109">We kunnen nu worden het probleem dat er op in de vorige sectie is verwerkt.</span><span class="sxs-lookup"><span data-stu-id="959fc-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="959fc-110">We kunnen de waarde van de vrije ruimte in de zojuist gemaakte objecten bijwerken en de uitvoer bevat de beschrijvende naam:</span><span class="sxs-lookup"><span data-stu-id="959fc-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```