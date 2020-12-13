---
ms.date: 09/13/2016
ms.topic: reference
title: Een argumentenreeks valideren
description: Een argumentenreeks valideren
ms.openlocfilehash: 50ec0a48277893584d896e14ad6aa843682a28cc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650367"
---
# <a name="how-to-validate-an-argument-set"></a>Een argumentenreeks valideren

In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om het parameter argument te controleren voordat de cmdlet wordt uitgevoerd. Deze validatie regel bevat een set van de geldige waarden voor het parameter argument.

> [!NOTE]
> Zie [System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.

## <a name="to-validate-an-argument-set"></a>Een argumentset valideren

- Voeg het kenmerk validate toe, zoals in de volgende code wordt weer gegeven. In dit voor beeld wordt een set van drie mogelijke waarden voor de `UserName` para meter opgegeven.

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

Zie [Validate-kenmerk declaratie](./validateset-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.

## <a name="see-also"></a>Zie ook

[System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Declaratie van het kenmerk ValidateSet](./validateset-attribute-declaration.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
