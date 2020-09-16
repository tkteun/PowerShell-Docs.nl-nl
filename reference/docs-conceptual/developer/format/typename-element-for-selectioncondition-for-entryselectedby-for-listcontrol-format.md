---
title: TypeName-element voor SelectionCondition voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bc58d630e65b316f9223bf3c529f928358e38ebc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787372"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="21b75-102">Het element TypeName voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="21b75-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="21b75-103">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="21b75-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="21b75-104">Wanneer dit type aanwezig is, wordt de vermelding in de lijst gebruikt.</span><span class="sxs-lookup"><span data-stu-id="21b75-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="21b75-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het object (indeling) ListControl element (indeling) (Format) element list item voor ListControl (indeling) element List entry voor List Entries (Format) EntrySelectedBy element voor List entry voor ListControl (Format) SelectionCondition-element voor het object voor de ListControl (Format) voor de SelectionCondition voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="21b75-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="21b75-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="21b75-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="21b75-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="21b75-107">Attributes and Elements</span></span>

<span data-ttu-id="21b75-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="21b75-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="21b75-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="21b75-109">Attributes</span></span>

<span data-ttu-id="21b75-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="21b75-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="21b75-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="21b75-111">Child Elements</span></span>

<span data-ttu-id="21b75-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="21b75-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="21b75-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="21b75-113">Parent Elements</span></span>

|<span data-ttu-id="21b75-114">Element</span><span class="sxs-lookup"><span data-stu-id="21b75-114">Element</span></span>|<span data-ttu-id="21b75-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="21b75-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="21b75-116">Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="21b75-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="21b75-117">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze lijst vermelding.</span><span class="sxs-lookup"><span data-stu-id="21b75-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="21b75-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="21b75-118">Text Value</span></span>

<span data-ttu-id="21b75-119">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="21b75-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="21b75-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="21b75-120">Remarks</span></span>

<span data-ttu-id="21b75-121">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="21b75-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="21b75-122">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="21b75-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="21b75-123">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over andere onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="21b75-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="21b75-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="21b75-124">See Also</span></span>

[<span data-ttu-id="21b75-125">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="21b75-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="21b75-126">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="21b75-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="21b75-127">Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="21b75-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="21b75-128">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="21b75-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
