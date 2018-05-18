---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.topic: conceptual
title: van de voorbeeldsjabloon van een bekend probleem of beperking Write-up
ms.openlocfilehash: 453d4e40b906ebcab7314f04e138ded271338846
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
><span data-ttu-id="58915-103">Opmerking: Geef een voorgestelde beschrijvende titel en een korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="58915-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="58915-104">Voorbeeld: Foutieve ExecutionPolicy fouten</span><span class="sxs-lookup"><span data-stu-id="58915-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="58915-105">In Windows 7, het gebruik van PowerShell-modules en DSC-resources mogelijk fouten tot gevolg gerapporteerd over ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="58915-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="58915-106">Oplossing</span><span class="sxs-lookup"><span data-stu-id="58915-106">Resolution</span></span>

<span data-ttu-id="58915-107">Ingesteld op te lossen, de **ExecutionPolicy** naar **RemoteSigned** met de volgende opdracht in een verhoogde PowerShell-sessie (als Administrator uitvoeren):</span><span class="sxs-lookup"><span data-stu-id="58915-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
