---
title: CustomControlName-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359051"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="1d249-102">Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1d249-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="1d249-103">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="1d249-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="1d249-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="1d249-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="1d249-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor View (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor de weer gave (Format) ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling) CustomControlName Element voor ExpressionBindine voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d249-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1d249-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1d249-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1d249-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1d249-107">Attributes and Elements</span></span>

<span data-ttu-id="1d249-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomControlName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="1d249-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1d249-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1d249-109">Attributes</span></span>

<span data-ttu-id="1d249-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="1d249-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1d249-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1d249-111">Child Elements</span></span>

<span data-ttu-id="1d249-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="1d249-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1d249-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1d249-113">Parent Elements</span></span>

|<span data-ttu-id="1d249-114">Element</span><span class="sxs-lookup"><span data-stu-id="1d249-114">Element</span></span>|<span data-ttu-id="1d249-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1d249-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1d249-116">ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d249-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="1d249-117">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1d249-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1d249-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="1d249-118">Text Value</span></span>

<span data-ttu-id="1d249-119">Geef de naam van het besturings element op.</span><span class="sxs-lookup"><span data-stu-id="1d249-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="1d249-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1d249-120">Remarks</span></span>

<span data-ttu-id="1d249-121">U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand, en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave.</span><span class="sxs-lookup"><span data-stu-id="1d249-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="1d249-122">De volgende elementen geven de namen van deze besturings elementen aan:</span><span class="sxs-lookup"><span data-stu-id="1d249-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="1d249-123">Element naam voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d249-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="1d249-124">Element naam voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d249-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="1d249-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1d249-125">See Also</span></span>

[<span data-ttu-id="1d249-126">Element naam voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d249-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="1d249-127">Element naam voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d249-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="1d249-128">ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d249-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="1d249-129">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="1d249-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
