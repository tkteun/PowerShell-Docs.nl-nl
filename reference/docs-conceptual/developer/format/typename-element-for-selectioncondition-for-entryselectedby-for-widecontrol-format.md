---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)
description: Het element TypeName voor SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)
ms.openlocfilehash: af6e4782c345b43e16bce59c333bdaaceba0d845
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645507"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="9a4a5-103">Het element TypeName voor SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9a4a5-103">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="9a4a5-104">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="9a4a5-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="9a4a5-105">Wanneer dit type aanwezig is, wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9a4a5-105">When this type is present, the definition is used.</span></span>

<span data-ttu-id="9a4a5-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionCondition-element voor EntrySelectedBy voor WideEntry (Format) voor SelectionCondition voor EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9a4a5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9a4a5-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="9a4a5-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a4a5-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="9a4a5-108">Attributes and Elements</span></span>

<span data-ttu-id="9a4a5-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="9a4a5-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a4a5-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="9a4a5-110">Attributes</span></span>

<span data-ttu-id="9a4a5-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="9a4a5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9a4a5-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9a4a5-112">Child Elements</span></span>

<span data-ttu-id="9a4a5-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="9a4a5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9a4a5-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9a4a5-114">Parent Elements</span></span>

|<span data-ttu-id="9a4a5-115">Element</span><span class="sxs-lookup"><span data-stu-id="9a4a5-115">Element</span></span>|<span data-ttu-id="9a4a5-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9a4a5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a4a5-117">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="9a4a5-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="9a4a5-118">Hiermee definieert u de voor waarde die voor deze brede vermelding moet bestaan om te worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9a4a5-118">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9a4a5-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="9a4a5-119">Text Value</span></span>

<span data-ttu-id="9a4a5-120">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="9a4a5-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a4a5-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9a4a5-121">Remarks</span></span>

<span data-ttu-id="9a4a5-122">Met de selectie voorwaarde kan een .NET-type of een selectieset worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9a4a5-122">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="9a4a5-123">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="9a4a5-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9a4a5-124">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="9a4a5-124">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9a4a5-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9a4a5-125">See Also</span></span>

[<span data-ttu-id="9a4a5-126">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="9a4a5-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9a4a5-127">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="9a4a5-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9a4a5-128">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="9a4a5-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="9a4a5-129">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9a4a5-129">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="9a4a5-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="9a4a5-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
