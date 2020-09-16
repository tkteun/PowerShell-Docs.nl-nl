---
title: CustomEntries-element voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c89eb25f6922a92e2c18298d0128c4c2ca93df3d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785962"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="5eb15-102">Het element CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5eb15-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="5eb15-103">Biedt de definities van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="5eb15-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="5eb15-104">In de aangepaste beheer weergave moeten een of meer definities worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="5eb15-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="5eb15-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer gave (indeling) CustomControl element (indeling) CustomEntries element voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5eb15-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5eb15-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5eb15-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5eb15-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="5eb15-107">Attributes and Elements</span></span>

<span data-ttu-id="5eb15-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomControlEntries` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="5eb15-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="5eb15-109">U moet een of meer onderliggende elementen opgeven.</span><span class="sxs-lookup"><span data-stu-id="5eb15-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5eb15-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="5eb15-110">Attributes</span></span>

<span data-ttu-id="5eb15-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="5eb15-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5eb15-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5eb15-112">Child Elements</span></span>

|<span data-ttu-id="5eb15-113">Element</span><span class="sxs-lookup"><span data-stu-id="5eb15-113">Element</span></span>|<span data-ttu-id="5eb15-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5eb15-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5eb15-115">CustomEntry-element voor CustomEntries voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5eb15-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="5eb15-116">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="5eb15-116">Required element.</span></span><br /><br /> <span data-ttu-id="5eb15-117">Biedt een definitie van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="5eb15-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5eb15-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5eb15-118">Parent Elements</span></span>

|<span data-ttu-id="5eb15-119">Element</span><span class="sxs-lookup"><span data-stu-id="5eb15-119">Element</span></span>|<span data-ttu-id="5eb15-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5eb15-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5eb15-121">Het element CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5eb15-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="5eb15-122">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="5eb15-122">Required element.</span></span><br /><br /> <span data-ttu-id="5eb15-123">Hiermee wordt een aangepaste besturings element-indeling gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="5eb15-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5eb15-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5eb15-124">Remarks</span></span>

<span data-ttu-id="5eb15-125">In de meeste gevallen heeft een besturings element slechts één definitie, die in één element is gedefinieerd `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="5eb15-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="5eb15-126">Het is echter mogelijk om meerdere definities te hebben als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5eb15-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="5eb15-127">In dergelijke gevallen kunt u een element definiëren `CustomEntry` voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="5eb15-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="5eb15-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5eb15-128">See Also</span></span>

[<span data-ttu-id="5eb15-129">Het element CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5eb15-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="5eb15-130">CustomEntry-element voor CustomEntries voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5eb15-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5eb15-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="5eb15-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
