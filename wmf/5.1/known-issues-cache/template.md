---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.topic: conceptual
title: van de voorbeeldsjabloon van een bekend probleem of beperking writeup
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055544"
---
 ><span data-ttu-id="6bea8-103">Opmerking: bieden een voorgestelde beschrijvende titel en een korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="6bea8-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="6bea8-104">Voorbeeld: Foutieve ExecutionPolicy fouten</span><span class="sxs-lookup"><span data-stu-id="6bea8-104">Example: Erroneous ExecutionPolicy errors</span></span>
<span data-ttu-id="6bea8-105">Op Windows 7, kan het gebruik van PowerShell-modules en DSC-resources leiden tot fouten gerapporteerd over ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="6bea8-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="6bea8-106">Oplossing</span><span class="sxs-lookup"><span data-stu-id="6bea8-106">Resolution</span></span>

<span data-ttu-id="6bea8-107">Ingesteld op te lossen, de **ExecutionPolicy** naar **RemoteSigned** door het uitvoeren van de volgende opdracht uit in een verhoogde PowerShell-sessie (als Administrator uitvoeren):</span><span class="sxs-lookup"><span data-stu-id="6bea8-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
