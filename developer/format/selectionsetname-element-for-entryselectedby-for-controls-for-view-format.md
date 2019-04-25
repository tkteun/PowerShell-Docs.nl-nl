---
title: SelectionSetName-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075644"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="a58a3-102">Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a58a3-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="a58a3-103">Hiermee geeft u een set van .NET-typen die gebruikmaken van deze definitie van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="a58a3-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="a58a3-104">Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.</span><span class="sxs-lookup"><span data-stu-id="a58a3-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="a58a3-105">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor besturingselementen voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) EntrySelectedBy Element voor CustomEntry voor besturingselementen voor weergave (indeling) SelectionSetName Element voor EntrySelectedBy voor besturingselementen voor weergave ( -Indeling)</span><span class="sxs-lookup"><span data-stu-id="a58a3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a58a3-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a58a3-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a58a3-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a58a3-107">Attributes and Elements</span></span>

<span data-ttu-id="a58a3-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="a58a3-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a58a3-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a58a3-109">Attributes</span></span>

<span data-ttu-id="a58a3-110">Geen</span><span class="sxs-lookup"><span data-stu-id="a58a3-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="a58a3-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a58a3-111">Child Elements</span></span>

<span data-ttu-id="a58a3-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="a58a3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a58a3-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a58a3-113">Parent Elements</span></span>

|<span data-ttu-id="a58a3-114">Element</span><span class="sxs-lookup"><span data-stu-id="a58a3-114">Element</span></span>|<span data-ttu-id="a58a3-115">Description</span><span class="sxs-lookup"><span data-stu-id="a58a3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a58a3-116">EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="a58a3-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="a58a3-117">Hiermee definieert u de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a58a3-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a58a3-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="a58a3-118">Text Value</span></span>

<span data-ttu-id="a58a3-119">Geef de naam van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="a58a3-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a58a3-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a58a3-120">Remarks</span></span>

<span data-ttu-id="a58a3-121">De besturingselementdefinitie van elk moet ten minste één naam, selectie instellen of selectievoorwaarde gedefinieerd hebben.</span><span class="sxs-lookup"><span data-stu-id="a58a3-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="a58a3-122">Selectiesets worden meestal gebruikt wanneer u wilt definiëren van een groep objecten die worden gebruikt in meerdere weergaven.</span><span class="sxs-lookup"><span data-stu-id="a58a3-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="a58a3-123">Zie voor meer informatie over het definiëren van selectiesets [definiëren voor de selectie wordt ingesteld](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a58a3-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a58a3-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a58a3-124">See Also</span></span>

[<span data-ttu-id="a58a3-125">EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="a58a3-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="a58a3-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="a58a3-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
