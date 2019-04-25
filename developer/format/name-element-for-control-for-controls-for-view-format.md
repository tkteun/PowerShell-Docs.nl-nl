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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065090"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="06b33-102">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="06b33-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="06b33-103">Hiermee geeft u de naam van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="06b33-103">Specifies the name of the control.</span></span>

<span data-ttu-id="06b33-104">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) bepaalt Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) naamelement voor beheer op voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06b33-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="06b33-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="06b33-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="06b33-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="06b33-106">Attributes and Elements</span></span>

<span data-ttu-id="06b33-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `Name` element.</span><span class="sxs-lookup"><span data-stu-id="06b33-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="06b33-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="06b33-108">Attributes</span></span>

<span data-ttu-id="06b33-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="06b33-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="06b33-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="06b33-110">Child Elements</span></span>

<span data-ttu-id="06b33-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="06b33-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="06b33-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="06b33-112">Parent Elements</span></span>

|<span data-ttu-id="06b33-113">Element</span><span class="sxs-lookup"><span data-stu-id="06b33-113">Element</span></span>|<span data-ttu-id="06b33-114">Description</span><span class="sxs-lookup"><span data-stu-id="06b33-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06b33-115">Controle-Element voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06b33-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="06b33-116">Hiermee definieert u een besturingselement dat kan worden gebruikt door de weergave en de naam die wordt gebruikt om te verwijzen naar het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="06b33-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="06b33-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="06b33-117">Text Value</span></span>

<span data-ttu-id="06b33-118">Geef de naam die wordt gebruikt om te verwijzen naar het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="06b33-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="06b33-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="06b33-119">Remarks</span></span>

<span data-ttu-id="06b33-120">Naam van de hier opgegeven kan in de volgende elementen worden gebruikt om te verwijzen naar dit besturingselement.</span><span class="sxs-lookup"><span data-stu-id="06b33-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="06b33-121">Bij het maken van een tabel, lijst, breed of aangepast besturingselement weergeven, kan het besturingselement door het volgende element worden opgegeven: [GroupBy-Element voor weergave (indeling)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="06b33-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="06b33-122">Bij het maken van een ander besturingselement dat kan worden gebruikt door een weergave, kan dit besturingselement kan worden opgegeven met het volgende element: [ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="06b33-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="06b33-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="06b33-123">See Also</span></span>

[<span data-ttu-id="06b33-124">GroupBy-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06b33-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="06b33-125">ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06b33-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="06b33-126">Controle-Element voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06b33-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="06b33-127">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="06b33-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
