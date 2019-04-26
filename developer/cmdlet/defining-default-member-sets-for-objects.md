---
title: Hiermee stelt u standaardlid voor objecten te definiëren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: 2d634e7638ec0e0117d65ca0b2d08e68f0068a03
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068246"
---
# <a name="defining-default-member-sets-for-objects"></a>Standaardledenreeksen voor objecten definiëren

De ledenset PSStandardMembers wordt gebruikt door Windows PowerShell voor het definiëren van de standaardsets de eigenschap voor een object. De eigenschap standaardsets kunnen worden gebruikt door opdrachten, zoals de opmaak-cmdlets om weer te geven alleen de eigenschappen die zijn gedefinieerd door de eigenschap is ingesteld. De eigenschap standaardsets zijn DefaultDisplayProperty DefaultDisplayPropertySet en DefaultKeyPropertySet. Windows PowerShell wordt genegeerd voor alle andere sets lid en eventuele andere eigenschappensets toegevoegd aan de set van PSStandardMembers lid.

## <a name="member-set-for-systemdiagnosticsprocess"></a>Ledenset voor System.Diagnostics.Process

In het volgende voorbeeld definieert de ledenset PSStandardMembers de DefaultDisplayPropertySet eigenschap is ingesteld voor [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objecten. Deze eigenschap is ingesteld, wordt gebruikt door de [lijst indeling](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.

```xml
<Type>
  <Name>System.Diagnostics.Process</Name>
  <Members>
    <MemberSet>
     <Name>PSStandardMembers</Name>
     <Members>
       <PropertySet>
         <Name>DefaultDisplayPropertySet</Name>
         <ReferencedProperties>
           <Name>Id</Name>
           <Name>Handles</Name>
           <Name>CPU</Name>
           <Name>Name</Name>
         </ReferencedProperties>
      </PropertySet>
    </Members>
  </MemberSet>
```

De volgende uitvoer ziet u de standaard-eigenschappen die wordt geretourneerd door de [lijst indeling](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet. Alleen de `Id`, `Handles`, `CPU`, en `Name` eigenschappen worden geretourneerd voor elk procesobject.

```powershell
Get-Process | format-list
```

```output
Id      : 2036
Handles : 27
CPU     :
Name    : AEADISRV

Id      : 272
Handles : 38
CPU     :
Name    : agrsmsvc
...
```

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
