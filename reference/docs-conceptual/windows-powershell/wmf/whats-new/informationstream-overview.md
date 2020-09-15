---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Gegevensstroom
ms.openlocfilehash: 1a8df66f7489910b964ec398e90b76e9f30cd2e2
ms.sourcegitcommit: 87b9b989f261b52969e99159e99ee28ad8d8839a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86567838"
---
# <a name="information-stream"></a><span data-ttu-id="871f8-103">Gegevensstroom</span><span class="sxs-lookup"><span data-stu-id="871f8-103">Information Stream</span></span>

<span data-ttu-id="871f8-104">Power shell 5,0 voegt een nieuwe gestructureerde **informatie** stroom toe voor het verzenden van gestructureerde gegevens tussen een script en de host.</span><span class="sxs-lookup"><span data-stu-id="871f8-104">PowerShell 5.0 adds a new structured **Information** stream to transmit structured data between a script and its host.</span></span> <span data-ttu-id="871f8-105">`Write-Host` is ook bijgewerkt met het verzenden van de uitvoer naar de **informatie** stroom waar u deze nu kunt vastleggen of stilte.</span><span class="sxs-lookup"><span data-stu-id="871f8-105">`Write-Host` has also been updated to emit its output to the **Information** stream where you can now capture or silence it.</span></span> <span data-ttu-id="871f8-106">De nieuwe `Write-Information` cmdlet die wordt gebruikt met de algemene para meters **InformationVariable** en **Information Action** biedt meer flexibiliteit en meer mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="871f8-106">The new `Write-Information` cmdlet used with **InformationVariable** and **InformationAction** common parameters enables more flexibility and capability.</span></span>

<span data-ttu-id="871f8-107">De volgende functie maakt gebruik van cmdlets die gebruikmaken van de nieuwe **informatie** stroom.</span><span class="sxs-lookup"><span data-stu-id="871f8-107">The following function uses cmdlets that take advantage of the new **Information** stream.</span></span>

```powershell
function OutputGusher {
  [CmdletBinding()]
  param()
  Write-Host -ForegroundColor Green 'Preparing to give you output!'
  Write-Host '============================='
  Write-Host 'I ' -ForegroundColor White -NoNewline
  Write-Host '<3 ' -ForegroundColor Red -NoNewline
  Write-Host 'Output' -ForegroundColor White
  Write-Host '============================='

  $p = Get-Process -id $pid
  $p

  Write-Information $p -Tag Process
  Write-Information 'Some spammy logging information' -Tag LogLow
  Write-Information 'Some important logging information' -Tag LogHigh

  Write-Host
  Write-Host -ForegroundColor Green 'SCRIPT COMPLETE!!'
}
```

<span data-ttu-id="871f8-108">In de volgende voor beelden ziet u de resultaten van het uitvoeren van deze functie.</span><span class="sxs-lookup"><span data-stu-id="871f8-108">The following examples show the results of running this function.</span></span>

```powershell
$r = OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

<span data-ttu-id="871f8-109">De `$r` variabele heeft de proces informatie vastgelegd in de script variabele `$p` .</span><span class="sxs-lookup"><span data-stu-id="871f8-109">The `$r` variable has captured the process information in the script variable `$p`.</span></span>

```powershell
$r.Id
4008
```

<span data-ttu-id="871f8-110">In tegens telling tot de `Write-Host` cmdlet kunt u met de para meter **InformationVariable** van `Write-Information` de uitvoer vastleggen in een variabele.</span><span class="sxs-lookup"><span data-stu-id="871f8-110">Unlike the `Write-Host` cmdlet, using the **InformationVariable** parameter of `Write-Information` allows you to capture the output in a variable.</span></span> <span data-ttu-id="871f8-111">Met behulp van de- **tag**kunt u afzonderlijke kanalen maken voor het bericht dat naar de **informatie** stroom wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="871f8-111">Using the **Tag**, you can create separate channels for message sent to the **Information** stream.</span></span>

```powershell
$r = OutputGusher -InformationVariable iv
$ivOutput = $iv | Group-Object -AsHash { $_.Tags[0] } -AsString
$ivOutput
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================
SCRIPT COMPLETE!!

Name                 Value
----                 -----
LogLow               {Some spammy logging information}
LogHigh              {Some important logging information}
Process              {System.Diagnostics.Process (powershell)}
PSHOST               {Preparing to give you output!, =============================, I , <3 ...}
```

<span data-ttu-id="871f8-112">Wanneer u een bericht verzendt naar de **informatie** stroom met een tag, wordt dat bericht niet weer gegeven in de hosttoepassing, maar kan het worden opgehaald met de label naam.</span><span class="sxs-lookup"><span data-stu-id="871f8-112">When you send a message to the **Information** stream with a tag, that message is not displayed in the host application but can be retrieved using the tag name.</span></span> <span data-ttu-id="871f8-113">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="871f8-113">For example:</span></span>

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```
