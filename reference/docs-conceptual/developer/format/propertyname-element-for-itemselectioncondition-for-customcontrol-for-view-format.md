---
title: Het element PropertyName voor ItemSelectionCondition voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0131fa86be4be4daec1d9d24b50397fb8529f050
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785571"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="b8d80-102">Het element PropertyName voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b8d80-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="b8d80-103">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b8d80-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b8d80-104">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b8d80-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="b8d80-105">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="b8d80-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="b8d80-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (Format) ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (Format) ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling) eigenschaps element voor ItemSelectionCondition voor CustomControl voor weer gave (Format</span><span class="sxs-lookup"><span data-stu-id="b8d80-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="b8d80-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="b8d80-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b8d80-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b8d80-108">Attributes and Elements</span></span>

<span data-ttu-id="b8d80-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="b8d80-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b8d80-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b8d80-110">Attributes</span></span>

<span data-ttu-id="b8d80-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="b8d80-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b8d80-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b8d80-112">Child Elements</span></span>

<span data-ttu-id="b8d80-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="b8d80-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b8d80-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b8d80-114">Parent Elements</span></span>

|<span data-ttu-id="b8d80-115">Element</span><span class="sxs-lookup"><span data-stu-id="b8d80-115">Element</span></span>|<span data-ttu-id="b8d80-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b8d80-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8d80-117">ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="b8d80-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="b8d80-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="b8d80-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b8d80-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="b8d80-119">Text Value</span></span>

<span data-ttu-id="b8d80-120">Geef de naam op van de .NET-eigenschap waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b8d80-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8d80-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b8d80-121">Remarks</span></span>

<span data-ttu-id="b8d80-122">Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.</span><span class="sxs-lookup"><span data-stu-id="b8d80-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8d80-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b8d80-123">See Also</span></span>

[<span data-ttu-id="b8d80-124">Het element ScriptBlock voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b8d80-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b8d80-125">ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="b8d80-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="b8d80-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b8d80-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
