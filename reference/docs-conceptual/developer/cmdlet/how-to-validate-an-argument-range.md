---
title: Een argument bereik valideren | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateRange attribute, example
ms.openlocfilehash: b48b1b87425add51e855c48ec700c78c3ae296c1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782069"
---
# <a name="how-to-validate-an-argument-range"></a>Een argumentenbereik valideren

In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om de minimum-en maximum waarden van het parameter argument te controleren voordat de cmdlet wordt uitgevoerd. U stelt deze validatie regel in door het kenmerk ValidateRange te declareren.

> [!NOTE]
> Zie [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.

### <a name="to-validate-an-argument-range"></a>Een argument bereik valideren

- Voeg het kenmerk ValidateRange toe, zoals wordt weer gegeven in de volgende code. In dit voor beeld wordt een bereik van 0 tot 5 voor de `InputData` para meter opgegeven.

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

Zie [ValidateRange kenmerk declaratie](./validaterange-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.

## <a name="see-also"></a>Zie ook

[Declaratie van het kenmerk ValidateRange](./validaterange-attribute-declaration.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
