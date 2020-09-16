---
title: CustomEntry-element voor CustomControl voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8b9d18bbb1abce8135f4c27418ad54a1736eb5a6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785928"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="69a57-102">Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="69a57-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="69a57-103">Biedt een definitie van het algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="69a57-103">Provides a definition of the common control.</span></span> <span data-ttu-id="69a57-104">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="69a57-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="69a57-105">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (indeling) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (indeling) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="69a57-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="69a57-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="69a57-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="69a57-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="69a57-107">Attributes and Elements</span></span>

<span data-ttu-id="69a57-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomEntry` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="69a57-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="69a57-109">U moet de items opgeven die worden weer gegeven door de definitie.</span><span class="sxs-lookup"><span data-stu-id="69a57-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="69a57-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="69a57-110">Attributes</span></span>

<span data-ttu-id="69a57-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="69a57-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="69a57-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="69a57-112">Child Elements</span></span>

|<span data-ttu-id="69a57-113">Element</span><span class="sxs-lookup"><span data-stu-id="69a57-113">Element</span></span>|<span data-ttu-id="69a57-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="69a57-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="69a57-115">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="69a57-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="69a57-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="69a57-116">Optional element.</span></span><br /><br /> <span data-ttu-id="69a57-117">Definieert de .NET-typen die gebruikmaken van de definitie van het algemene besturings element of de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="69a57-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="69a57-118">CustomItem-element voor CustomEntry voor besturings elementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="69a57-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="69a57-119">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="69a57-119">Required element.</span></span><br /><br /> <span data-ttu-id="69a57-120">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="69a57-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="69a57-121">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="69a57-121">Parent Elements</span></span>

|<span data-ttu-id="69a57-122">Element</span><span class="sxs-lookup"><span data-stu-id="69a57-122">Element</span></span>|<span data-ttu-id="69a57-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="69a57-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="69a57-124">CustomEntries-element voor CustomControl voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="69a57-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="69a57-125">Biedt de definities van het algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="69a57-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="69a57-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="69a57-126">Remarks</span></span>

<span data-ttu-id="69a57-127">In de meeste gevallen is slechts één definitie vereist voor elk algemeen aangepast besturings element, maar het is mogelijk om meerdere definities te hebben als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="69a57-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="69a57-128">In dergelijke gevallen kunt u een afzonderlijke definitie opgeven voor elk object of set met objecten.</span><span class="sxs-lookup"><span data-stu-id="69a57-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="69a57-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="69a57-129">See Also</span></span>

[<span data-ttu-id="69a57-130">CustomEntries-element voor CustomControl voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="69a57-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="69a57-131">CustomItem-element voor CustomEntry voor besturings elementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="69a57-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="69a57-132">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="69a57-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
