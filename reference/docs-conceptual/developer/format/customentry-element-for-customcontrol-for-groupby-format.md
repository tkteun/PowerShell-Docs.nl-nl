---
title: CustomEntry-element voor CustomControl voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355263"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="c0923-102">Het element CustomEntry voor CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c0923-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="c0923-103">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="c0923-103">Provides a definition of the control.</span></span> <span data-ttu-id="c0923-104">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c0923-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c0923-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c0923-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c0923-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c0923-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c0923-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c0923-107">Attributes and Elements</span></span>

<span data-ttu-id="c0923-108">In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het element `CustomEntry` beschreven.</span><span class="sxs-lookup"><span data-stu-id="c0923-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c0923-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c0923-109">Attributes</span></span>

<span data-ttu-id="c0923-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="c0923-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c0923-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c0923-111">Child Elements</span></span>

|<span data-ttu-id="c0923-112">Element</span><span class="sxs-lookup"><span data-stu-id="c0923-112">Element</span></span>|<span data-ttu-id="c0923-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c0923-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0923-114">EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c0923-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="c0923-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c0923-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c0923-116">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c0923-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="c0923-117">CustomItem-element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c0923-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="c0923-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="c0923-118">Required element.</span></span><br /><br /> <span data-ttu-id="c0923-119">Hiermee wordt gedefinieerd hoe de gegevens worden weer gegeven in het besturings element.</span><span class="sxs-lookup"><span data-stu-id="c0923-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c0923-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c0923-120">Parent Elements</span></span>

|<span data-ttu-id="c0923-121">Element</span><span class="sxs-lookup"><span data-stu-id="c0923-121">Element</span></span>|<span data-ttu-id="c0923-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c0923-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0923-123">CustomEntries-element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c0923-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="c0923-124">Bevat de definities voor het besturings element.</span><span class="sxs-lookup"><span data-stu-id="c0923-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c0923-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c0923-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="c0923-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c0923-126">See Also</span></span>

[<span data-ttu-id="c0923-127">EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c0923-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="c0923-128">CustomItem-element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c0923-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="c0923-129">CustomEntries-element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c0923-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="c0923-130">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c0923-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
