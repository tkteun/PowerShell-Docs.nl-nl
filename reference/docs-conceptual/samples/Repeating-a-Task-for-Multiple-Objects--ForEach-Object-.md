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
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="fcc5d-103">Een taak herhalen voor meerdere objecten (ForEach-object)</span><span class="sxs-lookup"><span data-stu-id="fcc5d-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="fcc5d-104">De **foreach-object-** cmdlet gebruikt script blokken en de `$_` descriptor voor het huidige pijplijn object, zodat u een opdracht kunt uitvoeren op elk object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="fcc5d-104">The **ForEach-Object** cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="fcc5d-105">Dit kan worden gebruikt voor het uitvoeren van enkele gecompliceerde taken.</span><span class="sxs-lookup"><span data-stu-id="fcc5d-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="fcc5d-106">Een situatie waarin dit nuttig kan zijn, is om het handiger te maken om de gegevens te bewerken.</span><span class="sxs-lookup"><span data-stu-id="fcc5d-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="fcc5d-107">Bijvoorbeeld, de klasse Win32_LogicalDisk van WMI kan worden gebruikt om informatie over de beschik bare ruimte voor elke lokale schijf te retour neren.</span><span class="sxs-lookup"><span data-stu-id="fcc5d-107">For example, the Win32_LogicalDisk class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="fcc5d-108">De gegevens worden weer gegeven in termen van bytes, waardoor het moeilijk te lezen is:</span><span class="sxs-lookup"><span data-stu-id="fcc5d-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

<span data-ttu-id="fcc5d-109">De vrije ruimte-waarde kan worden geconverteerd naar mega bytes door elke 1024 waarde twee keer te delen. na de eerste deling bevindt de gegevens zich in kilo bytes en na de tweede deling is dit mega bytes.</span><span class="sxs-lookup"><span data-stu-id="fcc5d-109">We can convert the FreeSpace value to megabytes by dividing each value by 1024 twice; after the first division, the data is in kilobytes, and after the second division it is megabytes.</span></span> <span data-ttu-id="fcc5d-110">U kunt dit doen in een script blok voor ForEach-objecten door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="fcc5d-110">You can do that in a ForEach-Object script block by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

<span data-ttu-id="fcc5d-111">Helaas is de uitvoer nu gegevens zonder bijbehorend label.</span><span class="sxs-lookup"><span data-stu-id="fcc5d-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="fcc5d-112">Omdat WMI-eigenschappen zoals dit alleen-lezen zijn, kunt u niet rechtstreeks vrije ruimte converteren.</span><span class="sxs-lookup"><span data-stu-id="fcc5d-112">Because WMI properties such as this are read-only, you cannot directly convert FreeSpace.</span></span> <span data-ttu-id="fcc5d-113">Als u dit typt:</span><span class="sxs-lookup"><span data-stu-id="fcc5d-113">If you type this:</span></span>

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="fcc5d-114">Er wordt een fout bericht weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="fcc5d-114">You get an error message:</span></span>

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="fcc5d-115">U kunt de gegevens opnieuw indelen met een aantal geavanceerde technieken, maar een eenvoudigere benadering is het maken van een nieuw object met behulp van **Select-object**.</span><span class="sxs-lookup"><span data-stu-id="fcc5d-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using **Select-Object**.</span></span>
