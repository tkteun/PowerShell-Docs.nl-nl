---
ms.date: 12/23/2019
keywords: Power shell, cmdlet
title: Een taak herhalen voor meerdere objecten ForEach-object
ms.openlocfilehash: bf89070fd9b006fa9b0b262ab63ffadd81072ecc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736876"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="e829b-103">Een taak herhalen voor meerdere objecten (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="e829b-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="e829b-104">De `ForEach-Object` cmdlet gebruikt script blokken en de `$_` descriptor voor het huidige pijplijn object, zodat u een opdracht kunt uitvoeren op elk object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="e829b-104">The `ForEach-Object` cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="e829b-105">Dit kan worden gebruikt voor het uitvoeren van enkele gecompliceerde taken.</span><span class="sxs-lookup"><span data-stu-id="e829b-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="e829b-106">Een situatie waarin dit nuttig kan zijn, is om het handiger te maken om de gegevens te bewerken.</span><span class="sxs-lookup"><span data-stu-id="e829b-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="e829b-107">Bijvoorbeeld, de klasse **Win32_LogicalDisk** van WMI kan worden gebruikt om informatie over de beschik bare ruimte voor elke lokale schijf te retour neren.</span><span class="sxs-lookup"><span data-stu-id="e829b-107">For example, the **Win32_LogicalDisk** class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="e829b-108">De gegevens worden weer gegeven in termen van bytes, waardoor het moeilijk te lezen is:</span><span class="sxs-lookup"><span data-stu-id="e829b-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

<span data-ttu-id="e829b-109">De **vrije ruimte** -waarde kan worden geconverteerd naar mega bytes door elke waarde te delen door 1 MB.</span><span class="sxs-lookup"><span data-stu-id="e829b-109">We can convert the **FreeSpace** value to megabytes by dividing each value by 1MB.</span></span> <span data-ttu-id="e829b-110">U kunt dit doen in een `ForEach-Object` script blok door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="e829b-110">You can do that in a `ForEach-Object` script block by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

<span data-ttu-id="e829b-111">Helaas is de uitvoer nu gegevens zonder bijbehorend label.</span><span class="sxs-lookup"><span data-stu-id="e829b-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="e829b-112">Omdat WMI-eigenschappen zoals dit alleen-lezen zijn, kunt u niet rechtstreeks **vrije ruimte**converteren.</span><span class="sxs-lookup"><span data-stu-id="e829b-112">Because WMI properties such as this are read-only, you cannot directly convert **FreeSpace**.</span></span> <span data-ttu-id="e829b-113">Als u dit typt:</span><span class="sxs-lookup"><span data-stu-id="e829b-113">If you type this:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

<span data-ttu-id="e829b-114">Er wordt een fout bericht weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="e829b-114">You get an error message:</span></span>

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

<span data-ttu-id="e829b-115">U kunt de gegevens opnieuw indelen met een aantal geavanceerde technieken, maar een eenvoudigere benadering is het maken van een nieuw object `Select-Object`met behulp van.</span><span class="sxs-lookup"><span data-stu-id="e829b-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using `Select-Object`.</span></span>
