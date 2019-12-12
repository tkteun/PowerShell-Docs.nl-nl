---
title: Standaard leden sets voor objecten definiëren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: 2d634e7638ec0e0117d65ca0b2d08e68f0068a03
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359380"
---
# <a name="defining-default-member-sets-for-objects"></a>Standaardledenreeksen voor objecten definiëren

De ledenset PSStandardMembers wordt gebruikt door Windows Power shell om de standaard eigenschappen sets voor een object te definiëren. De standaard eigenschappen sets kunnen worden gebruikt door opdrachten als de opmaak-cmdlets om alleen de eigenschappen weer te geven die zijn gedefinieerd door de eigenschappenset. De standaard eigenschappen sets zijn DefaultDisplayProperty, DefaultDisplayPropertySet en DefaultKeyPropertySet. Windows Power shell negeert alle andere leden sets en andere eigenschappen sets die zijn toegevoegd aan de PSStandardMembers-ledenset.

## <a name="member-set-for-systemdiagnosticsprocess"></a>Ledenset voor System. Diagnostics. process

In het volgende voor beeld definieert de ledenset PSStandardMembers de eigenschap DefaultDisplayPropertySet die is ingesteld voor [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objecten. Deze eigenschappenset wordt gebruikt door de [indeling-List-](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.

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

In de volgende uitvoer ziet u de standaard eigenschappen die worden geretourneerd door de [indeling-List-](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet. Voor elk proces object worden alleen de eigenschappen `Id`, `Handles`, `CPU`en `Name` geretourneerd.

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

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
