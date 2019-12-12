---
title: Parameter sets declareren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356348"
---
# <a name="how-to-declare-parameter-sets"></a>Parametersets declareren

In dit voor beeld ziet u hoe u twee parameter sets definieert wanneer u de para meters voor een cmdlet declareert. Elke parameterset heeft zowel een unieke para meter als een gedeelde para meter die wordt gebruikt door beide parameter sets. Zie [para meters](./cmdlet-parameter-sets.md)voor de cmdlet voor meer informatie over parameters sets, zoals het opgeven van de standaard parameterset.

> [!IMPORTANT]
> Als dat mogelijk is, definieert u de unieke para meter van een para meter die is ingesteld als een vereiste para meter. Als u de cmdlet echter wilt uitvoeren zonder para meters op te geven, kunt u een optionele para meter opgeven. Zo is de unieke para meter van de cmdlet `Get-Command` optioneel.

## <a name="how-to-define-two-parameter-sets"></a>Twee parameter sets definiëren

1. Voeg het sleutel woord `ParameterSet` toe aan het parameter kenmerk voor de unieke para meter van de eerste parameterset.

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

2. Voeg het sleutel woord `ParameterSet` toe aan het parameter kenmerk voor de unieke para meter van de tweede parameterset.

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

3. Voor de para meter die deel uitmaakt van beide parameter sets, voegt u een parameter kenmerk toe voor elke parameterset en voegt u vervolgens het sleutel woord `ParameterSet` toe aan elke set. In elk parameter kenmerk kunt u opgeven hoe die para meter wordt gedefinieerd. Een para meter kan optioneel zijn in een set en verplicht in een andere.

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

[Cmdlet-parameter sets](./cmdlet-parameter-sets.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
