---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomEntries voor CustomControl voor Besturingselementen voor Weergave (opmaak)
description: Het element CustomEntries voor CustomControl voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: 43187294a407d08f765f8c42aba25d13dba6d901
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652371"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="e2b11-103">Het element CustomEntries voor CustomControl voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e2b11-103">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="e2b11-104">Bevat de definities voor het besturings element.</span><span class="sxs-lookup"><span data-stu-id="e2b11-104">Provides the definitions for the control.</span></span> <span data-ttu-id="e2b11-105">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="e2b11-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e2b11-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (indeling) Control element (Format) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings element voor besturings elementen voor weer gave (Format) CustomEntries element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e2b11-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e2b11-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e2b11-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2b11-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e2b11-108">Attributes and Elements</span></span>

<span data-ttu-id="e2b11-109">In de volgende secties worden kenmerken, onderliggende elementen en bovenliggende elementen van het `CustomEntries` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="e2b11-109">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="e2b11-110">Er is geen maximum limiet voor het aantal onderliggende elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e2b11-110">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2b11-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e2b11-111">Attributes</span></span>

<span data-ttu-id="e2b11-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="e2b11-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2b11-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e2b11-113">Child Elements</span></span>

|<span data-ttu-id="e2b11-114">Element</span><span class="sxs-lookup"><span data-stu-id="e2b11-114">Element</span></span>|<span data-ttu-id="e2b11-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e2b11-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2b11-116">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e2b11-116">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="e2b11-117">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="e2b11-117">Required element.</span></span><br /><br /> <span data-ttu-id="e2b11-118">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="e2b11-118">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e2b11-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e2b11-119">Parent Elements</span></span>

|<span data-ttu-id="e2b11-120">Element</span><span class="sxs-lookup"><span data-stu-id="e2b11-120">Element</span></span>|<span data-ttu-id="e2b11-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e2b11-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2b11-122">Het element CustomControl voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e2b11-122">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="e2b11-123">Hiermee definieert u het besturings element dat wordt gebruikt door de weer gave.</span><span class="sxs-lookup"><span data-stu-id="e2b11-123">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e2b11-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e2b11-124">Remarks</span></span>

<span data-ttu-id="e2b11-125">In de meeste gevallen heeft een besturings element slechts één definitie, die in één element is opgegeven `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="e2b11-125">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="e2b11-126">Het is echter mogelijk om meerdere definities op te geven als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e2b11-126">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="e2b11-127">In dergelijke gevallen kunt u een element definiëren `CustomEntry` voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="e2b11-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2b11-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e2b11-128">See Also</span></span>

[<span data-ttu-id="e2b11-129">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e2b11-129">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="e2b11-130">Het element CustomControl voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e2b11-130">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="e2b11-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e2b11-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
