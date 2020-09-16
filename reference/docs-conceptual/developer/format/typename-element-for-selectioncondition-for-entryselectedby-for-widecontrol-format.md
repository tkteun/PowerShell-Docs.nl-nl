---
title: TypeName-element voor SelectionCondition voor EntrySelectedBy voor WideControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5021f665b994581f9ff982e13af922d7940ebf2b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783310"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="c5812-102">Het element TypeName voor SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c5812-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="c5812-103">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="c5812-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="c5812-104">Wanneer dit type aanwezig is, wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c5812-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="c5812-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionCondition-element voor EntrySelectedBy voor WideEntry (Format) voor SelectionCondition voor EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c5812-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c5812-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c5812-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c5812-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c5812-107">Attributes and Elements</span></span>

<span data-ttu-id="c5812-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="c5812-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c5812-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c5812-109">Attributes</span></span>

<span data-ttu-id="c5812-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="c5812-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c5812-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c5812-111">Child Elements</span></span>

<span data-ttu-id="c5812-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="c5812-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c5812-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c5812-113">Parent Elements</span></span>

|<span data-ttu-id="c5812-114">Element</span><span class="sxs-lookup"><span data-stu-id="c5812-114">Element</span></span>|<span data-ttu-id="c5812-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c5812-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c5812-116">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="c5812-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="c5812-117">Hiermee definieert u de voor waarde die voor deze brede vermelding moet bestaan om te worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c5812-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c5812-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="c5812-118">Text Value</span></span>

<span data-ttu-id="c5812-119">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="c5812-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5812-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c5812-120">Remarks</span></span>

<span data-ttu-id="c5812-121">Met de selectie voorwaarde kan een .NET-type of een selectieset worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="c5812-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="c5812-122">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="c5812-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c5812-123">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="c5812-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c5812-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c5812-124">See Also</span></span>

[<span data-ttu-id="c5812-125">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="c5812-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c5812-126">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="c5812-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c5812-127">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="c5812-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="c5812-128">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c5812-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="c5812-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c5812-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
