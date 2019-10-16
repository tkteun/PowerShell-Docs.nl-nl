---
title: CustomEntries-element voor CustomControl voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355284"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="4b1b5-102">Het element CustomEntries voor CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4b1b5-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="4b1b5-103">Bevat de definities voor het besturings element.</span><span class="sxs-lookup"><span data-stu-id="4b1b5-103">Provides the definitions for the control.</span></span> <span data-ttu-id="4b1b5-104">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4b1b5-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="4b1b5-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (indeling) CustomControl-element voor het element GroupBy</span><span class="sxs-lookup"><span data-stu-id="4b1b5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4b1b5-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="4b1b5-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4b1b5-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="4b1b5-107">Attributes and Elements</span></span>

<span data-ttu-id="4b1b5-108">In de volgende secties worden kenmerken, onderliggende elementen en bovenliggende elementen van het element `CustomEntries` beschreven.</span><span class="sxs-lookup"><span data-stu-id="4b1b5-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="4b1b5-109">Er is geen maximum limiet voor het aantal onderliggende elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="4b1b5-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="4b1b5-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="4b1b5-110">Attributes</span></span>

<span data-ttu-id="4b1b5-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="4b1b5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4b1b5-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4b1b5-112">Child Elements</span></span>

|<span data-ttu-id="4b1b5-113">Element</span><span class="sxs-lookup"><span data-stu-id="4b1b5-113">Element</span></span>|<span data-ttu-id="4b1b5-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4b1b5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b1b5-115">CustomEntry-element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="4b1b5-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="4b1b5-116">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="4b1b5-116">Required element.</span></span><br /><br /> <span data-ttu-id="4b1b5-117">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="4b1b5-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4b1b5-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4b1b5-118">Parent Elements</span></span>

|<span data-ttu-id="4b1b5-119">Element</span><span class="sxs-lookup"><span data-stu-id="4b1b5-119">Element</span></span>|<span data-ttu-id="4b1b5-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4b1b5-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b1b5-121">CustomControl-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="4b1b5-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="4b1b5-122">Hiermee definieert u het aangepaste besturings element waarin de nieuwe groep wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4b1b5-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4b1b5-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="4b1b5-123">Remarks</span></span>

<span data-ttu-id="4b1b5-124">In de meeste gevallen heeft een besturings element slechts één definitie, die is opgegeven in één `CustomEntry`-element.</span><span class="sxs-lookup"><span data-stu-id="4b1b5-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="4b1b5-125">Het is echter mogelijk om meerdere definities op te geven als u hetzelfde besturings element wilt gebruiken om verschillende groepen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="4b1b5-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="4b1b5-126">In dergelijke gevallen kunt u een `CustomEntry`-element definiëren voor een groep.</span><span class="sxs-lookup"><span data-stu-id="4b1b5-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b1b5-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4b1b5-127">See Also</span></span>

[<span data-ttu-id="4b1b5-128">CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="4b1b5-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="4b1b5-129">CustomControl-element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="4b1b5-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="4b1b5-130">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="4b1b5-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
