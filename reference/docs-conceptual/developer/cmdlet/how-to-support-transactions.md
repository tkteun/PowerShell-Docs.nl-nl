---
title: Het ondersteunen van trans acties | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6fda27394091195b589afef5ee53c6d3bec4efc0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786608"
---
# <a name="how-to-support-transactions"></a>Transacties ondersteunen

In dit voor beeld worden de basis code-elementen weer gegeven die ondersteuning voor trans acties toevoegen aan een cmdlet.

> [!IMPORTANT]
> Zie [about trans actions][about_Transactions](Engelstalig) voor meer informatie over het verwerken van trans acties in Windows Power shell.

## <a name="to-support-transactions"></a>Voor de ondersteuning van trans acties

1. Wanneer u het cmdlet-kenmerk declareert, geeft u op dat de cmdlet trans acties ondersteunt.
   Wanneer de cmdlet trans acties ondersteunt, voegt Windows Power shell de `UseTransaction` para meter aan de cmdlet toe wanneer deze wordt uitgevoerd.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. Voeg binnen een van de invoer verwerkings methoden een `if` blok toe om te bepalen of een trans actie beschikbaar is.
   Als de `if` instructie wordt omgezet in `true` , kunnen de acties binnen deze instructie worden uitgevoerd in de context van de huidige trans actie.

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

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
