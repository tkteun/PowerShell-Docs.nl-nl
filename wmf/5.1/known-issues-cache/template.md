---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
title: van de voorbeeldsjabloon van een bekend probleem of beperking Write-up
ms.openlocfilehash: b93393b2c84e76a301e6406d1388e82e95a2959c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
><span data-ttu-id="8d921-103">Opmerking: Geef een voorgestelde beschrijvende titel en een korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="8d921-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="8d921-104">Voorbeeld: Foutieve ExecutionPolicy fouten</span><span class="sxs-lookup"><span data-stu-id="8d921-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="8d921-105">In Windows 7, het gebruik van PowerShell-modules en DSC-resources mogelijk fouten tot gevolg gerapporteerd over ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="8d921-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="8d921-106">Oplossing</span><span class="sxs-lookup"><span data-stu-id="8d921-106">Resolution</span></span>

<span data-ttu-id="8d921-107">Ingesteld op te lossen, de **ExecutionPolicy** naar **RemoteSigned** met de volgende opdracht in een verhoogde PowerShell-sessie (als Administrator uitvoeren):</span><span class="sxs-lookup"><span data-stu-id="8d921-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

