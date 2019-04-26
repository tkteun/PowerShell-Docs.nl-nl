---
title: SelectionSetName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064009"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="77714-102">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="77714-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="77714-103">Hiermee geeft u de set met .NET-typen waarvoor de voorwaarde is geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="77714-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="77714-104">Wanneer een van de typen in deze set aanwezig zijn, de voorwaarde wordt voldaan en het object met behulp van dit besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="77714-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="77714-105">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="77714-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="77714-106">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor besturingselementen voor het besturingselement Configuratie (-indeling) CustomEntry-Element voor CustomControl controles voor configuratie (-indeling) EntrySelectedBy-Element voor CustomEntry controles voor configuratie (-indeling) SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor Configuratie (-indeling) SelectionSetName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="77714-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="77714-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="77714-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="77714-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="77714-108">Attributes and Elements</span></span>

<span data-ttu-id="77714-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="77714-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="77714-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="77714-110">Attributes</span></span>

<span data-ttu-id="77714-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="77714-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="77714-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="77714-112">Child Elements</span></span>

<span data-ttu-id="77714-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="77714-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="77714-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="77714-114">Parent Elements</span></span>

|<span data-ttu-id="77714-115">Element</span><span class="sxs-lookup"><span data-stu-id="77714-115">Element</span></span>|<span data-ttu-id="77714-116">Description</span><span class="sxs-lookup"><span data-stu-id="77714-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77714-117">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="77714-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="77714-118">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="77714-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="77714-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="77714-119">Text Value</span></span>

<span data-ttu-id="77714-120">Geef de naam van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="77714-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="77714-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="77714-121">Remarks</span></span>

<span data-ttu-id="77714-122">Selectiesets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een weergave met de opmaak-bestand definieert.</span><span class="sxs-lookup"><span data-stu-id="77714-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="77714-123">Zie voor meer informatie over het maken en verwijst naar een selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="77714-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="77714-124">De selectievoorwaarde een selectie instellen of .NET-type kunt opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="77714-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="77714-125">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="77714-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="77714-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="77714-126">See Also</span></span>

[<span data-ttu-id="77714-127">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="77714-127">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="77714-128">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="77714-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="77714-129">Selectiesets definiëren</span><span class="sxs-lookup"><span data-stu-id="77714-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="77714-130">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="77714-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
