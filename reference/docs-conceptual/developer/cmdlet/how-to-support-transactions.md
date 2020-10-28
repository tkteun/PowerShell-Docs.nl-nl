---
ms.date: 09/13/2016
ms.topic: reference
title: Transacties ondersteunen
description: Transacties ondersteunen
ms.openlocfilehash: 5691c246830dab9f4808801c04353ebfb2c3e981
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666957"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="384b7-103">Transacties ondersteunen</span><span class="sxs-lookup"><span data-stu-id="384b7-103">How to Support Transactions</span></span>

<span data-ttu-id="384b7-104">In dit voor beeld worden de basis code-elementen weer gegeven die ondersteuning voor trans acties toevoegen aan een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="384b7-104">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="384b7-105">Zie [about trans actions][about_Transactions](Engelstalig) voor meer informatie over het verwerken van trans acties in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="384b7-105">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="384b7-106">Voor de ondersteuning van trans acties</span><span class="sxs-lookup"><span data-stu-id="384b7-106">To support transactions</span></span>

1. <span data-ttu-id="384b7-107">Wanneer u het cmdlet-kenmerk declareert, geeft u op dat de cmdlet trans acties ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="384b7-107">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="384b7-108">Wanneer de cmdlet trans acties ondersteunt, voegt Windows Power shell de `UseTransaction` para meter aan de cmdlet toe wanneer deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="384b7-108">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="384b7-109">Voeg binnen een van de invoer verwerkings methoden een `if` blok toe om te bepalen of een trans actie beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="384b7-109">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="384b7-110">Als de `if` instructie wordt omgezet in `true` , kunnen de acties binnen deze instructie worden uitgevoerd in de context van de huidige trans actie.</span><span class="sxs-lookup"><span data-stu-id="384b7-110">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="384b7-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="384b7-111">See Also</span></span>

[<span data-ttu-id="384b7-112">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="384b7-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
