---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomEntries voor CustomControl voor Besturingselementen voor Configuratie (opmaak)
description: Het element CustomEntries voor CustomControl voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 86c2b517d0d7075a355a3190a14e25d9dd4fe374
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655405"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="c5838-103">Het element CustomEntries voor CustomControl voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c5838-103">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="c5838-104">Biedt de definities van een gemeen schappelijk besturings element.</span><span class="sxs-lookup"><span data-stu-id="c5838-104">Provides the definitions of a common control.</span></span> <span data-ttu-id="c5838-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="c5838-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="c5838-106">Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor CustomControl voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="c5838-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c5838-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="c5838-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c5838-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c5838-108">Attributes and Elements</span></span>

<span data-ttu-id="c5838-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomEntries` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="c5838-109">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="c5838-110">U moet een of meer onderliggende elementen opgeven.</span><span class="sxs-lookup"><span data-stu-id="c5838-110">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c5838-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c5838-111">Attributes</span></span>

<span data-ttu-id="c5838-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="c5838-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c5838-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c5838-113">Child Elements</span></span>

|<span data-ttu-id="c5838-114">Element</span><span class="sxs-lookup"><span data-stu-id="c5838-114">Element</span></span>|<span data-ttu-id="c5838-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c5838-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c5838-116">Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c5838-116">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="c5838-117">Biedt een definitie van het algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="c5838-117">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c5838-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c5838-118">Parent Elements</span></span>

|<span data-ttu-id="c5838-119">Element</span><span class="sxs-lookup"><span data-stu-id="c5838-119">Element</span></span>|<span data-ttu-id="c5838-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c5838-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c5838-121">CustomControl-element voor besturings element voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="c5838-121">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="c5838-122">Hiermee definieert u een algemeen besturings element.</span><span class="sxs-lookup"><span data-stu-id="c5838-122">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c5838-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c5838-123">Remarks</span></span>

<span data-ttu-id="c5838-124">In de meeste gevallen heeft een besturings element slechts één definitie, die in één element is gedefinieerd `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="c5838-124">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="c5838-125">Het is echter mogelijk om meerdere definities te hebben als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c5838-125">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="c5838-126">In dergelijke gevallen kunt u een element definiëren `CustomEntry` voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="c5838-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5838-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c5838-127">See Also</span></span>

[<span data-ttu-id="c5838-128">CustomControl-element voor besturings element voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="c5838-128">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="c5838-129">Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c5838-129">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="c5838-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c5838-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
