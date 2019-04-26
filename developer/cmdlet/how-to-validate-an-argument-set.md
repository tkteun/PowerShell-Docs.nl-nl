---
title: Het valideren van een Set voor Argument | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067707"
---
# <a name="how-to-validate-an-argument-set"></a>Een argumentenreeks valideren

In dit voorbeeld laat zien hoe om op te geven van een regel voor het valideren dat de runtime van de Windows PowerShell gebruiken kunt om te controleren op het parameterargument voordat de cmdlet wordt uitgevoerd. Deze regel voor het valideren biedt een set met geldige waarden voor de parameterargument.

> [!NOTE]
> Zie voor meer informatie over de klasse die dit kenmerk definieert, [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).

## <a name="to-validate-an-argument-set"></a>Voor het valideren van een argument instellen

- Voeg het kenmerk ValidateSet zoals wordt weergegeven in de volgende code. In dit voorbeeld geeft een reeks van drie mogelijke waarden voor de `UserName` parameter.

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

Zie voor meer informatie over hoe u dit kenmerk declareren [ValidateSet kenmerkdeclaratie](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[ValidateSet kenmerk declaratie](./validateset-attribute-declaration.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
