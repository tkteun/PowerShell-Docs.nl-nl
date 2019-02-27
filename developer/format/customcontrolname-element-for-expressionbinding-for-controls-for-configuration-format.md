---
title: CustomControlName-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5242935-2782-4d23-84f5-2446b2b7ba83
caps.latest.revision: 8
ms.openlocfilehash: c9abd9f22907b87323c16d603a9f75bb3d375a03
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847031"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="d2e94-102">Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d2e94-102">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d2e94-103">Hiermee geeft u de naam van een algemene besturingselement.</span><span class="sxs-lookup"><span data-stu-id="d2e94-103">Specifies the name of a common control.</span></span> <span data-ttu-id="d2e94-104">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="d2e94-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d2e94-105">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) CustomItem-Element voor CustomEntry voor besturingselementen voor ExpressionBinding, configuratie-Element voor CustomItem voor besturingselementen voor CustomControlName configuratie (-indeling) Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="d2e94-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d2e94-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d2e94-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d2e94-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d2e94-107">Attributes and Elements</span></span>

<span data-ttu-id="d2e94-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomControlName` element.</span><span class="sxs-lookup"><span data-stu-id="d2e94-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d2e94-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d2e94-109">Attributes</span></span>

<span data-ttu-id="d2e94-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="d2e94-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d2e94-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d2e94-111">Child Elements</span></span>

<span data-ttu-id="d2e94-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="d2e94-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d2e94-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d2e94-113">Parent Elements</span></span>

|<span data-ttu-id="d2e94-114">Element</span><span class="sxs-lookup"><span data-stu-id="d2e94-114">Element</span></span>|<span data-ttu-id="d2e94-115">Description</span><span class="sxs-lookup"><span data-stu-id="d2e94-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d2e94-116">ExpressionBinding-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="d2e94-116">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="d2e94-117">Definieert de gegevens die door het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="d2e94-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d2e94-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="d2e94-118">Text Value</span></span>

<span data-ttu-id="d2e94-119">Geef de naam van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="d2e94-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2e94-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d2e94-120">Remarks</span></span>

<span data-ttu-id="d2e94-121">Kunt u algemene besturingselementen die kunnen worden gebruikt door alle weergaven van een opmaak bestand maken en u kunt besturingselementen weergeven die kunnen worden gebruikt door een specifieke weergave maken.</span><span class="sxs-lookup"><span data-stu-id="d2e94-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="d2e94-122">De volgende elementen geeft de namen van deze besturingselementen:</span><span class="sxs-lookup"><span data-stu-id="d2e94-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="d2e94-123">Naamelement voor controle van besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="d2e94-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="d2e94-124">Naamelement voor controle van besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d2e94-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="d2e94-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d2e94-125">See Also</span></span>

[<span data-ttu-id="d2e94-126">Naamelement voor controle van besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="d2e94-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="d2e94-127">Naamelement voor controle van besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d2e94-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="d2e94-128">ExpressionBinding-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="d2e94-128">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="d2e94-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2e94-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
