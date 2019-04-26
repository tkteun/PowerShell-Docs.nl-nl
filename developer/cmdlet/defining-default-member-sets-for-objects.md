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
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="3e5f3-102">Standaardledenreeksen voor objecten definiëren</span><span class="sxs-lookup"><span data-stu-id="3e5f3-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="3e5f3-103">De ledenset PSStandardMembers wordt gebruikt door Windows PowerShell voor het definiëren van de standaardsets de eigenschap voor een object.</span><span class="sxs-lookup"><span data-stu-id="3e5f3-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="3e5f3-104">De eigenschap standaardsets kunnen worden gebruikt door opdrachten, zoals de opmaak-cmdlets om weer te geven alleen de eigenschappen die zijn gedefinieerd door de eigenschap is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="3e5f3-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="3e5f3-105">De eigenschap standaardsets zijn DefaultDisplayProperty DefaultDisplayPropertySet en DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="3e5f3-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="3e5f3-106">Windows PowerShell wordt genegeerd voor alle andere sets lid en eventuele andere eigenschappensets toegevoegd aan de set van PSStandardMembers lid.</span><span class="sxs-lookup"><span data-stu-id="3e5f3-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="3e5f3-107">Ledenset voor System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="3e5f3-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="3e5f3-108">In het volgende voorbeeld definieert de ledenset PSStandardMembers de DefaultDisplayPropertySet eigenschap is ingesteld voor [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objecten.</span><span class="sxs-lookup"><span data-stu-id="3e5f3-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="3e5f3-109">Deze eigenschap is ingesteld, wordt gebruikt door de [lijst indeling](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3e5f3-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="3e5f3-110">De volgende uitvoer ziet u de standaard-eigenschappen die wordt geretourneerd door de [lijst indeling](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3e5f3-110">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="3e5f3-111">Alleen de `Id`, `Handles`, `CPU`, en `Name` eigenschappen worden geretourneerd voor elk procesobject.</span><span class="sxs-lookup"><span data-stu-id="3e5f3-111">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3e5f3-112">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3e5f3-112">See Also</span></span>

[<span data-ttu-id="3e5f3-113">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e5f3-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
