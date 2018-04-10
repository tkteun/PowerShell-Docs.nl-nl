---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: d34a267bae7e48afe4442256d7f112da3a97eb7d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="clipboard-cmdlets"></a>Klembord-cmdlets
**Get-Klembord** en **Set Klembord** het eenvoudiger voor u om inhoud naar en van een Windows PowerShell-sessie te brengen. Bijvoorbeeld, als u Windows Verkenner gebruiken drie bestanden naar het Klembord te kopiëren (door ze te selecteren en op `ctrl-c`, bijvoorbeeld), u kunt vervolgens gemakkelijk toegang tot de inhoud van het Klembord als een lijst met bestanden:

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


De Klembord-cmdlets ondersteunen afbeeldingen, audio-bestanden, bestandslijsten en tekst.