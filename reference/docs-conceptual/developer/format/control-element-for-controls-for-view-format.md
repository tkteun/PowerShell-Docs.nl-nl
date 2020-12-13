---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Besturingselement voor Besturingselementen voor Weergave (opmaak)
description: Het element Besturingselement voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: c48b8b7ecaebfde5e6ed2123b837d92561551766
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668079"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="cd055-103">Het element Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd055-103">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="cd055-104">Hiermee wordt een besturings element gedefinieerd dat kan worden gebruikt door de weer gave en de naam die wordt gebruikt om te verwijzen naar het besturings element.</span><span class="sxs-lookup"><span data-stu-id="cd055-104">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="cd055-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer gave elementen (indeling) Controls element (Format) Control element (indeling) voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="cd055-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cd055-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="cd055-106">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cd055-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="cd055-107">Attributes and Elements</span></span>

<span data-ttu-id="cd055-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Control` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="cd055-108">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cd055-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="cd055-109">Attributes</span></span>

<span data-ttu-id="cd055-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="cd055-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cd055-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="cd055-111">Child Elements</span></span>

|<span data-ttu-id="cd055-112">Element</span><span class="sxs-lookup"><span data-stu-id="cd055-112">Element</span></span>|<span data-ttu-id="cd055-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cd055-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cd055-114">Naam element voor besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="cd055-114">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="cd055-115">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="cd055-115">Required element.</span></span><br /><br /> <span data-ttu-id="cd055-116">Hiermee geeft u de naam van het besturings element op.</span><span class="sxs-lookup"><span data-stu-id="cd055-116">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="cd055-117">Het element CustomControl voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd055-117">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="cd055-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="cd055-118">Required element.</span></span><br /><br /> <span data-ttu-id="cd055-119">Hiermee wordt het besturings element gedefinieerd dat door deze weer gave wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cd055-119">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cd055-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="cd055-120">Parent Elements</span></span>

|<span data-ttu-id="cd055-121">Element</span><span class="sxs-lookup"><span data-stu-id="cd055-121">Element</span></span>|<span data-ttu-id="cd055-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cd055-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cd055-123">Controls-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="cd055-123">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="cd055-124">Hiermee worden de weergave besturings elementen gedefinieerd die kunnen worden gebruikt door een specifieke weer gave.</span><span class="sxs-lookup"><span data-stu-id="cd055-124">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cd055-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="cd055-125">Remarks</span></span>

<span data-ttu-id="cd055-126">Dit besturings element kan worden opgegeven met de volgende elementen:</span><span class="sxs-lookup"><span data-stu-id="cd055-126">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="cd055-127">Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd055-127">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="cd055-128">Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd055-128">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="cd055-129">Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd055-129">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="cd055-130">Het element CustomControlName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd055-130">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="cd055-131">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cd055-131">See Also</span></span>

[<span data-ttu-id="cd055-132">Het element CustomControl voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd055-132">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="cd055-133">Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd055-133">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="cd055-134">Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd055-134">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cd055-135">Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd055-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="cd055-136">Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd055-136">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="cd055-137">Controls-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="cd055-137">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="cd055-138">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cd055-138">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="cd055-139">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="cd055-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
