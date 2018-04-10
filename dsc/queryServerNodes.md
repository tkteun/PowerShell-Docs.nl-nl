---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-functie op knooppunt querygegevens van pull-server.
ms.openlocfilehash: 5c10eefe9ded4fe6339c4e6252cc189bcd793978
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-function-to-query-node-information-from-pull-server"></a><span data-ttu-id="ca759-103">DSC-functie op knooppunt querygegevens van pull-server.</span><span class="sxs-lookup"><span data-stu-id="ca759-103">DSC function to query node information from pull server.</span></span>

```powershell
function QueryNodeInformation
{
Param (
       [string] $Uri =
"http://localhost:7070/PSDSCComplianceServer.svc/Status",
       [string] $ContentType = "application/json"
     )

  Write-Host "Querying node information from pull server URI  = $Uri" -ForegroundColor Green

  Write-Host "Querying node status in content type  = $ContentType " -ForegroundColor Green

   $response = Invoke-WebRequest -Uri $Uri -Method Get -ContentType $ContentType -UseDefaultCredentials -Headers
    @{Accept = $ContentType}

   if($response.StatusCode -ne 200)
 {
     Write-Host "node information was not retrieved." -ForegroundColor Red
 }

 $jsonResponse = ConvertFrom-Json $response.Content

  return $jsonResponse
}
```

<span data-ttu-id="ca759-104">Vervang de `Uri` parameter met de URI voor uw pull-server.</span><span class="sxs-lookup"><span data-stu-id="ca759-104">Replace the `Uri` parameter with the URI for your pull server.</span></span> <span data-ttu-id="ca759-105">Als u wilt dat de knooppuntgegevens in XML-indeling, stelt u `ContentType` naar `application/xml`.</span><span class="sxs-lookup"><span data-stu-id="ca759-105">If you want the node information in XML format, set `ContentType` to `application/xml`.</span></span>

<span data-ttu-id="ca759-106">Voor het ophalen van de knooppuntgegevens van de `$json` parameter, gebruikt u de volgende:</span><span class="sxs-lookup"><span data-stu-id="ca759-106">To retrieve the node information from the `$json` parameter, use the following:</span></span>

```powershell
$json = QueryNodeInformation –Uri http://localhost:7070/PSDSCComplianceServer.svc/Status

$json.value | Format-Table TargetName, ConfigurationId, ServerChecksum, NodeCompliant, LastComplianceTime, StatusCode
```