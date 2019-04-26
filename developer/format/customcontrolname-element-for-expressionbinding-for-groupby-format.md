---
title: CustomControlName-Element voor ExpressionBinding voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066563"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="10083-102">Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="10083-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="10083-103">Hiermee geeft u de naam van een algemene besturingselement of een besturingselement voor lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="10083-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="10083-104">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="10083-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="10083-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) CustomItem Element voor CustomEntry voor GroupBy (indeling) ExpressionBinding Element voor CustomItem voor GroupBy (indeling) CustomControlName Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="10083-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="10083-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="10083-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="10083-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="10083-107">Attributes and Elements</span></span>

<span data-ttu-id="10083-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomControlName` element.</span><span class="sxs-lookup"><span data-stu-id="10083-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="10083-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="10083-109">Attributes</span></span>

<span data-ttu-id="10083-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="10083-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="10083-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="10083-111">Child Elements</span></span>

<span data-ttu-id="10083-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="10083-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="10083-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="10083-113">Parent Elements</span></span>

|<span data-ttu-id="10083-114">Element</span><span class="sxs-lookup"><span data-stu-id="10083-114">Element</span></span>|<span data-ttu-id="10083-115">Description</span><span class="sxs-lookup"><span data-stu-id="10083-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="10083-116">ExpressionBinding-Element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="10083-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="10083-117">Definieert de gegevens die door het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="10083-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="10083-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="10083-118">Text Value</span></span>

<span data-ttu-id="10083-119">Geef de naam van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="10083-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="10083-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="10083-120">Remarks</span></span>

<span data-ttu-id="10083-121">Kunt u algemene besturingselementen die kunnen worden gebruikt door alle weergaven van een opmaak bestand maken en u kunt besturingselementen weergeven die kunnen worden gebruikt door een specifieke weergave maken.</span><span class="sxs-lookup"><span data-stu-id="10083-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="10083-122">De volgende elementen geeft de namen van deze besturingselementen:</span><span class="sxs-lookup"><span data-stu-id="10083-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="10083-123">Naamelement voor controle van besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="10083-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="10083-124">Naamelement voor controle van besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="10083-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="10083-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="10083-125">See Also</span></span>

[<span data-ttu-id="10083-126">Naamelement voor controle van besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="10083-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="10083-127">Naamelement voor controle van besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="10083-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="10083-128">ExpressionBinding-Element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="10083-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="10083-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="10083-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
