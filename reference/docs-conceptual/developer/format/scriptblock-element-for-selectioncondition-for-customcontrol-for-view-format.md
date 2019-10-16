---
title: Script block-element voor SelectionCondition voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358946"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="37f56-102">Het element ScriptBlock voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="37f56-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="37f56-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="37f56-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="37f56-104">Wanneer dit script wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="37f56-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="37f56-105">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="37f56-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="37f56-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element voor weer gave (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor CustomControl voor weer gave ( Format) CustomItem-element voor CustomEntry voor CustomControl voor weer gave (Format) SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (Format) script block element voor SelectionCondition voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="37f56-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="37f56-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="37f56-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="37f56-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="37f56-108">Attributes and Elements</span></span>

<span data-ttu-id="37f56-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ScriptBlock` beschreven.</span><span class="sxs-lookup"><span data-stu-id="37f56-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="37f56-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="37f56-110">Attributes</span></span>

<span data-ttu-id="37f56-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="37f56-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="37f56-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="37f56-112">Child Elements</span></span>

<span data-ttu-id="37f56-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="37f56-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="37f56-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="37f56-114">Parent Elements</span></span>

|<span data-ttu-id="37f56-115">Element</span><span class="sxs-lookup"><span data-stu-id="37f56-115">Element</span></span>|<span data-ttu-id="37f56-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="37f56-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37f56-117">SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="37f56-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="37f56-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="37f56-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="37f56-119">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="37f56-119">Text Value</span></span>

<span data-ttu-id="37f56-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="37f56-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="37f56-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="37f56-121">Remarks</span></span>

<span data-ttu-id="37f56-122">Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="37f56-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="37f56-123">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="37f56-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="37f56-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="37f56-124">See Also</span></span>

[<span data-ttu-id="37f56-125">SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="37f56-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="37f56-126">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="37f56-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
