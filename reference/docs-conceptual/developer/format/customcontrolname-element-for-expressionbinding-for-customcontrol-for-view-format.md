---
title: CustomControlName-element voor ExpressionBinding voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355298"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="b7af5-102">Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b7af5-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="b7af5-103">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="b7af5-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="b7af5-104">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="b7af5-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="b7af5-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element voor weer gave (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (indeling) CustomItem Element voor CustomEntry voor View (Format) ExpressionBinding element voor CustomItem (Format) CustomControlName element voor expressie binding voor CustomItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7af5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b7af5-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b7af5-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b7af5-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b7af5-107">Attributes and Elements</span></span>

<span data-ttu-id="b7af5-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomControlName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="b7af5-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b7af5-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b7af5-109">Attributes</span></span>

<span data-ttu-id="b7af5-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="b7af5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b7af5-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b7af5-111">Child Elements</span></span>

<span data-ttu-id="b7af5-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="b7af5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b7af5-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b7af5-113">Parent Elements</span></span>

|<span data-ttu-id="b7af5-114">Element</span><span class="sxs-lookup"><span data-stu-id="b7af5-114">Element</span></span>|<span data-ttu-id="b7af5-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b7af5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7af5-116">ExpressionBinding-element voor CustomItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7af5-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="b7af5-117">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b7af5-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b7af5-118">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="b7af5-118">Text Value</span></span>

<span data-ttu-id="b7af5-119">Geef de naam van het besturings element op.</span><span class="sxs-lookup"><span data-stu-id="b7af5-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7af5-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b7af5-120">Remarks</span></span>

<span data-ttu-id="b7af5-121">U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave.</span><span class="sxs-lookup"><span data-stu-id="b7af5-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="b7af5-122">De namen van deze besturings elementen worden aangegeven door de volgende elementen.</span><span class="sxs-lookup"><span data-stu-id="b7af5-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="b7af5-123">Element naam voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7af5-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="b7af5-124">Element naam voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7af5-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="b7af5-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b7af5-125">See Also</span></span>

[<span data-ttu-id="b7af5-126">Element naam voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7af5-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="b7af5-127">Element naam voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7af5-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="b7af5-128">ExpressionBinding-element voor CustomItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7af5-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="b7af5-129">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b7af5-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
