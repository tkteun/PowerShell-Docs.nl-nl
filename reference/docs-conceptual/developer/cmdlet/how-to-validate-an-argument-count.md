---
title: Het valideren van een argument aantal | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356292"
---
# <a name="how-to-validate-an-argument-count"></a>Het aantal argumenten valideren

In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om het aantal argumenten (de telling) te controleren dat door een para meter wordt geaccepteerd voordat de cmdlet wordt uitgevoerd. U stelt deze validatie regel in door het kenmerk ValidateCount te declareren.

> [!NOTE]
> Zie [System. Management. Automation. Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.

## <a name="to-validate-an-argument-count"></a>Een aantal argumenten valideren

- Voeg het kenmerk validate toe, zoals wordt weer gegeven in de volgende code. In dit voor beeld wordt aangegeven dat de para meter één argument of Maxi maal drie argumenten accepteert.

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

Zie [ValidateCount kenmerk declaratie](./validatecount-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.

## <a name="see-also"></a>Zie ook

[ValidateCount kenmerk declaratie](./validatecount-attribute-declaration.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
