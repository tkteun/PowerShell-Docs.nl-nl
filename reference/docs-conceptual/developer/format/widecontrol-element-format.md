---
title: WideControl-element (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b6f19cf94dcb440eeaf53547db407287e5462520
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784976"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="93ef8-102">Het element WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="93ef8-102">WideControl Element (Format)</span></span>

<span data-ttu-id="93ef8-103">Hiermee wordt een brede lijst indeling (enkelvoudige waarde) gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="93ef8-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="93ef8-104">In deze weer gave wordt één eigenschaps waarde of script waarde voor elk object weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="93ef8-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="93ef8-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="93ef8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="93ef8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="93ef8-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="93ef8-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="93ef8-107">Attributes and Elements</span></span>

<span data-ttu-id="93ef8-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `WideControl` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="93ef8-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="93ef8-109">U kunt de `AutoSize` elementen en niet `ColumnNumber` tegelijkertijd opgeven.</span><span class="sxs-lookup"><span data-stu-id="93ef8-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="93ef8-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="93ef8-110">Attributes</span></span>

<span data-ttu-id="93ef8-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="93ef8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="93ef8-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="93ef8-112">Child Elements</span></span>

|<span data-ttu-id="93ef8-113">Element</span><span class="sxs-lookup"><span data-stu-id="93ef8-113">Element</span></span>|<span data-ttu-id="93ef8-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="93ef8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="93ef8-115">Het element AutoSize voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="93ef8-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="93ef8-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="93ef8-116">Optional element.</span></span><br /><br /> <span data-ttu-id="93ef8-117">Hiermee wordt aangegeven of de kolom grootte en het aantal kolommen worden aangepast op basis van de grootte van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="93ef8-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="93ef8-118">Het element ColumnNumber voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="93ef8-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="93ef8-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="93ef8-119">Optional element.</span></span><br /><br /> <span data-ttu-id="93ef8-120">Hiermee geeft u het aantal kolommen op dat wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="93ef8-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="93ef8-121">WideEntries-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="93ef8-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="93ef8-122">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="93ef8-122">Required element.</span></span><br /><br /> <span data-ttu-id="93ef8-123">Biedt de definities van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="93ef8-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="93ef8-124">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="93ef8-124">Parent Elements</span></span>

|<span data-ttu-id="93ef8-125">Element</span><span class="sxs-lookup"><span data-stu-id="93ef8-125">Element</span></span>|<span data-ttu-id="93ef8-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="93ef8-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="93ef8-127">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="93ef8-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="93ef8-128">Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om een of meer .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="93ef8-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="93ef8-129">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="93ef8-129">Remarks</span></span>

<span data-ttu-id="93ef8-130">Bij het definiëren van een brede weer gave kunt u het `AutoSize` element toevoegen of het, `ColumnNumber` maar u kunt niet beide toevoegen.</span><span class="sxs-lookup"><span data-stu-id="93ef8-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="93ef8-131">In de meeste gevallen is er slechts één definitie vereist voor elke brede weer gave, maar het is mogelijk om meerdere definities te hebben als u dezelfde weer gave wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="93ef8-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="93ef8-132">In dergelijke gevallen kunt u een afzonderlijke definitie opgeven voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="93ef8-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="93ef8-133">Zie [Wide View-onderdelen](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="93ef8-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="93ef8-134">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="93ef8-134">Example</span></span>

<span data-ttu-id="93ef8-135">In het volgende voor beeld ziet u een- `WideControl` element dat wordt gebruikt om een eigenschap van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) weer te geven.</span><span class="sxs-lookup"><span data-stu-id="93ef8-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="93ef8-136">Zie [Wide View (Basic)](./wide-view-basic.md)voor een volledig voor beeld van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="93ef8-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="93ef8-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="93ef8-137">See Also</span></span>

[<span data-ttu-id="93ef8-138">Het element AutoSize voor WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="93ef8-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="93ef8-139">Het element ColumnNumber voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="93ef8-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="93ef8-140">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="93ef8-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="93ef8-141">WideEntries-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="93ef8-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="93ef8-142">Brede weergave (Basis)</span><span class="sxs-lookup"><span data-stu-id="93ef8-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="93ef8-143">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="93ef8-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="93ef8-144">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="93ef8-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
