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
ms.locfileid: "34221932"
---
>Opmerking: Geef een voorgestelde beschrijvende titel en een korte beschrijving

## <a name="example-erroneous-executionpolicy-errors"></a>Voorbeeld: Foutieve ExecutionPolicy fouten ##
In Windows 7, het gebruik van PowerShell-modules en DSC-resources mogelijk fouten tot gevolg gerapporteerd over ExecutionPolicy.

### <a name="resolution"></a>Oplossing

Ingesteld op te lossen, de **ExecutionPolicy** naar **RemoteSigned** met de volgende opdracht in een verhoogde PowerShell-sessie (als Administrator uitvoeren):

```powershell
Set-ExecutionPolicy RemoteSigned
```
