---
title: CustomControl-element voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354773"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="4fb50-102">Het element CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4fb50-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="4fb50-103">Hiermee wordt een aangepaste besturings element-indeling gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="4fb50-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="4fb50-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="4fb50-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4fb50-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="4fb50-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4fb50-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="4fb50-106">Attributes and Elements</span></span>

<span data-ttu-id="4fb50-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomControl` beschreven.</span><span class="sxs-lookup"><span data-stu-id="4fb50-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="4fb50-108">U moet één onderliggend element opgeven.</span><span class="sxs-lookup"><span data-stu-id="4fb50-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4fb50-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="4fb50-109">Attributes</span></span>

<span data-ttu-id="4fb50-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="4fb50-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4fb50-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4fb50-111">Child Elements</span></span>

|<span data-ttu-id="4fb50-112">Element</span><span class="sxs-lookup"><span data-stu-id="4fb50-112">Element</span></span>|<span data-ttu-id="4fb50-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4fb50-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4fb50-114">CustomEntries-element voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="4fb50-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="4fb50-115">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="4fb50-115">Required element.</span></span><br /><br /> <span data-ttu-id="4fb50-116">Biedt de definities van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="4fb50-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4fb50-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4fb50-117">Parent Elements</span></span>

|<span data-ttu-id="4fb50-118">Element</span><span class="sxs-lookup"><span data-stu-id="4fb50-118">Element</span></span>|<span data-ttu-id="4fb50-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4fb50-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4fb50-120">Element weer geven (indeling)</span><span class="sxs-lookup"><span data-stu-id="4fb50-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="4fb50-121">Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om een of meer .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="4fb50-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4fb50-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="4fb50-122">Remarks</span></span>

<span data-ttu-id="4fb50-123">In de meeste gevallen is er slechts één definitie vereist voor elke controle weergave, maar het is mogelijk om meerdere definities op te geven als u dezelfde weer gave wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="4fb50-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="4fb50-124">In dergelijke gevallen kunt u een afzonderlijke definitie opgeven voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="4fb50-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="4fb50-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4fb50-125">See Also</span></span>

[<span data-ttu-id="4fb50-126">CustomEntries-element voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="4fb50-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4fb50-127">Element weer geven (indeling)</span><span class="sxs-lookup"><span data-stu-id="4fb50-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="4fb50-128">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="4fb50-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
