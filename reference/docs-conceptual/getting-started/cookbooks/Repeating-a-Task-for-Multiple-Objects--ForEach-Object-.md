---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Een taak te herhalen voor meerdere objecten ForEach-Object
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 8b8002af3ade0905421760ce29cdc84b084236e9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="0dbd0-103">Een taak herhalen voor meerdere objecten (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="0dbd0-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="0dbd0-104">De **ForEach-Object** cmdlet maakt gebruik van scriptblokken en de $_ descriptor voor de huidige pipeline-object waarmee u een opdracht uitvoeren op elk object in de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-104">The **ForEach-Object** cmdlet uses script blocks and the $_ descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="0dbd0-105">Dit kan worden gebruikt voor een aantal complexe taken uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="0dbd0-106">Een situatie waarin dit kan handig zijn met het bewerken van de gegevens zodat nuttiger.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="0dbd0-107">De Win32_LogicalDisk-klasse van WMI kan bijvoorbeeld worden gebruikt om informatie van de vrije ruimte voor elke lokale schijf te retourneren.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-107">For example, the Win32_LogicalDisk class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="0dbd0-108">De gegevens worden geretourneerd in termen van bytes, waardoor het moeilijk te lezen:</span><span class="sxs-lookup"><span data-stu-id="0dbd0-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

<span data-ttu-id="0dbd0-109">We kunnen de waarde FreeSpace omzetten in megabytes door elke waarde te delen door 1024 tweemaal te gebruiken. na de eerste deling worden de gegevens zich in kilobytes en na het tweede getal is in megabytes.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-109">We can convert the FreeSpace value to megabytes by dividing each value by 1024 twice; after the first division, the data is in kilobytes, and after the second division it is megabytes.</span></span> <span data-ttu-id="0dbd0-110">U kunt dit doen in een scriptblok ForEach-Object te typen:</span><span class="sxs-lookup"><span data-stu-id="0dbd0-110">You can do that in a ForEach-Object script block by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

<span data-ttu-id="0dbd0-111">De uitvoer is nu gegevens zonder bijbehorende label.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="0dbd0-112">Omdat WMI-eigenschappen zoals deze alleen-lezen zijn, kunt u niet rechtstreeks FreeSpace converteren.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-112">Because WMI properties such as this are read-only, you cannot directly convert FreeSpace.</span></span> <span data-ttu-id="0dbd0-113">Als u dit typt:</span><span class="sxs-lookup"><span data-stu-id="0dbd0-113">If you type this:</span></span>

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="0dbd0-114">U er een foutbericht weergegeven:</span><span class="sxs-lookup"><span data-stu-id="0dbd0-114">You get an error message:</span></span>

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="0dbd0-115">U kunt de gegevens opnieuw indelen met behulp van sommige geavanceerde technieken, maar het eenvoudiger is voor het maken van een nieuw object met behulp van **Select-Object**.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using **Select-Object**.</span></span>