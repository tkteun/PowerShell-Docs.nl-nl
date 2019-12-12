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
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="25437-102">Standaardledenreeksen voor objecten definiëren</span><span class="sxs-lookup"><span data-stu-id="25437-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="25437-103">De ledenset PSStandardMembers wordt gebruikt door Windows Power shell om de standaard eigenschappen sets voor een object te definiëren.</span><span class="sxs-lookup"><span data-stu-id="25437-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="25437-104">De standaard eigenschappen sets kunnen worden gebruikt door opdrachten als de opmaak-cmdlets om alleen de eigenschappen weer te geven die zijn gedefinieerd door de eigenschappenset.</span><span class="sxs-lookup"><span data-stu-id="25437-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="25437-105">De standaard eigenschappen sets zijn DefaultDisplayProperty, DefaultDisplayPropertySet en DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="25437-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="25437-106">Windows Power shell negeert alle andere leden sets en andere eigenschappen sets die zijn toegevoegd aan de PSStandardMembers-ledenset.</span><span class="sxs-lookup"><span data-stu-id="25437-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="25437-107">Ledenset voor System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="25437-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="25437-108">In het volgende voor beeld definieert de ledenset PSStandardMembers de eigenschap DefaultDisplayPropertySet die is ingesteld voor [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objecten.</span><span class="sxs-lookup"><span data-stu-id="25437-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="25437-109">Deze eigenschappenset wordt gebruikt door de [indeling-List-](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="25437-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="25437-110">In de volgende uitvoer ziet u de standaard eigenschappen die worden geretourneerd door de [indeling-List-](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="25437-110">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="25437-111">Voor elk proces object worden alleen de eigenschappen `Id`, `Handles`, `CPU`en `Name` geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="25437-111">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="25437-112">Zie ook</span><span class="sxs-lookup"><span data-stu-id="25437-112">See Also</span></span>

[<span data-ttu-id="25437-113">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="25437-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
