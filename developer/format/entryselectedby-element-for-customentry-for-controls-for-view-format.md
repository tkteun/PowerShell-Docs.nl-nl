---
title: EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066240"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="dfc54-102">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dfc54-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="dfc54-103">Hiermee definieert u de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dfc54-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="dfc54-104">Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.</span><span class="sxs-lookup"><span data-stu-id="dfc54-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="dfc54-105">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor besturingselementen voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) EntrySelectedBy Element voor CustomEntry voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="dfc54-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dfc54-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="dfc54-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dfc54-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="dfc54-107">Attributes and Elements</span></span>

<span data-ttu-id="dfc54-108">De volgende secties worden de kenmerken en onderliggende elementen bovenliggend element van de `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="dfc54-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="dfc54-109">U moet ten minste één type, selectie instellen of selectievoorwaarde voor een definitie opgeven.</span><span class="sxs-lookup"><span data-stu-id="dfc54-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="dfc54-110">Er is geen maximale limiet voor het aantal onderliggende elementen die u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="dfc54-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="dfc54-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="dfc54-111">Attributes</span></span>

<span data-ttu-id="dfc54-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="dfc54-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dfc54-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="dfc54-113">Child Elements</span></span>

|<span data-ttu-id="dfc54-114">Element</span><span class="sxs-lookup"><span data-stu-id="dfc54-114">Element</span></span>|<span data-ttu-id="dfc54-115">Description</span><span class="sxs-lookup"><span data-stu-id="dfc54-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dfc54-116">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="dfc54-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="dfc54-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="dfc54-117">Optional element.</span></span><br /><br /> <span data-ttu-id="dfc54-118">Hiermee definieert u de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dfc54-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="dfc54-119">SelectionSetName-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="dfc54-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="dfc54-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="dfc54-120">Optional element.</span></span><br /><br /> <span data-ttu-id="dfc54-121">Hiermee geeft u een set van .NET-typen die gebruikmaken van deze definitie van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="dfc54-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="dfc54-122">TypeName-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="dfc54-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="dfc54-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="dfc54-123">Optional element.</span></span><br /><br /> <span data-ttu-id="dfc54-124">Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="dfc54-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dfc54-125">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="dfc54-125">Parent Elements</span></span>

|<span data-ttu-id="dfc54-126">Element</span><span class="sxs-lookup"><span data-stu-id="dfc54-126">Element</span></span>|<span data-ttu-id="dfc54-127">Description</span><span class="sxs-lookup"><span data-stu-id="dfc54-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dfc54-128">CustomEntry-Element voor CustomEntries voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="dfc54-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="dfc54-129">Bevat een definitie van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="dfc54-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dfc54-130">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="dfc54-130">Remarks</span></span>

<span data-ttu-id="dfc54-131">Selectie voorwaarden worden gebruikt voor het definiëren van een voorwaarde moet bestaan voor de definitie moet worden gebruikt, bijvoorbeeld wanneer een object een bepaalde eigenschap heeft of wanneer de waarde van een bepaalde eigenschap of script wordt geëvalueerd als `true`.</span><span class="sxs-lookup"><span data-stu-id="dfc54-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="dfc54-132">Zie voor meer informatie over de voorwaarden van de selectie [definiëren voorwaarden voor wanneer een item weergeven of Item wordt gebruikt](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="dfc54-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dfc54-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="dfc54-133">See Also</span></span>

[<span data-ttu-id="dfc54-134">CustomEntry-Element voor CustomEntries voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="dfc54-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="dfc54-135">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="dfc54-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
