---
title: CustomEntries-element voor CustomControl voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a52bd2368044c34a0b73da331785d55597e30260
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783701"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="5a2b6-102">Het element CustomEntries voor CustomControl voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5a2b6-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="5a2b6-103">Bevat de definities voor het besturings element.</span><span class="sxs-lookup"><span data-stu-id="5a2b6-103">Provides the definitions for the control.</span></span> <span data-ttu-id="5a2b6-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="5a2b6-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="5a2b6-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (indeling) Control element (Format) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings element voor besturings elementen voor weer gave (Format) CustomEntries element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5a2b6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5a2b6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5a2b6-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5a2b6-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="5a2b6-107">Attributes and Elements</span></span>

<span data-ttu-id="5a2b6-108">In de volgende secties worden kenmerken, onderliggende elementen en bovenliggende elementen van het `CustomEntries` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="5a2b6-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="5a2b6-109">Er is geen maximum limiet voor het aantal onderliggende elementen dat kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="5a2b6-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="5a2b6-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="5a2b6-110">Attributes</span></span>

<span data-ttu-id="5a2b6-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="5a2b6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5a2b6-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5a2b6-112">Child Elements</span></span>

|<span data-ttu-id="5a2b6-113">Element</span><span class="sxs-lookup"><span data-stu-id="5a2b6-113">Element</span></span>|<span data-ttu-id="5a2b6-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5a2b6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5a2b6-115">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5a2b6-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="5a2b6-116">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="5a2b6-116">Required element.</span></span><br /><br /> <span data-ttu-id="5a2b6-117">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="5a2b6-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5a2b6-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5a2b6-118">Parent Elements</span></span>

|<span data-ttu-id="5a2b6-119">Element</span><span class="sxs-lookup"><span data-stu-id="5a2b6-119">Element</span></span>|<span data-ttu-id="5a2b6-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5a2b6-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5a2b6-121">Het element CustomControl voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5a2b6-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="5a2b6-122">Hiermee definieert u het besturings element dat wordt gebruikt door de weer gave.</span><span class="sxs-lookup"><span data-stu-id="5a2b6-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5a2b6-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5a2b6-123">Remarks</span></span>

<span data-ttu-id="5a2b6-124">In de meeste gevallen heeft een besturings element slechts één definitie, die in één element is opgegeven `CustomEntry` .</span><span class="sxs-lookup"><span data-stu-id="5a2b6-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="5a2b6-125">Het is echter mogelijk om meerdere definities op te geven als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5a2b6-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="5a2b6-126">In dergelijke gevallen kunt u een element definiëren `CustomEntry` voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="5a2b6-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a2b6-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5a2b6-127">See Also</span></span>

[<span data-ttu-id="5a2b6-128">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5a2b6-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="5a2b6-129">Het element CustomControl voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5a2b6-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="5a2b6-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="5a2b6-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
