---
title: CustomEntries-element voor CustomControl voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359042"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="8349e-102">Het element CustomEntries voor CustomControl voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8349e-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="8349e-103">Biedt de definities van een gemeen schappelijk besturings element.</span><span class="sxs-lookup"><span data-stu-id="8349e-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="8349e-104">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="8349e-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="8349e-105">Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het configureren van een configuratie ( Formatteer</span><span class="sxs-lookup"><span data-stu-id="8349e-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8349e-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="8349e-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="8349e-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="8349e-107">Attributes and Elements</span></span>

<span data-ttu-id="8349e-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomEntries` beschreven.</span><span class="sxs-lookup"><span data-stu-id="8349e-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="8349e-109">U moet een of meer onderliggende elementen opgeven.</span><span class="sxs-lookup"><span data-stu-id="8349e-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8349e-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="8349e-110">Attributes</span></span>

<span data-ttu-id="8349e-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="8349e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8349e-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8349e-112">Child Elements</span></span>

|<span data-ttu-id="8349e-113">Element</span><span class="sxs-lookup"><span data-stu-id="8349e-113">Element</span></span>|<span data-ttu-id="8349e-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8349e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8349e-115">CustomEntry-element voor CustomControl voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="8349e-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="8349e-116">Biedt een definitie van het algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="8349e-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8349e-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8349e-117">Parent Elements</span></span>

|<span data-ttu-id="8349e-118">Element</span><span class="sxs-lookup"><span data-stu-id="8349e-118">Element</span></span>|<span data-ttu-id="8349e-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8349e-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8349e-120">CustomControl-element voor besturings element voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="8349e-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="8349e-121">Hiermee definieert u een algemeen besturings element.</span><span class="sxs-lookup"><span data-stu-id="8349e-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8349e-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="8349e-122">Remarks</span></span>

<span data-ttu-id="8349e-123">In de meeste gevallen heeft een besturings element slechts één definitie, die is gedefinieerd in één `CustomEntry`-element.</span><span class="sxs-lookup"><span data-stu-id="8349e-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="8349e-124">Het is echter mogelijk om meerdere definities te hebben als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="8349e-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="8349e-125">In dergelijke gevallen kunt u een `CustomEntry`-element definiëren voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="8349e-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="8349e-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8349e-126">See Also</span></span>

[<span data-ttu-id="8349e-127">CustomControl-element voor besturings element voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="8349e-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="8349e-128">CustomEntry-element voor CustomControl voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="8349e-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="8349e-129">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="8349e-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
