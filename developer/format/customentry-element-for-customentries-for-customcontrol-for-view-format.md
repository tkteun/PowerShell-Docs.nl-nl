---
title: CustomEntry-Element voor CustomEntries voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850881"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="c95b3-102">Het element CustomEntry voor CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c95b3-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="c95b3-103">Bevat een definitie van de weergave van het aangepaste besturingselement.</span><span class="sxs-lookup"><span data-stu-id="c95b3-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="c95b3-104">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c95b3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c95b3-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c95b3-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c95b3-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c95b3-106">Attributes and Elements</span></span>

<span data-ttu-id="c95b3-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="c95b3-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="c95b3-108">U moet de items worden weergegeven door de definitie opgeven.</span><span class="sxs-lookup"><span data-stu-id="c95b3-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="c95b3-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c95b3-109">Attributes</span></span>

<span data-ttu-id="c95b3-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="c95b3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c95b3-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c95b3-111">Child Elements</span></span>

|<span data-ttu-id="c95b3-112">Element</span><span class="sxs-lookup"><span data-stu-id="c95b3-112">Element</span></span>|<span data-ttu-id="c95b3-113">Description</span><span class="sxs-lookup"><span data-stu-id="c95b3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c95b3-114">EntrySelectedBy-Element voor CustomEntry voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c95b3-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="c95b3-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c95b3-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c95b3-116">Hiermee definieert u de .NET-typen die gebruikmaken van de definitie van de weergave van het aangepaste besturingselement of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c95b3-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="c95b3-117">CustomItem-Element voor CustomEntry voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c95b3-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="c95b3-118">Hiermee definieert u een besturingselement voor de definitie van het aangepaste besturingselement.</span><span class="sxs-lookup"><span data-stu-id="c95b3-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c95b3-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c95b3-119">Parent Elements</span></span>

|<span data-ttu-id="c95b3-120">Element</span><span class="sxs-lookup"><span data-stu-id="c95b3-120">Element</span></span>|<span data-ttu-id="c95b3-121">Description</span><span class="sxs-lookup"><span data-stu-id="c95b3-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c95b3-122">CustomEntries-Element voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c95b3-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="c95b3-123">Bevat de definities van de weergave van het aangepaste besturingselement.</span><span class="sxs-lookup"><span data-stu-id="c95b3-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="c95b3-124">De weergave van het aangepaste besturingselement moet een of meer netwerkdefinities opgeven.</span><span class="sxs-lookup"><span data-stu-id="c95b3-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c95b3-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c95b3-125">Remarks</span></span>

<span data-ttu-id="c95b3-126">In de meeste gevallen slechts één definitie is vereist voor elke weergave aangepast besturingselement, maar het is mogelijk dat meerdere definities als u wilt de dezelfde weergave gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c95b3-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="c95b3-127">In deze gevallen kunt u de definitie van een afzonderlijke voor elk object of een set van objecten opgeven.</span><span class="sxs-lookup"><span data-stu-id="c95b3-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="c95b3-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c95b3-128">See Also</span></span>

[<span data-ttu-id="c95b3-129">CustomControl-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c95b3-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="c95b3-130">CustomItem-Element voor CustomEntry voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c95b3-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c95b3-131">EntrySelectedBy-Element voor CustomEntry voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c95b3-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c95b3-132">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="c95b3-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
