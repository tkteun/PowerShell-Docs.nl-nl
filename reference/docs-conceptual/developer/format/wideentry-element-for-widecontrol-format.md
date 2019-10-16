---
title: WideEntry-element voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353156"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="a95b9-102">Het element WideEntry voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a95b9-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="a95b9-103">Biedt een definitie van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="a95b9-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="a95b9-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a95b9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a95b9-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a95b9-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a95b9-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a95b9-106">Attributes and Elements</span></span>

<span data-ttu-id="a95b9-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `WideEntry` beschreven.</span><span class="sxs-lookup"><span data-stu-id="a95b9-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="a95b9-108">U moet één onderliggend `WideItem`-element opgeven.</span><span class="sxs-lookup"><span data-stu-id="a95b9-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a95b9-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a95b9-109">Attributes</span></span>

<span data-ttu-id="a95b9-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="a95b9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a95b9-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a95b9-111">Child Elements</span></span>

|<span data-ttu-id="a95b9-112">Element</span><span class="sxs-lookup"><span data-stu-id="a95b9-112">Element</span></span>|<span data-ttu-id="a95b9-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a95b9-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a95b9-114">EntrySelectedBy-element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a95b9-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="a95b9-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a95b9-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a95b9-116">Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie voor grote vermeldingen of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a95b9-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="a95b9-117">WideItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a95b9-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="a95b9-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="a95b9-118">Required element.</span></span><br /><br /> <span data-ttu-id="a95b9-119">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a95b9-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a95b9-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a95b9-120">Parent Elements</span></span>

|<span data-ttu-id="a95b9-121">Element</span><span class="sxs-lookup"><span data-stu-id="a95b9-121">Element</span></span>|<span data-ttu-id="a95b9-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a95b9-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a95b9-123">WideEntries-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a95b9-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="a95b9-124">Biedt de definities van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="a95b9-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a95b9-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a95b9-125">Remarks</span></span>

<span data-ttu-id="a95b9-126">Een brede weer gave is een lijst indeling waarin één eigenschaps waarde of script waarde voor elk object wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a95b9-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="a95b9-127">In tegens telling tot andere typen weer gaven kunt u slechts één item element voor elke weergave definitie opgeven.</span><span class="sxs-lookup"><span data-stu-id="a95b9-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="a95b9-128">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over de andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="a95b9-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a95b9-129">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="a95b9-129">Example</span></span>

<span data-ttu-id="a95b9-130">In het volgende voor beeld ziet u een `WideEntry`-element dat één `WideItem`-element definieert.</span><span class="sxs-lookup"><span data-stu-id="a95b9-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="a95b9-131">Het element `WideItem` definieert de eigenschap waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="a95b9-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="a95b9-132">Zie [Wide View (Basic)](./wide-view-basic.md)voor een volledig voor beeld van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="a95b9-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a95b9-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a95b9-133">See Also</span></span>

[<span data-ttu-id="a95b9-134">Een brede weer gave maken</span><span class="sxs-lookup"><span data-stu-id="a95b9-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="a95b9-135">SelectionCondition-element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a95b9-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="a95b9-136">SelectionSetName-element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a95b9-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="a95b9-137">TypeName-element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a95b9-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="a95b9-138">WideEntries-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a95b9-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="a95b9-139">WideItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a95b9-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="a95b9-140">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="a95b9-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
