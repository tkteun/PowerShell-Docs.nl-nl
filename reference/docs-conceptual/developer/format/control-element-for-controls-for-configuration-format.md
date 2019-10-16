---
title: Control-element voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359087"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="e0141-102">Het element Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e0141-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e0141-103">Hiermee wordt een algemeen besturings element gedefinieerd dat kan worden gebruikt door alle weer gaven van het opmaak bestand en de naam die wordt gebruikt om te verwijzen naar het besturings element.</span><span class="sxs-lookup"><span data-stu-id="e0141-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="e0141-104">Configuratie-element (Format) Controls element van configuratie-element (Format) voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0141-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e0141-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e0141-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0141-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e0141-106">Attributes and Elements</span></span>

<span data-ttu-id="e0141-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element voor het element `Control` beschreven.</span><span class="sxs-lookup"><span data-stu-id="e0141-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="e0141-108">U moet slechts één van beide onderliggende elementen opgeven.</span><span class="sxs-lookup"><span data-stu-id="e0141-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0141-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e0141-109">Attributes</span></span>

<span data-ttu-id="e0141-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="e0141-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e0141-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e0141-111">Child Elements</span></span>

|<span data-ttu-id="e0141-112">Element</span><span class="sxs-lookup"><span data-stu-id="e0141-112">Element</span></span>|<span data-ttu-id="e0141-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e0141-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0141-114">CustomControl-element voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0141-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="e0141-115">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="e0141-115">Required element.</span></span><br /><br /> <span data-ttu-id="e0141-116">Hiermee wordt het besturings element gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="e0141-116">Defines the control.</span></span>|
|[<span data-ttu-id="e0141-117">Naam element voor besturings element voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0141-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="e0141-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="e0141-118">Required element.</span></span><br /><br /> <span data-ttu-id="e0141-119">Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar het besturings element.</span><span class="sxs-lookup"><span data-stu-id="e0141-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e0141-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e0141-120">Parent Elements</span></span>

|<span data-ttu-id="e0141-121">Element</span><span class="sxs-lookup"><span data-stu-id="e0141-121">Element</span></span>|<span data-ttu-id="e0141-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e0141-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0141-123">Beheert element van configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0141-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="e0141-124">Hiermee definieert u de algemene besturings elementen die kunnen worden gebruikt door alle weer gaven van het opmaak bestand of door andere besturings elementen.</span><span class="sxs-lookup"><span data-stu-id="e0141-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e0141-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e0141-125">Remarks</span></span>

<span data-ttu-id="e0141-126">In de volgende elementen kan worden verwezen naar de naam die aan dit besturings element wordt gegeven:</span><span class="sxs-lookup"><span data-stu-id="e0141-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="e0141-127">ExpressionBinding-element voor CustomItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0141-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="e0141-128">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0141-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="e0141-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e0141-129">See Also</span></span>

[<span data-ttu-id="e0141-130">Beheert element van configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0141-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="e0141-131">CustomControl-element voor besturings element voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0141-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="e0141-132">ExpressionBinding-element voor CustomItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0141-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="e0141-133">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0141-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="e0141-134">Element naam voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="e0141-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="e0141-135">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e0141-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
