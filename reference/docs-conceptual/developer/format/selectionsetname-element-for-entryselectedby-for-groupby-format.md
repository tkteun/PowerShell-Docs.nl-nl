---
title: SelectionSetName-element voor EntrySelectedBy voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 362f7844c09a52494387a62e329adfb309767427
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785282"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="75186-102">Het element SelectionSetName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="75186-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="75186-103">Hiermee geeft u een set .NET-objecten voor de lijst vermelding op.</span><span class="sxs-lookup"><span data-stu-id="75186-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="75186-104">Er is geen limiet voor het aantal selectie sets dat voor een vermelding kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="75186-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="75186-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="75186-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="75186-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="75186-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="75186-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="75186-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75186-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="75186-108">Attributes and Elements</span></span>

<span data-ttu-id="75186-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="75186-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="75186-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="75186-110">Attributes</span></span>

<span data-ttu-id="75186-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="75186-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="75186-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="75186-112">Child Elements</span></span>

<span data-ttu-id="75186-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="75186-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="75186-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="75186-114">Parent Elements</span></span>

|<span data-ttu-id="75186-115">Element</span><span class="sxs-lookup"><span data-stu-id="75186-115">Element</span></span>|<span data-ttu-id="75186-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="75186-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75186-117">Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="75186-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="75186-118">Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste vermelding of de voor waarde die moet bestaan voor deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="75186-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="75186-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="75186-119">Text Value</span></span>

<span data-ttu-id="75186-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="75186-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="75186-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="75186-121">Remarks</span></span>

<span data-ttu-id="75186-122">Voor elke aangepaste besturings definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="75186-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="75186-123">Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven.</span><span class="sxs-lookup"><span data-stu-id="75186-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="75186-124">U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten.</span><span class="sxs-lookup"><span data-stu-id="75186-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="75186-125">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="75186-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="75186-126">Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="75186-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="75186-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="75186-127">See Also</span></span>

[<span data-ttu-id="75186-128">Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="75186-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="75186-129">Aangepaste besturingselementen maken</span><span class="sxs-lookup"><span data-stu-id="75186-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="75186-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="75186-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
