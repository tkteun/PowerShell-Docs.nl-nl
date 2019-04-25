---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: d5ec95abb1d3160afc4179cff991cb5ef72d85fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057295"
---
# <a name="clipboard-cmdlets"></a>Klembord-cmdlets
**Get-Klembord** en **Set-Klembord** maken het gemakkelijker voor u om inhoud naar en van een Windows PowerShell-sessie te brengen. Bijvoorbeeld, als u Windows Verkenner gebruiken drie bestanden naar het Klembord te kopiëren (door ze te selecteren en op `ctrl-c`, bijvoorbeeld), u kunt vervolgens gemakkelijk toegang tot de inhoud van het Klembord als een lijst van bestanden:

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


De Klembord-cmdlets bieden ondersteuning voor afbeeldingen, audio-bestanden, bestandslijsten en tekst.
