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
ms.openlocfilehash: 41a6aaa24e5850bd390c8e3b6505cc88fc80b7b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846954"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="93d2b-102">Het element ScriptBlock voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="93d2b-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="93d2b-103">Hiermee geeft u het script dat een nieuwe groep wordt gestart wanneer de waarde ervan verandert.</span><span class="sxs-lookup"><span data-stu-id="93d2b-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="93d2b-104">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) ScriptBlock-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="93d2b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="93d2b-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="93d2b-105">Syntax</span></span>

```xml
<ScriptBolck>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="93d2b-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="93d2b-106">Attributes and Elements</span></span>

<span data-ttu-id="93d2b-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="93d2b-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="93d2b-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="93d2b-108">Attributes</span></span>

<span data-ttu-id="93d2b-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="93d2b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="93d2b-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="93d2b-110">Child Elements</span></span>

<span data-ttu-id="93d2b-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="93d2b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="93d2b-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="93d2b-112">Parent Elements</span></span>

|<span data-ttu-id="93d2b-113">Element</span><span class="sxs-lookup"><span data-stu-id="93d2b-113">Element</span></span>|<span data-ttu-id="93d2b-114">Description</span><span class="sxs-lookup"><span data-stu-id="93d2b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="93d2b-115">GroupBy-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="93d2b-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="93d2b-116">Hiermee definieert u hoe u een groep van .NET-objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="93d2b-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="93d2b-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="93d2b-117">Text Value</span></span>

<span data-ttu-id="93d2b-118">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="93d2b-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="93d2b-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="93d2b-119">Remarks</span></span>

<span data-ttu-id="93d2b-120">Windows PowerShell wordt een nieuwe groep gestart wanneer de waarde van dit script wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="93d2b-120">Windows PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="93d2b-121">Wanneer dit element is opgegeven, wordt u niet opgeven de [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element naar een nieuwe groep.</span><span class="sxs-lookup"><span data-stu-id="93d2b-121">When this element is specified, you cannot specify the [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="93d2b-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="93d2b-122">See Also</span></span>

[<span data-ttu-id="93d2b-123">PropertyName-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="93d2b-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="93d2b-124">GroupBy-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="93d2b-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="93d2b-125">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="93d2b-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
