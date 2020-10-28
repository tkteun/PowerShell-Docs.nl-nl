---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor EntrySelectedBy voor WideControl (opmaak)
description: Het element SelectionSetName voor EntrySelectedBy voor WideControl (opmaak)
ms.openlocfilehash: bf6a44bb733421f36a9140d0ec10e61aedfbda6a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651700"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="49596-103">Het element SelectionSetName voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="49596-103">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="49596-104">Hiermee geeft u een set .NET-objecten voor de definitie op.</span><span class="sxs-lookup"><span data-stu-id="49596-104">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="49596-105">De definitie wordt gebruikt wanneer een van deze objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="49596-105">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="49596-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionSetName-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="49596-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="49596-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="49596-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="49596-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="49596-108">Attributes and Elements</span></span>

<span data-ttu-id="49596-109">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="49596-109">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="49596-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="49596-110">Attributes</span></span>

<span data-ttu-id="49596-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="49596-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="49596-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="49596-112">Child Elements</span></span>

<span data-ttu-id="49596-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="49596-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="49596-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="49596-114">Parent Elements</span></span>

|<span data-ttu-id="49596-115">Element</span><span class="sxs-lookup"><span data-stu-id="49596-115">Element</span></span>|<span data-ttu-id="49596-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="49596-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="49596-117">Het element EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="49596-117">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="49596-118">Hiermee definieert u de .NET-typen die gebruikmaken van deze brede vermelding of de voor waarde die moet bestaan voor deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="49596-118">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="49596-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="49596-119">Text Value</span></span>

<span data-ttu-id="49596-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="49596-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="49596-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="49596-121">Remarks</span></span>

<span data-ttu-id="49596-122">Elke definitie moet een type naam, selectieset of selectie voorwaarde opgeven.</span><span class="sxs-lookup"><span data-stu-id="49596-122">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="49596-123">Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven.</span><span class="sxs-lookup"><span data-stu-id="49596-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="49596-124">U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten.</span><span class="sxs-lookup"><span data-stu-id="49596-124">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="49596-125">Zie [sets van objecten voor een weer gave definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="49596-125">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="49596-126">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="49596-126">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="49596-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="49596-127">See Also</span></span>

[<span data-ttu-id="49596-128">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="49596-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="49596-129">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="49596-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="49596-130">Het element EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="49596-130">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="49596-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="49596-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
