---
title: CustomEntry-Element voor CustomControl voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066470"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="7150c-102">Het element CustomEntry voor CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7150c-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="7150c-103">Bevat een definitie van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="7150c-103">Provides a definition of the control.</span></span> <span data-ttu-id="7150c-104">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="7150c-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="7150c-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7150c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7150c-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7150c-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7150c-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7150c-107">Attributes and Elements</span></span>

<span data-ttu-id="7150c-108">De volgende secties beschrijven kenmerken, onderliggende elementen en de bovenliggende elementen van de `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="7150c-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7150c-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7150c-109">Attributes</span></span>

<span data-ttu-id="7150c-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="7150c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7150c-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7150c-111">Child Elements</span></span>

|<span data-ttu-id="7150c-112">Element</span><span class="sxs-lookup"><span data-stu-id="7150c-112">Element</span></span>|<span data-ttu-id="7150c-113">Description</span><span class="sxs-lookup"><span data-stu-id="7150c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7150c-114">EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7150c-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="7150c-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7150c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="7150c-116">Hiermee definieert u de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7150c-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="7150c-117">CustomItem-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7150c-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="7150c-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="7150c-118">Required element.</span></span><br /><br /> <span data-ttu-id="7150c-119">Hiermee definieert u hoe de gegevens in het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="7150c-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7150c-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7150c-120">Parent Elements</span></span>

|<span data-ttu-id="7150c-121">Element</span><span class="sxs-lookup"><span data-stu-id="7150c-121">Element</span></span>|<span data-ttu-id="7150c-122">Description</span><span class="sxs-lookup"><span data-stu-id="7150c-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7150c-123">CustomEntries-Element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7150c-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="7150c-124">Bevat de definities voor het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="7150c-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7150c-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7150c-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="7150c-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7150c-126">See Also</span></span>

[<span data-ttu-id="7150c-127">EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7150c-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="7150c-128">CustomItem-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7150c-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="7150c-129">CustomEntries-Element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7150c-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="7150c-130">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="7150c-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
