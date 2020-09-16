---
title: Een argument set valideren | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateSet attribute, example
ms.openlocfilehash: 6173f1380583f5b27e2b188990a5ea041f447c57
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782001"
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
