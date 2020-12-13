---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)
description: Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 42e9d2b00f7690e46242b2c4602245e4bf391bbf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664950"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="01103-103">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="01103-103">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="01103-104">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="01103-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="01103-105">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="01103-105">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="01103-106">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="01103-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="01103-107">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries-element voor het element CustomControl voor configuratie (Format) CustomEntry CustomControl voor besturings elementen voor configuratie (indeling) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor configuratie (Format) SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor configuratie (Format) script block-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="01103-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="01103-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="01103-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="01103-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="01103-109">Attributes and Elements</span></span>

<span data-ttu-id="01103-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="01103-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="01103-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="01103-111">Attributes</span></span>

<span data-ttu-id="01103-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="01103-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="01103-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="01103-113">Child Elements</span></span>

<span data-ttu-id="01103-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="01103-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="01103-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="01103-115">Parent Elements</span></span>

|<span data-ttu-id="01103-116">Element</span><span class="sxs-lookup"><span data-stu-id="01103-116">Element</span></span>|<span data-ttu-id="01103-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="01103-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="01103-118">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="01103-118">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="01103-119">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de algemene definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="01103-119">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="01103-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="01103-120">Text Value</span></span>

<span data-ttu-id="01103-121">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="01103-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="01103-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="01103-122">Remarks</span></span>

<span data-ttu-id="01103-123">Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="01103-123">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="01103-124">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="01103-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="01103-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="01103-125">See Also</span></span>

[<span data-ttu-id="01103-126">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="01103-126">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="01103-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="01103-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
