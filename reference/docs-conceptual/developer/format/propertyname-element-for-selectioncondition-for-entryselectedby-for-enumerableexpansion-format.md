---
title: Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c0081cb724ccaf1c04241aafa177880d7c0e5dbe
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783463"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="239db-102">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="239db-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="239db-103">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="239db-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="239db-104">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="239db-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="239db-105">Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) EntrySelectedBy element voor EnumerableExpansion (Format) SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (Format) eigenschap Naam element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="239db-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="239db-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="239db-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="239db-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="239db-107">Attributes and Elements</span></span>

<span data-ttu-id="239db-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="239db-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="239db-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="239db-109">Attributes</span></span>

<span data-ttu-id="239db-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="239db-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="239db-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="239db-111">Child Elements</span></span>

<span data-ttu-id="239db-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="239db-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="239db-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="239db-113">Parent Elements</span></span>

|<span data-ttu-id="239db-114">Element</span><span class="sxs-lookup"><span data-stu-id="239db-114">Element</span></span>|<span data-ttu-id="239db-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="239db-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="239db-116">Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="239db-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="239db-117">Hiermee definieert u de voor waarde die moet bestaan om de verzamelings objecten van deze definitie uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="239db-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="239db-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="239db-118">Text Value</span></span>

<span data-ttu-id="239db-119">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="239db-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="239db-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="239db-120">Remarks</span></span>

<span data-ttu-id="239db-121">Voor de selectie voorwaarde moet ten minste één eigenschaps naam of een script worden opgegeven om te evalueren, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="239db-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="239db-122">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="239db-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="239db-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="239db-123">See Also</span></span>

[<span data-ttu-id="239db-124">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="239db-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="239db-125">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="239db-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="239db-126">Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="239db-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="239db-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="239db-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
