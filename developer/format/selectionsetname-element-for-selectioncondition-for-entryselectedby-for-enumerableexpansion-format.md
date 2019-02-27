---
title: SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850461"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="4c392-102">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4c392-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="4c392-103">Hiermee geeft u de set met .NET-typen waarvoor de voorwaarde is geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="4c392-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="4c392-104">Wanneer een van de typen in deze set aanwezig zijn, wordt de voorwaarde wordt voldaan.</span><span class="sxs-lookup"><span data-stu-id="4c392-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="4c392-105">Configuratie van Element DefaultSettings Element (indeling) EnumerableExpansions-Element (indeling) EnumerableExpansions-Element (indeling) EntrySelectedBy Element voor EnumerableExpansion (indeling) SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling) SelectionSetName Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="4c392-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4c392-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="4c392-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4c392-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="4c392-107">Attributes and Elements</span></span>

<span data-ttu-id="4c392-108">De volgende secties worden de kenmerken en onderliggende elementen bovenliggend element van de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="4c392-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4c392-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="4c392-109">Attributes</span></span>

<span data-ttu-id="4c392-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="4c392-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4c392-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4c392-111">Child Elements</span></span>

<span data-ttu-id="4c392-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="4c392-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4c392-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4c392-113">Parent Elements</span></span>

|<span data-ttu-id="4c392-114">Element</span><span class="sxs-lookup"><span data-stu-id="4c392-114">Element</span></span>|<span data-ttu-id="4c392-115">Description</span><span class="sxs-lookup"><span data-stu-id="4c392-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4c392-116">SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="4c392-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="4c392-117">De voorwaarde die moet aanwezig zijn om uit te breiden, de verzameling objecten van deze definitie wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="4c392-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4c392-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="4c392-118">Text Value</span></span>

<span data-ttu-id="4c392-119">Geef de naam van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="4c392-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="4c392-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="4c392-120">Remarks</span></span>

<span data-ttu-id="4c392-121">De selectievoorwaarde een selectie instellen of .NET-type kunt opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="4c392-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="4c392-122">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="4c392-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="4c392-123">Selectiesets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een weergave met de opmaak-bestand definieert.</span><span class="sxs-lookup"><span data-stu-id="4c392-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="4c392-124">Zie voor meer informatie over het maken en verwijst naar een selectiesets [definiëren voor de selectie wordt ingesteld](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="4c392-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4c392-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4c392-125">See Also</span></span>

[<span data-ttu-id="4c392-126">Selectiesets definiëren</span><span class="sxs-lookup"><span data-stu-id="4c392-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="4c392-127">SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="4c392-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="4c392-128">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="4c392-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
