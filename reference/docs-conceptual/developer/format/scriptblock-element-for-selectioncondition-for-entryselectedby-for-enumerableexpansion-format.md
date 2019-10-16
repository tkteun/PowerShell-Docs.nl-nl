---
title: Script block-element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358942"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="b9a70-102">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b9a70-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="b9a70-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b9a70-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="b9a70-104">Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) EntrySelectedBy element voor EnumerableExpansion (Format) SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (Format) script block-element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="b9a70-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b9a70-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b9a70-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b9a70-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b9a70-106">Attributes and Elements</span></span>

<span data-ttu-id="b9a70-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ScriptBlock` beschreven.</span><span class="sxs-lookup"><span data-stu-id="b9a70-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b9a70-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b9a70-108">Attributes</span></span>

<span data-ttu-id="b9a70-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="b9a70-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b9a70-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b9a70-110">Child Elements</span></span>

<span data-ttu-id="b9a70-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="b9a70-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b9a70-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b9a70-112">Parent Elements</span></span>

|<span data-ttu-id="b9a70-113">Element</span><span class="sxs-lookup"><span data-stu-id="b9a70-113">Element</span></span>|<span data-ttu-id="b9a70-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b9a70-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9a70-115">SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="b9a70-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b9a70-116">Hiermee definieert u de voor waarde die moet bestaan om de verzamelings objecten van deze definitie uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="b9a70-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b9a70-117">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="b9a70-117">Text Value</span></span>

<span data-ttu-id="b9a70-118">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="b9a70-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9a70-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b9a70-119">Remarks</span></span>

<span data-ttu-id="b9a70-120">Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b9a70-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="b9a70-121">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="b9a70-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b9a70-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b9a70-122">See Also</span></span>

[<span data-ttu-id="b9a70-123">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="b9a70-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b9a70-124">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="b9a70-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="b9a70-125">SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="b9a70-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="b9a70-126">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b9a70-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
