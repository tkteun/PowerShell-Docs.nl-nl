---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Objecten sorteren
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 272d550a67b206f9924ebe143eca2f5906c0a304
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="sorting-objects"></a><span data-ttu-id="8236d-103">Objecten sorteren</span><span class="sxs-lookup"><span data-stu-id="8236d-103">Sorting Objects</span></span>

<span data-ttu-id="8236d-104">We kunnen ordenen weergegeven gegevens om het gemakkelijker om te scannen met de **Sort-Object** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8236d-104">We can organize displayed data to make it easier to scan by using the **Sort-Object** cmdlet.</span></span> <span data-ttu-id="8236d-105">**Sort-Object** wordt de naam van een of meer eigenschappen om te sorteren op en retourneert gegevens die zijn gesorteerd op basis van de waarden van deze eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="8236d-105">**Sort-Object** takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

<span data-ttu-id="8236d-106">U kunt het probleem van de aanbieding Win32_SystemDriver exemplaren.</span><span class="sxs-lookup"><span data-stu-id="8236d-106">Consider the problem of listing Win32_SystemDriver instances.</span></span> <span data-ttu-id="8236d-107">Als we sorteren wilt op **status** en vervolgens op **naam**, we kunt dit doen door te typen:</span><span class="sxs-lookup"><span data-stu-id="8236d-107">If we want to sort by **State** and then by **Name**, we can do it by typing:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

<span data-ttu-id="8236d-108">Hoewel dit een langdurige weergeven, kunt u de items zien met de dezelfde status gegroepeerd:</span><span class="sxs-lookup"><span data-stu-id="8236d-108">Although this is a lengthy display, you can see items with the same state grouped together:</span></span>

```output
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

<span data-ttu-id="8236d-109">U kunt de objecten ook in omgekeerde volgorde sorteren door op te geven de **aflopend** parameter.</span><span class="sxs-lookup"><span data-stu-id="8236d-109">You can also sort the objects in reverse order by specifying the **Descending** parameter.</span></span> <span data-ttu-id="8236d-110">Hiermee wordt de sorteervolgorde zodat namen in omgekeerde alfabetische volgorde worden gesorteerd en getallen worden gesorteerd in aflopende grootte.</span><span class="sxs-lookup"><span data-stu-id="8236d-110">This reverses the sort order so that names are sorted in reverse alphabetical order and numbers are sorted by descending size.</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```