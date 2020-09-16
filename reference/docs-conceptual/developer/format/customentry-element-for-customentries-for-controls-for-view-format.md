---
title: CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4fc960ab803580f684ce0f224b1db4d7d4af1720
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785894"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="e4496-102">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e4496-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="e4496-103">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="e4496-103">Provides a definition of the control.</span></span> <span data-ttu-id="e4496-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="e4496-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e4496-105">Element van het configuratie-element (indeling) ViewDefinitions element (indeling) besturings element element (indeling) Controls-element (Format) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings element voor Controls voor Controls (Format) CustomEntries element voor de weer gave van besturings elementen (Format)</span><span class="sxs-lookup"><span data-stu-id="e4496-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e4496-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e4496-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e4496-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e4496-107">Attributes and Elements</span></span>

<span data-ttu-id="e4496-108">In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het `CustomEntry` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="e4496-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e4496-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e4496-109">Attributes</span></span>

<span data-ttu-id="e4496-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="e4496-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e4496-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e4496-111">Child Elements</span></span>

|<span data-ttu-id="e4496-112">Element</span><span class="sxs-lookup"><span data-stu-id="e4496-112">Element</span></span>|<span data-ttu-id="e4496-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e4496-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e4496-114">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e4496-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="e4496-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e4496-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e4496-116">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e4496-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="e4496-117">Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e4496-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="e4496-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="e4496-118">Required element.</span></span><br /><br /> <span data-ttu-id="e4496-119">Hiermee wordt gedefinieerd hoe de gegevens worden weer gegeven in het besturings element.</span><span class="sxs-lookup"><span data-stu-id="e4496-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e4496-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e4496-120">Parent Elements</span></span>

|<span data-ttu-id="e4496-121">Element</span><span class="sxs-lookup"><span data-stu-id="e4496-121">Element</span></span>|<span data-ttu-id="e4496-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e4496-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e4496-123">Het element CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e4496-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="e4496-124">Bevat de definities voor het besturings element.</span><span class="sxs-lookup"><span data-stu-id="e4496-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e4496-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e4496-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e4496-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e4496-126">See Also</span></span>

[<span data-ttu-id="e4496-127">Het element CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e4496-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e4496-128">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e4496-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
