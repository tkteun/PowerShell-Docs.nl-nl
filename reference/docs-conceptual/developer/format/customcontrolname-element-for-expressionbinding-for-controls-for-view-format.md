---
title: CustomControlName-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 871c6afd89db9360ea5012191b08863a9441f899
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786013"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="c30e7-102">Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c30e7-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="c30e7-103">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="c30e7-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="c30e7-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="c30e7-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c30e7-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (indeling) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings elementen voor het element Control Format) CustomEntry-element voor CustomEntries voor besturings elementen voor de weer gave (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor het ExpressionBinding-element van de CustomItem voor de Controls (Format) voor weer gave (Format) voor CustomControlName voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c30e7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c30e7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c30e7-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c30e7-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c30e7-107">Attributes and Elements</span></span>

<span data-ttu-id="c30e7-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomControlName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="c30e7-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c30e7-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c30e7-109">Attributes</span></span>

<span data-ttu-id="c30e7-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="c30e7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c30e7-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c30e7-111">Child Elements</span></span>

<span data-ttu-id="c30e7-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="c30e7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c30e7-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c30e7-113">Parent Elements</span></span>

|<span data-ttu-id="c30e7-114">Element</span><span class="sxs-lookup"><span data-stu-id="c30e7-114">Element</span></span>|<span data-ttu-id="c30e7-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c30e7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c30e7-116">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c30e7-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="c30e7-117">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c30e7-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c30e7-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="c30e7-118">Text Value</span></span>

<span data-ttu-id="c30e7-119">Geef de naam van het besturings element op.</span><span class="sxs-lookup"><span data-stu-id="c30e7-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="c30e7-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c30e7-120">Remarks</span></span>

<span data-ttu-id="c30e7-121">U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand, en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave.</span><span class="sxs-lookup"><span data-stu-id="c30e7-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="c30e7-122">De volgende elementen geven de namen van deze besturings elementen aan:</span><span class="sxs-lookup"><span data-stu-id="c30e7-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="c30e7-123">Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c30e7-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="c30e7-124">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c30e7-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="c30e7-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c30e7-125">See Also</span></span>

[<span data-ttu-id="c30e7-126">Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c30e7-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="c30e7-127">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c30e7-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="c30e7-128">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c30e7-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="c30e7-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c30e7-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
