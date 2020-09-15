---
title: Het element PropertyName voor SelectionCondition voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8ada9a8ca7fbfdba5b2fea1881b2670c56a71d4f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773076"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="f763e-102">Het element PropertyName voor SelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f763e-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="f763e-103">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="f763e-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="f763e-104">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f763e-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="f763e-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f763e-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="f763e-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) voor SelectionCondition voor GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f763e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f763e-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="f763e-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f763e-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f763e-108">Attributes and Elements</span></span>

<span data-ttu-id="f763e-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="f763e-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f763e-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f763e-110">Attributes</span></span>

<span data-ttu-id="f763e-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="f763e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f763e-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f763e-112">Child Elements</span></span>

<span data-ttu-id="f763e-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="f763e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f763e-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f763e-114">Parent Elements</span></span>

|<span data-ttu-id="f763e-115">Element</span><span class="sxs-lookup"><span data-stu-id="f763e-115">Element</span></span>|<span data-ttu-id="f763e-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f763e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f763e-117">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f763e-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="f763e-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="f763e-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f763e-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="f763e-119">Text Value</span></span>

<span data-ttu-id="f763e-120">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="f763e-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="f763e-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f763e-121">Remarks</span></span>

<span data-ttu-id="f763e-122">De selectie voorwaarde moet ten minste één eigenschaps naam of een script opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="f763e-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="f763e-123">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f763e-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f763e-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f763e-124">See Also</span></span>

[<span data-ttu-id="f763e-125">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f763e-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="f763e-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="f763e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
