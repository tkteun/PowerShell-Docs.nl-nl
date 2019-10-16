---
title: Een argument set valideren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356278"
---
# <a name="how-to-validate-an-argument-set"></a>Een argumentenreeks valideren

In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om het parameter argument te controleren voordat de cmdlet wordt uitgevoerd. Deze validatie regel bevat een set van de geldige waarden voor het parameter argument.

> [!NOTE]
> Zie [System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.

## <a name="to-validate-an-argument-set"></a>Een argumentset valideren

- Voeg het kenmerk validate toe, zoals in de volgende code wordt weer gegeven. In dit voor beeld wordt een set van drie mogelijke waarden opgegeven voor de para meter `UserName`.

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

[Verklaring van de kenmerkset validate](./validateset-attribute-declaration.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
