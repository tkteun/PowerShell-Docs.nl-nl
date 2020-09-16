---
title: CustomControlName-element voor ExpressionBinding voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 06e612b25accf81467108ca48500943153efd575
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785996"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="4a2cb-102">Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4a2cb-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="4a2cb-103">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="4a2cb-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="4a2cb-104">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4a2cb-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="4a2cb-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) ExpressionBinding voor CustomItem voor GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4a2cb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4a2cb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4a2cb-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4a2cb-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="4a2cb-107">Attributes and Elements</span></span>

<span data-ttu-id="4a2cb-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomControlName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="4a2cb-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4a2cb-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="4a2cb-109">Attributes</span></span>

<span data-ttu-id="4a2cb-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="4a2cb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4a2cb-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4a2cb-111">Child Elements</span></span>

<span data-ttu-id="4a2cb-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="4a2cb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4a2cb-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4a2cb-113">Parent Elements</span></span>

|<span data-ttu-id="4a2cb-114">Element</span><span class="sxs-lookup"><span data-stu-id="4a2cb-114">Element</span></span>|<span data-ttu-id="4a2cb-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4a2cb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4a2cb-116">Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4a2cb-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="4a2cb-117">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4a2cb-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4a2cb-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="4a2cb-118">Text Value</span></span>

<span data-ttu-id="4a2cb-119">Geef de naam van het besturings element op.</span><span class="sxs-lookup"><span data-stu-id="4a2cb-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a2cb-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="4a2cb-120">Remarks</span></span>

<span data-ttu-id="4a2cb-121">U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand, en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave.</span><span class="sxs-lookup"><span data-stu-id="4a2cb-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="4a2cb-122">De volgende elementen geven de namen van deze besturings elementen aan:</span><span class="sxs-lookup"><span data-stu-id="4a2cb-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="4a2cb-123">Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4a2cb-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="4a2cb-124">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4a2cb-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="4a2cb-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4a2cb-125">See Also</span></span>

[<span data-ttu-id="4a2cb-126">Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4a2cb-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="4a2cb-127">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4a2cb-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="4a2cb-128">Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4a2cb-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="4a2cb-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="4a2cb-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
