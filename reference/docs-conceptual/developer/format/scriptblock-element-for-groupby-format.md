---
title: Script block-element voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e761e02a7910cd598449d564e827889162da9f25
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787679"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="c36d3-102">Het element ScriptBlock voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c36d3-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="c36d3-103">Hiermee geeft u het script op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c36d3-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="c36d3-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (Format) script block-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c36d3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c36d3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c36d3-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c36d3-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c36d3-106">Attributes and Elements</span></span>

<span data-ttu-id="c36d3-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="c36d3-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c36d3-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c36d3-108">Attributes</span></span>

<span data-ttu-id="c36d3-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="c36d3-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c36d3-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c36d3-110">Child Elements</span></span>

<span data-ttu-id="c36d3-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="c36d3-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c36d3-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c36d3-112">Parent Elements</span></span>

|<span data-ttu-id="c36d3-113">Element</span><span class="sxs-lookup"><span data-stu-id="c36d3-113">Element</span></span>|<span data-ttu-id="c36d3-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c36d3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c36d3-115">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c36d3-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="c36d3-116">Hiermee definieert u hoe een groep .NET-objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c36d3-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c36d3-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="c36d3-117">Text Value</span></span>

<span data-ttu-id="c36d3-118">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="c36d3-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="c36d3-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c36d3-119">Remarks</span></span>

<span data-ttu-id="c36d3-120">Power shell start een nieuwe groep wanneer de waarde van dit script wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c36d3-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="c36d3-121">Als dit element is opgegeven, kunt u het element [PropertyName](propertyname-element-for-groupby-format.md) niet opgeven om een nieuwe groep te starten.</span><span class="sxs-lookup"><span data-stu-id="c36d3-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="c36d3-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c36d3-122">See Also</span></span>

[<span data-ttu-id="c36d3-123">Het element PropertyName voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c36d3-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="c36d3-124">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c36d3-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="c36d3-125">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c36d3-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
