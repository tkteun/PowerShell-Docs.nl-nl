---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomEntries voor CustomControl voor Weergave (opmaak)
description: Het element CustomEntries voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 6e757bccdface2503667f8786462a2b43134a07d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649970"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="8f5d5-103">Het element CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8f5d5-103">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="8f5d5-104">Biedt de definities van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="8f5d5-104">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="8f5d5-105">In de aangepaste beheer weergave moeten een of meer definities worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="8f5d5-105">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="8f5d5-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer gave (indeling) CustomControl element (indeling) CustomEntries element voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="8f5d5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8f5d5-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="8f5d5-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f5d5-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="8f5d5-108">Attributes and Elements</span></span>

<span data-ttu-id="8f5d5-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomControlEntries` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="8f5d5-109">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="8f5d5-110">U moet een of meer onderliggende elementen opgeven.</span><span class="sxs-lookup"><span data-stu-id="8f5d5-110">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f5d5-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="8f5d5-111">Attributes</span></span>

<span data-ttu-id="8f5d5-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="8f5d5-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8f5d5-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8f5d5-113">Child Elements</span></span>

|<span data-ttu-id="8f5d5-114">Element</span><span class="sxs-lookup"><span data-stu-id="8f5d5-114">Element</span></span>|<span data-ttu-id="8f5d5-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8f5d5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f5d5-116">CustomEntry-element voor CustomEntries voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="8f5d5-116">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="8f5d5-117">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="8f5d5-117">Required element.</span></span><br /><br /> <span data-ttu-id="8f5d5-118">Biedt een definitie van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="8f5d5-118">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8f5d5-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8f5d5-119">Parent Elements</span></span>

|<span data-ttu-id="8f5d5-120">Element</span><span class="sxs-lookup"><span data-stu-id="8f5d5-120">Element</span></span>|<span data-ttu-id="8f5d5-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8f5d5-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f5d5-122">Het element CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8f5d5-122">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="8f5d5-123">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="8f5d5-123">Required element.</span></span><br /><br /> <span data-ttu-id="8f5d5-124">Hiermee wordt een aangepaste besturings element-indeling gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="8f5d5-124">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8f5d5-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="8f5d5-125">Remarks</span></span>

<span data-ttu-id="8f5d5-126">In de meeste gevallen heeft een besturings element slechts één definitie, die in één element is gedefinieerd `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="8f5d5-126">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="8f5d5-127">Het is echter mogelijk om meerdere definities te hebben als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="8f5d5-127">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="8f5d5-128">In dergelijke gevallen kunt u een element definiëren `CustomEntry` voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="8f5d5-128">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f5d5-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8f5d5-129">See Also</span></span>

[<span data-ttu-id="8f5d5-130">Het element CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8f5d5-130">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="8f5d5-131">CustomEntry-element voor CustomEntries voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="8f5d5-131">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="8f5d5-132">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="8f5d5-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
