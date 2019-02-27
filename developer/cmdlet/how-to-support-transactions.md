---
title: Hoe transacties worden ondersteund | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847591"
---
# <a name="how-to-support-transactions"></a>Transacties ondersteunen

In dit voorbeeld ziet u de basic-code-elementen die ondersteuning voor transacties aan een cmdlet toevoegen.

> [!IMPORTANT]
> Zie voor meer informatie over hoe Windows PowerShell transacties verwerkt [over transacties][about_Transactions].

## <a name="to-support-transactions"></a>Ter ondersteuning van transacties

1. Wanneer u de Cmdlet-kenmerk declareert, moet u opgeven dat de cmdlet biedt ondersteuning voor transacties.
   Wanneer de cmdlet biedt ondersteuning voor transacties, Windows PowerShell wordt toegevoegd de `UseTransaction` parameter aan de cmdlet wanneer deze wordt uitgevoerd.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. Binnen een van de verwerking van methoden invoer toevoegen een `if` blokkeren om te bepalen of een transactie beschikbaar is.
   Als de `if` instructie wordt omgezet naar `true`, de acties binnen deze instructie kunnen worden uitgevoerd binnen de context van de huidige transactie.

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
