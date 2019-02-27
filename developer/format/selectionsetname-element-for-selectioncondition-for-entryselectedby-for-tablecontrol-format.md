---
title: SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851903"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="e280e-102">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e280e-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="e280e-103">Hiermee geeft u de set met .NET-typen waarvoor de voorwaarde is geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="e280e-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="e280e-104">Wanneer een van de typen in deze set aanwezig zijn, de voorwaarde wordt voldaan en het object wordt weergegeven met behulp van deze definitie van de tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="e280e-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="e280e-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries-Element (indeling) TableRowEntry-Element (indeling) EntrySelectedBy Element voor TableRowEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling) SelectionSetName Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="e280e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e280e-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e280e-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e280e-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e280e-107">Attributes and Elements</span></span>

<span data-ttu-id="e280e-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="e280e-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e280e-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e280e-109">Attributes</span></span>

<span data-ttu-id="e280e-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="e280e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e280e-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e280e-111">Child Elements</span></span>

<span data-ttu-id="e280e-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="e280e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e280e-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e280e-113">Parent Elements</span></span>

|<span data-ttu-id="e280e-114">Element</span><span class="sxs-lookup"><span data-stu-id="e280e-114">Element</span></span>|<span data-ttu-id="e280e-115">Description</span><span class="sxs-lookup"><span data-stu-id="e280e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e280e-116">SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="e280e-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e280e-117">Hiermee definieert u de voorwaarde die moet aanwezig zijn als u wilt gebruiken voor deze definitie van de tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="e280e-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e280e-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="e280e-118">Text Value</span></span>

<span data-ttu-id="e280e-119">Geef de naam van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="e280e-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e280e-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e280e-120">Remarks</span></span>

<span data-ttu-id="e280e-121">De selectievoorwaarde een selectie instellen of .NET-type kunt opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="e280e-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="e280e-122">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e280e-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e280e-123">Selectiesets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een weergave met de opmaak-bestand definieert.</span><span class="sxs-lookup"><span data-stu-id="e280e-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="e280e-124">Zie voor meer informatie over het maken en verwijst naar een selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e280e-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="e280e-125">Zie voor meer informatie over andere onderdelen van een brede weergave [het maken van een tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e280e-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e280e-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e280e-126">See Also</span></span>

[<span data-ttu-id="e280e-127">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="e280e-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e280e-128">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="e280e-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e280e-129">TypeName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="e280e-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e280e-130">SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="e280e-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e280e-131">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="e280e-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
