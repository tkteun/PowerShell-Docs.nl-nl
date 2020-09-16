---
title: Script block-element voor SelectionCondition voor EntrySelectedBy voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e70e1555a8f2fe0d15d3e864d80d35527af81b03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785384"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="6d416-102">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6d416-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="6d416-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="6d416-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="6d416-104">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6d416-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="6d416-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6d416-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="6d416-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) SelectionCondition voor EntrySelectedBy voor GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6d416-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6d416-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="6d416-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6d416-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="6d416-108">Attributes and Elements</span></span>

<span data-ttu-id="6d416-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="6d416-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6d416-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="6d416-110">Attributes</span></span>

<span data-ttu-id="6d416-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="6d416-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6d416-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6d416-112">Child Elements</span></span>

<span data-ttu-id="6d416-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="6d416-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6d416-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6d416-114">Parent Elements</span></span>

|<span data-ttu-id="6d416-115">Element</span><span class="sxs-lookup"><span data-stu-id="6d416-115">Element</span></span>|<span data-ttu-id="6d416-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6d416-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d416-117">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6d416-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="6d416-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="6d416-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6d416-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="6d416-119">Text Value</span></span>

<span data-ttu-id="6d416-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="6d416-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="6d416-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6d416-121">Remarks</span></span>

<span data-ttu-id="6d416-122">Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d416-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="6d416-123">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6d416-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6d416-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6d416-124">See Also</span></span>

[<span data-ttu-id="6d416-125">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6d416-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="6d416-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="6d416-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
