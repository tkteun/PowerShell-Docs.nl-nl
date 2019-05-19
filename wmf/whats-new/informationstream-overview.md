---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Gegevensstroom
ms.openlocfilehash: c54603cf0dd4f0b69f8147620130f9f29bc3e5ec
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856383"
---
# <a name="information-stream"></a><span data-ttu-id="1f014-103">Gegevensstroom</span><span class="sxs-lookup"><span data-stu-id="1f014-103">Information Stream</span></span>

<span data-ttu-id="1f014-104">PowerShell 5.0 voegt een nieuwe gestructureerde **informatie** stream om gestructureerde gegevens tussen een script en de host te verzenden.</span><span class="sxs-lookup"><span data-stu-id="1f014-104">PowerShell 5.0 adds a new structured **Information** stream to transmit structured data between a script and its host.</span></span> <span data-ttu-id="1f014-105">`Write-Host` is ook bijgewerkt voor het verzenden van de uitvoer naar de **informatie** stream kunt u nu vastleggen of het stilte.</span><span class="sxs-lookup"><span data-stu-id="1f014-105">`Write-Host` has also been updated to emit its output to the **Information** stream where you can now capture or silence it.</span></span> <span data-ttu-id="1f014-106">De nieuwe `Write-Information` cmdlet die wordt gebruikt met **InformationVariable** en **InformationAction** algemene parameters kunt u meer flexibiliteit en mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="1f014-106">The new `Write-Information` cmdlet used with **InformationVariable** and **InformationAction** common parameters enables more flexibility and capability.</span></span>

<span data-ttu-id="1f014-107">De volgende functie maakt gebruik van cmdlets die van de nieuwe gebruikmaken **informatie** stream.</span><span class="sxs-lookup"><span data-stu-id="1f014-107">The following function uses cmdlets that take advantage of the new **Information** stream.</span></span>

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

<span data-ttu-id="1f014-108">De volgende voorbeelden tonen de resultaten van het uitvoeren van deze functie.</span><span class="sxs-lookup"><span data-stu-id="1f014-108">The following examples show the results of running this function.</span></span>

```powershell
$r = c:\temp\OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

<span data-ttu-id="1f014-109">De `$r` variabele de procesinformatie in de script-variabele heeft vastgelegd `$p`.</span><span class="sxs-lookup"><span data-stu-id="1f014-109">The `$r` variable has captured the process information in the script variable `$p`.</span></span>

```powershell
$r.Id
4008
```

<span data-ttu-id="1f014-110">In tegenstelling tot de `Write-Host` cmdlet, met behulp van de **InformationVariable** parameter van `Write-Information` kunt u om vast te leggen van de uitvoer in een variabele.</span><span class="sxs-lookup"><span data-stu-id="1f014-110">Unlike the `Write-Host` cmdlet, using the **InformationVariable** parameter of `Write-Information` allows you to capture the output in a variable.</span></span> <span data-ttu-id="1f014-111">Met behulp van de **Tag**, kunt u afzonderlijke kanalen voor het bericht is verzonden naar de **informatie** stream.</span><span class="sxs-lookup"><span data-stu-id="1f014-111">Using the **Tag**, you can create separate channels for message sent to the **Information** stream.</span></span>

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

<span data-ttu-id="1f014-112">Wanneer u een bericht verzendt de **informatie** stream met een label, dat bericht wordt pas weergegeven in de hosttoepassing, maar kunnen worden opgehaald met de naam van de tag.</span><span class="sxs-lookup"><span data-stu-id="1f014-112">When you send a message to the **Information** stream with a tag, that message is not displayed in the host application but can be retrieved using the tag name.</span></span> <span data-ttu-id="1f014-113">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1f014-113">For example:</span></span>

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```