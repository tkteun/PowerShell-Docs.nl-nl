---
title: Het element PropertyName voor SelectionCondition voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: aa3955b84b8de9901f394e8108f31440fcb6c942
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780794"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="fc571-102">Het element PropertyName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fc571-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="fc571-103">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="fc571-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="fc571-104">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fc571-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="fc571-105">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="fc571-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="fc571-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element voor weer gave (indeling) CustomEntries-element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor CustomControl voor weer gave (Format) CustomItem-element voor CustomEntry voor CustomControl voor weer gave (Format) EntrySelectedBy-element voor CustomEntry voor de weer gave (Format) SelectionCondition-element voor EntrySelectedBy voor het object CustomControl voor de weer gave (Format) voor SelectionCondition voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fc571-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fc571-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="fc571-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fc571-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="fc571-108">Attributes and Elements</span></span>

<span data-ttu-id="fc571-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="fc571-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fc571-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="fc571-110">Attributes</span></span>

<span data-ttu-id="fc571-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="fc571-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fc571-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fc571-112">Child Elements</span></span>

<span data-ttu-id="fc571-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="fc571-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fc571-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fc571-114">Parent Elements</span></span>

|<span data-ttu-id="fc571-115">Element</span><span class="sxs-lookup"><span data-stu-id="fc571-115">Element</span></span>|<span data-ttu-id="fc571-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fc571-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fc571-117">SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fc571-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="fc571-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="fc571-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fc571-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="fc571-119">Text Value</span></span>

<span data-ttu-id="fc571-120">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="fc571-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc571-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="fc571-121">Remarks</span></span>

<span data-ttu-id="fc571-122">De selectie voorwaarde moet ten minste één eigenschaps naam of een script opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="fc571-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="fc571-123">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fc571-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fc571-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fc571-124">See Also</span></span>

[<span data-ttu-id="fc571-125">SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fc571-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="fc571-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="fc571-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
