---
title: Het element PropertyName voor SelectionCondition voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7730951a840fcfcd8bf819fff5182049bd6b6c23
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773127"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="b9742-102">Het element PropertyName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b9742-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b9742-103">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b9742-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b9742-104">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de vermelding gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b9742-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="b9742-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="b9742-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b9742-106">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (Format) CustomEntry-element voor CustomControl voor besturings elementen voor de configuratie (indeling) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de configuratie (indeling) SelectionCondition-element voor EntrySelectedBy voor CustomEntry voor de configuratie (Format) eigenschap naam van SelectionCondition for EntrySelectedBy voor List entry (Format)</span><span class="sxs-lookup"><span data-stu-id="b9742-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b9742-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="b9742-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b9742-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b9742-108">Attributes and Elements</span></span>

<span data-ttu-id="b9742-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="b9742-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b9742-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b9742-110">Attributes</span></span>

<span data-ttu-id="b9742-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="b9742-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b9742-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b9742-112">Child Elements</span></span>

<span data-ttu-id="b9742-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="b9742-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b9742-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b9742-114">Parent Elements</span></span>

|<span data-ttu-id="b9742-115">Element</span><span class="sxs-lookup"><span data-stu-id="b9742-115">Element</span></span>|<span data-ttu-id="b9742-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b9742-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9742-117">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b9742-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="b9742-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een algemene definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="b9742-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b9742-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="b9742-119">Text Value</span></span>

<span data-ttu-id="b9742-120">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="b9742-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9742-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b9742-121">Remarks</span></span>

<span data-ttu-id="b9742-122">De selectie voorwaarde moet ten minste één eigenschaps naam of een script opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="b9742-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="b9742-123">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b9742-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b9742-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b9742-124">See Also</span></span>

[<span data-ttu-id="b9742-125">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b9742-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="b9742-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b9742-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
