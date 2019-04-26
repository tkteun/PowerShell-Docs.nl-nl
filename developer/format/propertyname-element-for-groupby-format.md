---
title: PropertyName-Element voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075865"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="d9c46-102">Het element PropertyName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d9c46-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="d9c46-103">Hiermee geeft u de .NET-eigenschap die een nieuwe groep wordt gestart wanneer de waarde ervan verandert.</span><span class="sxs-lookup"><span data-stu-id="d9c46-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="d9c46-104">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) PropertyName-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="d9c46-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d9c46-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d9c46-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d9c46-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d9c46-106">Attributes and Elements</span></span>

<span data-ttu-id="d9c46-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="d9c46-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d9c46-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d9c46-108">Attributes</span></span>

<span data-ttu-id="d9c46-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="d9c46-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d9c46-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d9c46-110">Child Elements</span></span>

<span data-ttu-id="d9c46-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="d9c46-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d9c46-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d9c46-112">Parent Elements</span></span>

|<span data-ttu-id="d9c46-113">Element</span><span class="sxs-lookup"><span data-stu-id="d9c46-113">Element</span></span>|<span data-ttu-id="d9c46-114">Description</span><span class="sxs-lookup"><span data-stu-id="d9c46-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9c46-115">GroupBy-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d9c46-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="d9c46-116">Hiermee definieert u hoe u een groep van .NET-objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="d9c46-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d9c46-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="d9c46-117">Text Value</span></span>

<span data-ttu-id="d9c46-118">Geef de naam van de .NET-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="d9c46-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="d9c46-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d9c46-119">Remarks</span></span>

<span data-ttu-id="d9c46-120">Windows PowerShell wordt een nieuwe groep gestart wanneer de waarde van deze eigenschap wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="d9c46-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="d9c46-121">Wanneer dit element is opgegeven, wordt u niet opgeven de [ScriptBlock](./scriptblock-element-for-groupby-format.md) element naar een nieuwe groep.</span><span class="sxs-lookup"><span data-stu-id="d9c46-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="d9c46-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="d9c46-122">Example</span></span>

<span data-ttu-id="d9c46-123">Het volgende voorbeeld ziet hoe u een nieuwe groep wordt gestart wanneer de waarde van een eigenschap wijzigt.</span><span class="sxs-lookup"><span data-stu-id="d9c46-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="d9c46-124">Zie voor een voorbeeld van een volledige opmaak bestand waarin dit element [brede weergave (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="d9c46-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d9c46-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d9c46-125">See Also</span></span>

[<span data-ttu-id="d9c46-126">GroupBy-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d9c46-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="d9c46-127">ScriptBlock-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="d9c46-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="d9c46-128">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="d9c46-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
