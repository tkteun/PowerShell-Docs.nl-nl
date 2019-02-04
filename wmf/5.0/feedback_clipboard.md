---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: d5ec95abb1d3160afc4179cff991cb5ef72d85fe
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685919"
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="7f22b-102">Klembord-cmdlets</span><span class="sxs-lookup"><span data-stu-id="7f22b-102">Clipboard cmdlets</span></span>
<span data-ttu-id="7f22b-103">**Get-Klembord** en **Set-Klembord** maken het gemakkelijker voor u om inhoud naar en van een Windows PowerShell-sessie te brengen.</span><span class="sxs-lookup"><span data-stu-id="7f22b-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="7f22b-104">Bijvoorbeeld, als u Windows Verkenner gebruiken drie bestanden naar het Klembord te kopiëren (door ze te selecteren en op `ctrl-c`, bijvoorbeeld), u kunt vervolgens gemakkelijk toegang tot de inhoud van het Klembord als een lijst van bestanden:</span><span class="sxs-lookup"><span data-stu-id="7f22b-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="7f22b-105">De Klembord-cmdlets bieden ondersteuning voor afbeeldingen, audio-bestanden, bestandslijsten en tekst.</span><span class="sxs-lookup"><span data-stu-id="7f22b-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>
