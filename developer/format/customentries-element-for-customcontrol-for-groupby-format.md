---
title: CustomEntries-Element voor CustomControl voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845183"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="bc84f-102">Het element CustomEntries voor CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="bc84f-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="bc84f-103">Bevat de definities voor het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="bc84f-103">Provides the definitions for the control.</span></span> <span data-ttu-id="bc84f-104">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bc84f-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="bc84f-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl-Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="bc84f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bc84f-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="bc84f-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bc84f-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="bc84f-107">Attributes and Elements</span></span>

<span data-ttu-id="bc84f-108">De volgende secties beschrijven kenmerken, elementen van de onderliggende en bovenliggende elementen van de `CustomEntries` element.</span><span class="sxs-lookup"><span data-stu-id="bc84f-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="bc84f-109">Er is geen maximale limiet voor het aantal onderliggende elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bc84f-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc84f-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="bc84f-110">Attributes</span></span>

<span data-ttu-id="bc84f-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="bc84f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bc84f-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="bc84f-112">Child Elements</span></span>

|<span data-ttu-id="bc84f-113">Element</span><span class="sxs-lookup"><span data-stu-id="bc84f-113">Element</span></span>|<span data-ttu-id="bc84f-114">Description</span><span class="sxs-lookup"><span data-stu-id="bc84f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc84f-115">CustomEntry-Element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="bc84f-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="bc84f-116">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="bc84f-116">Required element.</span></span><br /><br /> <span data-ttu-id="bc84f-117">Bevat een definitie van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="bc84f-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bc84f-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="bc84f-118">Parent Elements</span></span>

|<span data-ttu-id="bc84f-119">Element</span><span class="sxs-lookup"><span data-stu-id="bc84f-119">Element</span></span>|<span data-ttu-id="bc84f-120">Description</span><span class="sxs-lookup"><span data-stu-id="bc84f-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc84f-121">CustomControl-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="bc84f-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="bc84f-122">Hiermee definieert u het aangepaste besturingselement weergegeven met de nieuwe groep.</span><span class="sxs-lookup"><span data-stu-id="bc84f-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bc84f-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="bc84f-123">Remarks</span></span>

<span data-ttu-id="bc84f-124">In de meeste gevallen een besturingselement heeft slechts één definitie die is opgegeven in een enkel `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="bc84f-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="bc84f-125">Het is echter mogelijk om meerdere definities als u wilt de hetzelfde besturingselement gebruiken om verschillende groepen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="bc84f-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="bc84f-126">In deze gevallen kunt u een `CustomEntry` -element voor een groep.</span><span class="sxs-lookup"><span data-stu-id="bc84f-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc84f-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bc84f-127">See Also</span></span>

[<span data-ttu-id="bc84f-128">CustomEntry-Element voor CustomEntries voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="bc84f-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="bc84f-129">CustomControl-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="bc84f-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="bc84f-130">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc84f-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
