---
title: Hiermee bepaalt u Element voor configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850433"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="2d76b-102">Het element Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2d76b-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="2d76b-103">Hiermee definieert u de algemene besturingselementen die kunnen worden gebruikt door alle weergaven van de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="2d76b-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="2d76b-104">Configuratie-Element (indeling) besturingselementen-Element van de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="2d76b-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2d76b-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="2d76b-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2d76b-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="2d76b-106">Attributes and Elements</span></span>

<span data-ttu-id="2d76b-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `Controls` element.</span><span class="sxs-lookup"><span data-stu-id="2d76b-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2d76b-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2d76b-108">Attributes</span></span>

<span data-ttu-id="2d76b-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="2d76b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2d76b-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2d76b-110">Child Elements</span></span>

|<span data-ttu-id="2d76b-111">Element</span><span class="sxs-lookup"><span data-stu-id="2d76b-111">Element</span></span>|<span data-ttu-id="2d76b-112">Description</span><span class="sxs-lookup"><span data-stu-id="2d76b-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2d76b-113">Controle-Element voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="2d76b-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="2d76b-114">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="2d76b-114">Required element.</span></span><br /><br /> <span data-ttu-id="2d76b-115">Hiermee definieert u een algemene besturingselement dat kan worden gebruikt door alle weergaven van de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="2d76b-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2d76b-116">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2d76b-116">Parent Elements</span></span>

|<span data-ttu-id="2d76b-117">Element</span><span class="sxs-lookup"><span data-stu-id="2d76b-117">Element</span></span>|<span data-ttu-id="2d76b-118">Description</span><span class="sxs-lookup"><span data-stu-id="2d76b-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2d76b-119">Configuratie-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="2d76b-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="2d76b-120">Hiermee geeft u het element op het hoogste niveau van een bestand met opmaak.</span><span class="sxs-lookup"><span data-stu-id="2d76b-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2d76b-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2d76b-121">Remarks</span></span>

<span data-ttu-id="2d76b-122">U kunt een willekeurig aantal veelgebruikte besturingselementen kunt maken.</span><span class="sxs-lookup"><span data-stu-id="2d76b-122">You can create any number of common controls.</span></span> <span data-ttu-id="2d76b-123">Voor elk besturingselement, moet u de naam die wordt gebruikt om te verwijzen naar het besturingselement en de onderdelen van het besturingselement opgeven.</span><span class="sxs-lookup"><span data-stu-id="2d76b-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d76b-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2d76b-124">See Also</span></span>

[<span data-ttu-id="2d76b-125">Configuratie-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="2d76b-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="2d76b-126">Controle-Element voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="2d76b-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="2d76b-127">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="2d76b-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
