---
title: SelectionSetName-element voor EntrySelectedBy voor EnumerableExpansion (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8745ef9e6f326c3e8a5dbf185a595bbe93e92414
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785316"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="118ca-102">Het element SelectionSetName voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="118ca-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="118ca-103">Hiermee geeft u de set .NET-typen op die door deze definitie worden uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="118ca-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="118ca-104">Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) EntrySelectedBy element voor EnumerableExpansion (Format) SelectionSetName-element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="118ca-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="118ca-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="118ca-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="118ca-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="118ca-106">Attributes and Elements</span></span>

<span data-ttu-id="118ca-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="118ca-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="118ca-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="118ca-108">Attributes</span></span>

<span data-ttu-id="118ca-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="118ca-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="118ca-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="118ca-110">Child Elements</span></span>

<span data-ttu-id="118ca-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="118ca-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="118ca-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="118ca-112">Parent Elements</span></span>

|<span data-ttu-id="118ca-113">Element</span><span class="sxs-lookup"><span data-stu-id="118ca-113">Element</span></span>|<span data-ttu-id="118ca-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="118ca-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="118ca-115">Het element EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="118ca-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="118ca-116">Hiermee definieert u de .NET-verzamelings objecten die door deze definitie worden uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="118ca-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="118ca-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="118ca-117">Text Value</span></span>

<span data-ttu-id="118ca-118">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="118ca-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="118ca-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="118ca-119">Remarks</span></span>

<span data-ttu-id="118ca-120">Elke definitie moet een of meer type namen, een selectieset of een selectie voorwaarde opgeven.</span><span class="sxs-lookup"><span data-stu-id="118ca-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="118ca-121">Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven.</span><span class="sxs-lookup"><span data-stu-id="118ca-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="118ca-122">U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten.</span><span class="sxs-lookup"><span data-stu-id="118ca-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="118ca-123">Zie [sets van objecten voor een weer gave definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="118ca-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="118ca-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="118ca-124">See Also</span></span>

[<span data-ttu-id="118ca-125">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="118ca-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="118ca-126">Het element EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="118ca-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="118ca-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="118ca-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
