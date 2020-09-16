---
title: Script block-element voor ItemSelectionCondition voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7738b180f328c7360275058cdb9dea01df6ea285
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787645"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="334db-102">Het element ScriptBlock voor ItemSelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="334db-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="334db-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="334db-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="334db-104">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="334db-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="334db-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="334db-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="334db-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor GroupBy (Format) CustomEntry voor het element GroupBy (Format) CustomItem voor CustomEntry voor de ExpressionBinding-element van GroupBy (Format) voor CustomItem voor het element GroupBy (Format) ItemSelectionCondition voor ExpressionBinding voor het element GroupBy (Format) script Block voor ItemSelectionCondition voor GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="334db-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="334db-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="334db-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="334db-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="334db-108">Attributes and Elements</span></span>

<span data-ttu-id="334db-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="334db-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="334db-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="334db-110">Attributes</span></span>

<span data-ttu-id="334db-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="334db-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="334db-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="334db-112">Child Elements</span></span>

<span data-ttu-id="334db-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="334db-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="334db-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="334db-114">Parent Elements</span></span>

|<span data-ttu-id="334db-115">Element</span><span class="sxs-lookup"><span data-stu-id="334db-115">Element</span></span>|<span data-ttu-id="334db-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="334db-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="334db-117">Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="334db-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="334db-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="334db-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="334db-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="334db-119">Text Value</span></span>

<span data-ttu-id="334db-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="334db-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="334db-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="334db-121">Remarks</span></span>

<span data-ttu-id="334db-122">Als dit element wordt gebruikt, kunt u het kenmerk [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) niet opgeven bij het definiëren van de selectie voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="334db-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="334db-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="334db-123">See Also</span></span>

[<span data-ttu-id="334db-124">Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="334db-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="334db-125">Het element PropertyName voor ItemSelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="334db-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="334db-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="334db-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
