---
title: CustomControlName-element voor ExpressionBinding voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6f1ffca045b7efcecb4dce4e788a8c508fa6ef08
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783752"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="f225e-102">Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f225e-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="f225e-103">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="f225e-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="f225e-104">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="f225e-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="f225e-105">Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl-element voor weer gave (Format) CustomEntries-element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (Format) ExpressionBinding element voor CustomItem (Format) voor expressie binding voor CustomControlName (indeling)</span><span class="sxs-lookup"><span data-stu-id="f225e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f225e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f225e-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f225e-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f225e-107">Attributes and Elements</span></span>

<span data-ttu-id="f225e-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomControlName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="f225e-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f225e-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f225e-109">Attributes</span></span>

<span data-ttu-id="f225e-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="f225e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f225e-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f225e-111">Child Elements</span></span>

<span data-ttu-id="f225e-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="f225e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f225e-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f225e-113">Parent Elements</span></span>

|<span data-ttu-id="f225e-114">Element</span><span class="sxs-lookup"><span data-stu-id="f225e-114">Element</span></span>|<span data-ttu-id="f225e-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f225e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f225e-116">ExpressionBinding-element voor CustomItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="f225e-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="f225e-117">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f225e-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f225e-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="f225e-118">Text Value</span></span>

<span data-ttu-id="f225e-119">Geef de naam van het besturings element op.</span><span class="sxs-lookup"><span data-stu-id="f225e-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="f225e-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f225e-120">Remarks</span></span>

<span data-ttu-id="f225e-121">U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave.</span><span class="sxs-lookup"><span data-stu-id="f225e-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="f225e-122">De namen van deze besturings elementen worden aangegeven door de volgende elementen.</span><span class="sxs-lookup"><span data-stu-id="f225e-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="f225e-123">Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f225e-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="f225e-124">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f225e-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="f225e-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f225e-125">See Also</span></span>

[<span data-ttu-id="f225e-126">Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f225e-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="f225e-127">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f225e-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="f225e-128">ExpressionBinding-element voor CustomItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="f225e-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="f225e-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="f225e-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
