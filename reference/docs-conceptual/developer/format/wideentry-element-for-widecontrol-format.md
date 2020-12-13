---
ms.date: 09/13/2016
ms.topic: reference
title: Het element WideEntry voor WideControl (opmaak)
description: Het element WideEntry voor WideControl (opmaak)
ms.openlocfilehash: 3faaf767d11914792effd6765beed956a502c642
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664543"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="280e9-103">Het element WideEntry voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="280e9-103">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="280e9-104">Biedt een definitie van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="280e9-104">Provides a definition of the wide view.</span></span>

<span data-ttu-id="280e9-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling)</span><span class="sxs-lookup"><span data-stu-id="280e9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="280e9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="280e9-106">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="280e9-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="280e9-107">Attributes and Elements</span></span>

<span data-ttu-id="280e9-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `WideEntry` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="280e9-108">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="280e9-109">U moet één `WideItem` onderliggend element opgeven.</span><span class="sxs-lookup"><span data-stu-id="280e9-109">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="280e9-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="280e9-110">Attributes</span></span>

<span data-ttu-id="280e9-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="280e9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="280e9-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="280e9-112">Child Elements</span></span>

|<span data-ttu-id="280e9-113">Element</span><span class="sxs-lookup"><span data-stu-id="280e9-113">Element</span></span>|<span data-ttu-id="280e9-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="280e9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="280e9-115">Het element EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="280e9-115">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="280e9-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="280e9-116">Optional element.</span></span><br /><br /> <span data-ttu-id="280e9-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie voor grote vermeldingen of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="280e9-117">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="280e9-118">WideItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="280e9-118">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="280e9-119">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="280e9-119">Required element.</span></span><br /><br /> <span data-ttu-id="280e9-120">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="280e9-120">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="280e9-121">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="280e9-121">Parent Elements</span></span>

|<span data-ttu-id="280e9-122">Element</span><span class="sxs-lookup"><span data-stu-id="280e9-122">Element</span></span>|<span data-ttu-id="280e9-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="280e9-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="280e9-124">WideEntries-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="280e9-124">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="280e9-125">Biedt de definities van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="280e9-125">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="280e9-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="280e9-126">Remarks</span></span>

<span data-ttu-id="280e9-127">Een brede weer gave is een lijst indeling waarin één eigenschaps waarde of script waarde voor elk object wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="280e9-127">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="280e9-128">In tegens telling tot andere typen weer gaven kunt u slechts één item element voor elke weergave definitie opgeven.</span><span class="sxs-lookup"><span data-stu-id="280e9-128">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="280e9-129">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over de andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="280e9-129">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="280e9-130">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="280e9-130">Example</span></span>

<span data-ttu-id="280e9-131">In het volgende voor beeld ziet u een- `WideEntry` element dat één `WideItem` element definieert.</span><span class="sxs-lookup"><span data-stu-id="280e9-131">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="280e9-132">Het `WideItem` element definieert de eigenschap waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="280e9-132">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="280e9-133">Zie [Wide View (Basic)](./wide-view-basic.md)voor een volledig voor beeld van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="280e9-133">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="280e9-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="280e9-134">See Also</span></span>

[<span data-ttu-id="280e9-135">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="280e9-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="280e9-136">SelectionCondition-element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="280e9-136">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="280e9-137">SelectionSetName-element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="280e9-137">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="280e9-138">TypeName-element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="280e9-138">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="280e9-139">WideEntries-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="280e9-139">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="280e9-140">WideItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="280e9-140">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="280e9-141">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="280e9-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
