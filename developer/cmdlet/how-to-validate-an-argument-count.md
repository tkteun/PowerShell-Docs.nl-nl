---
title: Het valideren van een aantal argumenten | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067804"
---
# <a name="how-to-validate-an-argument-count"></a>Het aantal argumenten valideren

Dit voorbeeld laat zien hoe u kunt een regel voor het valideren dat de runtime van de Windows PowerShell gebruiken kunt om te controleren of het aantal argumenten (aantal) die een parameter accepteert opgeven voordat de cmdlet wordt uitgevoerd. U kunt deze regel voor het valideren instellen door op te geven het kenmerk ValidateCount.

> [!NOTE]
> Zie voor meer informatie over de klasse die dit kenmerk definieert, [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).

## <a name="to-validate-an-argument-count"></a>Een aantal argumenten valideren

- Voeg het kenmerk valideren zoals wordt weergegeven in de volgende code. In dit voorbeeld geeft aan dat de parameter één argument of maximaal drie argumenten accepteert.

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

Zie voor meer informatie over hoe u dit kenmerk declareren [ValidateCount kenmerkdeclaratie](./validatecount-attribute-declaration.md).

## <a name="see-also"></a>Zie ook

[ValidateCount kenmerk declaratie](./validatecount-attribute-declaration.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
