---
title: ScriptBlock-Element voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229314"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="81794-102">Het element ScriptBlock voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="81794-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="81794-103">Hiermee geeft u het script dat een nieuwe groep wordt gestart wanneer de waarde ervan verandert.</span><span class="sxs-lookup"><span data-stu-id="81794-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="81794-104">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) ScriptBlock-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="81794-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="81794-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="81794-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="81794-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="81794-106">Attributes and Elements</span></span>

<span data-ttu-id="81794-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="81794-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="81794-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="81794-108">Attributes</span></span>

<span data-ttu-id="81794-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="81794-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="81794-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="81794-110">Child Elements</span></span>

<span data-ttu-id="81794-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="81794-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="81794-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="81794-112">Parent Elements</span></span>

|<span data-ttu-id="81794-113">Element</span><span class="sxs-lookup"><span data-stu-id="81794-113">Element</span></span>|<span data-ttu-id="81794-114">Description</span><span class="sxs-lookup"><span data-stu-id="81794-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="81794-115">GroupBy-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="81794-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="81794-116">Hiermee definieert u hoe u een groep van .NET-objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="81794-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="81794-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="81794-117">Text Value</span></span>

<span data-ttu-id="81794-118">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="81794-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="81794-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="81794-119">Remarks</span></span>

<span data-ttu-id="81794-120">PowerShell wordt een nieuwe groep gestart wanneer de waarde van dit script wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="81794-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="81794-121">Wanneer dit element is opgegeven, wordt u niet opgeven de [PropertyName](propertyname-element-for-groupby-format.md) element naar een nieuwe groep.</span><span class="sxs-lookup"><span data-stu-id="81794-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="81794-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="81794-122">See Also</span></span>

[<span data-ttu-id="81794-123">PropertyName-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="81794-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="81794-124">GroupBy-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="81794-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="81794-125">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="81794-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
