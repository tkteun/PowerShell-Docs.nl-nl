---
title: Script block-element voor SelectionCondition voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355781"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="8447b-102">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8447b-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="8447b-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="8447b-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="8447b-104">Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8447b-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="8447b-105">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="8447b-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="8447b-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor besturings elementen voor weer gave (indeling) CustomEntry element voor CustomEntries voor besturings elementen voor de weer gave (Format) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de weer gave (Format) SelectionCondition-element voor EntrySelectedBy for Controls ( Format) script block-element voor SelectionCondition voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="8447b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8447b-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="8447b-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8447b-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="8447b-108">Attributes and Elements</span></span>

<span data-ttu-id="8447b-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ScriptBlock` beschreven.</span><span class="sxs-lookup"><span data-stu-id="8447b-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8447b-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="8447b-110">Attributes</span></span>

<span data-ttu-id="8447b-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="8447b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8447b-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8447b-112">Child Elements</span></span>

<span data-ttu-id="8447b-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="8447b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8447b-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8447b-114">Parent Elements</span></span>

|<span data-ttu-id="8447b-115">Element</span><span class="sxs-lookup"><span data-stu-id="8447b-115">Element</span></span>|<span data-ttu-id="8447b-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8447b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8447b-117">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="8447b-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="8447b-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="8447b-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8447b-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="8447b-119">Text Value</span></span>

<span data-ttu-id="8447b-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="8447b-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="8447b-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="8447b-121">Remarks</span></span>

<span data-ttu-id="8447b-122">Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="8447b-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="8447b-123">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8447b-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8447b-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8447b-124">See Also</span></span>

[<span data-ttu-id="8447b-125">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="8447b-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="8447b-126">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="8447b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
