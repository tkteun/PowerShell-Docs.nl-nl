---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomEntry voor CustomControl voor GroupBy (opmaak)
description: Het element CustomEntry voor CustomControl voor GroupBy (opmaak)
ms.openlocfilehash: 0df2ff9c15308939e6d2552f51e2961bdabc59fb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646064"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="d9585-103">Het element CustomEntry voor CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d9585-103">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="d9585-104">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="d9585-104">Provides a definition of the control.</span></span> <span data-ttu-id="d9585-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d9585-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="d9585-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor GroupBy (Format) CustomEntry-element voor het object GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="d9585-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d9585-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d9585-107">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d9585-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d9585-108">Attributes and Elements</span></span>

<span data-ttu-id="d9585-109">In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het `CustomEntry` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="d9585-109">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d9585-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d9585-110">Attributes</span></span>

<span data-ttu-id="d9585-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="d9585-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d9585-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d9585-112">Child Elements</span></span>

|<span data-ttu-id="d9585-113">Element</span><span class="sxs-lookup"><span data-stu-id="d9585-113">Element</span></span>|<span data-ttu-id="d9585-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d9585-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9585-115">Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d9585-115">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="d9585-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d9585-116">Optional element.</span></span><br /><br /> <span data-ttu-id="d9585-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d9585-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="d9585-118">Het element CustomItem voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d9585-118">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="d9585-119">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="d9585-119">Required element.</span></span><br /><br /> <span data-ttu-id="d9585-120">Hiermee wordt gedefinieerd hoe de gegevens worden weer gegeven in het besturings element.</span><span class="sxs-lookup"><span data-stu-id="d9585-120">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d9585-121">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d9585-121">Parent Elements</span></span>

|<span data-ttu-id="d9585-122">Element</span><span class="sxs-lookup"><span data-stu-id="d9585-122">Element</span></span>|<span data-ttu-id="d9585-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d9585-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9585-124">Het element CustomEntries voor CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d9585-124">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="d9585-125">Bevat de definities voor het besturings element.</span><span class="sxs-lookup"><span data-stu-id="d9585-125">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d9585-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d9585-126">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="d9585-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d9585-127">See Also</span></span>

[<span data-ttu-id="d9585-128">Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d9585-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="d9585-129">Het element CustomItem voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d9585-129">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="d9585-130">Het element CustomEntries voor CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d9585-130">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="d9585-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d9585-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
