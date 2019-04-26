---
title: Het valideren van de lengte van het Argument | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067706"
---
# <a name="how-to-validate-the-argument-length"></a>Een argumentlengte valideren

In dit voorbeeld laat zien hoe om op te geven van een regel voor het valideren dat de runtime van de Windows PowerShell gebruiken kunt om te controleren op het aantal tekens (de lengte) van de parameterargument voordat de cmdlet wordt uitgevoerd. U kunt deze regel voor het valideren instellen door op te geven het kenmerk ValidateLength.

> [!NOTE]
> Zie voor meer informatie over de klasse die dit kenmerk definieert, [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).

## <a name="to-validate-the-argument-length"></a>De lengte van het argument valideren

- Voeg het kenmerk valideren zoals wordt weergegeven in de volgende code. In dit voorbeeld geeft aan dat de lengte van het argument een lengte van 0 tot en met 10 tekens moet zijn.

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

Zie voor meer informatie over hoe u dit kenmerk declareren [ValidateLength kenmerkdeclaratie](./validatelength-attribute-declaration.md).

## <a name="see-also"></a>Zie ook

[ValidateLength kenmerk declaratie](./validatelength-attribute-declaration.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
