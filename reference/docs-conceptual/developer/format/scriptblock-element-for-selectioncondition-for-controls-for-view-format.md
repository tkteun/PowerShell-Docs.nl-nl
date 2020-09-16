---
title: Script block-element voor SelectionCondition voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e5f4295a989307cb6ffb655c2c39596f3d1ea806
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785418"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="6c06c-102">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6c06c-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="6c06c-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="6c06c-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="6c06c-104">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6c06c-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="6c06c-105">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="6c06c-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="6c06c-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (indeling) Control element (Format) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings elementen voor het element Control (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor de weer gave (Format) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de weer gave (Format) SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor de weer gave (indeling) script block element voor SelectionCondition voor besturings elementen</span><span class="sxs-lookup"><span data-stu-id="6c06c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6c06c-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="6c06c-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6c06c-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="6c06c-108">Attributes and Elements</span></span>

<span data-ttu-id="6c06c-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="6c06c-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6c06c-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="6c06c-110">Attributes</span></span>

<span data-ttu-id="6c06c-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="6c06c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6c06c-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6c06c-112">Child Elements</span></span>

<span data-ttu-id="6c06c-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="6c06c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6c06c-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6c06c-114">Parent Elements</span></span>

|<span data-ttu-id="6c06c-115">Element</span><span class="sxs-lookup"><span data-stu-id="6c06c-115">Element</span></span>|<span data-ttu-id="6c06c-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6c06c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6c06c-117">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6c06c-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="6c06c-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="6c06c-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6c06c-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="6c06c-119">Text Value</span></span>

<span data-ttu-id="6c06c-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="6c06c-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="6c06c-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6c06c-121">Remarks</span></span>

<span data-ttu-id="6c06c-122">Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6c06c-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="6c06c-123">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6c06c-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6c06c-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6c06c-124">See Also</span></span>

[<span data-ttu-id="6c06c-125">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6c06c-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="6c06c-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="6c06c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
