---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
title: van de voorbeeldsjabloon van een bekend probleem of beperking Write-up
ms.openlocfilehash: cecf31127aaa1942471877a2056230ab592bd095
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
>Opmerking: Geef een voorgestelde beschrijvende titel en een korte beschrijving

## <a name="example-erroneous-executionpolicy-errors"></a>Voorbeeld: Foutieve ExecutionPolicy fouten ##
In Windows 7, het gebruik van PowerShell-modules en DSC-resources mogelijk fouten tot gevolg gerapporteerd over ExecutionPolicy.

### <a name="resolution"></a>Oplossing

Ingesteld op te lossen, de **ExecutionPolicy** naar **RemoteSigned** met de volgende opdracht in een verhoogde PowerShell-sessie (als Administrator uitvoeren):

```powershell
Set-ExecutionPolicy RemoteSigned
```