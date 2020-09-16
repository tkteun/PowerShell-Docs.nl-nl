---
title: CustomControl-element voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 660e8fd6531862790a2af7ab27a82e073c230693
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786047"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="85220-102">Het element CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="85220-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="85220-103">Hiermee wordt een aangepaste besturings element-indeling gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="85220-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="85220-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="85220-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="85220-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="85220-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="85220-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="85220-106">Attributes and Elements</span></span>

<span data-ttu-id="85220-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomControl` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="85220-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="85220-108">U moet één onderliggend element opgeven.</span><span class="sxs-lookup"><span data-stu-id="85220-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="85220-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="85220-109">Attributes</span></span>

<span data-ttu-id="85220-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="85220-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="85220-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="85220-111">Child Elements</span></span>

|<span data-ttu-id="85220-112">Element</span><span class="sxs-lookup"><span data-stu-id="85220-112">Element</span></span>|<span data-ttu-id="85220-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="85220-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="85220-114">Het element CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="85220-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="85220-115">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="85220-115">Required element.</span></span><br /><br /> <span data-ttu-id="85220-116">Biedt de definities van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="85220-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="85220-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="85220-117">Parent Elements</span></span>

|<span data-ttu-id="85220-118">Element</span><span class="sxs-lookup"><span data-stu-id="85220-118">Element</span></span>|<span data-ttu-id="85220-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="85220-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="85220-120">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="85220-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="85220-121">Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om een of meer .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="85220-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="85220-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="85220-122">Remarks</span></span>

<span data-ttu-id="85220-123">In de meeste gevallen is er slechts één definitie vereist voor elke controle weergave, maar het is mogelijk om meerdere definities op te geven als u dezelfde weer gave wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="85220-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="85220-124">In dergelijke gevallen kunt u een afzonderlijke definitie opgeven voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="85220-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="85220-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="85220-125">See Also</span></span>

[<span data-ttu-id="85220-126">Het element CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="85220-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="85220-127">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="85220-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="85220-128">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="85220-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
