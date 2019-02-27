---
title: Naam van Element voor controle voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851280"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="262fa-102">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="262fa-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="262fa-103">Hiermee geeft u de naam van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="262fa-103">Specifies the name of the control.</span></span>

<span data-ttu-id="262fa-104">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) bepaalt Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) naamelement voor beheer op voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="262fa-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="262fa-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="262fa-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="262fa-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="262fa-106">Attributes and Elements</span></span>

<span data-ttu-id="262fa-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `Name` element.</span><span class="sxs-lookup"><span data-stu-id="262fa-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="262fa-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="262fa-108">Attributes</span></span>

<span data-ttu-id="262fa-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="262fa-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="262fa-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="262fa-110">Child Elements</span></span>

<span data-ttu-id="262fa-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="262fa-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="262fa-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="262fa-112">Parent Elements</span></span>

|<span data-ttu-id="262fa-113">Element</span><span class="sxs-lookup"><span data-stu-id="262fa-113">Element</span></span>|<span data-ttu-id="262fa-114">Description</span><span class="sxs-lookup"><span data-stu-id="262fa-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="262fa-115">Controle-Element voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="262fa-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="262fa-116">Hiermee definieert u een besturingselement dat kan worden gebruikt door de weergave en de naam die wordt gebruikt om te verwijzen naar het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="262fa-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="262fa-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="262fa-117">Text Value</span></span>

<span data-ttu-id="262fa-118">Geef de naam die wordt gebruikt om te verwijzen naar het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="262fa-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="262fa-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="262fa-119">Remarks</span></span>

<span data-ttu-id="262fa-120">Naam van de hier opgegeven kan in de volgende elementen worden gebruikt om te verwijzen naar dit besturingselement.</span><span class="sxs-lookup"><span data-stu-id="262fa-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="262fa-121">Bij het maken van een tabel, lijst, breed of aangepast besturingselement weergeven, kan het besturingselement door het volgende element worden opgegeven: [GroupBy-Element voor weergave (indeling)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="262fa-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="262fa-122">Bij het maken van een ander besturingselement dat kan worden gebruikt door een weergave, kan dit besturingselement kan worden opgegeven met het volgende element: [ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="262fa-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="262fa-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="262fa-123">See Also</span></span>

[<span data-ttu-id="262fa-124">GroupBy-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="262fa-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="262fa-125">ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="262fa-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="262fa-126">Controle-Element voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="262fa-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="262fa-127">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="262fa-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
