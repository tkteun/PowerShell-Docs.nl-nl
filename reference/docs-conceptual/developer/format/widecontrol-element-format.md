---
title: WideControl-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358706"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="e5f25-102">Het element WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e5f25-102">WideControl Element (Format)</span></span>

<span data-ttu-id="e5f25-103">Hiermee wordt een brede lijst indeling (enkelvoudige waarde) gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="e5f25-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="e5f25-104">In deze weer gave wordt één eigenschaps waarde of script waarde voor elk object weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e5f25-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="e5f25-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f25-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5f25-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e5f25-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5f25-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e5f25-107">Attributes and Elements</span></span>

<span data-ttu-id="e5f25-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `WideControl` beschreven.</span><span class="sxs-lookup"><span data-stu-id="e5f25-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="e5f25-109">U kunt de elementen `AutoSize` en `ColumnNumber` niet tegelijk opgeven.</span><span class="sxs-lookup"><span data-stu-id="e5f25-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5f25-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e5f25-110">Attributes</span></span>

<span data-ttu-id="e5f25-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="e5f25-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5f25-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e5f25-112">Child Elements</span></span>

|<span data-ttu-id="e5f25-113">Element</span><span class="sxs-lookup"><span data-stu-id="e5f25-113">Element</span></span>|<span data-ttu-id="e5f25-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e5f25-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5f25-115">Het element AutoSize voor WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e5f25-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="e5f25-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e5f25-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e5f25-117">Hiermee wordt aangegeven of de kolom grootte en het aantal kolommen worden aangepast op basis van de grootte van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="e5f25-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="e5f25-118">ColumnNumber-element voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f25-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="e5f25-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e5f25-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e5f25-120">Hiermee geeft u het aantal kolommen op dat wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="e5f25-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="e5f25-121">WideEntries-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f25-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="e5f25-122">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="e5f25-122">Required element.</span></span><br /><br /> <span data-ttu-id="e5f25-123">Biedt de definities van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="e5f25-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5f25-124">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e5f25-124">Parent Elements</span></span>

|<span data-ttu-id="e5f25-125">Element</span><span class="sxs-lookup"><span data-stu-id="e5f25-125">Element</span></span>|<span data-ttu-id="e5f25-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e5f25-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5f25-127">Element weer geven (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f25-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="e5f25-128">Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om een of meer .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e5f25-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5f25-129">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e5f25-129">Remarks</span></span>

<span data-ttu-id="e5f25-130">Bij het definiëren van een brede weer gave kunt u het element `AutoSize` of de `ColumnNumber` toevoegen, maar u kunt niet beide toevoegen.</span><span class="sxs-lookup"><span data-stu-id="e5f25-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="e5f25-131">In de meeste gevallen is er slechts één definitie vereist voor elke brede weer gave, maar het is mogelijk om meerdere definities te hebben als u dezelfde weer gave wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e5f25-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="e5f25-132">In dergelijke gevallen kunt u een afzonderlijke definitie opgeven voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="e5f25-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="e5f25-133">Zie [Wide View-onderdelen](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="e5f25-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e5f25-134">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e5f25-134">Example</span></span>

<span data-ttu-id="e5f25-135">In het volgende voor beeld ziet u een `WideControl`-element dat wordt gebruikt om een eigenschap van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e5f25-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="e5f25-136">Zie [Wide View (Basic)](./wide-view-basic.md)voor een volledig voor beeld van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="e5f25-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e5f25-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e5f25-137">See Also</span></span>

[<span data-ttu-id="e5f25-138">Het element AutoSize voor WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e5f25-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="e5f25-139">ColumnNumber-element voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f25-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="e5f25-140">Element weer geven (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f25-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="e5f25-141">WideEntries-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f25-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="e5f25-142">Brede weer gave (basis)</span><span class="sxs-lookup"><span data-stu-id="e5f25-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="e5f25-143">Een brede weer gave maken</span><span class="sxs-lookup"><span data-stu-id="e5f25-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e5f25-144">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e5f25-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
