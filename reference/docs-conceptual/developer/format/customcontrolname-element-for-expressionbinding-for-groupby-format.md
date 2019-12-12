---
title: CustomControlName-element voor ExpressionBinding voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359040"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="29988-102">Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="29988-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="29988-103">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="29988-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="29988-104">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="29988-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="29988-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor het element GroupBy (Format) CustomItem voor CustomEntry voor het element GroupBy (Format) ExpressionBinding voor CustomItem voor het element GroupBy (Format) CustomControlName voor ExpressionBinding voor GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="29988-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="29988-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="29988-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="29988-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="29988-107">Attributes and Elements</span></span>

<span data-ttu-id="29988-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomControlName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="29988-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="29988-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="29988-109">Attributes</span></span>

<span data-ttu-id="29988-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="29988-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="29988-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="29988-111">Child Elements</span></span>

<span data-ttu-id="29988-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="29988-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="29988-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="29988-113">Parent Elements</span></span>

|<span data-ttu-id="29988-114">Element</span><span class="sxs-lookup"><span data-stu-id="29988-114">Element</span></span>|<span data-ttu-id="29988-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="29988-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="29988-116">ExpressionBinding-element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="29988-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="29988-117">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="29988-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="29988-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="29988-118">Text Value</span></span>

<span data-ttu-id="29988-119">Geef de naam van het besturings element op.</span><span class="sxs-lookup"><span data-stu-id="29988-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="29988-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="29988-120">Remarks</span></span>

<span data-ttu-id="29988-121">U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand, en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave.</span><span class="sxs-lookup"><span data-stu-id="29988-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="29988-122">De volgende elementen geven de namen van deze besturings elementen aan:</span><span class="sxs-lookup"><span data-stu-id="29988-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="29988-123">Element naam voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="29988-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="29988-124">Element naam voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="29988-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="29988-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="29988-125">See Also</span></span>

[<span data-ttu-id="29988-126">Element naam voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="29988-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="29988-127">Element naam voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="29988-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="29988-128">ExpressionBinding-element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="29988-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="29988-129">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="29988-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
