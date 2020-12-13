---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Besturingselement voor Besturingselementen voor Configuratie (opmaak)
description: Het element Besturingselement voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 43424de025cb89d81533e973abd7c39c09533747
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655664"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="7c26a-103">Het element Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7c26a-103">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="7c26a-104">Hiermee wordt een algemeen besturings element gedefinieerd dat kan worden gebruikt door alle weer gaven van het opmaak bestand en de naam die wordt gebruikt om te verwijzen naar het besturings element.</span><span class="sxs-lookup"><span data-stu-id="7c26a-104">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="7c26a-105">Configuratie-element (Format) Controls element van configuratie-element (Format) voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="7c26a-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7c26a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7c26a-106">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7c26a-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7c26a-107">Attributes and Elements</span></span>

<span data-ttu-id="7c26a-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Control` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="7c26a-108">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="7c26a-109">U moet slechts één van beide onderliggende elementen opgeven.</span><span class="sxs-lookup"><span data-stu-id="7c26a-109">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7c26a-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7c26a-110">Attributes</span></span>

<span data-ttu-id="7c26a-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="7c26a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7c26a-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7c26a-112">Child Elements</span></span>

|<span data-ttu-id="7c26a-113">Element</span><span class="sxs-lookup"><span data-stu-id="7c26a-113">Element</span></span>|<span data-ttu-id="7c26a-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7c26a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c26a-115">Het element CustomControl voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7c26a-115">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="7c26a-116">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="7c26a-116">Required element.</span></span><br /><br /> <span data-ttu-id="7c26a-117">Hiermee wordt het besturings element gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="7c26a-117">Defines the control.</span></span>|
|[<span data-ttu-id="7c26a-118">Naam element voor besturings element voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="7c26a-118">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="7c26a-119">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="7c26a-119">Required element.</span></span><br /><br /> <span data-ttu-id="7c26a-120">Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar het besturings element.</span><span class="sxs-lookup"><span data-stu-id="7c26a-120">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7c26a-121">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7c26a-121">Parent Elements</span></span>

|<span data-ttu-id="7c26a-122">Element</span><span class="sxs-lookup"><span data-stu-id="7c26a-122">Element</span></span>|<span data-ttu-id="7c26a-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7c26a-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c26a-124">Beheert element van configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="7c26a-124">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="7c26a-125">Hiermee definieert u de algemene besturings elementen die kunnen worden gebruikt door alle weer gaven van het opmaak bestand of door andere besturings elementen.</span><span class="sxs-lookup"><span data-stu-id="7c26a-125">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7c26a-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7c26a-126">Remarks</span></span>

<span data-ttu-id="7c26a-127">In de volgende elementen kan worden verwezen naar de naam die aan dit besturings element wordt gegeven:</span><span class="sxs-lookup"><span data-stu-id="7c26a-127">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="7c26a-128">ExpressionBinding-element voor CustomItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="7c26a-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="7c26a-129">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="7c26a-129">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="7c26a-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7c26a-130">See Also</span></span>

[<span data-ttu-id="7c26a-131">Beheert element van configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="7c26a-131">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="7c26a-132">CustomControl-element voor besturings element voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="7c26a-132">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="7c26a-133">ExpressionBinding-element voor CustomItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="7c26a-133">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="7c26a-134">Element GroupBy voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="7c26a-134">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="7c26a-135">Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7c26a-135">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="7c26a-136">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="7c26a-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
