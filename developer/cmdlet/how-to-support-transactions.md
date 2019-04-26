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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067855"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="419db-102">Transacties ondersteunen</span><span class="sxs-lookup"><span data-stu-id="419db-102">How to Support Transactions</span></span>

<span data-ttu-id="419db-103">In dit voorbeeld ziet u de basic-code-elementen die ondersteuning voor transacties aan een cmdlet toevoegen.</span><span class="sxs-lookup"><span data-stu-id="419db-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="419db-104">Zie voor meer informatie over hoe Windows PowerShell transacties verwerkt [over transacties][about_Transactions].</span><span class="sxs-lookup"><span data-stu-id="419db-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="419db-105">Ter ondersteuning van transacties</span><span class="sxs-lookup"><span data-stu-id="419db-105">To support transactions</span></span>

1. <span data-ttu-id="419db-106">Wanneer u de Cmdlet-kenmerk declareert, moet u opgeven dat de cmdlet biedt ondersteuning voor transacties.</span><span class="sxs-lookup"><span data-stu-id="419db-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="419db-107">Wanneer de cmdlet biedt ondersteuning voor transacties, Windows PowerShell wordt toegevoegd de `UseTransaction` parameter aan de cmdlet wanneer deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="419db-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="419db-108">Binnen een van de verwerking van methoden invoer toevoegen een `if` blokkeren om te bepalen of een transactie beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="419db-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="419db-109">Als de `if` instructie wordt omgezet naar `true`, de acties binnen deze instructie kunnen worden uitgevoerd binnen de context van de huidige transactie.</span><span class="sxs-lookup"><span data-stu-id="419db-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="419db-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="419db-110">See Also</span></span>

[<span data-ttu-id="419db-111">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="419db-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
