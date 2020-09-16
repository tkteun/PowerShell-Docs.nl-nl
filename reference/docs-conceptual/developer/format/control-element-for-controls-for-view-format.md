---
title: Besturings element voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 13ea2f09aec7fea8e5460197f133b5f5219cd369
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783803"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="027ac-102">Het element Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="027ac-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="027ac-103">Hiermee wordt een besturings element gedefinieerd dat kan worden gebruikt door de weer gave en de naam die wordt gebruikt om te verwijzen naar het besturings element.</span><span class="sxs-lookup"><span data-stu-id="027ac-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="027ac-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer gave elementen (indeling) Controls element (Format) Control element (indeling) voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="027ac-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="027ac-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="027ac-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="027ac-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="027ac-106">Attributes and Elements</span></span>

<span data-ttu-id="027ac-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Control` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="027ac-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="027ac-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="027ac-108">Attributes</span></span>

<span data-ttu-id="027ac-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="027ac-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="027ac-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="027ac-110">Child Elements</span></span>

|<span data-ttu-id="027ac-111">Element</span><span class="sxs-lookup"><span data-stu-id="027ac-111">Element</span></span>|<span data-ttu-id="027ac-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="027ac-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="027ac-113">Naam element voor besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="027ac-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="027ac-114">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="027ac-114">Required element.</span></span><br /><br /> <span data-ttu-id="027ac-115">Hiermee geeft u de naam van het besturings element op.</span><span class="sxs-lookup"><span data-stu-id="027ac-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="027ac-116">Het element CustomControl voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="027ac-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="027ac-117">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="027ac-117">Required element.</span></span><br /><br /> <span data-ttu-id="027ac-118">Hiermee wordt het besturings element gedefinieerd dat door deze weer gave wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="027ac-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="027ac-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="027ac-119">Parent Elements</span></span>

|<span data-ttu-id="027ac-120">Element</span><span class="sxs-lookup"><span data-stu-id="027ac-120">Element</span></span>|<span data-ttu-id="027ac-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="027ac-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="027ac-122">Controls-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="027ac-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="027ac-123">Hiermee worden de weergave besturings elementen gedefinieerd die kunnen worden gebruikt door een specifieke weer gave.</span><span class="sxs-lookup"><span data-stu-id="027ac-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="027ac-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="027ac-124">Remarks</span></span>

<span data-ttu-id="027ac-125">Dit besturings element kan worden opgegeven met de volgende elementen:</span><span class="sxs-lookup"><span data-stu-id="027ac-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="027ac-126">Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="027ac-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="027ac-127">Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="027ac-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="027ac-128">Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="027ac-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="027ac-129">Het element CustomControlName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="027ac-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="027ac-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="027ac-130">See Also</span></span>

[<span data-ttu-id="027ac-131">Het element CustomControl voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="027ac-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="027ac-132">Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="027ac-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="027ac-133">Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="027ac-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="027ac-134">Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="027ac-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="027ac-135">Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="027ac-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="027ac-136">Controls-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="027ac-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="027ac-137">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="027ac-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="027ac-138">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="027ac-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
