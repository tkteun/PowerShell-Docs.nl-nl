---
ms.date: 09/13/2016
ms.topic: reference
title: Standaardledenreeksen voor objecten definiëren
description: Standaardledenreeksen voor objecten definiëren
ms.openlocfilehash: 919f7ba65322c6a56a27e046fb211bde151abf7d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653124"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="37664-103">Standaardledenreeksen voor objecten definiëren</span><span class="sxs-lookup"><span data-stu-id="37664-103">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="37664-104">De ledenset PSStandardMembers wordt gebruikt door Windows Power shell om de standaard eigenschappen sets voor een object te definiëren.</span><span class="sxs-lookup"><span data-stu-id="37664-104">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="37664-105">De standaard eigenschappen sets kunnen worden gebruikt door opdrachten als de opmaak-cmdlets om alleen de eigenschappen weer te geven die zijn gedefinieerd door de eigenschappenset.</span><span class="sxs-lookup"><span data-stu-id="37664-105">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="37664-106">De standaard eigenschappen sets zijn DefaultDisplayProperty, DefaultDisplayPropertySet en DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="37664-106">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="37664-107">Windows Power shell negeert alle andere leden sets en andere eigenschappen sets die zijn toegevoegd aan de PSStandardMembers-ledenset.</span><span class="sxs-lookup"><span data-stu-id="37664-107">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="37664-108">Ledenset voor System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="37664-108">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="37664-109">In het volgende voor beeld definieert de ledenset PSStandardMembers de eigenschap DefaultDisplayPropertySet die is ingesteld voor [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objecten.</span><span class="sxs-lookup"><span data-stu-id="37664-109">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="37664-110">Deze eigenschappenset wordt gebruikt door de [indeling-List-](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="37664-110">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="37664-111">In de volgende uitvoer ziet u de standaard eigenschappen die worden geretourneerd door de [indeling-List-](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="37664-111">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="37664-112">Alleen de `Id` `Handles` Eigenschappen,, en `CPU` `Name` worden voor elk proces object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="37664-112">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="37664-113">Zie ook</span><span class="sxs-lookup"><span data-stu-id="37664-113">See Also</span></span>

[<span data-ttu-id="37664-114">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="37664-114">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
