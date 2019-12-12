---
title: Element naam voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355991"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="a8c27-102">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a8c27-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="a8c27-103">Hiermee geeft u de naam van het besturings element op.</span><span class="sxs-lookup"><span data-stu-id="a8c27-103">Specifies the name of the control.</span></span>

<span data-ttu-id="a8c27-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (indeling) voor besturings elementen voor weer gave (Format) naam element voor besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="a8c27-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a8c27-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a8c27-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a8c27-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a8c27-106">Attributes and Elements</span></span>

<span data-ttu-id="a8c27-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `Name` beschreven.</span><span class="sxs-lookup"><span data-stu-id="a8c27-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a8c27-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a8c27-108">Attributes</span></span>

<span data-ttu-id="a8c27-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="a8c27-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a8c27-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a8c27-110">Child Elements</span></span>

<span data-ttu-id="a8c27-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="a8c27-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a8c27-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a8c27-112">Parent Elements</span></span>

|<span data-ttu-id="a8c27-113">Element</span><span class="sxs-lookup"><span data-stu-id="a8c27-113">Element</span></span>|<span data-ttu-id="a8c27-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a8c27-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a8c27-115">Besturings element voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="a8c27-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="a8c27-116">Hiermee wordt een besturings element gedefinieerd dat kan worden gebruikt door de weer gave en de naam die wordt gebruikt om te verwijzen naar het besturings element.</span><span class="sxs-lookup"><span data-stu-id="a8c27-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a8c27-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="a8c27-117">Text Value</span></span>

<span data-ttu-id="a8c27-118">Geef de naam op die wordt gebruikt om te verwijzen naar het besturings element.</span><span class="sxs-lookup"><span data-stu-id="a8c27-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="a8c27-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a8c27-119">Remarks</span></span>

<span data-ttu-id="a8c27-120">De naam die u hier opgeeft, kan worden gebruikt in de volgende elementen om te verwijzen naar dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="a8c27-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="a8c27-121">Bij het maken van een tabel, lijst, brede of aangepaste beheer weergave kan het besturings element worden opgegeven door het volgende element: element [GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="a8c27-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="a8c27-122">Wanneer u een ander besturings element maakt dat door een weer gave kan worden gebruikt, kan dit besturings element worden opgegeven met het volgende element: [ExpressionBinding element voor CustomItem voor besturings elementen voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="a8c27-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="a8c27-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a8c27-123">See Also</span></span>

[<span data-ttu-id="a8c27-124">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="a8c27-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="a8c27-125">ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="a8c27-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="a8c27-126">Besturings element voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="a8c27-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="a8c27-127">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="a8c27-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
