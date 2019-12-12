---
title: Script block-element voor ItemSelectionCondition voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355802"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="99f96-102">Het element ScriptBlock voor ItemSelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="99f96-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="99f96-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="99f96-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="99f96-104">Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="99f96-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="99f96-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="99f96-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="99f96-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor het element GroupBy (Format) CustomItem voor CustomEntry voor het element GroupBy (Format) ExpressionBinding voor CustomItem voor het element GroupBy (Format) ItemSelectionCondition voor ExpressionBinding voor het element GroupBy (Format) script Block voor ItemSelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="99f96-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="99f96-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="99f96-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="99f96-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="99f96-108">Attributes and Elements</span></span>

<span data-ttu-id="99f96-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ScriptBlock` beschreven.</span><span class="sxs-lookup"><span data-stu-id="99f96-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="99f96-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="99f96-110">Attributes</span></span>

<span data-ttu-id="99f96-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="99f96-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="99f96-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="99f96-112">Child Elements</span></span>

<span data-ttu-id="99f96-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="99f96-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="99f96-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="99f96-114">Parent Elements</span></span>

|<span data-ttu-id="99f96-115">Element</span><span class="sxs-lookup"><span data-stu-id="99f96-115">Element</span></span>|<span data-ttu-id="99f96-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="99f96-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="99f96-117">ItemSelectionCondition-element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="99f96-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="99f96-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="99f96-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="99f96-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="99f96-119">Text Value</span></span>

<span data-ttu-id="99f96-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="99f96-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="99f96-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="99f96-121">Remarks</span></span>

<span data-ttu-id="99f96-122">Als dit element wordt gebruikt, kunt u het kenmerk [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) niet opgeven bij het definiëren van de selectie voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="99f96-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="99f96-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="99f96-123">See Also</span></span>

[<span data-ttu-id="99f96-124">ItemSelectionCondition-element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="99f96-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="99f96-125">Het element PropertyName voor ItemSelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="99f96-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="99f96-126">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="99f96-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
