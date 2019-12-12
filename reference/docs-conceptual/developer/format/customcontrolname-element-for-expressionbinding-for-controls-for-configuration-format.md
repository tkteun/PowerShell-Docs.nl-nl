---
title: CustomControlName-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5242935-2782-4d23-84f5-2446b2b7ba83
caps.latest.revision: 8
ms.openlocfilehash: c9abd9f22907b87323c16d603a9f75bb3d375a03
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355305"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="1ef3e-102">Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1ef3e-102">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="1ef3e-103">Hiermee geeft u de naam van een gemeen schappelijk besturings element op.</span><span class="sxs-lookup"><span data-stu-id="1ef3e-103">Specifies the name of a common control.</span></span> <span data-ttu-id="1ef3e-104">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="1ef3e-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="1ef3e-105">Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het configureren van een configuratie ( Format) CustomEntry element voor CustomControl voor besturings elementen voor de configuratie (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor configuratie-ExpressionBinding element voor CustomItem voor besturings elementen voor configuratie (indeling) CustomControlName Element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1ef3e-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1ef3e-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1ef3e-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1ef3e-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1ef3e-107">Attributes and Elements</span></span>

<span data-ttu-id="1ef3e-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomControlName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="1ef3e-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1ef3e-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1ef3e-109">Attributes</span></span>

<span data-ttu-id="1ef3e-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="1ef3e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1ef3e-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1ef3e-111">Child Elements</span></span>

<span data-ttu-id="1ef3e-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="1ef3e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1ef3e-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1ef3e-113">Parent Elements</span></span>

|<span data-ttu-id="1ef3e-114">Element</span><span class="sxs-lookup"><span data-stu-id="1ef3e-114">Element</span></span>|<span data-ttu-id="1ef3e-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1ef3e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1ef3e-116">ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1ef3e-116">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="1ef3e-117">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1ef3e-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1ef3e-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="1ef3e-118">Text Value</span></span>

<span data-ttu-id="1ef3e-119">Geef de naam van het besturings element op.</span><span class="sxs-lookup"><span data-stu-id="1ef3e-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ef3e-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1ef3e-120">Remarks</span></span>

<span data-ttu-id="1ef3e-121">U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand, en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave.</span><span class="sxs-lookup"><span data-stu-id="1ef3e-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="1ef3e-122">De volgende elementen geven de namen van deze besturings elementen aan:</span><span class="sxs-lookup"><span data-stu-id="1ef3e-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="1ef3e-123">Element naam voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1ef3e-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="1ef3e-124">Element naam voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="1ef3e-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="1ef3e-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1ef3e-125">See Also</span></span>

[<span data-ttu-id="1ef3e-126">Element naam voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1ef3e-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="1ef3e-127">Element naam voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="1ef3e-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="1ef3e-128">ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1ef3e-128">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="1ef3e-129">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="1ef3e-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
