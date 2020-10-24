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
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="b5a29-104">Een taak herhalen voor meerdere objecten (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="b5a29-104">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="b5a29-105">De `ForEach-Object` cmdlet gebruikt script blokken en de `$_` descriptor voor het huidige pijplijn object, zodat u een opdracht kunt uitvoeren op elk object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="b5a29-105">The `ForEach-Object` cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="b5a29-106">Dit kan worden gebruikt voor het uitvoeren van enkele gecompliceerde taken.</span><span class="sxs-lookup"><span data-stu-id="b5a29-106">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="b5a29-107">Een situatie waarin dit nuttig kan zijn, is om het handiger te maken om de gegevens te bewerken.</span><span class="sxs-lookup"><span data-stu-id="b5a29-107">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="b5a29-108">Bijvoorbeeld, de klasse **Win32_LogicalDisk** van WMI kan worden gebruikt om informatie over de beschik bare ruimte voor elke lokale schijf te retour neren.</span><span class="sxs-lookup"><span data-stu-id="b5a29-108">For example, the **Win32_LogicalDisk** class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="b5a29-109">De gegevens worden weer gegeven in termen van bytes, waardoor het moeilijk te lezen is:</span><span class="sxs-lookup"><span data-stu-id="b5a29-109">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

<span data-ttu-id="b5a29-110">De **vrije ruimte** -waarde kan worden geconverteerd naar mega bytes door elke waarde te delen door 1 MB.</span><span class="sxs-lookup"><span data-stu-id="b5a29-110">We can convert the **FreeSpace** value to megabytes by dividing each value by 1MB.</span></span> <span data-ttu-id="b5a29-111">U kunt dit doen in een `ForEach-Object` script blok door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="b5a29-111">You can do that in a `ForEach-Object` script block by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

<span data-ttu-id="b5a29-112">Helaas is de uitvoer nu gegevens zonder bijbehorend label.</span><span class="sxs-lookup"><span data-stu-id="b5a29-112">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="b5a29-113">Omdat WMI-eigenschappen zoals dit alleen-lezen zijn, kunt u niet rechtstreeks **vrije ruimte**converteren.</span><span class="sxs-lookup"><span data-stu-id="b5a29-113">Because WMI properties such as this are read-only, you cannot directly convert **FreeSpace**.</span></span> <span data-ttu-id="b5a29-114">Als u dit typt:</span><span class="sxs-lookup"><span data-stu-id="b5a29-114">If you type this:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

<span data-ttu-id="b5a29-115">Er wordt een fout bericht weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="b5a29-115">You get an error message:</span></span>

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

<span data-ttu-id="b5a29-116">U kunt de gegevens opnieuw indelen met een aantal geavanceerde technieken, maar een eenvoudigere benadering is het maken van een nieuw object met behulp van `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="b5a29-116">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using `Select-Object`.</span></span>
