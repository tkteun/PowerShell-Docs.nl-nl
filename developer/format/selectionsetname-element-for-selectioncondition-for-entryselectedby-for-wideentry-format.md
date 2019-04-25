---
title: SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075474"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="dc9c0-102">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dc9c0-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="dc9c0-103">Hiermee geeft u de set met .NET-typen waarvoor de voorwaarde is geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="dc9c0-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="dc9c0-104">Wanneer een van de typen in deze set aanwezig zijn, de voorwaarde wordt voldaan en het object met behulp van deze definitie van de brede weergave wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="dc9c0-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="dc9c0-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) EntrySelectedBy Element voor WideEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling) SelectionSetName Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="dc9c0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dc9c0-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="dc9c0-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dc9c0-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="dc9c0-107">Attributes and Elements</span></span>

<span data-ttu-id="dc9c0-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="dc9c0-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dc9c0-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="dc9c0-109">Attributes</span></span>

<span data-ttu-id="dc9c0-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="dc9c0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dc9c0-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="dc9c0-111">Child Elements</span></span>

<span data-ttu-id="dc9c0-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="dc9c0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dc9c0-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="dc9c0-113">Parent Elements</span></span>

|<span data-ttu-id="dc9c0-114">Element</span><span class="sxs-lookup"><span data-stu-id="dc9c0-114">Element</span></span>|<span data-ttu-id="dc9c0-115">Description</span><span class="sxs-lookup"><span data-stu-id="dc9c0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc9c0-116">SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="dc9c0-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="dc9c0-117">Hiermee definieert u de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dc9c0-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dc9c0-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="dc9c0-118">Text Value</span></span>

<span data-ttu-id="dc9c0-119">Geef de naam van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="dc9c0-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="dc9c0-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="dc9c0-120">Remarks</span></span>

<span data-ttu-id="dc9c0-121">De selectievoorwaarde een selectie instellen of .NET-type kunt opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="dc9c0-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="dc9c0-122">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="dc9c0-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="dc9c0-123">Selectiesets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een weergave met de opmaak-bestand definieert.</span><span class="sxs-lookup"><span data-stu-id="dc9c0-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="dc9c0-124">Zie voor meer informatie over het maken en verwijst naar een selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="dc9c0-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="dc9c0-125">Zie voor meer informatie over andere onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="dc9c0-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dc9c0-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="dc9c0-126">See Also</span></span>

[<span data-ttu-id="dc9c0-127">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="dc9c0-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="dc9c0-128">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="dc9c0-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="dc9c0-129">Selectiesets definiëren</span><span class="sxs-lookup"><span data-stu-id="dc9c0-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="dc9c0-130">SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="dc9c0-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="dc9c0-131">TypeName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="dc9c0-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="dc9c0-132">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="dc9c0-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
