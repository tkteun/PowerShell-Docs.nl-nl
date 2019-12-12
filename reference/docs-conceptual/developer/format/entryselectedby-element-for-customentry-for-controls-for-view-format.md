---
title: EntrySelectedBy-element voor CustomEntry voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355144"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="49c00-102">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="49c00-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="49c00-103">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="49c00-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="49c00-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="49c00-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="49c00-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor besturings elementen voor weer gave (indeling) CustomEntry element voor CustomEntries voor besturings elementen voor de weer gave (Format) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="49c00-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="49c00-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="49c00-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="49c00-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="49c00-107">Attributes and Elements</span></span>

<span data-ttu-id="49c00-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `EntrySelectedBy` beschreven.</span><span class="sxs-lookup"><span data-stu-id="49c00-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="49c00-109">U moet ten minste één type, selectieset of selectie voorwaarde voor een definitie opgeven.</span><span class="sxs-lookup"><span data-stu-id="49c00-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="49c00-110">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="49c00-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="49c00-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="49c00-111">Attributes</span></span>

<span data-ttu-id="49c00-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="49c00-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="49c00-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="49c00-113">Child Elements</span></span>

|<span data-ttu-id="49c00-114">Element</span><span class="sxs-lookup"><span data-stu-id="49c00-114">Element</span></span>|<span data-ttu-id="49c00-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="49c00-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="49c00-116">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="49c00-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="49c00-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="49c00-117">Optional element.</span></span><br /><br /> <span data-ttu-id="49c00-118">Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="49c00-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="49c00-119">SelectionSetName-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="49c00-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="49c00-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="49c00-120">Optional element.</span></span><br /><br /> <span data-ttu-id="49c00-121">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="49c00-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="49c00-122">TypeName-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="49c00-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="49c00-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="49c00-123">Optional element.</span></span><br /><br /> <span data-ttu-id="49c00-124">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="49c00-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="49c00-125">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="49c00-125">Parent Elements</span></span>

|<span data-ttu-id="49c00-126">Element</span><span class="sxs-lookup"><span data-stu-id="49c00-126">Element</span></span>|<span data-ttu-id="49c00-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="49c00-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="49c00-128">CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="49c00-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="49c00-129">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="49c00-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="49c00-130">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="49c00-130">Remarks</span></span>

<span data-ttu-id="49c00-131">De selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of wanneer een specifieke eigenschaps waarde of script wordt geëvalueerd als `true`.</span><span class="sxs-lookup"><span data-stu-id="49c00-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="49c00-132">Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="49c00-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="49c00-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="49c00-133">See Also</span></span>

[<span data-ttu-id="49c00-134">CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="49c00-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="49c00-135">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="49c00-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
