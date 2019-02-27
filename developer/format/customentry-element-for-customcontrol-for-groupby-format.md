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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849866"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="71eb8-102">Het element CustomEntry voor CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="71eb8-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="71eb8-103">Bevat een definitie van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="71eb8-103">Provides a definition of the control.</span></span> <span data-ttu-id="71eb8-104">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="71eb8-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="71eb8-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="71eb8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="71eb8-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="71eb8-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="71eb8-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="71eb8-107">Attributes and Elements</span></span>

<span data-ttu-id="71eb8-108">De volgende secties beschrijven kenmerken, onderliggende elementen en de bovenliggende elementen van de `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="71eb8-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="71eb8-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="71eb8-109">Attributes</span></span>

<span data-ttu-id="71eb8-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="71eb8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="71eb8-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="71eb8-111">Child Elements</span></span>

|<span data-ttu-id="71eb8-112">Element</span><span class="sxs-lookup"><span data-stu-id="71eb8-112">Element</span></span>|<span data-ttu-id="71eb8-113">Description</span><span class="sxs-lookup"><span data-stu-id="71eb8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="71eb8-114">EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="71eb8-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="71eb8-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="71eb8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="71eb8-116">Hiermee definieert u de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="71eb8-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="71eb8-117">CustomItem-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="71eb8-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="71eb8-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="71eb8-118">Required element.</span></span><br /><br /> <span data-ttu-id="71eb8-119">Hiermee definieert u hoe de gegevens in het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="71eb8-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="71eb8-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="71eb8-120">Parent Elements</span></span>

|<span data-ttu-id="71eb8-121">Element</span><span class="sxs-lookup"><span data-stu-id="71eb8-121">Element</span></span>|<span data-ttu-id="71eb8-122">Description</span><span class="sxs-lookup"><span data-stu-id="71eb8-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="71eb8-123">CustomEntries-Element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="71eb8-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="71eb8-124">Bevat de definities voor het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="71eb8-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="71eb8-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="71eb8-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="71eb8-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="71eb8-126">See Also</span></span>

[<span data-ttu-id="71eb8-127">EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="71eb8-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="71eb8-128">CustomItem-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="71eb8-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="71eb8-129">CustomEntries-Element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="71eb8-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="71eb8-130">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="71eb8-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
