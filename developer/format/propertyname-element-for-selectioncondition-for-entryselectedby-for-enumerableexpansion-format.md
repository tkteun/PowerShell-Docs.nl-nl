---
title: PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849348"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="abac3-102">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="abac3-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="abac3-103">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="abac3-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="abac3-104">Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="abac3-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="abac3-105">Configuratie van Element (indeling) DefaultSettings-Element (indeling) EnumerableExpansions-Element (indeling) EnumerableExpansion-Element (indeling) EntrySelectedBy Element voor EnumerableExpansion (indeling) SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling) PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="abac3-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="abac3-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="abac3-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="abac3-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="abac3-107">Attributes and Elements</span></span>

<span data-ttu-id="abac3-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="abac3-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="abac3-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="abac3-109">Attributes</span></span>

<span data-ttu-id="abac3-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="abac3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="abac3-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="abac3-111">Child Elements</span></span>

<span data-ttu-id="abac3-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="abac3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="abac3-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="abac3-113">Parent Elements</span></span>

|<span data-ttu-id="abac3-114">Element</span><span class="sxs-lookup"><span data-stu-id="abac3-114">Element</span></span>|<span data-ttu-id="abac3-115">Description</span><span class="sxs-lookup"><span data-stu-id="abac3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="abac3-116">SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="abac3-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="abac3-117">De voorwaarde die moet aanwezig zijn om uit te breiden, de verzameling objecten van deze definitie wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="abac3-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="abac3-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="abac3-118">Text Value</span></span>

<span data-ttu-id="abac3-119">Geef de naam van de .NET-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="abac3-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="abac3-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="abac3-120">Remarks</span></span>

<span data-ttu-id="abac3-121">De selectievoorwaarde moet opgeven de naam van ten minste één eigenschap of een script om te evalueren, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="abac3-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="abac3-122">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="abac3-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="abac3-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="abac3-123">See Also</span></span>

[<span data-ttu-id="abac3-124">Voorwaarden voor wanneer gegevens definiëren wordt weergegeven</span><span class="sxs-lookup"><span data-stu-id="abac3-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="abac3-125">ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="abac3-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="abac3-126">SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="abac3-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="abac3-127">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="abac3-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
