---
title: SelectionSetName-element voor EntrySelectedBy voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353807"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="fcb78-102">Het element SelectionSetName voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fcb78-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="fcb78-103">Hiermee geeft u een set .NET-objecten voor de definitie op.</span><span class="sxs-lookup"><span data-stu-id="fcb78-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="fcb78-104">De definitie wordt gebruikt wanneer een van deze objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fcb78-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="fcb78-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionSetName-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="fcb78-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fcb78-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="fcb78-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="fcb78-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="fcb78-107">Attributes and Elements</span></span>

<span data-ttu-id="fcb78-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionSetName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="fcb78-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fcb78-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="fcb78-109">Attributes</span></span>

<span data-ttu-id="fcb78-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="fcb78-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fcb78-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fcb78-111">Child Elements</span></span>

<span data-ttu-id="fcb78-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="fcb78-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fcb78-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fcb78-113">Parent Elements</span></span>

|<span data-ttu-id="fcb78-114">Element</span><span class="sxs-lookup"><span data-stu-id="fcb78-114">Element</span></span>|<span data-ttu-id="fcb78-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fcb78-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fcb78-116">EntrySelectedBy-element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="fcb78-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="fcb78-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze brede vermelding of de voor waarde die moet bestaan voor deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="fcb78-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fcb78-118">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="fcb78-118">Text Value</span></span>

<span data-ttu-id="fcb78-119">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="fcb78-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="fcb78-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="fcb78-120">Remarks</span></span>

<span data-ttu-id="fcb78-121">Elke definitie moet een type naam, selectieset of selectie voorwaarde opgeven.</span><span class="sxs-lookup"><span data-stu-id="fcb78-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="fcb78-122">Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven.</span><span class="sxs-lookup"><span data-stu-id="fcb78-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="fcb78-123">U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten.</span><span class="sxs-lookup"><span data-stu-id="fcb78-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="fcb78-124">Zie [sets van objecten voor een weer gave definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="fcb78-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="fcb78-125">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="fcb78-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fcb78-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fcb78-126">See Also</span></span>

[<span data-ttu-id="fcb78-127">Een brede weer gave maken</span><span class="sxs-lookup"><span data-stu-id="fcb78-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="fcb78-128">Selectie sets definiëren</span><span class="sxs-lookup"><span data-stu-id="fcb78-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="fcb78-129">EntrySelectedBy-element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="fcb78-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="fcb78-130">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="fcb78-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
