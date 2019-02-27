---
title: CustomControl-Element voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850489"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="17e7d-102">Het element CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="17e7d-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="17e7d-103">Hiermee definieert u een aangepast besturingselement-indeling voor de weergave.</span><span class="sxs-lookup"><span data-stu-id="17e7d-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="17e7d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="17e7d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="17e7d-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="17e7d-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="17e7d-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="17e7d-106">Attributes and Elements</span></span>

<span data-ttu-id="17e7d-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomControl` element.</span><span class="sxs-lookup"><span data-stu-id="17e7d-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="17e7d-108">U kunt één onderliggend element moet opgeven.</span><span class="sxs-lookup"><span data-stu-id="17e7d-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="17e7d-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="17e7d-109">Attributes</span></span>

<span data-ttu-id="17e7d-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="17e7d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="17e7d-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="17e7d-111">Child Elements</span></span>

|<span data-ttu-id="17e7d-112">Element</span><span class="sxs-lookup"><span data-stu-id="17e7d-112">Element</span></span>|<span data-ttu-id="17e7d-113">Description</span><span class="sxs-lookup"><span data-stu-id="17e7d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="17e7d-114">CustomEntries-Element voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="17e7d-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="17e7d-115">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="17e7d-115">Required element.</span></span><br /><br /> <span data-ttu-id="17e7d-116">Bevat de definities van de weergave van het aangepaste besturingselement.</span><span class="sxs-lookup"><span data-stu-id="17e7d-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="17e7d-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="17e7d-117">Parent Elements</span></span>

|<span data-ttu-id="17e7d-118">Element</span><span class="sxs-lookup"><span data-stu-id="17e7d-118">Element</span></span>|<span data-ttu-id="17e7d-119">Description</span><span class="sxs-lookup"><span data-stu-id="17e7d-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="17e7d-120">Weergave-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="17e7d-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="17e7d-121">Hiermee definieert u een weergave die wordt gebruikt om een of meer .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="17e7d-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="17e7d-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="17e7d-122">Remarks</span></span>

<span data-ttu-id="17e7d-123">In de meeste gevallen slechts één definitie is vereist voor de weergave van elk besturingselement, maar het is mogelijk om meerdere definities als u wilt de dezelfde weergave gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="17e7d-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="17e7d-124">In deze gevallen kunt u de definitie van een afzonderlijke voor elk object of een set van objecten opgeven.</span><span class="sxs-lookup"><span data-stu-id="17e7d-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="17e7d-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="17e7d-125">See Also</span></span>

[<span data-ttu-id="17e7d-126">CustomEntries-Element voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="17e7d-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="17e7d-127">Weergave-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="17e7d-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="17e7d-128">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="17e7d-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
