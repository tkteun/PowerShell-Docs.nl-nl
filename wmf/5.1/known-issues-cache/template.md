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
 >Opmerking: bieden een voorgestelde beschrijvende titel en een korte beschrijving

## <a name="example-erroneous-executionpolicy-errors"></a>Voorbeeld: Foutieve ExecutionPolicy fouten
Op Windows 7, kan het gebruik van PowerShell-modules en DSC-resources leiden tot fouten gerapporteerd over ExecutionPolicy.

### <a name="resolution"></a>Oplossing

Ingesteld op te lossen, de **ExecutionPolicy** naar **RemoteSigned** door het uitvoeren van de volgende opdracht uit in een verhoogde PowerShell-sessie (als Administrator uitvoeren):

```powershell
Set-ExecutionPolicy RemoteSigned
```
