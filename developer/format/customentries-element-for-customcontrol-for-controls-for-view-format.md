---
title: CustomEntries-Element voor CustomControl voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850874"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="ff841-102">Het element CustomEntries voor CustomControl voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ff841-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="ff841-103">Bevat de definities voor het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="ff841-103">Provides the definitions for the control.</span></span> <span data-ttu-id="ff841-104">Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.</span><span class="sxs-lookup"><span data-stu-id="ff841-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="ff841-105">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ff841-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ff841-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ff841-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ff841-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ff841-107">Attributes and Elements</span></span>

<span data-ttu-id="ff841-108">De volgende secties beschrijven kenmerken, elementen van de onderliggende en bovenliggende elementen van de `CustomEntries` element.</span><span class="sxs-lookup"><span data-stu-id="ff841-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="ff841-109">Er is geen maximale limiet voor het aantal onderliggende elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ff841-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="ff841-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ff841-110">Attributes</span></span>

<span data-ttu-id="ff841-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="ff841-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ff841-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ff841-112">Child Elements</span></span>

|<span data-ttu-id="ff841-113">Element</span><span class="sxs-lookup"><span data-stu-id="ff841-113">Element</span></span>|<span data-ttu-id="ff841-114">Description</span><span class="sxs-lookup"><span data-stu-id="ff841-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff841-115">CustomEntry-Element voor CustomEntries voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ff841-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="ff841-116">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="ff841-116">Required element.</span></span><br /><br /> <span data-ttu-id="ff841-117">Bevat een definitie van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="ff841-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ff841-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ff841-118">Parent Elements</span></span>

|<span data-ttu-id="ff841-119">Element</span><span class="sxs-lookup"><span data-stu-id="ff841-119">Element</span></span>|<span data-ttu-id="ff841-120">Description</span><span class="sxs-lookup"><span data-stu-id="ff841-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff841-121">CustomControl-Element voor het besturingselement voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ff841-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="ff841-122">Hiermee definieert u het besturingselement wordt gebruikt door de weergave.</span><span class="sxs-lookup"><span data-stu-id="ff841-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ff841-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ff841-123">Remarks</span></span>

<span data-ttu-id="ff841-124">In de meeste gevallen een besturingselement heeft slechts één definitie die is opgegeven in een enkel `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="ff841-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="ff841-125">Het is echter mogelijk om meerdere definities als u wilt de hetzelfde besturingselement gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="ff841-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="ff841-126">In deze gevallen kunt u een `CustomEntry` -element voor elk object of een set van objecten.</span><span class="sxs-lookup"><span data-stu-id="ff841-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff841-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ff841-127">See Also</span></span>

[<span data-ttu-id="ff841-128">CustomEntry-Element voor CustomEntries voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ff841-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="ff841-129">CustomControl-Element voor het besturingselement voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ff841-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="ff841-130">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff841-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
