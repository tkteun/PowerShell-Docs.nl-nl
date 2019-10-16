---
title: Een argument patroon valideren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356313"
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

[ValidatePattern kenmerk declaratie](./validatepattern-attribute-declaration.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
