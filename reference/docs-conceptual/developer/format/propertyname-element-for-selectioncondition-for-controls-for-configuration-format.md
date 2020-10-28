---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)
description: Het element PropertyName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 5e4368a9546307c5ff223ae42ecaa1d2872bc587
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665954"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="199fb-103">Het element PropertyName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="199fb-103">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="199fb-104">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="199fb-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="199fb-105">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de vermelding gebruikt.</span><span class="sxs-lookup"><span data-stu-id="199fb-105">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="199fb-106">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="199fb-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="199fb-107">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (Format) CustomEntry-element voor CustomControl voor besturings elementen voor de configuratie (indeling) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de configuratie (indeling) SelectionCondition-element voor EntrySelectedBy voor CustomEntry voor de configuratie (Format) eigenschap naam van SelectionCondition for EntrySelectedBy voor List entry (Format)</span><span class="sxs-lookup"><span data-stu-id="199fb-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="199fb-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="199fb-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="199fb-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="199fb-109">Attributes and Elements</span></span>

<span data-ttu-id="199fb-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="199fb-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="199fb-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="199fb-111">Attributes</span></span>

<span data-ttu-id="199fb-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="199fb-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="199fb-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="199fb-113">Child Elements</span></span>

<span data-ttu-id="199fb-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="199fb-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="199fb-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="199fb-115">Parent Elements</span></span>

|<span data-ttu-id="199fb-116">Element</span><span class="sxs-lookup"><span data-stu-id="199fb-116">Element</span></span>|<span data-ttu-id="199fb-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="199fb-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="199fb-118">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="199fb-118">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="199fb-119">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een algemene definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="199fb-119">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="199fb-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="199fb-120">Text Value</span></span>

<span data-ttu-id="199fb-121">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="199fb-121">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="199fb-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="199fb-122">Remarks</span></span>

<span data-ttu-id="199fb-123">De selectie voorwaarde moet ten minste één eigenschaps naam of een script opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="199fb-123">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="199fb-124">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="199fb-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="199fb-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="199fb-125">See Also</span></span>

[<span data-ttu-id="199fb-126">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="199fb-126">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="199fb-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="199fb-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
