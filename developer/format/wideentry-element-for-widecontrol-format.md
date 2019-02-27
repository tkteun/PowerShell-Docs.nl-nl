---
title: WideEntry-Element voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847178"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="9cab0-102">Het element WideEntry voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9cab0-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="9cab0-103">Bevat een definitie van de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="9cab0-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="9cab0-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="9cab0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9cab0-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="9cab0-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9cab0-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="9cab0-106">Attributes and Elements</span></span>

<span data-ttu-id="9cab0-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `WideEntry` element.</span><span class="sxs-lookup"><span data-stu-id="9cab0-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="9cab0-108">U moet een enkel `WideItem` onderliggend element.</span><span class="sxs-lookup"><span data-stu-id="9cab0-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9cab0-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="9cab0-109">Attributes</span></span>

<span data-ttu-id="9cab0-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="9cab0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9cab0-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9cab0-111">Child Elements</span></span>

|<span data-ttu-id="9cab0-112">Element</span><span class="sxs-lookup"><span data-stu-id="9cab0-112">Element</span></span>|<span data-ttu-id="9cab0-113">Description</span><span class="sxs-lookup"><span data-stu-id="9cab0-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9cab0-114">EntrySelectedBy-Element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="9cab0-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="9cab0-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="9cab0-115">Optional element.</span></span><br /><br /> <span data-ttu-id="9cab0-116">Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie breed vermelding of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9cab0-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="9cab0-117">WideItem-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="9cab0-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="9cab0-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="9cab0-118">Required element.</span></span><br /><br /> <span data-ttu-id="9cab0-119">Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="9cab0-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9cab0-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9cab0-120">Parent Elements</span></span>

|<span data-ttu-id="9cab0-121">Element</span><span class="sxs-lookup"><span data-stu-id="9cab0-121">Element</span></span>|<span data-ttu-id="9cab0-122">Description</span><span class="sxs-lookup"><span data-stu-id="9cab0-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9cab0-123">WideEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="9cab0-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="9cab0-124">Bevat de definities van de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="9cab0-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9cab0-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9cab0-125">Remarks</span></span>

<span data-ttu-id="9cab0-126">Een brede weergave wordt een lijst met-indeling die een waarde van één eigenschap of Scriptwaarde voor elk object wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="9cab0-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="9cab0-127">In tegenstelling tot andere typen weergaven, kunt u slechts één itemelement voor de weergavedefinitie van elke opgeven.</span><span class="sxs-lookup"><span data-stu-id="9cab0-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="9cab0-128">Zie voor meer informatie over de andere onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="9cab0-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9cab0-129">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="9cab0-129">Example</span></span>

<span data-ttu-id="9cab0-130">Het volgende voorbeeld wordt een `WideEntry` element waarin één `WideItem` element.</span><span class="sxs-lookup"><span data-stu-id="9cab0-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="9cab0-131">De `WideItem` element wordt gedefinieerd voor de eigenschap waarvan de waarde wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="9cab0-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="9cab0-132">Zie voor een compleet voorbeeld van een brede weergave, [brede weergave (basis)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="9cab0-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9cab0-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9cab0-133">See Also</span></span>

[<span data-ttu-id="9cab0-134">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="9cab0-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9cab0-135">SelectionCondition-Element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="9cab0-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="9cab0-136">SelectionSetName-Element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="9cab0-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="9cab0-137">TypeName-Element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="9cab0-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="9cab0-138">WideEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="9cab0-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="9cab0-139">WideItem-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="9cab0-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="9cab0-140">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="9cab0-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
