---
title: Standaard leden sets voor objecten definiëren | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 80e1f54890d3aac1702414699ead16fcf38271e1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774623"
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

In de volgende uitvoer ziet u de standaard eigenschappen die worden geretourneerd door de [indeling-List-](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet. Alleen de `Id` `Handles` Eigenschappen,, en `CPU` `Name` worden voor elk proces object geretourneerd.

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

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
