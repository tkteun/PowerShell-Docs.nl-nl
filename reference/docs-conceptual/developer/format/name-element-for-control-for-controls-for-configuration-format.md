---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)
description: Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 0c1c83f827482886ca742f2c0174e8383f87fb52
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666498"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="2e362-103">Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2e362-103">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="2e362-104">Hiermee geeft u de naam van het besturings element op.</span><span class="sxs-lookup"><span data-stu-id="2e362-104">Specifies the name of the control.</span></span> <span data-ttu-id="2e362-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="2e362-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="2e362-106">Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor de configuratie (indeling) naam element voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="2e362-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2e362-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="2e362-107">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="2e362-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="2e362-108">Attributes and Elements</span></span>

<span data-ttu-id="2e362-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Name` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="2e362-109">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e362-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2e362-110">Attributes</span></span>

<span data-ttu-id="2e362-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="2e362-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e362-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2e362-112">Child Elements</span></span>

<span data-ttu-id="2e362-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="2e362-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2e362-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2e362-114">Parent Elements</span></span>

|<span data-ttu-id="2e362-115">Element</span><span class="sxs-lookup"><span data-stu-id="2e362-115">Element</span></span>|<span data-ttu-id="2e362-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2e362-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e362-117">Het element Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2e362-117">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="2e362-118">Hiermee wordt een algemeen besturings element gedefinieerd dat kan worden gebruikt door alle weer gaven van het opmaak bestand en de naam die wordt gebruikt om te verwijzen naar het besturings element.</span><span class="sxs-lookup"><span data-stu-id="2e362-118">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2e362-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="2e362-119">Text Value</span></span>

<span data-ttu-id="2e362-120">Geef de naam op die wordt gebruikt om naar dit besturings element te verwijzen.</span><span class="sxs-lookup"><span data-stu-id="2e362-120">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="2e362-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2e362-121">Remarks</span></span>

<span data-ttu-id="2e362-122">De naam die u hier opgeeft, kan worden gebruikt in de volgende elementen om te verwijzen naar dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="2e362-122">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="2e362-123">Bij het maken van een tabel, lijst, brede of aangepaste beheer weergave kan het besturings element worden opgegeven door het volgende element: element [GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="2e362-123">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="2e362-124">Wanneer u een ander algemeen besturings element maakt, kan dit besturings element worden opgegeven met het volgende element: [ExpressionBinding element voor CustomItem voor besturings elementen voor configuratie (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="2e362-124">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="2e362-125">Wanneer u een besturings element maakt dat kan worden gebruikt door een weer gave, kan dit besturings element worden opgegeven met het volgende element: [ExpressionBinding element voor CustomItem voor besturings elementen voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="2e362-125">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="2e362-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2e362-126">See Also</span></span>

[<span data-ttu-id="2e362-127">Het element Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2e362-127">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="2e362-128">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2e362-128">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="2e362-129">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2e362-129">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="2e362-130">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2e362-130">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="2e362-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="2e362-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
