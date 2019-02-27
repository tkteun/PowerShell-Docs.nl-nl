---
title: CustomControlName-Element voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849824"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="26e71-102">Het element CustomControlName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="26e71-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="26e71-103">Hiermee geeft u de naam van een aangepast besturingselement dat wordt gebruikt om de nieuwe groep weer te geven.</span><span class="sxs-lookup"><span data-stu-id="26e71-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="26e71-104">Dit element wordt gebruikt bij het definiëren van een tabel, lijst, breed of aangepast besturingselement weergeven.</span><span class="sxs-lookup"><span data-stu-id="26e71-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="26e71-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControlName-Element van GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="26e71-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="26e71-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="26e71-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="26e71-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="26e71-107">Attributes and Elements</span></span>

<span data-ttu-id="26e71-108">De volgende secties worden de kenmerken, de onderliggende elementen en de bovenliggende elementen van de `CustomControlName` element.</span><span class="sxs-lookup"><span data-stu-id="26e71-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="26e71-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="26e71-109">Attributes</span></span>

<span data-ttu-id="26e71-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="26e71-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="26e71-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="26e71-111">Child Elements</span></span>

<span data-ttu-id="26e71-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="26e71-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="26e71-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="26e71-113">Parent Elements</span></span>

|<span data-ttu-id="26e71-114">Element</span><span class="sxs-lookup"><span data-stu-id="26e71-114">Element</span></span>|<span data-ttu-id="26e71-115">Description</span><span class="sxs-lookup"><span data-stu-id="26e71-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="26e71-116">GroupBy-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="26e71-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="26e71-117">Hiermee definieert u hoe een nieuwe groep objecten worden weergegeven in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26e71-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="26e71-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="26e71-118">Text Value</span></span>

<span data-ttu-id="26e71-119">Geef de naam van het aangepaste besturingselement dat wordt gebruikt om een nieuwe groep weer te geven.</span><span class="sxs-lookup"><span data-stu-id="26e71-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="26e71-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="26e71-120">Remarks</span></span>

<span data-ttu-id="26e71-121">Kunt u algemene besturingselementen die kunnen worden gebruikt door alle weergaven van een opmaak bestand maken en u kunt besturingselementen weergeven die kunnen worden gebruikt door een specifieke weergave maken.</span><span class="sxs-lookup"><span data-stu-id="26e71-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="26e71-122">De volgende elementen geeft de namen van deze aangepaste besturingselementen:</span><span class="sxs-lookup"><span data-stu-id="26e71-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="26e71-123">Naamelement voor controle van besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="26e71-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="26e71-124">Naamelement voor controle van besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="26e71-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="26e71-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="26e71-125">See Also</span></span>

[<span data-ttu-id="26e71-126">GroupBy-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="26e71-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="26e71-127">Naamelement voor controle van besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="26e71-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="26e71-128">Naamelement voor controle van besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="26e71-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="26e71-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="26e71-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
