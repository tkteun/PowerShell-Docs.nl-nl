---
title: CustomEntry-Element voor CustomControl voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849474"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="d902a-102">Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d902a-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d902a-103">Bevat een definitie van de algemene besturingselementen.</span><span class="sxs-lookup"><span data-stu-id="d902a-103">Provides a definition of the common control.</span></span> <span data-ttu-id="d902a-104">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="d902a-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d902a-105">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="d902a-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d902a-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d902a-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d902a-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d902a-107">Attributes and Elements</span></span>

<span data-ttu-id="d902a-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="d902a-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="d902a-109">U moet de items worden weergegeven door de definitie opgeven.</span><span class="sxs-lookup"><span data-stu-id="d902a-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="d902a-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d902a-110">Attributes</span></span>

<span data-ttu-id="d902a-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="d902a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d902a-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d902a-112">Child Elements</span></span>

|<span data-ttu-id="d902a-113">Element</span><span class="sxs-lookup"><span data-stu-id="d902a-113">Element</span></span>|<span data-ttu-id="d902a-114">Description</span><span class="sxs-lookup"><span data-stu-id="d902a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d902a-115">EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="d902a-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="d902a-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d902a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="d902a-117">Hiermee definieert u de .NET-typen die gebruikmaken van de definitie van de algemene controle of de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d902a-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="d902a-118">CustomItem-Element voor CustomEntry voor besturingselementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="d902a-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="d902a-119">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="d902a-119">Required element.</span></span><br /><br /> <span data-ttu-id="d902a-120">Bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="d902a-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d902a-121">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d902a-121">Parent Elements</span></span>

|<span data-ttu-id="d902a-122">Element</span><span class="sxs-lookup"><span data-stu-id="d902a-122">Element</span></span>|<span data-ttu-id="d902a-123">Description</span><span class="sxs-lookup"><span data-stu-id="d902a-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d902a-124">CustomEntries-Element voor CustomControl voor configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="d902a-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="d902a-125">Bevat de definities van de algemene besturingselementen.</span><span class="sxs-lookup"><span data-stu-id="d902a-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d902a-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d902a-126">Remarks</span></span>

<span data-ttu-id="d902a-127">In de meeste gevallen slechts één definitie is vereist voor elke algemene aangepast besturingselement, maar het is mogelijk dat meerdere definities als u wilt de hetzelfde besturingselement gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="d902a-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="d902a-128">In deze gevallen kunt u de definitie van een afzonderlijke voor elk object of een set van objecten opgeven.</span><span class="sxs-lookup"><span data-stu-id="d902a-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="d902a-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d902a-129">See Also</span></span>

[<span data-ttu-id="d902a-130">CustomEntries-Element voor CustomControl voor configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="d902a-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="d902a-131">CustomItem-Element voor CustomEntry voor besturingselementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="d902a-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="d902a-132">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="d902a-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
