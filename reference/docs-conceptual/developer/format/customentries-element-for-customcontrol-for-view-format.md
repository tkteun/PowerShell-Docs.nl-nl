---
title: CustomEntries-element voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355277"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="49d0f-102">Het element CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="49d0f-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="49d0f-103">Biedt de definities van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="49d0f-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="49d0f-104">In de aangepaste beheer weergave moeten een of meer definities worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="49d0f-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="49d0f-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer gave (indeling) CustomControl element (indeling) CustomEntries element voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="49d0f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="49d0f-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="49d0f-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="49d0f-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="49d0f-107">Attributes and Elements</span></span>

<span data-ttu-id="49d0f-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomControlEntries` beschreven.</span><span class="sxs-lookup"><span data-stu-id="49d0f-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="49d0f-109">U moet een of meer onderliggende elementen opgeven.</span><span class="sxs-lookup"><span data-stu-id="49d0f-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="49d0f-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="49d0f-110">Attributes</span></span>

<span data-ttu-id="49d0f-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="49d0f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="49d0f-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="49d0f-112">Child Elements</span></span>

|<span data-ttu-id="49d0f-113">Element</span><span class="sxs-lookup"><span data-stu-id="49d0f-113">Element</span></span>|<span data-ttu-id="49d0f-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="49d0f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="49d0f-115">CustomEntry-element voor CustomEntries voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="49d0f-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="49d0f-116">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="49d0f-116">Required element.</span></span><br /><br /> <span data-ttu-id="49d0f-117">Biedt een definitie van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="49d0f-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="49d0f-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="49d0f-118">Parent Elements</span></span>

|<span data-ttu-id="49d0f-119">Element</span><span class="sxs-lookup"><span data-stu-id="49d0f-119">Element</span></span>|<span data-ttu-id="49d0f-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="49d0f-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="49d0f-121">CustomControl-element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="49d0f-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="49d0f-122">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="49d0f-122">Required element.</span></span><br /><br /> <span data-ttu-id="49d0f-123">Hiermee wordt een aangepaste besturings element-indeling gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="49d0f-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="49d0f-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="49d0f-124">Remarks</span></span>

<span data-ttu-id="49d0f-125">In de meeste gevallen heeft een besturings element slechts één definitie, die in één `CustomEntry` element is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="49d0f-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="49d0f-126">Het is echter mogelijk om meerdere definities te hebben als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="49d0f-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="49d0f-127">In dergelijke gevallen kunt u een `CustomEntry` element definiëren voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="49d0f-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="49d0f-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="49d0f-128">See Also</span></span>

[<span data-ttu-id="49d0f-129">CustomControl-element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="49d0f-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="49d0f-130">CustomEntry-element voor CustomEntries voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="49d0f-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="49d0f-131">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="49d0f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
