---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomEntry voor CustomEntries voor CustomControl voor Weergave (opmaak)
description: Het element CustomEntry voor CustomEntries voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: ff481f13e6f16267bdda4c3053faebc96d9a6d3a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646055"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="78e0c-103">Het element CustomEntry voor CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="78e0c-103">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="78e0c-104">Biedt een definitie van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="78e0c-104">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="78e0c-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="78e0c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="78e0c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="78e0c-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="78e0c-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="78e0c-107">Attributes and Elements</span></span>

<span data-ttu-id="78e0c-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomEntry` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="78e0c-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="78e0c-109">U moet de items opgeven die worden weer gegeven door de definitie.</span><span class="sxs-lookup"><span data-stu-id="78e0c-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="78e0c-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="78e0c-110">Attributes</span></span>

<span data-ttu-id="78e0c-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="78e0c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="78e0c-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="78e0c-112">Child Elements</span></span>

|<span data-ttu-id="78e0c-113">Element</span><span class="sxs-lookup"><span data-stu-id="78e0c-113">Element</span></span>|<span data-ttu-id="78e0c-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="78e0c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="78e0c-115">EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="78e0c-115">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="78e0c-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="78e0c-116">Optional element.</span></span><br /><br /> <span data-ttu-id="78e0c-117">Hiermee definieert u de .NET-typen die gebruikmaken van de definitie van de aangepaste beheer weergave of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="78e0c-117">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="78e0c-118">CustomItem-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="78e0c-118">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="78e0c-119">Hiermee definieert u een besturings element voor de aangepaste besturings element definitie.</span><span class="sxs-lookup"><span data-stu-id="78e0c-119">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="78e0c-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="78e0c-120">Parent Elements</span></span>

|<span data-ttu-id="78e0c-121">Element</span><span class="sxs-lookup"><span data-stu-id="78e0c-121">Element</span></span>|<span data-ttu-id="78e0c-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="78e0c-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="78e0c-123">Het element CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="78e0c-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="78e0c-124">Biedt de definities van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="78e0c-124">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="78e0c-125">In de aangepaste beheer weergave moeten een of meer definities worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="78e0c-125">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="78e0c-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="78e0c-126">Remarks</span></span>

<span data-ttu-id="78e0c-127">In de meeste gevallen is er slechts één definitie vereist voor elke aangepaste controle weergave, maar het is mogelijk om meerdere definities te hebben als u dezelfde weer gave wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="78e0c-127">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="78e0c-128">In dergelijke gevallen kunt u een afzonderlijke definitie opgeven voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="78e0c-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="78e0c-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="78e0c-129">See Also</span></span>

[<span data-ttu-id="78e0c-130">Het element CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="78e0c-130">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="78e0c-131">CustomItem-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="78e0c-131">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="78e0c-132">EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="78e0c-132">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="78e0c-133">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="78e0c-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
