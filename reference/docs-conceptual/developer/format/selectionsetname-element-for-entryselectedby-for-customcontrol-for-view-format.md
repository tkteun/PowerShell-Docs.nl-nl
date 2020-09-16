---
title: SelectionSetName-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3728a1886d5406b8fa4888125d1c031d0f9b1b03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785299"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="2b165-102">Het element SelectionSetName voor EntrySelectedBy voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2b165-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="2b165-103">Hiermee geeft u een set .NET-objecten voor de lijst vermelding op.</span><span class="sxs-lookup"><span data-stu-id="2b165-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="2b165-104">Er is geen limiet voor het aantal selectie sets dat voor een vermelding kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2b165-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="2b165-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) EntrySelectedBy element voor CustomEntry voor weer gave (Format) SelectionSetName-element voor EntrySelectedBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="2b165-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b165-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2b165-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b165-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="2b165-107">Attributes and Elements</span></span>

<span data-ttu-id="2b165-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="2b165-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b165-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2b165-109">Attributes</span></span>

<span data-ttu-id="2b165-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="2b165-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2b165-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2b165-111">Child Elements</span></span>

<span data-ttu-id="2b165-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="2b165-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2b165-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2b165-113">Parent Elements</span></span>

|<span data-ttu-id="2b165-114">Element</span><span class="sxs-lookup"><span data-stu-id="2b165-114">Element</span></span>|<span data-ttu-id="2b165-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2b165-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b165-116">EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="2b165-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="2b165-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste vermelding of de voor waarde die moet bestaan voor deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="2b165-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2b165-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="2b165-118">Text Value</span></span>

<span data-ttu-id="2b165-119">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="2b165-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b165-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2b165-120">Remarks</span></span>

<span data-ttu-id="2b165-121">Voor elke aangepaste controle vermelding moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="2b165-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="2b165-122">Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven.</span><span class="sxs-lookup"><span data-stu-id="2b165-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="2b165-123">U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten.</span><span class="sxs-lookup"><span data-stu-id="2b165-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="2b165-124">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="2b165-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="2b165-125">Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="2b165-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b165-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2b165-126">See Also</span></span>

[<span data-ttu-id="2b165-127">EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="2b165-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2b165-128">Aangepaste besturings elementen weer geven</span><span class="sxs-lookup"><span data-stu-id="2b165-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="2b165-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="2b165-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
