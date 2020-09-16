---
title: WideItem-element voor WideControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6b2f7c97978c20350caeec894589c5995ae7ccc4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779893"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="76dbd-102">Het element WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="76dbd-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="76dbd-103">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="76dbd-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="76dbd-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) WideItem element (indeling)</span><span class="sxs-lookup"><span data-stu-id="76dbd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="76dbd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="76dbd-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="76dbd-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="76dbd-106">Attributes and Elements</span></span>

<span data-ttu-id="76dbd-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `WideItem` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="76dbd-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="76dbd-108">Het `FormatString` element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="76dbd-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="76dbd-109">U moet echter een or- `PropertyName` `ScriptBlock` element opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="76dbd-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="76dbd-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="76dbd-110">Attributes</span></span>

<span data-ttu-id="76dbd-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="76dbd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="76dbd-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="76dbd-112">Child Elements</span></span>

|<span data-ttu-id="76dbd-113">Element</span><span class="sxs-lookup"><span data-stu-id="76dbd-113">Element</span></span>|<span data-ttu-id="76dbd-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="76dbd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="76dbd-115">Het element FormatString voor WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="76dbd-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="76dbd-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="76dbd-116">Optional element.</span></span><br /><br /> <span data-ttu-id="76dbd-117">Geeft een indelings patroon aan dat definieert hoe de eigenschap of script waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="76dbd-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="76dbd-118">Het element PropertyName voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="76dbd-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="76dbd-119">Hiermee geeft u de eigenschap op van het object waarvan de waarde wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="76dbd-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="76dbd-120">Script block-element voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="76dbd-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="76dbd-121">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="76dbd-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="76dbd-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="76dbd-122">Parent Elements</span></span>

|<span data-ttu-id="76dbd-123">Element</span><span class="sxs-lookup"><span data-stu-id="76dbd-123">Element</span></span>|<span data-ttu-id="76dbd-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="76dbd-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="76dbd-125">WideEntry-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="76dbd-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="76dbd-126">Biedt een definitie van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="76dbd-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="76dbd-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="76dbd-127">Remarks</span></span>

<span data-ttu-id="76dbd-128">Zie [brede weer gave](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="76dbd-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="76dbd-129">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="76dbd-129">Example</span></span>

<span data-ttu-id="76dbd-130">In het volgende voor beeld ziet u een- `WideEntry` element dat één `WideItem` element definieert.</span><span class="sxs-lookup"><span data-stu-id="76dbd-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="76dbd-131">Het `WideItem` element definieert de eigenschap of het script waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="76dbd-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="76dbd-132">Zie [Wide View (Basic)](./wide-view-basic.md)voor een volledig voor beeld van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="76dbd-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="76dbd-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="76dbd-133">See Also</span></span>

[<span data-ttu-id="76dbd-134">Het element FormatString voor WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="76dbd-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="76dbd-135">Het element PropertyName voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="76dbd-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="76dbd-136">Script block-element voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="76dbd-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="76dbd-137">WideEntry-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="76dbd-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="76dbd-138">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="76dbd-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
