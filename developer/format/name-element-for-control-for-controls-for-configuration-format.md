---
title: Naam van Element voor controle voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849670"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="d96b5-102">Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d96b5-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d96b5-103">Hiermee geeft u de naam van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="d96b5-103">Specifies the name of the control.</span></span> <span data-ttu-id="d96b5-104">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="d96b5-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d96b5-105">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) naamelement voor controle van besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="d96b5-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d96b5-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d96b5-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d96b5-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d96b5-107">Attributes and Elements</span></span>

<span data-ttu-id="d96b5-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `Name` element.</span><span class="sxs-lookup"><span data-stu-id="d96b5-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d96b5-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d96b5-109">Attributes</span></span>

<span data-ttu-id="d96b5-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="d96b5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d96b5-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d96b5-111">Child Elements</span></span>

<span data-ttu-id="d96b5-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="d96b5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d96b5-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d96b5-113">Parent Elements</span></span>

|<span data-ttu-id="d96b5-114">Element</span><span class="sxs-lookup"><span data-stu-id="d96b5-114">Element</span></span>|<span data-ttu-id="d96b5-115">Description</span><span class="sxs-lookup"><span data-stu-id="d96b5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d96b5-116">Controle-Element voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="d96b5-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="d96b5-117">Hiermee definieert u een algemene besturingselement dat kan worden gebruikt door alle weergaven van de opmaak bestands- en de naam die wordt gebruikt om te verwijzen naar het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="d96b5-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d96b5-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="d96b5-118">Text Value</span></span>

<span data-ttu-id="d96b5-119">Geef de naam die wordt gebruikt om te verwijzen naar dit besturingselement.</span><span class="sxs-lookup"><span data-stu-id="d96b5-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="d96b5-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d96b5-120">Remarks</span></span>

<span data-ttu-id="d96b5-121">Naam van de hier opgegeven kan in de volgende elementen worden gebruikt om te verwijzen naar dit besturingselement.</span><span class="sxs-lookup"><span data-stu-id="d96b5-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="d96b5-122">Bij het maken van een tabel, lijst, breed of aangepast besturingselement weergeven, kan het besturingselement door het volgende element worden opgegeven: [GroupBy-Element voor weergave (indeling)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="d96b5-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="d96b5-123">Bij het maken van een andere algemene besturingselement, kan dit besturingselement kan worden opgegeven met het volgende element: [ExpressionBinding-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="d96b5-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="d96b5-124">Bij het maken van een besturingselement dat kan worden gebruikt door een weergave, kan dit besturingselement kan worden opgegeven met het volgende element: [ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="d96b5-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="d96b5-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d96b5-125">See Also</span></span>

[<span data-ttu-id="d96b5-126">Controle-Element voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="d96b5-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="d96b5-127">ExpressionBinding-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="d96b5-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="d96b5-128">ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d96b5-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="d96b5-129">GroupBy-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d96b5-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="d96b5-130">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="d96b5-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
