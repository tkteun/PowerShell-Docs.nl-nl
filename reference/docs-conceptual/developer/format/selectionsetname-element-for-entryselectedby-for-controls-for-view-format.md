---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)
description: Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: 3211b7cacd7e57770b48b03f4aade33da506f180
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664737"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="03689-103">Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="03689-103">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="03689-104">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="03689-104">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="03689-105">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="03689-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="03689-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor besturings elementen voor weer gave (indeling) CustomEntry element voor CustomEntries voor besturings elementen voor de weer gave (Format) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de weer gave (Format) SelectionSetName-element voor EntrySelectedBy voor besturings elementen</span><span class="sxs-lookup"><span data-stu-id="03689-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="03689-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="03689-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="03689-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="03689-108">Attributes and Elements</span></span>

<span data-ttu-id="03689-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="03689-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="03689-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="03689-110">Attributes</span></span>

<span data-ttu-id="03689-111">Geen</span><span class="sxs-lookup"><span data-stu-id="03689-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="03689-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="03689-112">Child Elements</span></span>

<span data-ttu-id="03689-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="03689-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="03689-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="03689-114">Parent Elements</span></span>

|<span data-ttu-id="03689-115">Element</span><span class="sxs-lookup"><span data-stu-id="03689-115">Element</span></span>|<span data-ttu-id="03689-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="03689-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="03689-117">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="03689-117">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="03689-118">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="03689-118">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="03689-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="03689-119">Text Value</span></span>

<span data-ttu-id="03689-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="03689-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="03689-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="03689-121">Remarks</span></span>

<span data-ttu-id="03689-122">Voor elke controle definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="03689-122">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="03689-123">Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven.</span><span class="sxs-lookup"><span data-stu-id="03689-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="03689-124">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="03689-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="03689-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="03689-125">See Also</span></span>

[<span data-ttu-id="03689-126">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="03689-126">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="03689-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="03689-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
