---
ms.date: 09/13/2016
ms.topic: reference
title: Het element WideControl (opmaak)
description: Het element WideControl (opmaak)
ms.openlocfilehash: f88e1ce18f87e5e47de473298b3ecf070b71c192
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651269"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="c42c2-103">Het element WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c42c2-103">WideControl Element (Format)</span></span>

<span data-ttu-id="c42c2-104">Hiermee wordt een brede lijst indeling (enkelvoudige waarde) gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="c42c2-104">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="c42c2-105">In deze weer gave wordt één eigenschaps waarde of script waarde voor elk object weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c42c2-105">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="c42c2-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c42c2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c42c2-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="c42c2-107">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c42c2-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c42c2-108">Attributes and Elements</span></span>

<span data-ttu-id="c42c2-109">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `WideControl` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="c42c2-109">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="c42c2-110">U kunt de `AutoSize` elementen en niet `ColumnNumber` tegelijkertijd opgeven.</span><span class="sxs-lookup"><span data-stu-id="c42c2-110">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="c42c2-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c42c2-111">Attributes</span></span>

<span data-ttu-id="c42c2-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="c42c2-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c42c2-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c42c2-113">Child Elements</span></span>

|<span data-ttu-id="c42c2-114">Element</span><span class="sxs-lookup"><span data-stu-id="c42c2-114">Element</span></span>|<span data-ttu-id="c42c2-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c42c2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c42c2-116">Het element AutoSize voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c42c2-116">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="c42c2-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c42c2-117">Optional element.</span></span><br /><br /> <span data-ttu-id="c42c2-118">Hiermee wordt aangegeven of de kolom grootte en het aantal kolommen worden aangepast op basis van de grootte van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="c42c2-118">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="c42c2-119">Het element ColumnNumber voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c42c2-119">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="c42c2-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c42c2-120">Optional element.</span></span><br /><br /> <span data-ttu-id="c42c2-121">Hiermee geeft u het aantal kolommen op dat wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="c42c2-121">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="c42c2-122">WideEntries-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c42c2-122">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="c42c2-123">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="c42c2-123">Required element.</span></span><br /><br /> <span data-ttu-id="c42c2-124">Biedt de definities van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="c42c2-124">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c42c2-125">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c42c2-125">Parent Elements</span></span>

|<span data-ttu-id="c42c2-126">Element</span><span class="sxs-lookup"><span data-stu-id="c42c2-126">Element</span></span>|<span data-ttu-id="c42c2-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c42c2-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c42c2-128">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c42c2-128">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="c42c2-129">Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om een of meer .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c42c2-129">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c42c2-130">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c42c2-130">Remarks</span></span>

<span data-ttu-id="c42c2-131">Bij het definiëren van een brede weer gave kunt u het `AutoSize` element toevoegen of het, `ColumnNumber` maar u kunt niet beide toevoegen.</span><span class="sxs-lookup"><span data-stu-id="c42c2-131">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="c42c2-132">In de meeste gevallen is er slechts één definitie vereist voor elke brede weer gave, maar het is mogelijk om meerdere definities te hebben als u dezelfde weer gave wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c42c2-132">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="c42c2-133">In dergelijke gevallen kunt u een afzonderlijke definitie opgeven voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="c42c2-133">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="c42c2-134">Zie [Wide View-onderdelen](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="c42c2-134">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c42c2-135">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c42c2-135">Example</span></span>

<span data-ttu-id="c42c2-136">In het volgende voor beeld ziet u een- `WideControl` element dat wordt gebruikt om een eigenschap van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c42c2-136">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="c42c2-137">Zie [Wide View (Basic)](./wide-view-basic.md)voor een volledig voor beeld van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="c42c2-137">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c42c2-138">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c42c2-138">See Also</span></span>

[<span data-ttu-id="c42c2-139">Het element AutoSize voor WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c42c2-139">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="c42c2-140">Het element ColumnNumber voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c42c2-140">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="c42c2-141">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c42c2-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="c42c2-142">WideEntries-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c42c2-142">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="c42c2-143">Brede weergave (Basis)</span><span class="sxs-lookup"><span data-stu-id="c42c2-143">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="c42c2-144">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="c42c2-144">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c42c2-145">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c42c2-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
