---
title: Het element PropertyName voor SelectionCondition voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354101"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="7b08b-102">Het element PropertyName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7b08b-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="7b08b-103">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="7b08b-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="7b08b-104">Als deze eigenschap aanwezig is of als deze wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt de vermelding gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7b08b-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="7b08b-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="7b08b-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="7b08b-106">Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het configureren van een configuratie ( Format) CustomEntry element voor CustomControl voor besturings elementen voor de configuratie (indeling) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de configuratie (Format) SelectionCondition element voor EntrySelectedBy voor de configuratie ( Indeling) eigenschaps element voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="7b08b-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7b08b-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7b08b-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7b08b-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7b08b-108">Attributes and Elements</span></span>

<span data-ttu-id="7b08b-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `PropertyName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="7b08b-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7b08b-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7b08b-110">Attributes</span></span>

<span data-ttu-id="7b08b-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="7b08b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7b08b-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7b08b-112">Child Elements</span></span>

<span data-ttu-id="7b08b-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="7b08b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7b08b-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7b08b-114">Parent Elements</span></span>

|<span data-ttu-id="7b08b-115">Element</span><span class="sxs-lookup"><span data-stu-id="7b08b-115">Element</span></span>|<span data-ttu-id="7b08b-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7b08b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b08b-117">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="7b08b-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="7b08b-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een algemene definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="7b08b-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7b08b-119">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="7b08b-119">Text Value</span></span>

<span data-ttu-id="7b08b-120">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="7b08b-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b08b-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7b08b-121">Remarks</span></span>

<span data-ttu-id="7b08b-122">De selectie voorwaarde moet ten minste één eigenschaps naam of een script opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="7b08b-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="7b08b-123">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7b08b-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7b08b-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7b08b-124">See Also</span></span>

[<span data-ttu-id="7b08b-125">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="7b08b-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="7b08b-126">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="7b08b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
