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
# <a name="how-to-support-transactions"></a><span data-ttu-id="e402d-102">Transacties ondersteunen</span><span class="sxs-lookup"><span data-stu-id="e402d-102">How to Support Transactions</span></span>

<span data-ttu-id="e402d-103">In dit voor beeld worden de basis code-elementen weer gegeven die ondersteuning voor trans acties toevoegen aan een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e402d-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e402d-104">Zie [about trans actions][about_Transactions](Engelstalig) voor meer informatie over het verwerken van trans acties in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="e402d-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="e402d-105">Voor de ondersteuning van trans acties</span><span class="sxs-lookup"><span data-stu-id="e402d-105">To support transactions</span></span>

1. <span data-ttu-id="e402d-106">Wanneer u het cmdlet-kenmerk declareert, geeft u op dat de cmdlet trans acties ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="e402d-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="e402d-107">Wanneer de cmdlet trans acties ondersteunt, voegt Windows Power shell de para meter `UseTransaction` toe aan de cmdlet wanneer deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e402d-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="e402d-108">Voeg binnen een van de invoer verwerkings methoden een Block `if` toe om te bepalen of een trans actie beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="e402d-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="e402d-109">Als de instructie `if` wordt omgezet in `true`, kunnen de acties binnen deze instructie worden uitgevoerd in de context van de huidige trans actie.</span><span class="sxs-lookup"><span data-stu-id="e402d-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="e402d-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e402d-110">See Also</span></span>

[<span data-ttu-id="e402d-111">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="e402d-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
