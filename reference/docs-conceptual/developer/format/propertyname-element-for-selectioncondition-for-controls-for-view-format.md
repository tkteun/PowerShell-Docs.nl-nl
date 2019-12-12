---
title: Het element PropertyName voor SelectionCondition voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354073"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="58aec-102">Het element PropertyName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="58aec-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="58aec-103">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="58aec-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="58aec-104">Wanneer deze eigenschap aanwezig is of wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt de vermelding gebruikt.</span><span class="sxs-lookup"><span data-stu-id="58aec-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="58aec-105">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="58aec-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="58aec-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor besturings elementen voor weer gave (indeling) CustomEntry element voor CustomEntries voor besturings elementen voor de weer gave (Format) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de weer gave (Format) SelectionCondition-element voor EntrySelectedBy for Controls ( Indeling) element PropertyName voor SelectionCondition voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="58aec-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="58aec-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="58aec-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="58aec-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="58aec-108">Attributes and Elements</span></span>

<span data-ttu-id="58aec-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `PropertyName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="58aec-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="58aec-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="58aec-110">Attributes</span></span>

<span data-ttu-id="58aec-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="58aec-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="58aec-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="58aec-112">Child Elements</span></span>

<span data-ttu-id="58aec-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="58aec-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="58aec-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="58aec-114">Parent Elements</span></span>

|<span data-ttu-id="58aec-115">Element</span><span class="sxs-lookup"><span data-stu-id="58aec-115">Element</span></span>|<span data-ttu-id="58aec-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="58aec-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="58aec-117">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="58aec-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="58aec-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="58aec-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="58aec-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="58aec-119">Text Value</span></span>

<span data-ttu-id="58aec-120">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="58aec-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="58aec-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="58aec-121">Remarks</span></span>

<span data-ttu-id="58aec-122">De selectie voorwaarde moet ten minste één eigenschaps naam of een script opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="58aec-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="58aec-123">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="58aec-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="58aec-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="58aec-124">See Also</span></span>

[<span data-ttu-id="58aec-125">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="58aec-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="58aec-126">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="58aec-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
