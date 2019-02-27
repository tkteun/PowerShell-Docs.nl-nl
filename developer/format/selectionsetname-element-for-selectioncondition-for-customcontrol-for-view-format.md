---
title: SelectionSetName-Element voor SelectionCondition voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851546"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="6e4b9-102">Het element SelectionSetName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6e4b9-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="6e4b9-103">Hiermee geeft u de set met .NET-typen waarvoor de voorwaarde is geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="6e4b9-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="6e4b9-104">Wanneer een van de typen in deze set aanwezig zijn, de voorwaarde wordt voldaan en het object wordt weergegeven met behulp van dit besturingselement.</span><span class="sxs-lookup"><span data-stu-id="6e4b9-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="6e4b9-105">Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.</span><span class="sxs-lookup"><span data-stu-id="6e4b9-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="6e4b9-106">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor EntrySelectedBy weergeven (indeling) Element voor CustomEntry voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="6e4b9-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6e4b9-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6e4b9-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6e4b9-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="6e4b9-108">Attributes and Elements</span></span>

<span data-ttu-id="6e4b9-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="6e4b9-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6e4b9-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="6e4b9-110">Attributes</span></span>

<span data-ttu-id="6e4b9-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="6e4b9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6e4b9-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6e4b9-112">Child Elements</span></span>

<span data-ttu-id="6e4b9-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="6e4b9-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6e4b9-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6e4b9-114">Parent Elements</span></span>

|<span data-ttu-id="6e4b9-115">Element</span><span class="sxs-lookup"><span data-stu-id="6e4b9-115">Element</span></span>|<span data-ttu-id="6e4b9-116">Description</span><span class="sxs-lookup"><span data-stu-id="6e4b9-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6e4b9-117">SelectionCondition-Element voor EntrySelectedBy voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="6e4b9-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="6e4b9-118">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6e4b9-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6e4b9-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="6e4b9-119">Text Value</span></span>

<span data-ttu-id="6e4b9-120">Geef de naam van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="6e4b9-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="6e4b9-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6e4b9-121">Remarks</span></span>

<span data-ttu-id="6e4b9-122">Selectiesets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een weergave met de opmaak-bestand definieert.</span><span class="sxs-lookup"><span data-stu-id="6e4b9-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="6e4b9-123">Zie voor meer informatie over het maken en verwijst naar een selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="6e4b9-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="6e4b9-124">De selectievoorwaarde een selectie instellen of .NET-type kunt opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="6e4b9-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="6e4b9-125">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6e4b9-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e4b9-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6e4b9-126">See Also</span></span>

[<span data-ttu-id="6e4b9-127">SelectionCondition-Element voor EntrySelectedBy voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="6e4b9-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="6e4b9-128">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="6e4b9-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6e4b9-129">Selectiesets definiëren</span><span class="sxs-lookup"><span data-stu-id="6e4b9-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="6e4b9-130">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e4b9-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
