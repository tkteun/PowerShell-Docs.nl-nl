---
title: CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355256"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="e05fd-102">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e05fd-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="e05fd-103">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="e05fd-103">Provides a definition of the control.</span></span> <span data-ttu-id="e05fd-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="e05fd-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e05fd-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor View (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e05fd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e05fd-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e05fd-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e05fd-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e05fd-107">Attributes and Elements</span></span>

<span data-ttu-id="e05fd-108">In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het element `CustomEntry` beschreven.</span><span class="sxs-lookup"><span data-stu-id="e05fd-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e05fd-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e05fd-109">Attributes</span></span>

<span data-ttu-id="e05fd-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="e05fd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e05fd-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e05fd-111">Child Elements</span></span>

|<span data-ttu-id="e05fd-112">Element</span><span class="sxs-lookup"><span data-stu-id="e05fd-112">Element</span></span>|<span data-ttu-id="e05fd-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e05fd-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e05fd-114">EntrySelectedBy-element voor CustomEntry voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e05fd-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="e05fd-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e05fd-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e05fd-116">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e05fd-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="e05fd-117">CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e05fd-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="e05fd-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="e05fd-118">Required element.</span></span><br /><br /> <span data-ttu-id="e05fd-119">Hiermee wordt gedefinieerd hoe de gegevens worden weer gegeven in het besturings element.</span><span class="sxs-lookup"><span data-stu-id="e05fd-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e05fd-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e05fd-120">Parent Elements</span></span>

|<span data-ttu-id="e05fd-121">Element</span><span class="sxs-lookup"><span data-stu-id="e05fd-121">Element</span></span>|<span data-ttu-id="e05fd-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e05fd-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e05fd-123">CustomEntries-element voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e05fd-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="e05fd-124">Bevat de definities voor het besturings element.</span><span class="sxs-lookup"><span data-stu-id="e05fd-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e05fd-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e05fd-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e05fd-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e05fd-126">See Also</span></span>

[<span data-ttu-id="e05fd-127">CustomEntries-element voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="e05fd-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e05fd-128">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e05fd-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
