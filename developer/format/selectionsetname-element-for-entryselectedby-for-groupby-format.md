---
title: SelectionSetName-Element voor EntrySelectedBy voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064064"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="1c00e-102">Het element SelectionSetName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1c00e-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="1c00e-103">Hiermee geeft u een set van .NET-objecten voor de vermelding in de lijst.</span><span class="sxs-lookup"><span data-stu-id="1c00e-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="1c00e-104">Er is geen limiet voor het aantal selectiesets die kan worden opgegeven voor een vermelding.</span><span class="sxs-lookup"><span data-stu-id="1c00e-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="1c00e-105">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="1c00e-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1c00e-106">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) EntrySelectedBy Element voor CustomEntry voor GroupBy (indeling) SelectionSetName Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="1c00e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1c00e-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1c00e-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1c00e-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1c00e-108">Attributes and Elements</span></span>

<span data-ttu-id="1c00e-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="1c00e-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1c00e-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1c00e-110">Attributes</span></span>

<span data-ttu-id="1c00e-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="1c00e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1c00e-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1c00e-112">Child Elements</span></span>

<span data-ttu-id="1c00e-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="1c00e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1c00e-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1c00e-114">Parent Elements</span></span>

|<span data-ttu-id="1c00e-115">Element</span><span class="sxs-lookup"><span data-stu-id="1c00e-115">Element</span></span>|<span data-ttu-id="1c00e-116">Description</span><span class="sxs-lookup"><span data-stu-id="1c00e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c00e-117">EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="1c00e-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="1c00e-118">Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste vermelding of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1c00e-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1c00e-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="1c00e-119">Text Value</span></span>

<span data-ttu-id="1c00e-120">Geef de naam van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="1c00e-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c00e-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1c00e-121">Remarks</span></span>

<span data-ttu-id="1c00e-122">De definitie van elk aangepast besturingselement moet ten minste één typenaam, selectie instellen of selectievoorwaarde gedefinieerd hebben.</span><span class="sxs-lookup"><span data-stu-id="1c00e-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="1c00e-123">Selectiesets worden meestal gebruikt wanneer u wilt definiëren van een groep objecten die worden gebruikt in meerdere weergaven.</span><span class="sxs-lookup"><span data-stu-id="1c00e-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="1c00e-124">U wilt bijvoorbeeld een tabel en een lijstweergave voor dezelfde set objecten maken.</span><span class="sxs-lookup"><span data-stu-id="1c00e-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="1c00e-125">Zie voor meer informatie over het definiëren van selectiesets [definiëren voor de selectie wordt ingesteld](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="1c00e-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="1c00e-126">Zie voor meer informatie over de onderdelen van de weergave van een aangepast besturingselement [het maken van aangepaste besturingselementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="1c00e-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c00e-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1c00e-127">See Also</span></span>

[<span data-ttu-id="1c00e-128">EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="1c00e-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="1c00e-129">Het maken van aangepaste besturingselementen</span><span class="sxs-lookup"><span data-stu-id="1c00e-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="1c00e-130">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c00e-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
