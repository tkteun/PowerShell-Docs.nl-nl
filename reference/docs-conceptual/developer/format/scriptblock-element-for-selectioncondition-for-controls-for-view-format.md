---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)
description: Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: 7eed3b8a06bc45396026b8e2a7454447b3090d74
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664942"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="6ab4b-103">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6ab4b-103">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="6ab4b-104">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="6ab4b-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="6ab4b-105">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6ab4b-105">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="6ab4b-106">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="6ab4b-106">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="6ab4b-107">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (indeling) Control element (Format) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings elementen voor het element Control (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor de weer gave (Format) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de weer gave (Format) SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor de weer gave (indeling) script block element voor SelectionCondition voor besturings elementen</span><span class="sxs-lookup"><span data-stu-id="6ab4b-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6ab4b-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="6ab4b-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6ab4b-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="6ab4b-109">Attributes and Elements</span></span>

<span data-ttu-id="6ab4b-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="6ab4b-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6ab4b-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="6ab4b-111">Attributes</span></span>

<span data-ttu-id="6ab4b-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="6ab4b-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6ab4b-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6ab4b-113">Child Elements</span></span>

<span data-ttu-id="6ab4b-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="6ab4b-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6ab4b-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6ab4b-115">Parent Elements</span></span>

|<span data-ttu-id="6ab4b-116">Element</span><span class="sxs-lookup"><span data-stu-id="6ab4b-116">Element</span></span>|<span data-ttu-id="6ab4b-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6ab4b-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6ab4b-118">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6ab4b-118">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="6ab4b-119">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="6ab4b-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6ab4b-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="6ab4b-120">Text Value</span></span>

<span data-ttu-id="6ab4b-121">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="6ab4b-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="6ab4b-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6ab4b-122">Remarks</span></span>

<span data-ttu-id="6ab4b-123">Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6ab4b-123">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="6ab4b-124">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6ab4b-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6ab4b-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6ab4b-125">See Also</span></span>

[<span data-ttu-id="6ab4b-126">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6ab4b-126">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="6ab4b-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="6ab4b-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
