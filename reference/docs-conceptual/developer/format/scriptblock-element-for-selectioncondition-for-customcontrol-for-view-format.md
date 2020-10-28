---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor SelectionCondition voor CustomControl voor Weergave (opmaak)
description: Het element ScriptBlock voor SelectionCondition voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 78b977548243b6f3a658f15a0249d8cad12e2f1b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664920"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="5723b-103">Het element ScriptBlock voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5723b-103">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="5723b-104">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="5723b-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="5723b-105">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5723b-105">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="5723b-106">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="5723b-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="5723b-107">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (Format) CustomControl element voor weer gave (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor CustomControl voor weer gave (Format) CustomItem-element voor CustomEntry voor het object CustomControl voor weer gave (Format) SelectionCondition voor EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="5723b-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5723b-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="5723b-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5723b-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="5723b-109">Attributes and Elements</span></span>

<span data-ttu-id="5723b-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="5723b-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5723b-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="5723b-111">Attributes</span></span>

<span data-ttu-id="5723b-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="5723b-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5723b-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5723b-113">Child Elements</span></span>

<span data-ttu-id="5723b-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="5723b-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5723b-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5723b-115">Parent Elements</span></span>

|<span data-ttu-id="5723b-116">Element</span><span class="sxs-lookup"><span data-stu-id="5723b-116">Element</span></span>|<span data-ttu-id="5723b-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5723b-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5723b-118">SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5723b-118">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="5723b-119">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="5723b-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5723b-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="5723b-120">Text Value</span></span>

<span data-ttu-id="5723b-121">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="5723b-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="5723b-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5723b-122">Remarks</span></span>

<span data-ttu-id="5723b-123">Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="5723b-123">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="5723b-124">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5723b-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5723b-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5723b-125">See Also</span></span>

[<span data-ttu-id="5723b-126">SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5723b-126">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="5723b-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="5723b-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
