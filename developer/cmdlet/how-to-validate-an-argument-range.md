---
title: Het valideren van het bereik van een Argument | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067787"
---
# <a name="how-to-validate-an-argument-range"></a>Een argumentenbereik valideren

In dit voorbeeld laat zien hoe om op te geven van een regel voor het valideren dat de runtime van de Windows PowerShell gebruiken kunt om te controleren of de minimale en maximale waarden van de parameterargument voordat de cmdlet wordt uitgevoerd. U kunt deze regel voor het valideren instellen door op te geven het kenmerk ValidateRange.

> [!NOTE]
> Zie voor meer informatie over de klasse die dit kenmerk definieert, [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).

### <a name="to-validate-an-argument-range"></a>Een argument adresbereik valideren

- Voeg het kenmerk ValidateRange zoals wordt weergegeven in de volgende code. In dit voorbeeld geeft een bereik van 0 tot en met 5 voor de `InputData` parameter.

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

Zie voor meer informatie over hoe u dit kenmerk declareren [ValidateRange kenmerkdeclaratie](./validaterange-attribute-declaration.md).

## <a name="see-also"></a>Zie ook

[ValidateRange kenmerk declaratie](./validaterange-attribute-declaration.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
