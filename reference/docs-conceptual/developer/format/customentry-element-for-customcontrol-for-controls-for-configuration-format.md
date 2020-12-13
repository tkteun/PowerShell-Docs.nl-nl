---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)
description: Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 3967be86a1d6c12c7215ef19d50bac9fafd5ad6d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648284"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="f4301-103">Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f4301-103">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f4301-104">Biedt een definitie van het algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="f4301-104">Provides a definition of the common control.</span></span> <span data-ttu-id="f4301-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="f4301-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f4301-106">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (indeling) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (indeling) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="f4301-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f4301-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="f4301-107">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="f4301-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f4301-108">Attributes and Elements</span></span>

<span data-ttu-id="f4301-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomEntry` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="f4301-109">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="f4301-110">U moet de items opgeven die worden weer gegeven door de definitie.</span><span class="sxs-lookup"><span data-stu-id="f4301-110">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="f4301-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f4301-111">Attributes</span></span>

<span data-ttu-id="f4301-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="f4301-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f4301-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f4301-113">Child Elements</span></span>

|<span data-ttu-id="f4301-114">Element</span><span class="sxs-lookup"><span data-stu-id="f4301-114">Element</span></span>|<span data-ttu-id="f4301-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f4301-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4301-116">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f4301-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="f4301-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f4301-117">Optional element.</span></span><br /><br /> <span data-ttu-id="f4301-118">Definieert de .NET-typen die gebruikmaken van de definitie van het algemene besturings element of de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="f4301-118">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="f4301-119">CustomItem-element voor CustomEntry voor besturings elementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="f4301-119">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="f4301-120">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="f4301-120">Required element.</span></span><br /><br /> <span data-ttu-id="f4301-121">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f4301-121">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f4301-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f4301-122">Parent Elements</span></span>

|<span data-ttu-id="f4301-123">Element</span><span class="sxs-lookup"><span data-stu-id="f4301-123">Element</span></span>|<span data-ttu-id="f4301-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f4301-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4301-125">CustomEntries-element voor CustomControl voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="f4301-125">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="f4301-126">Biedt de definities van het algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="f4301-126">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f4301-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f4301-127">Remarks</span></span>

<span data-ttu-id="f4301-128">In de meeste gevallen is slechts één definitie vereist voor elk algemeen aangepast besturings element, maar het is mogelijk om meerdere definities te hebben als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f4301-128">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="f4301-129">In dergelijke gevallen kunt u een afzonderlijke definitie opgeven voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="f4301-129">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4301-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f4301-130">See Also</span></span>

[<span data-ttu-id="f4301-131">CustomEntries-element voor CustomControl voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="f4301-131">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="f4301-132">CustomItem-element voor CustomEntry voor besturings elementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="f4301-132">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="f4301-133">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="f4301-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
