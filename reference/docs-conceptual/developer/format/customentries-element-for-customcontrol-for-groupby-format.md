---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomEntries voor CustomControl voor GroupBy (opmaak)
description: Het element CustomEntries voor CustomControl voor GroupBy (opmaak)
ms.openlocfilehash: cde59d38b83930cb64a3a0040891783e4ab96723
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666787"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="80b16-103">Het element CustomEntries voor CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80b16-103">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="80b16-104">Bevat de definities voor het besturings element.</span><span class="sxs-lookup"><span data-stu-id="80b16-104">Provides the definitions for the control.</span></span> <span data-ttu-id="80b16-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="80b16-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="80b16-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (indeling) CustomControl-element voor het element GroupBy</span><span class="sxs-lookup"><span data-stu-id="80b16-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="80b16-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="80b16-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80b16-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="80b16-108">Attributes and Elements</span></span>

<span data-ttu-id="80b16-109">In de volgende secties worden kenmerken, onderliggende elementen en bovenliggende elementen van het `CustomEntries` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="80b16-109">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="80b16-110">Er is geen maximum limiet voor het aantal onderliggende elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="80b16-110">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="80b16-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="80b16-111">Attributes</span></span>

<span data-ttu-id="80b16-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="80b16-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="80b16-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="80b16-113">Child Elements</span></span>

|<span data-ttu-id="80b16-114">Element</span><span class="sxs-lookup"><span data-stu-id="80b16-114">Element</span></span>|<span data-ttu-id="80b16-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="80b16-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80b16-116">Het element CustomEntry voor CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80b16-116">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="80b16-117">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="80b16-117">Required element.</span></span><br /><br /> <span data-ttu-id="80b16-118">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="80b16-118">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="80b16-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="80b16-119">Parent Elements</span></span>

|<span data-ttu-id="80b16-120">Element</span><span class="sxs-lookup"><span data-stu-id="80b16-120">Element</span></span>|<span data-ttu-id="80b16-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="80b16-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80b16-122">Het element CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80b16-122">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="80b16-123">Hiermee definieert u het aangepaste besturings element waarin de nieuwe groep wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="80b16-123">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="80b16-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="80b16-124">Remarks</span></span>

<span data-ttu-id="80b16-125">In de meeste gevallen heeft een besturings element slechts één definitie, die in één element is opgegeven `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="80b16-125">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="80b16-126">Het is echter mogelijk om meerdere definities op te geven als u hetzelfde besturings element wilt gebruiken om verschillende groepen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="80b16-126">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="80b16-127">In dergelijke gevallen kunt u een element definiëren `CustomEntry` voor een groep.</span><span class="sxs-lookup"><span data-stu-id="80b16-127">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="80b16-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="80b16-128">See Also</span></span>

[<span data-ttu-id="80b16-129">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80b16-129">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="80b16-130">Het element CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80b16-130">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="80b16-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="80b16-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
