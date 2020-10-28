---
ms.date: 09/13/2016
ms.topic: reference
title: Het aantal argumenten valideren
description: Het aantal argumenten valideren
ms.openlocfilehash: 46a32d61138fb50bceea98171f76749c9d96734d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666940"
---
# <a name="how-to-validate-an-argument-count"></a>Het aantal argumenten valideren

In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om het aantal argumenten (de telling) te controleren dat door een para meter wordt geaccepteerd voordat de cmdlet wordt uitgevoerd. U stelt deze validatie regel in door het kenmerk ValidateCount te declareren.

> [!NOTE]
> Zie [System. Management. Automation. Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.

## <a name="to-validate-an-argument-count"></a>Een aantal argumenten valideren

- Voeg het kenmerk validate toe, zoals wordt weer gegeven in de volgende code. In dit voor beeld wordt aangegeven dat de para meter één argument of Maxi maal drie argumenten accepteert.

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

Zie [ValidateCount kenmerk declaratie](./validatecount-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.

## <a name="see-also"></a>Zie ook

[Declaratie van het kenmerk ValidateCount](./validatecount-attribute-declaration.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
