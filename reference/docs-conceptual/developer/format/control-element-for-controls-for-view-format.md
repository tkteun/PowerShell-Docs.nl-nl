---
title: Besturings element voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354850"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="fd9ff-102">Het element Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="fd9ff-103">Hiermee wordt een besturings element gedefinieerd dat kan worden gebruikt door de weer gave en de naam die wordt gebruikt om te verwijzen naar het besturings element.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="fd9ff-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer gave elementen (indeling) Controls element (Format) Control element (indeling) voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fd9ff-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="fd9ff-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fd9ff-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="fd9ff-106">Attributes and Elements</span></span>

<span data-ttu-id="fd9ff-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Control` beschreven.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fd9ff-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="fd9ff-108">Attributes</span></span>

<span data-ttu-id="fd9ff-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fd9ff-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fd9ff-110">Child Elements</span></span>

|<span data-ttu-id="fd9ff-111">Element</span><span class="sxs-lookup"><span data-stu-id="fd9ff-111">Element</span></span>|<span data-ttu-id="fd9ff-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fd9ff-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fd9ff-113">Naam element voor besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="fd9ff-114">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-114">Required element.</span></span><br /><br /> <span data-ttu-id="fd9ff-115">Hiermee geeft u de naam van het besturings element op.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="fd9ff-116">CustomControl-element voor besturings elementen voor de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="fd9ff-117">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-117">Required element.</span></span><br /><br /> <span data-ttu-id="fd9ff-118">Hiermee wordt het besturings element gedefinieerd dat door deze weer gave wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fd9ff-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fd9ff-119">Parent Elements</span></span>

|<span data-ttu-id="fd9ff-120">Element</span><span class="sxs-lookup"><span data-stu-id="fd9ff-120">Element</span></span>|<span data-ttu-id="fd9ff-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fd9ff-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fd9ff-122">Controls-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="fd9ff-123">Hiermee worden de weergave besturings elementen gedefinieerd die kunnen worden gebruikt door een specifieke weer gave.</span><span class="sxs-lookup"><span data-stu-id="fd9ff-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fd9ff-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="fd9ff-124">Remarks</span></span>

<span data-ttu-id="fd9ff-125">Dit besturings element kan worden opgegeven met de volgende elementen:</span><span class="sxs-lookup"><span data-stu-id="fd9ff-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="fd9ff-126">CustomControlName-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="fd9ff-127">CustomControlName-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="fd9ff-128">CustomControlName-element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="fd9ff-129">CustomControlName-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="fd9ff-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fd9ff-130">See Also</span></span>

[<span data-ttu-id="fd9ff-131">CustomControl-element voor besturings elementen voor de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="fd9ff-132">CustomControlName-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="fd9ff-133">CustomControlName-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="fd9ff-134">CustomControlName-element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="fd9ff-135">CustomControlName-element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="fd9ff-136">Controls-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="fd9ff-137">Element naam voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fd9ff-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="fd9ff-138">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="fd9ff-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
