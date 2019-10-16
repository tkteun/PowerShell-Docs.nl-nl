---
title: TypeName-element voor SelectionCondition voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353513"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="7b5c6-102">Het element TypeName voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7b5c6-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="7b5c6-103">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="7b5c6-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="7b5c6-104">Wanneer dit type aanwezig is, wordt de vermelding in de lijst gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7b5c6-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="7b5c6-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling). element (Format) voor ListControl List entry voor ListControl (Format) SelectionCondition-element voor EntrySelectedBy voor ListControl (Format) TypeName-element voor SelectionCondition voor de EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="7b5c6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7b5c6-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7b5c6-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7b5c6-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7b5c6-107">Attributes and Elements</span></span>

<span data-ttu-id="7b5c6-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `TypeName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="7b5c6-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7b5c6-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7b5c6-109">Attributes</span></span>

<span data-ttu-id="7b5c6-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="7b5c6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7b5c6-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7b5c6-111">Child Elements</span></span>

<span data-ttu-id="7b5c6-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="7b5c6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7b5c6-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7b5c6-113">Parent Elements</span></span>

|<span data-ttu-id="7b5c6-114">Element</span><span class="sxs-lookup"><span data-stu-id="7b5c6-114">Element</span></span>|<span data-ttu-id="7b5c6-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7b5c6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b5c6-116">SelectionCondition-element voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="7b5c6-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="7b5c6-117">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze lijst vermelding.</span><span class="sxs-lookup"><span data-stu-id="7b5c6-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7b5c6-118">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="7b5c6-118">Text Value</span></span>

<span data-ttu-id="7b5c6-119">Geef de volledig gekwalificeerde naam van het .NET-type op, bijvoorbeeld `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="7b5c6-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b5c6-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7b5c6-120">Remarks</span></span>

<span data-ttu-id="7b5c6-121">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="7b5c6-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="7b5c6-122">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="7b5c6-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7b5c6-123">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over andere onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="7b5c6-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7b5c6-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7b5c6-124">See Also</span></span>

[<span data-ttu-id="7b5c6-125">Een lijst weergave maken</span><span class="sxs-lookup"><span data-stu-id="7b5c6-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7b5c6-126">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="7b5c6-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7b5c6-127">SelectionCondition-element voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="7b5c6-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="7b5c6-128">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="7b5c6-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
