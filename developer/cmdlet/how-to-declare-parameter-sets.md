---
title: Hoe om te declareren parametersets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067889"
---
# <a name="how-to-declare-parameter-sets"></a>Parametersets declareren

In dit voorbeeld ziet u hoe u twee parametersets wanneer u de parameters voor een cmdlet declareren. Elke parameterset is zowel een unieke parameter als een gedeelde parameter die wordt gebruikt door beide parametersets. Zie voor meer informatie over parameters sets, met inbegrip van het opgeven van de parameter standaardset [Cmdlet-Parameter stelt](./cmdlet-parameter-sets.md).

> [!IMPORTANT]
> Indien mogelijk, definieert u de unieke parameter van een parameter is ingesteld als een vereiste parameter. Als u wilt dat de cmdlet uit te voeren zonder parameters op te geven, kan de unieke parameter echter een optionele parameter zijn. Bijvoorbeeld, de unieke parameter van de `Get-Command` cmdlet is optioneel.

## <a name="how-to-define-two-parameter-sets"></a>Over het definiëren van twee parametersets

1. Voeg de `ParameterSet` sleutelwoord met de Parameter-kenmerk voor de unieke parameter van de eerste parameter is ingesteld.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. Voeg de `ParameterSet` sleutelwoord met de Parameter-kenmerk voor de unieke parameter van de tweede parameter is ingesteld.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. Voor de parameter die deel uitmaakt van beide parametersets, Voeg een parameterkenmerk voor elke parameter is ingesteld en voeg vervolgens de `ParameterSet` sleutelwoord voor elke set. In elk kenmerk Parameter kunt u opgeven hoe deze parameter wordt gedefinieerd. Een parameter kan worden in één set optioneel en verplichte in een andere.

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a>Zie ook

[Hiermee stelt u cmdlet-Parameter](./cmdlet-parameter-sets.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
