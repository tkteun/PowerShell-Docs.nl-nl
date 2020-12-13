---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)
description: Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: 52b7170777a35596767c34f2d58106dfa6479567
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666481"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="83b17-103">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="83b17-103">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="83b17-104">Hiermee geeft u de naam van het besturings element op.</span><span class="sxs-lookup"><span data-stu-id="83b17-104">Specifies the name of the control.</span></span>

<span data-ttu-id="83b17-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (indeling) voor besturings elementen voor weer gave (Format) naam element voor besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="83b17-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="83b17-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="83b17-106">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="83b17-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="83b17-107">Attributes and Elements</span></span>

<span data-ttu-id="83b17-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Name` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="83b17-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="83b17-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="83b17-109">Attributes</span></span>

<span data-ttu-id="83b17-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="83b17-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="83b17-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="83b17-111">Child Elements</span></span>

<span data-ttu-id="83b17-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="83b17-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="83b17-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="83b17-113">Parent Elements</span></span>

|<span data-ttu-id="83b17-114">Element</span><span class="sxs-lookup"><span data-stu-id="83b17-114">Element</span></span>|<span data-ttu-id="83b17-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="83b17-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="83b17-116">Besturings element voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="83b17-116">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="83b17-117">Hiermee wordt een besturings element gedefinieerd dat kan worden gebruikt door de weer gave en de naam die wordt gebruikt om te verwijzen naar het besturings element.</span><span class="sxs-lookup"><span data-stu-id="83b17-117">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="83b17-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="83b17-118">Text Value</span></span>

<span data-ttu-id="83b17-119">Geef de naam op die wordt gebruikt om te verwijzen naar het besturings element.</span><span class="sxs-lookup"><span data-stu-id="83b17-119">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="83b17-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="83b17-120">Remarks</span></span>

<span data-ttu-id="83b17-121">De naam die u hier opgeeft, kan worden gebruikt in de volgende elementen om te verwijzen naar dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="83b17-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="83b17-122">Bij het maken van een tabel, lijst, brede of aangepaste beheer weergave kan het besturings element worden opgegeven door het volgende element: element [GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="83b17-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="83b17-123">Wanneer u een ander besturings element maakt dat door een weer gave kan worden gebruikt, kan dit besturings element worden opgegeven met het volgende element: [ExpressionBinding element voor CustomItem voor besturings elementen voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="83b17-123">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="83b17-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="83b17-124">See Also</span></span>

[<span data-ttu-id="83b17-125">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="83b17-125">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="83b17-126">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="83b17-126">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="83b17-127">Besturings element voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="83b17-127">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="83b17-128">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="83b17-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
