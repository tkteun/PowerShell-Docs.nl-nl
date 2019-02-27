---
title: WideControl-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849488"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="e2f21-102">Het element WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e2f21-102">WideControl Element (Format)</span></span>

<span data-ttu-id="e2f21-103">Definieert een breed (één waarde) lijstweergave voor de weergave.</span><span class="sxs-lookup"><span data-stu-id="e2f21-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="e2f21-104">Deze weergave bevat een waarde van één eigenschap of een Scriptwaarde voor elk object.</span><span class="sxs-lookup"><span data-stu-id="e2f21-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="e2f21-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) WideControl Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e2f21-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e2f21-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e2f21-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2f21-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e2f21-107">Attributes and Elements</span></span>

<span data-ttu-id="e2f21-108">De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `WideControl` element.</span><span class="sxs-lookup"><span data-stu-id="e2f21-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="e2f21-109">U kunt geen opgeven de `AutoSize` en `ColumnNumber` elementen op hetzelfde moment.</span><span class="sxs-lookup"><span data-stu-id="e2f21-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2f21-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e2f21-110">Attributes</span></span>

<span data-ttu-id="e2f21-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="e2f21-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2f21-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e2f21-112">Child Elements</span></span>

|<span data-ttu-id="e2f21-113">Element</span><span class="sxs-lookup"><span data-stu-id="e2f21-113">Element</span></span>|<span data-ttu-id="e2f21-114">Description</span><span class="sxs-lookup"><span data-stu-id="e2f21-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2f21-115">AutoSize-Element voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="e2f21-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="e2f21-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e2f21-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e2f21-117">Hiermee geeft u op of de kolomgrootte en het aantal kolommen zijn aangepast op basis van de grootte van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="e2f21-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="e2f21-118">ColumnNumber-Element voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="e2f21-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="e2f21-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e2f21-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e2f21-120">Hiermee geeft u het aantal kolommen in de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="e2f21-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="e2f21-121">WideEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="e2f21-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="e2f21-122">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="e2f21-122">Required element.</span></span><br /><br /> <span data-ttu-id="e2f21-123">Bevat de definities van de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="e2f21-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e2f21-124">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e2f21-124">Parent Elements</span></span>

|<span data-ttu-id="e2f21-125">Element</span><span class="sxs-lookup"><span data-stu-id="e2f21-125">Element</span></span>|<span data-ttu-id="e2f21-126">Description</span><span class="sxs-lookup"><span data-stu-id="e2f21-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2f21-127">Weergave-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e2f21-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="e2f21-128">Hiermee definieert u een weergave die wordt gebruikt om een of meer .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e2f21-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e2f21-129">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e2f21-129">Remarks</span></span>

<span data-ttu-id="e2f21-130">Bij het definiëren van een brede weergave, kunt u toevoegen de `AutoSize` element of de `ColumnNumber` , maar u kunt beide niet toevoegen.</span><span class="sxs-lookup"><span data-stu-id="e2f21-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="e2f21-131">In de meeste gevallen slechts één definitie is vereist voor elke brede weergave, maar het is mogelijk dat meerdere definities als u wilt de dezelfde weergave gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e2f21-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="e2f21-132">In deze gevallen kunt u de definitie van een afzonderlijke voor elk object of een set van objecten opgeven.</span><span class="sxs-lookup"><span data-stu-id="e2f21-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="e2f21-133">Zie voor meer informatie over de onderdelen van een brede weergave [brede weergave onderdelen](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="e2f21-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e2f21-134">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e2f21-134">Example</span></span>

<span data-ttu-id="e2f21-135">Het volgende voorbeeld wordt een `WideControl` element dat wordt gebruikt om weer te geven van een eigenschap van de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span><span class="sxs-lookup"><span data-stu-id="e2f21-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

<span data-ttu-id="e2f21-136">Zie voor een compleet voorbeeld van een brede weergave, [brede weergave (basis)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="e2f21-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2f21-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e2f21-137">See Also</span></span>

[<span data-ttu-id="e2f21-138">AutoSize-Element voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="e2f21-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="e2f21-139">ColumnNumber-Element voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="e2f21-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="e2f21-140">Weergave-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e2f21-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="e2f21-141">WideEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="e2f21-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="e2f21-142">Brede weergave (basis)</span><span class="sxs-lookup"><span data-stu-id="e2f21-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="e2f21-143">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="e2f21-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e2f21-144">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2f21-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
