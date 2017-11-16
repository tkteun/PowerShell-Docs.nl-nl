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
>Opmerking: Geef een voorgestelde beschrijvende titel en een korte beschrijving

## <a name="example-erroneous-executionpolicy-errors"></a>Voorbeeld: Foutieve ExecutionPolicy fouten ##
In Windows 7, het gebruik van PowerShell-modules en DSC-resources mogelijk fouten tot gevolg gerapporteerd over ExecutionPolicy.

### <a name="resolution"></a>Oplossing

Ingesteld op te lossen, de **ExecutionPolicy** naar **RemoteSigned** met de volgende opdracht in een verhoogde PowerShell-sessie (als Administrator uitvoeren):

```powershell
Set-ExecutionPolicy RemoteSigned
```

