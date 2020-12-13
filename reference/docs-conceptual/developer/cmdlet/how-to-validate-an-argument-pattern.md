---
ms.date: 09/13/2016
ms.topic: reference
title: Een argumentenpatroon valideren
description: Een argumentenpatroon valideren
ms.openlocfilehash: ab5777c918a53c0a3900f87c52e7f14f9cb9b726
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666906"
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
