---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)
description: Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: a525b198c8f595e04dc0804d36b5533b94f43c6b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646087"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="61a62-103">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="61a62-103">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="61a62-104">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="61a62-104">Provides a definition of the control.</span></span> <span data-ttu-id="61a62-105">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="61a62-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="61a62-106">Element van het configuratie-element (indeling) ViewDefinitions element (indeling) besturings element element (indeling) Controls-element (Format) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings element voor Controls voor Controls (Format) CustomEntries element voor de weer gave van besturings elementen (Format)</span><span class="sxs-lookup"><span data-stu-id="61a62-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="61a62-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="61a62-107">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="61a62-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="61a62-108">Attributes and Elements</span></span>

<span data-ttu-id="61a62-109">In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het `CustomEntry` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="61a62-109">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="61a62-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="61a62-110">Attributes</span></span>

<span data-ttu-id="61a62-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="61a62-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="61a62-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="61a62-112">Child Elements</span></span>

|<span data-ttu-id="61a62-113">Element</span><span class="sxs-lookup"><span data-stu-id="61a62-113">Element</span></span>|<span data-ttu-id="61a62-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="61a62-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="61a62-115">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="61a62-115">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="61a62-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="61a62-116">Optional element.</span></span><br /><br /> <span data-ttu-id="61a62-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="61a62-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="61a62-118">Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="61a62-118">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="61a62-119">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="61a62-119">Required element.</span></span><br /><br /> <span data-ttu-id="61a62-120">Hiermee wordt gedefinieerd hoe de gegevens worden weer gegeven in het besturings element.</span><span class="sxs-lookup"><span data-stu-id="61a62-120">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="61a62-121">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="61a62-121">Parent Elements</span></span>

|<span data-ttu-id="61a62-122">Element</span><span class="sxs-lookup"><span data-stu-id="61a62-122">Element</span></span>|<span data-ttu-id="61a62-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="61a62-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="61a62-124">Het element CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="61a62-124">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="61a62-125">Bevat de definities voor het besturings element.</span><span class="sxs-lookup"><span data-stu-id="61a62-125">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="61a62-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="61a62-126">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="61a62-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="61a62-127">See Also</span></span>

[<span data-ttu-id="61a62-128">Het element CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="61a62-128">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="61a62-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="61a62-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
