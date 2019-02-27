---
title: Element beheren voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845218"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="e54de-102">Het element Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e54de-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="e54de-103">Hiermee definieert u een besturingselement dat kan worden gebruikt door de weergave en de naam die wordt gebruikt om te verwijzen naar het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="e54de-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="e54de-104">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) bepaalt Element (indeling) controle-Element voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e54de-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e54de-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e54de-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e54de-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e54de-106">Attributes and Elements</span></span>

<span data-ttu-id="e54de-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `Control` element.</span><span class="sxs-lookup"><span data-stu-id="e54de-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e54de-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e54de-108">Attributes</span></span>

<span data-ttu-id="e54de-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="e54de-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e54de-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e54de-110">Child Elements</span></span>

|<span data-ttu-id="e54de-111">Element</span><span class="sxs-lookup"><span data-stu-id="e54de-111">Element</span></span>|<span data-ttu-id="e54de-112">Description</span><span class="sxs-lookup"><span data-stu-id="e54de-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e54de-113">Naamelement voor controle voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e54de-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="e54de-114">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="e54de-114">Required element.</span></span><br /><br /> <span data-ttu-id="e54de-115">Hiermee geeft u de naam van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="e54de-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="e54de-116">CustomControl-Element voor het besturingselement voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e54de-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="e54de-117">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="e54de-117">Required element.</span></span><br /><br /> <span data-ttu-id="e54de-118">Hiermee definieert u het besturingselement wordt gebruikt door deze weergave.</span><span class="sxs-lookup"><span data-stu-id="e54de-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e54de-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e54de-119">Parent Elements</span></span>

|<span data-ttu-id="e54de-120">Element</span><span class="sxs-lookup"><span data-stu-id="e54de-120">Element</span></span>|<span data-ttu-id="e54de-121">Description</span><span class="sxs-lookup"><span data-stu-id="e54de-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e54de-122">Besturingselementen Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e54de-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="e54de-123">Hiermee definieert u de weergave-besturingselementen die kunnen worden gebruikt door een specifieke weergave.</span><span class="sxs-lookup"><span data-stu-id="e54de-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e54de-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e54de-124">Remarks</span></span>

<span data-ttu-id="e54de-125">Dit besturingselement kan worden opgegeven met de volgende elementen:</span><span class="sxs-lookup"><span data-stu-id="e54de-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="e54de-126">CustomControlName-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e54de-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="e54de-127">CustomControlName-Element voor ExpressionBinding voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e54de-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="e54de-128">CustomControlName-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e54de-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="e54de-129">CustomControlName-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e54de-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="e54de-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e54de-130">See Also</span></span>

[<span data-ttu-id="e54de-131">CustomControl-Element voor het besturingselement voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e54de-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="e54de-132">CustomControlName-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e54de-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="e54de-133">CustomControlName-Element voor ExpressionBinding voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e54de-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e54de-134">CustomControlName-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e54de-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="e54de-135">CustomControlName-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e54de-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="e54de-136">Besturingselementen Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e54de-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="e54de-137">Naamelement voor controle van besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e54de-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="e54de-138">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="e54de-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
