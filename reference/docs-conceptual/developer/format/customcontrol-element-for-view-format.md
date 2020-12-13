---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomControl voor Weergave (opmaak)
description: Het element CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 41352be55f0c03b2eaca0dbe2d7345e7cf804a7c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655471"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="93bb5-103">Het element CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="93bb5-103">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="93bb5-104">Hiermee wordt een aangepaste besturings element-indeling gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="93bb5-104">Defines a custom control format for the view.</span></span>

<span data-ttu-id="93bb5-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="93bb5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="93bb5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="93bb5-106">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="93bb5-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="93bb5-107">Attributes and Elements</span></span>

<span data-ttu-id="93bb5-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomControl` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="93bb5-108">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="93bb5-109">U moet één onderliggend element opgeven.</span><span class="sxs-lookup"><span data-stu-id="93bb5-109">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="93bb5-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="93bb5-110">Attributes</span></span>

<span data-ttu-id="93bb5-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="93bb5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="93bb5-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="93bb5-112">Child Elements</span></span>

|<span data-ttu-id="93bb5-113">Element</span><span class="sxs-lookup"><span data-stu-id="93bb5-113">Element</span></span>|<span data-ttu-id="93bb5-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="93bb5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="93bb5-115">Het element CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="93bb5-115">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="93bb5-116">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="93bb5-116">Required element.</span></span><br /><br /> <span data-ttu-id="93bb5-117">Biedt de definities van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="93bb5-117">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="93bb5-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="93bb5-118">Parent Elements</span></span>

|<span data-ttu-id="93bb5-119">Element</span><span class="sxs-lookup"><span data-stu-id="93bb5-119">Element</span></span>|<span data-ttu-id="93bb5-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="93bb5-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="93bb5-121">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="93bb5-121">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="93bb5-122">Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om een of meer .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="93bb5-122">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="93bb5-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="93bb5-123">Remarks</span></span>

<span data-ttu-id="93bb5-124">In de meeste gevallen is er slechts één definitie vereist voor elke controle weergave, maar het is mogelijk om meerdere definities op te geven als u dezelfde weer gave wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="93bb5-124">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="93bb5-125">In dergelijke gevallen kunt u een afzonderlijke definitie opgeven voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="93bb5-125">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="93bb5-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="93bb5-126">See Also</span></span>

[<span data-ttu-id="93bb5-127">Het element CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="93bb5-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="93bb5-128">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="93bb5-128">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="93bb5-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="93bb5-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
