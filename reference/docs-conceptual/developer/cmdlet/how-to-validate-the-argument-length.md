---
title: De lengte van het argument valideren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, example
ms.assetid: d5ddaa6e-4904-46da-beb0-0295a8f38332
caps.latest.revision: 12
ms.openlocfilehash: 8a21675acd087df93f93c25952c78931255d60b3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356264"
---
# <a name="how-to-validate-the-argument-length"></a>Een argumentlengte valideren

In dit voor beeld ziet u hoe u een validatie regel opgeeft die door Windows Power shell runtime kan worden gebruikt om het aantal tekens (de lengte) van het parameter argument te controleren voordat de cmdlet wordt uitgevoerd. U stelt deze validatie regel in door het kenmerk ValidateLength te declareren.

> [!NOTE]
> Zie [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.

## <a name="to-validate-the-argument-length"></a>De lengte van het argument valideren

- Voeg het kenmerk validate toe, zoals wordt weer gegeven in de volgende code. In dit voor beeld wordt opgegeven dat de lengte van het argument een lengte van 0 tot 10 tekens moet hebben.

    ```csharp
    [ValidateLength(0, 10)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Zie [ValidateLength kenmerk declaratie](./validatelength-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.

## <a name="see-also"></a>Zie ook

[ValidateLength kenmerk declaratie](./validatelength-attribute-declaration.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
