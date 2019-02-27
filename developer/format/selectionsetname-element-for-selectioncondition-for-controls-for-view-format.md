---
title: SelectionSetName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846191"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="40809-102">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="40809-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="40809-103">Hiermee geeft u de set met .NET-typen waarvoor de voorwaarde is geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="40809-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="40809-104">Wanneer een van de typen in deze set aanwezig zijn, de voorwaarde wordt voldaan en het object wordt weergegeven met behulp van dit besturingselement.</span><span class="sxs-lookup"><span data-stu-id="40809-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="40809-105">Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.</span><span class="sxs-lookup"><span data-stu-id="40809-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="40809-106">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor besturingselementen voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) EntrySelectedBy Element voor CustomEntry voor besturingselementen voor weergave (indeling) SelectionCondition Element voor EntrySelectedBy voor besturingselementen voor weergave ( -Indeling) SelectionSetName Element voor SelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="40809-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="40809-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="40809-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="40809-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="40809-108">Attributes and Elements</span></span>

<span data-ttu-id="40809-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="40809-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="40809-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="40809-110">Attributes</span></span>

<span data-ttu-id="40809-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="40809-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="40809-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="40809-112">Child Elements</span></span>

<span data-ttu-id="40809-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="40809-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="40809-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="40809-114">Parent Elements</span></span>

|<span data-ttu-id="40809-115">Element</span><span class="sxs-lookup"><span data-stu-id="40809-115">Element</span></span>|<span data-ttu-id="40809-116">Description</span><span class="sxs-lookup"><span data-stu-id="40809-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="40809-117">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="40809-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="40809-118">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="40809-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="40809-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="40809-119">Text Value</span></span>

<span data-ttu-id="40809-120">Geef de naam van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="40809-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="40809-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="40809-121">Remarks</span></span>

<span data-ttu-id="40809-122">Selectiesets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een weergave met de opmaak-bestand definieert.</span><span class="sxs-lookup"><span data-stu-id="40809-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="40809-123">Zie voor meer informatie over het maken en verwijst naar een selectiesets [definiëren voor de selectie wordt ingesteld](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="40809-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="40809-124">De selectievoorwaarde een selectie instellen of .NET-type kunt opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="40809-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="40809-125">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="40809-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="40809-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="40809-126">See Also</span></span>

[<span data-ttu-id="40809-127">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="40809-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="40809-128">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="40809-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="40809-129">Selectiesets definiëren</span><span class="sxs-lookup"><span data-stu-id="40809-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="40809-130">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="40809-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
