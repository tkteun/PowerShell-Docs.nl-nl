---
title: SelectionSetName-Element voor EntrySelectedBy voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847367"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="43a28-102">Het element SelectionSetName voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="43a28-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="43a28-103">Hiermee geeft u een set van .NET-objecten voor de definitie.</span><span class="sxs-lookup"><span data-stu-id="43a28-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="43a28-104">De definitie wordt gebruikt als een van deze objecten wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="43a28-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="43a28-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) EntrySelectedBy Element voor WideEntry (indeling) SelectionSetName-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="43a28-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="43a28-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="43a28-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="43a28-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="43a28-107">Attributes and Elements</span></span>

<span data-ttu-id="43a28-108">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="43a28-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="43a28-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="43a28-109">Attributes</span></span>

<span data-ttu-id="43a28-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="43a28-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="43a28-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="43a28-111">Child Elements</span></span>

<span data-ttu-id="43a28-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="43a28-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="43a28-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="43a28-113">Parent Elements</span></span>

|<span data-ttu-id="43a28-114">Element</span><span class="sxs-lookup"><span data-stu-id="43a28-114">Element</span></span>|<span data-ttu-id="43a28-115">Description</span><span class="sxs-lookup"><span data-stu-id="43a28-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43a28-116">EntrySelectedBy-Element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="43a28-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="43a28-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze vermelding breed of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="43a28-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="43a28-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="43a28-118">Text Value</span></span>

<span data-ttu-id="43a28-119">Geef de naam van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="43a28-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="43a28-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="43a28-120">Remarks</span></span>

<span data-ttu-id="43a28-121">Elke definitie moet een naam, selectie instellen of selectievoorwaarde opgeven.</span><span class="sxs-lookup"><span data-stu-id="43a28-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="43a28-122">Selectiesets worden meestal gebruikt wanneer u wilt definiëren van een groep objecten die worden gebruikt in meerdere weergaven.</span><span class="sxs-lookup"><span data-stu-id="43a28-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="43a28-123">Bijvoorbeeld, als u wilt weergeven als een tabel en een lijst weergeven voor dezelfde set objecten maken.</span><span class="sxs-lookup"><span data-stu-id="43a28-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="43a28-124">Zie voor meer informatie over het definiëren van selectiesets [definiëren ingesteld van objecten voor een weergave](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="43a28-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="43a28-125">Zie voor meer informatie over andere onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="43a28-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="43a28-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="43a28-126">See Also</span></span>

[<span data-ttu-id="43a28-127">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="43a28-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="43a28-128">Selectiesets definiëren</span><span class="sxs-lookup"><span data-stu-id="43a28-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="43a28-129">EntrySelectedBy-Element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="43a28-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="43a28-130">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="43a28-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
