---
title: CustomEntries-element voor CustomControl voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b1f494cf1a254d71362830ba9eb0f4905a2a484d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785979"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="a31ae-102">Het element CustomEntries voor CustomControl voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a31ae-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a31ae-103">Biedt de definities van een gemeen schappelijk besturings element.</span><span class="sxs-lookup"><span data-stu-id="a31ae-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="a31ae-104">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="a31ae-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a31ae-105">Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor CustomControl voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="a31ae-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a31ae-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a31ae-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a31ae-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a31ae-107">Attributes and Elements</span></span>

<span data-ttu-id="a31ae-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomEntries` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="a31ae-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="a31ae-109">U moet een of meer onderliggende elementen opgeven.</span><span class="sxs-lookup"><span data-stu-id="a31ae-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a31ae-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a31ae-110">Attributes</span></span>

<span data-ttu-id="a31ae-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="a31ae-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a31ae-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a31ae-112">Child Elements</span></span>

|<span data-ttu-id="a31ae-113">Element</span><span class="sxs-lookup"><span data-stu-id="a31ae-113">Element</span></span>|<span data-ttu-id="a31ae-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a31ae-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a31ae-115">Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a31ae-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="a31ae-116">Biedt een definitie van het algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="a31ae-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a31ae-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a31ae-117">Parent Elements</span></span>

|<span data-ttu-id="a31ae-118">Element</span><span class="sxs-lookup"><span data-stu-id="a31ae-118">Element</span></span>|<span data-ttu-id="a31ae-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a31ae-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a31ae-120">CustomControl-element voor besturings element voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="a31ae-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="a31ae-121">Hiermee definieert u een algemeen besturings element.</span><span class="sxs-lookup"><span data-stu-id="a31ae-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a31ae-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a31ae-122">Remarks</span></span>

<span data-ttu-id="a31ae-123">In de meeste gevallen heeft een besturings element slechts één definitie, die in één element is gedefinieerd `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="a31ae-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="a31ae-124">Het is echter mogelijk om meerdere definities te hebben als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a31ae-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="a31ae-125">In dergelijke gevallen kunt u een element definiëren `CustomEntry` voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="a31ae-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="a31ae-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a31ae-126">See Also</span></span>

[<span data-ttu-id="a31ae-127">CustomControl-element voor besturings element voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="a31ae-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="a31ae-128">Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a31ae-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="a31ae-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="a31ae-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
