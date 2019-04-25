---
title: ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064370"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="e3720-102">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e3720-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="e3720-103">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="e3720-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="e3720-104">Configuratie van Element (indeling) DefaultSettings-Element (indeling) EnumerableExpansions-Element (indeling) EnumerableExpansion-Element (indeling) EntrySelectedBy Element voor EnumerableExpansion (indeling) SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling) ScriptBlock Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="e3720-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3720-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e3720-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3720-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e3720-106">Attributes and Elements</span></span>

<span data-ttu-id="e3720-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="e3720-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3720-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e3720-108">Attributes</span></span>

<span data-ttu-id="e3720-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="e3720-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3720-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e3720-110">Child Elements</span></span>

<span data-ttu-id="e3720-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="e3720-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e3720-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e3720-112">Parent Elements</span></span>

|<span data-ttu-id="e3720-113">Element</span><span class="sxs-lookup"><span data-stu-id="e3720-113">Element</span></span>|<span data-ttu-id="e3720-114">Description</span><span class="sxs-lookup"><span data-stu-id="e3720-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3720-115">SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="e3720-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="e3720-116">De voorwaarde die moet aanwezig zijn om uit te breiden, de verzameling objecten van deze definitie wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="e3720-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e3720-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="e3720-117">Text Value</span></span>

<span data-ttu-id="e3720-118">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="e3720-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3720-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e3720-119">Remarks</span></span>

<span data-ttu-id="e3720-120">De selectievoorwaarde moet Geef ten minste één script of eigenschap op om te evalueren, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="e3720-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="e3720-121">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e3720-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3720-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e3720-122">See Also</span></span>

[<span data-ttu-id="e3720-123">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="e3720-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e3720-124">PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="e3720-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e3720-125">SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="e3720-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e3720-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3720-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
