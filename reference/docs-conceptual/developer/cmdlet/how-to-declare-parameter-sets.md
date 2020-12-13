---
ms.date: 09/13/2016
ms.topic: reference
title: Parametersets declareren
description: Parametersets declareren
ms.openlocfilehash: bd4d504a9fe6c7f7626901c49bc08851244f0995
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667059"
---
# <a name="how-to-declare-parameter-sets"></a>Parametersets declareren

In dit voor beeld ziet u hoe u twee parameter sets definieert wanneer u de para meters voor een cmdlet declareert. Elke parameterset heeft zowel een unieke para meter als een gedeelde para meter die wordt gebruikt door beide parameter sets. Zie [para meters](./cmdlet-parameter-sets.md)voor de cmdlet voor meer informatie over parameters sets, zoals het opgeven van de standaard parameterset.

> [!IMPORTANT]
> Als dat mogelijk is, definieert u de unieke para meter van een para meter die is ingesteld als een vereiste para meter. Als u de cmdlet echter wilt uitvoeren zonder para meters op te geven, kunt u een optionele para meter opgeven. Zo is de unieke para meter van de `Get-Command` cmdlet optioneel.

## <a name="how-to-define-two-parameter-sets"></a>Twee parameter sets definiëren

1. Voeg het `ParameterSet` tref woord toe aan het parameter kenmerk voor de unieke para meter van de eerste parameterset.

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

2. Voeg het `ParameterSet` tref woord toe aan het parameter kenmerk voor de unieke para meter van de tweede parameterset.

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

3. Voor de para meter die deel uitmaakt van beide parameter sets, voegt u een parameter kenmerk toe voor elke parameterset en voegt u vervolgens het `ParameterSet` tref woord toe aan elke set. In elk parameter kenmerk kunt u opgeven hoe die para meter wordt gedefinieerd. Een para meter kan optioneel zijn in een set en verplicht in een andere.

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

[Parametersets voor cmdlets](./cmdlet-parameter-sets.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
