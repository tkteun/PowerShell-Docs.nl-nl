---
title: CustomEntry-element voor CustomEntries voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355235"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="3af9a-102">Het element CustomEntry voor CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3af9a-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="3af9a-103">Biedt een definitie van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="3af9a-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="3af9a-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="3af9a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3af9a-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="3af9a-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3af9a-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="3af9a-106">Attributes and Elements</span></span>

<span data-ttu-id="3af9a-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomEntry` beschreven.</span><span class="sxs-lookup"><span data-stu-id="3af9a-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="3af9a-108">U moet de items opgeven die worden weer gegeven door de definitie.</span><span class="sxs-lookup"><span data-stu-id="3af9a-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="3af9a-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="3af9a-109">Attributes</span></span>

<span data-ttu-id="3af9a-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="3af9a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3af9a-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3af9a-111">Child Elements</span></span>

|<span data-ttu-id="3af9a-112">Element</span><span class="sxs-lookup"><span data-stu-id="3af9a-112">Element</span></span>|<span data-ttu-id="3af9a-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3af9a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3af9a-114">EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="3af9a-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="3af9a-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="3af9a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3af9a-116">Hiermee definieert u de .NET-typen die gebruikmaken van de definitie van de aangepaste beheer weergave of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3af9a-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="3af9a-117">CustomItem-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="3af9a-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="3af9a-118">Hiermee definieert u een besturings element voor de aangepaste besturings element definitie.</span><span class="sxs-lookup"><span data-stu-id="3af9a-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3af9a-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3af9a-119">Parent Elements</span></span>

|<span data-ttu-id="3af9a-120">Element</span><span class="sxs-lookup"><span data-stu-id="3af9a-120">Element</span></span>|<span data-ttu-id="3af9a-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3af9a-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3af9a-122">CustomEntries-element voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="3af9a-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="3af9a-123">Biedt de definities van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="3af9a-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="3af9a-124">In de aangepaste beheer weergave moeten een of meer definities worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3af9a-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3af9a-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3af9a-125">Remarks</span></span>

<span data-ttu-id="3af9a-126">In de meeste gevallen is er slechts één definitie vereist voor elke aangepaste controle weergave, maar het is mogelijk om meerdere definities te hebben als u dezelfde weer gave wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="3af9a-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="3af9a-127">In dergelijke gevallen kunt u een afzonderlijke definitie opgeven voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="3af9a-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="3af9a-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3af9a-128">See Also</span></span>

[<span data-ttu-id="3af9a-129">CustomControl-element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="3af9a-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="3af9a-130">CustomItem-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="3af9a-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3af9a-131">EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="3af9a-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3af9a-132">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="3af9a-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
