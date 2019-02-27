---
title: TypeName-Element voor SelectionCondition voor EntrySelectedBy voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 0d7bbfd8be3bf2bd1af75a45ca4db016dfb6bff6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848179"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="f9a65-102">Het element TypeName voor SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f9a65-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="f9a65-103">Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="f9a65-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="f9a65-104">Wanneer dit type aanwezig is, wordt de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f9a65-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="f9a65-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) EntrySelectedBy Element voor WideEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling) TypeName Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="f9a65-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f9a65-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f9a65-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f9a65-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f9a65-107">Attributes and Elements</span></span>

<span data-ttu-id="f9a65-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="f9a65-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f9a65-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f9a65-109">Attributes</span></span>

<span data-ttu-id="f9a65-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="f9a65-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f9a65-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f9a65-111">Child Elements</span></span>

<span data-ttu-id="f9a65-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="f9a65-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f9a65-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f9a65-113">Parent Elements</span></span>

|<span data-ttu-id="f9a65-114">Element</span><span class="sxs-lookup"><span data-stu-id="f9a65-114">Element</span></span>|<span data-ttu-id="f9a65-115">Description</span><span class="sxs-lookup"><span data-stu-id="f9a65-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f9a65-116">SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="f9a65-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="f9a65-117">Hiermee definieert u de voorwaarde die moet bestaan voor deze breed vermelding moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f9a65-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f9a65-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="f9a65-118">Text Value</span></span>

<span data-ttu-id="f9a65-119">Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="f9a65-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="f9a65-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f9a65-120">Remarks</span></span>

<span data-ttu-id="f9a65-121">De selectievoorwaarde een .NET-type kunt opgeven of een selectie instellen, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="f9a65-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="f9a65-122">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f9a65-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f9a65-123">Zie voor meer informatie over andere onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f9a65-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f9a65-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f9a65-124">See Also</span></span>

[<span data-ttu-id="f9a65-125">Een brede weergave opgelost</span><span class="sxs-lookup"><span data-stu-id="f9a65-125">Creatng a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f9a65-126">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="f9a65-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f9a65-127">SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="f9a65-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f9a65-128">SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="f9a65-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="f9a65-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="f9a65-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
