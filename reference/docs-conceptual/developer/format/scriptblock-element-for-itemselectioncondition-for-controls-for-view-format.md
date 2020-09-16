---
title: Script block-element voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 74b3e23005f595c4c550320849cac5b196e9d479
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787662"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="d70d5-102">Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d70d5-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="d70d5-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="d70d5-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="d70d5-104">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d70d5-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="d70d5-105">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="d70d5-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d70d5-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (indeling) Control element (Format) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries-element voor object voor weer gave (indeling) voor besturings elementen voor de weer gave (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (Format) ExpressionBinding-element voor CustomItem voor besturings elementen voor de weer gave (indeling) ItemSelectionCondition element van ExpressionBinding voor besturings elementen voor weer gave (indeling) script block element voor ItemSelectionCondition for Controls (indeling)</span><span class="sxs-lookup"><span data-stu-id="d70d5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d70d5-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d70d5-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d70d5-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d70d5-108">Attributes and Elements</span></span>

<span data-ttu-id="d70d5-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="d70d5-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d70d5-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d70d5-110">Attributes</span></span>

<span data-ttu-id="d70d5-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="d70d5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d70d5-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d70d5-112">Child Elements</span></span>

<span data-ttu-id="d70d5-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="d70d5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d70d5-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d70d5-114">Parent Elements</span></span>

|<span data-ttu-id="d70d5-115">Element</span><span class="sxs-lookup"><span data-stu-id="d70d5-115">Element</span></span>|<span data-ttu-id="d70d5-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d70d5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d70d5-117">ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d70d5-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="d70d5-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="d70d5-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d70d5-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="d70d5-119">Text Value</span></span>

<span data-ttu-id="d70d5-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="d70d5-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="d70d5-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d70d5-121">Remarks</span></span>

<span data-ttu-id="d70d5-122">Als dit element wordt gebruikt, kunt u het kenmerk [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) niet opgeven bij het definiëren van de selectie voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="d70d5-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="d70d5-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d70d5-123">See Also</span></span>

[<span data-ttu-id="d70d5-124">Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d70d5-124">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="d70d5-125">ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d70d5-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="d70d5-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d70d5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
