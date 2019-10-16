---
title: Het ondersteunen van trans acties | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356299"
---
# <a name="how-to-support-transactions"></a>Transacties ondersteunen

In dit voor beeld worden de basis code-elementen weer gegeven die ondersteuning voor trans acties toevoegen aan een cmdlet.

> [!IMPORTANT]
> Zie [about trans actions][about_Transactions](Engelstalig) voor meer informatie over het verwerken van trans acties in Windows Power shell.

## <a name="to-support-transactions"></a>Voor de ondersteuning van trans acties

1. Wanneer u het cmdlet-kenmerk declareert, geeft u op dat de cmdlet trans acties ondersteunt.
   Wanneer de cmdlet trans acties ondersteunt, voegt Windows Power shell de para meter `UseTransaction` toe aan de cmdlet wanneer deze wordt uitgevoerd.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. Voeg binnen een van de invoer verwerkings methoden een Block `if` toe om te bepalen of een trans actie beschikbaar is.
   Als de instructie `if` wordt omgezet in `true`, kunnen de acties binnen deze instructie worden uitgevoerd in de context van de huidige trans actie.

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

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
