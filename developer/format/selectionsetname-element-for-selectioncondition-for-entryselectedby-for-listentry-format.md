---
title: SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851147"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="d5f79-102">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor ListEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d5f79-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="d5f79-103">Hiermee geeft u de set met .NET-typen waarvoor de voorwaarde is geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="d5f79-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="d5f79-104">Wanneer een van de typen in deze set aanwezig zijn, de voorwaarde wordt voldaan en het object wordt weergegeven met behulp van deze definitie van de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="d5f79-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="d5f79-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries-Element (indeling) ListEntry-Element (indeling) EntrySelectedBy Element voor ListEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor ListEntry (indeling) SelectionSetName Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="d5f79-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d5f79-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d5f79-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d5f79-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d5f79-107">Attributes and Elements</span></span>

<span data-ttu-id="d5f79-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="d5f79-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d5f79-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d5f79-109">Attributes</span></span>

<span data-ttu-id="d5f79-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="d5f79-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d5f79-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d5f79-111">Child Elements</span></span>

<span data-ttu-id="d5f79-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="d5f79-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d5f79-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d5f79-113">Parent Elements</span></span>

|<span data-ttu-id="d5f79-114">Element</span><span class="sxs-lookup"><span data-stu-id="d5f79-114">Element</span></span>|<span data-ttu-id="d5f79-115">Description</span><span class="sxs-lookup"><span data-stu-id="d5f79-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d5f79-116">SelectionCondition-Element voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="d5f79-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="d5f79-117">Hiermee definieert u de voorwaarde die moet bestaan voor het gebruik van deze definitie van de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="d5f79-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d5f79-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="d5f79-118">Text Value</span></span>

<span data-ttu-id="d5f79-119">Geef de naam van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="d5f79-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d5f79-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d5f79-120">Remarks</span></span>

<span data-ttu-id="d5f79-121">De selectievoorwaarde een selectie instellen of .NET-type kunt opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="d5f79-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="d5f79-122">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d5f79-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d5f79-123">Selectiesets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een weergave met de opmaak-bestand definieert.</span><span class="sxs-lookup"><span data-stu-id="d5f79-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="d5f79-124">Zie voor meer informatie over het maken en verwijst naar een selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d5f79-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="d5f79-125">Zie voor meer informatie over andere onderdelen van een lijst weergeven, [het maken van een lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="d5f79-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d5f79-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d5f79-126">See Also</span></span>

[<span data-ttu-id="d5f79-127">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="d5f79-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d5f79-128">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="d5f79-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d5f79-129">SelectionCondition-Element voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="d5f79-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="d5f79-130">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5f79-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
