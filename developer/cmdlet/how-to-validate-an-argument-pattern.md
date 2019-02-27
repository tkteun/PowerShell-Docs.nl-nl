---
title: Het valideren van een patroon Argument | Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846156"
---
# <a name="how-to-validate-an-argument-pattern"></a>Een argumentenpatroon valideren

In dit voorbeeld laat zien hoe om op te geven van een regel voor het valideren dat de runtime van de Windows PowerShell gebruiken kunt om te controleren op het teken-patroon van de parameterargument voordat de cmdlet wordt uitgevoerd. U kunt deze regel voor het valideren instellen door op te geven het kenmerk ValidatePattern.

> [!NOTE]
> Zie voor meer informatie over de klasse die dit kenmerk definieert, [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).

## <a name="to-validate-an-argument-pattern"></a>Voor het valideren van een argument-patroon

- Voeg het kenmerk valideren zoals wordt weergegeven in de volgende code. Dit voorbeeld wordt een patroon van vier cijfers, waarbij elk cijfer een waarde van 0 t/m 9 heeft.

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

Zie voor meer informatie over hoe u dit kenmerk declareren [ValidatePattern kenmerkdeclaratie](./validatepattern-attribute-declaration.md).

## <a name="see-also"></a>Zie ook

[ValidatePattern kenmerk declaratie](./validatepattern-attribute-declaration.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
