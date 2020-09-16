---
title: Script block-element voor SelectionCondition voor EntrySelectedBy voor WideControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8f2223d4a1217786a930eb82390c24b81d2f72e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787611"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="20db3-102">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20db3-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="20db3-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="20db3-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="20db3-104">Wanneer dit script wordt geëvalueerd naar `true` , wordt voldaan aan de voor waarde en wordt de definitie van het grote item gebruikt.</span><span class="sxs-lookup"><span data-stu-id="20db3-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="20db3-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionCondition-element voor EntrySelectedBy voor WideEntry (Format) script block-element voor SelectionCondition voor EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="20db3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="20db3-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="20db3-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20db3-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="20db3-107">Attributes and Elements</span></span>

<span data-ttu-id="20db3-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="20db3-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="20db3-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="20db3-109">Attributes</span></span>

<span data-ttu-id="20db3-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="20db3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="20db3-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="20db3-111">Child Elements</span></span>

<span data-ttu-id="20db3-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="20db3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="20db3-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="20db3-113">Parent Elements</span></span>

|<span data-ttu-id="20db3-114">Element</span><span class="sxs-lookup"><span data-stu-id="20db3-114">Element</span></span>|<span data-ttu-id="20db3-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="20db3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20db3-116">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="20db3-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="20db3-117">Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="20db3-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="20db3-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="20db3-118">Text Value</span></span>

<span data-ttu-id="20db3-119">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="20db3-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="20db3-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="20db3-120">Remarks</span></span>

<span data-ttu-id="20db3-121">Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="20db3-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="20db3-122">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="20db3-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="20db3-123">Zie [brede weer gave](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="20db3-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="20db3-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="20db3-124">See Also</span></span>

[<span data-ttu-id="20db3-125">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="20db3-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="20db3-126">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="20db3-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="20db3-127">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20db3-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="20db3-128">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="20db3-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="20db3-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="20db3-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
