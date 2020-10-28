---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)
description: Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: b775aa8a3184aa3ebcbda17a8e3191c69d67a700
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645721"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="7b6df-103">Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7b6df-103">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="7b6df-104">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="7b6df-104">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="7b6df-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="7b6df-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="7b6df-106">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (indeling) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (Format) EntrySelectedBy-element voor SelectionSetName voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="7b6df-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7b6df-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="7b6df-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="7b6df-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7b6df-108">Attributes and Elements</span></span>

<span data-ttu-id="7b6df-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="7b6df-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7b6df-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7b6df-110">Attributes</span></span>

<span data-ttu-id="7b6df-111">Geen</span><span class="sxs-lookup"><span data-stu-id="7b6df-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="7b6df-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7b6df-112">Child Elements</span></span>

<span data-ttu-id="7b6df-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="7b6df-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7b6df-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7b6df-114">Parent Elements</span></span>

|<span data-ttu-id="7b6df-115">Element</span><span class="sxs-lookup"><span data-stu-id="7b6df-115">Element</span></span>|<span data-ttu-id="7b6df-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7b6df-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b6df-117">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7b6df-117">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="7b6df-118">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7b6df-118">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7b6df-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="7b6df-119">Text Value</span></span>

<span data-ttu-id="7b6df-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="7b6df-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b6df-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7b6df-121">Remarks</span></span>

<span data-ttu-id="7b6df-122">Voor elke controle definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="7b6df-122">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="7b6df-123">Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven.</span><span class="sxs-lookup"><span data-stu-id="7b6df-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="7b6df-124">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="7b6df-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7b6df-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7b6df-125">See Also</span></span>

[<span data-ttu-id="7b6df-126">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7b6df-126">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="7b6df-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="7b6df-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
