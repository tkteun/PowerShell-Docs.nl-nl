---
title: SelectionSetName-Element voor SelectionCondition voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063758"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="65bd4-102">Het element SelectionSetName voor SelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="65bd4-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="65bd4-103">Hiermee geeft u de set met .NET-typen waarvoor de voorwaarde is geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="65bd4-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="65bd4-104">Wanneer een van de typen in deze set aanwezig zijn, de voorwaarde wordt voldaan en het object met behulp van dit besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="65bd4-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="65bd4-105">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="65bd4-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="65bd4-106">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) EntrySelectedBy Element voor CustomEntry voor GroupBy (indeling) SelectionCondition Element voor EntrySelectedBy voor GroupBy (indeling) SelectionSetName Element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="65bd4-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="65bd4-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="65bd4-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="65bd4-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="65bd4-108">Attributes and Elements</span></span>

<span data-ttu-id="65bd4-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="65bd4-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="65bd4-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="65bd4-110">Attributes</span></span>

<span data-ttu-id="65bd4-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="65bd4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="65bd4-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="65bd4-112">Child Elements</span></span>

<span data-ttu-id="65bd4-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="65bd4-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="65bd4-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="65bd4-114">Parent Elements</span></span>

|<span data-ttu-id="65bd4-115">Element</span><span class="sxs-lookup"><span data-stu-id="65bd4-115">Element</span></span>|<span data-ttu-id="65bd4-116">Description</span><span class="sxs-lookup"><span data-stu-id="65bd4-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="65bd4-117">SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="65bd4-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="65bd4-118">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="65bd4-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="65bd4-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="65bd4-119">Text Value</span></span>

<span data-ttu-id="65bd4-120">Geef de naam van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="65bd4-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="65bd4-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="65bd4-121">Remarks</span></span>

<span data-ttu-id="65bd4-122">Selectiesets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een weergave met de opmaak-bestand definieert.</span><span class="sxs-lookup"><span data-stu-id="65bd4-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="65bd4-123">Zie voor meer informatie over het maken en verwijst naar een selectiesets [definiëren voor de selectie wordt ingesteld](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="65bd4-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="65bd4-124">Wanneer dit element is opgegeven, wordt u niet opgeven de [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="65bd4-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="65bd4-125">Zie voor meer informatie over het definiëren van de voorwaarden van de selectie [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="65bd4-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="65bd4-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="65bd4-126">See Also</span></span>

[<span data-ttu-id="65bd4-127">TypeName-Element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="65bd4-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="65bd4-128">SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="65bd4-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="65bd4-129">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="65bd4-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="65bd4-130">Selectiesets definiëren</span><span class="sxs-lookup"><span data-stu-id="65bd4-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="65bd4-131">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="65bd4-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
