---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)
description: Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 42e9d2b00f7690e46242b2c4602245e4bf391bbf
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664950"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="ac472-103">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ac472-103">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="ac472-104">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="ac472-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="ac472-105">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ac472-105">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="ac472-106">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="ac472-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="ac472-107">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries-element voor het element CustomControl voor configuratie (Format) CustomEntry CustomControl voor besturings elementen voor configuratie (indeling) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor configuratie (Format) SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor configuratie (Format) script block-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="ac472-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ac472-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="ac472-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ac472-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ac472-109">Attributes and Elements</span></span>

<span data-ttu-id="ac472-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="ac472-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ac472-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ac472-111">Attributes</span></span>

<span data-ttu-id="ac472-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="ac472-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ac472-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ac472-113">Child Elements</span></span>

<span data-ttu-id="ac472-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="ac472-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ac472-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ac472-115">Parent Elements</span></span>

|<span data-ttu-id="ac472-116">Element</span><span class="sxs-lookup"><span data-stu-id="ac472-116">Element</span></span>|<span data-ttu-id="ac472-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ac472-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ac472-118">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ac472-118">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="ac472-119">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de algemene definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="ac472-119">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ac472-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="ac472-120">Text Value</span></span>

<span data-ttu-id="ac472-121">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="ac472-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="ac472-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ac472-122">Remarks</span></span>

<span data-ttu-id="ac472-123">Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ac472-123">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="ac472-124">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ac472-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ac472-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ac472-125">See Also</span></span>

[<span data-ttu-id="ac472-126">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ac472-126">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="ac472-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="ac472-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
