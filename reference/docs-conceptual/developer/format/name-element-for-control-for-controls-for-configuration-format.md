---
title: Naam element voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354318"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="87063-102">Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="87063-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="87063-103">Hiermee geeft u de naam van het besturings element op.</span><span class="sxs-lookup"><span data-stu-id="87063-103">Specifies the name of the control.</span></span> <span data-ttu-id="87063-104">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="87063-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="87063-105">Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor de configuratie (indeling) naam element voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="87063-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="87063-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="87063-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="87063-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="87063-107">Attributes and Elements</span></span>

<span data-ttu-id="87063-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `Name` beschreven.</span><span class="sxs-lookup"><span data-stu-id="87063-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="87063-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="87063-109">Attributes</span></span>

<span data-ttu-id="87063-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="87063-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="87063-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="87063-111">Child Elements</span></span>

<span data-ttu-id="87063-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="87063-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="87063-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="87063-113">Parent Elements</span></span>

|<span data-ttu-id="87063-114">Element</span><span class="sxs-lookup"><span data-stu-id="87063-114">Element</span></span>|<span data-ttu-id="87063-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="87063-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87063-116">Control-element voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="87063-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="87063-117">Hiermee wordt een algemeen besturings element gedefinieerd dat kan worden gebruikt door alle weer gaven van het opmaak bestand en de naam die wordt gebruikt om te verwijzen naar het besturings element.</span><span class="sxs-lookup"><span data-stu-id="87063-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="87063-118">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="87063-118">Text Value</span></span>

<span data-ttu-id="87063-119">Geef de naam op die wordt gebruikt om naar dit besturings element te verwijzen.</span><span class="sxs-lookup"><span data-stu-id="87063-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="87063-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="87063-120">Remarks</span></span>

<span data-ttu-id="87063-121">De naam die u hier opgeeft, kan worden gebruikt in de volgende elementen om te verwijzen naar dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="87063-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="87063-122">Bij het maken van een tabel, lijst, brede of aangepaste beheer weergave kan het besturings element worden opgegeven door het volgende element: element [GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="87063-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="87063-123">Wanneer u een ander algemeen besturings element maakt, kan dit besturings element worden opgegeven met het volgende element: [ExpressionBinding element voor CustomItem voor besturings elementen voor configuratie (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="87063-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="87063-124">Wanneer u een besturings element maakt dat kan worden gebruikt door een weer gave, kan dit besturings element worden opgegeven met het volgende element: [ExpressionBinding element voor CustomItem voor besturings elementen voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="87063-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="87063-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="87063-125">See Also</span></span>

[<span data-ttu-id="87063-126">Control-element voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="87063-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="87063-127">ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="87063-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="87063-128">ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="87063-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="87063-129">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="87063-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="87063-130">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="87063-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
