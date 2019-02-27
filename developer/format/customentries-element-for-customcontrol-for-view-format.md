---
title: CustomEntries-Element voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850797"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="5e8c2-102">Het element CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5e8c2-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="5e8c2-103">Bevat de definities van de weergave van het aangepaste besturingselement.</span><span class="sxs-lookup"><span data-stu-id="5e8c2-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="5e8c2-104">De weergave van het aangepaste besturingselement moet een of meer netwerkdefinities opgeven.</span><span class="sxs-lookup"><span data-stu-id="5e8c2-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="5e8c2-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5e8c2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5e8c2-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5e8c2-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5e8c2-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="5e8c2-107">Attributes and Elements</span></span>

<span data-ttu-id="5e8c2-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomControlEntries` element.</span><span class="sxs-lookup"><span data-stu-id="5e8c2-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="5e8c2-109">U moet een of meer onderliggende elementen.</span><span class="sxs-lookup"><span data-stu-id="5e8c2-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5e8c2-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="5e8c2-110">Attributes</span></span>

<span data-ttu-id="5e8c2-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="5e8c2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5e8c2-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5e8c2-112">Child Elements</span></span>

|<span data-ttu-id="5e8c2-113">Element</span><span class="sxs-lookup"><span data-stu-id="5e8c2-113">Element</span></span>|<span data-ttu-id="5e8c2-114">Description</span><span class="sxs-lookup"><span data-stu-id="5e8c2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5e8c2-115">CustomEntry-Element voor CustomEntries voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5e8c2-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="5e8c2-116">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="5e8c2-116">Required element.</span></span><br /><br /> <span data-ttu-id="5e8c2-117">Bevat een definitie van de weergave van het aangepaste besturingselement.</span><span class="sxs-lookup"><span data-stu-id="5e8c2-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5e8c2-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5e8c2-118">Parent Elements</span></span>

|<span data-ttu-id="5e8c2-119">Element</span><span class="sxs-lookup"><span data-stu-id="5e8c2-119">Element</span></span>|<span data-ttu-id="5e8c2-120">Description</span><span class="sxs-lookup"><span data-stu-id="5e8c2-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5e8c2-121">CustomControl-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5e8c2-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="5e8c2-122">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="5e8c2-122">Required element.</span></span><br /><br /> <span data-ttu-id="5e8c2-123">Hiermee definieert u een aangepast besturingselement-indeling voor de weergave.</span><span class="sxs-lookup"><span data-stu-id="5e8c2-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5e8c2-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5e8c2-124">Remarks</span></span>

<span data-ttu-id="5e8c2-125">In de meeste gevallen een besturingselement heeft slechts één definitie die is gedefinieerd in een enkel `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="5e8c2-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="5e8c2-126">Het is echter mogelijk om meerdere definities als u wilt de hetzelfde besturingselement gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5e8c2-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="5e8c2-127">In deze gevallen kunt u een `CustomEntry` -element voor elk object of een set van objecten.</span><span class="sxs-lookup"><span data-stu-id="5e8c2-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e8c2-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5e8c2-128">See Also</span></span>

[<span data-ttu-id="5e8c2-129">CustomControl-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5e8c2-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="5e8c2-130">CustomEntry-Element voor CustomEntries voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5e8c2-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5e8c2-131">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e8c2-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
