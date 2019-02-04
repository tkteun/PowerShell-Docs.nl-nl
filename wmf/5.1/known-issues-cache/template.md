---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.topic: conceptual
title: van de voorbeeldsjabloon van een bekend probleem of beperking writeup
ms.openlocfilehash: ed7ae3de392c8902917e5b98fd4fc9d5138ccaed
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688677"
---
>Opmerking: bieden een voorgestelde beschrijvende titel en een korte beschrijving

## <a name="example-erroneous-executionpolicy-errors"></a>Voorbeeld: Foutieve ExecutionPolicy fouten ##
Op Windows 7, kan het gebruik van PowerShell-modules en DSC-resources leiden tot fouten gerapporteerd over ExecutionPolicy.

### <a name="resolution"></a>Oplossing

Ingesteld op te lossen, de **ExecutionPolicy** naar **RemoteSigned** door het uitvoeren van de volgende opdracht uit in een verhoogde PowerShell-sessie (als Administrator uitvoeren):

```powershell
Set-ExecutionPolicy RemoteSigned
```
