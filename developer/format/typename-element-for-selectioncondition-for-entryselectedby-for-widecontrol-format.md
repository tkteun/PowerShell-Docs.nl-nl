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
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055974"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="f70de-102">Het element TypeName voor SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f70de-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="f70de-103">Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="f70de-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="f70de-104">Wanneer dit type aanwezig is, wordt de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f70de-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="f70de-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) EntrySelectedBy Element voor WideEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling) TypeName Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="f70de-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f70de-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f70de-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f70de-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f70de-107">Attributes and Elements</span></span>

<span data-ttu-id="f70de-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="f70de-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f70de-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f70de-109">Attributes</span></span>

<span data-ttu-id="f70de-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="f70de-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f70de-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f70de-111">Child Elements</span></span>

<span data-ttu-id="f70de-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="f70de-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f70de-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f70de-113">Parent Elements</span></span>

|<span data-ttu-id="f70de-114">Element</span><span class="sxs-lookup"><span data-stu-id="f70de-114">Element</span></span>|<span data-ttu-id="f70de-115">Description</span><span class="sxs-lookup"><span data-stu-id="f70de-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f70de-116">SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="f70de-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="f70de-117">Hiermee definieert u de voorwaarde die moet bestaan voor deze breed vermelding moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f70de-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f70de-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="f70de-118">Text Value</span></span>

<span data-ttu-id="f70de-119">Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="f70de-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="f70de-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f70de-120">Remarks</span></span>

<span data-ttu-id="f70de-121">De selectievoorwaarde een .NET-type kunt opgeven of een selectie instellen, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="f70de-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="f70de-122">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f70de-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f70de-123">Zie voor meer informatie over andere onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f70de-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f70de-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f70de-124">See Also</span></span>

[<span data-ttu-id="f70de-125">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="f70de-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f70de-126">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="f70de-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f70de-127">SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="f70de-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f70de-128">SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="f70de-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="f70de-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="f70de-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
