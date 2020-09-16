---
title: Een argument patroon valideren | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidatePattern attribute, example
ms.openlocfilehash: 35104e786d4b809a711d97fea52ae0e348dd5ca3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782086"
---
# <a name="how-to-validate-an-argument-pattern"></a>Een argumentenpatroon valideren

In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om het teken patroon van het parameter argument te controleren voordat de cmdlet wordt uitgevoerd. U stelt deze validatie regel in door het kenmerk ValidatePattern te declareren.

> [!NOTE]
> Zie [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.

## <a name="to-validate-an-argument-pattern"></a>Een argument patroon valideren

- Voeg het kenmerk validate toe, zoals wordt weer gegeven in de volgende code. In dit voor beeld wordt een patroon van vier cijfers opgegeven, waarbij elk cijfer een waarde van 0 tot en met 9 heeft.

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

Zie [ValidatePattern kenmerk declaratie](./validatepattern-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.

## <a name="see-also"></a>Zie ook

[Declaratie van het kenmerk ValidatePattern](./validatepattern-attribute-declaration.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
