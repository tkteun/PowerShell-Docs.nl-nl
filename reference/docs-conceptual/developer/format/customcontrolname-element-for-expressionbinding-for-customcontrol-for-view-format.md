---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)
description: Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 24b27428c07d7178f0069f6d0e5b7ffc555efe34
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666804"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="3c0ca-103">Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3c0ca-103">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="3c0ca-104">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-104">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="3c0ca-105">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="3c0ca-106">Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl-element voor weer gave (Format) CustomEntries-element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (Format) ExpressionBinding element voor CustomItem (Format) voor expressie binding voor CustomControlName (indeling)</span><span class="sxs-lookup"><span data-stu-id="3c0ca-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3c0ca-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="3c0ca-107">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3c0ca-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="3c0ca-108">Attributes and Elements</span></span>

<span data-ttu-id="3c0ca-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomControlName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-109">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c0ca-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="3c0ca-110">Attributes</span></span>

<span data-ttu-id="3c0ca-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3c0ca-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3c0ca-112">Child Elements</span></span>

<span data-ttu-id="3c0ca-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3c0ca-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3c0ca-114">Parent Elements</span></span>

|<span data-ttu-id="3c0ca-115">Element</span><span class="sxs-lookup"><span data-stu-id="3c0ca-115">Element</span></span>|<span data-ttu-id="3c0ca-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3c0ca-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c0ca-117">ExpressionBinding-element voor CustomItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="3c0ca-117">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="3c0ca-118">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-118">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3c0ca-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="3c0ca-119">Text Value</span></span>

<span data-ttu-id="3c0ca-120">Geef de naam van het besturings element op.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-120">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="3c0ca-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3c0ca-121">Remarks</span></span>

<span data-ttu-id="3c0ca-122">U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-122">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="3c0ca-123">De namen van deze besturings elementen worden aangegeven door de volgende elementen.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-123">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="3c0ca-124">Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3c0ca-124">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="3c0ca-125">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3c0ca-125">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="3c0ca-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3c0ca-126">See Also</span></span>

[<span data-ttu-id="3c0ca-127">Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3c0ca-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="3c0ca-128">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3c0ca-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="3c0ca-129">ExpressionBinding-element voor CustomItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="3c0ca-129">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="3c0ca-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="3c0ca-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
