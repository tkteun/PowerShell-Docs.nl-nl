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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356299"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="98df7-102">Transacties ondersteunen</span><span class="sxs-lookup"><span data-stu-id="98df7-102">How to Support Transactions</span></span>

<span data-ttu-id="98df7-103">In dit voor beeld worden de basis code-elementen weer gegeven die ondersteuning voor trans acties toevoegen aan een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="98df7-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98df7-104">Zie [about trans actions][about_Transactions](Engelstalig) voor meer informatie over het verwerken van trans acties in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="98df7-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="98df7-105">Voor de ondersteuning van trans acties</span><span class="sxs-lookup"><span data-stu-id="98df7-105">To support transactions</span></span>

1. <span data-ttu-id="98df7-106">Wanneer u het cmdlet-kenmerk declareert, geeft u op dat de cmdlet trans acties ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="98df7-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="98df7-107">Wanneer de cmdlet trans acties ondersteunt, voegt Windows Power shell de para meter `UseTransaction` aan de cmdlet toe wanneer deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="98df7-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="98df7-108">Voeg binnen een van de invoer verwerkings methoden een `if` blok toe om te bepalen of een trans actie beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="98df7-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="98df7-109">Als de `if`-instructie wordt omgezet in `true`, kunnen de acties binnen deze instructie worden uitgevoerd in de context van de huidige trans actie.</span><span class="sxs-lookup"><span data-stu-id="98df7-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="98df7-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="98df7-110">See Also</span></span>

[<span data-ttu-id="98df7-111">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="98df7-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
