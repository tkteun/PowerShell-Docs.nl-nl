---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor EntrySelectedBy voor WideEntry (opmaak)
description: Het element TypeName voor EntrySelectedBy voor WideEntry (opmaak)
ms.openlocfilehash: 2e0facd6ff7c6fec96dabf488449a8502429bcff
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654781"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="91b15-103">Het element TypeName voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="91b15-103">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="91b15-104">Hiermee geeft u een .NET-type voor de definitie op.</span><span class="sxs-lookup"><span data-stu-id="91b15-104">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="91b15-105">De definitie wordt gebruikt wanneer dit object wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="91b15-105">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="91b15-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (indeling) element-TypeName voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="91b15-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="91b15-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="91b15-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="91b15-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="91b15-108">Attributes and Elements</span></span>

<span data-ttu-id="91b15-109">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="91b15-109">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="91b15-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="91b15-110">Attributes</span></span>

<span data-ttu-id="91b15-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="91b15-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="91b15-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="91b15-112">Child Elements</span></span>

<span data-ttu-id="91b15-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="91b15-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="91b15-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="91b15-114">Parent Elements</span></span>

|<span data-ttu-id="91b15-115">Element</span><span class="sxs-lookup"><span data-stu-id="91b15-115">Element</span></span>|<span data-ttu-id="91b15-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="91b15-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="91b15-117">Het element EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="91b15-117">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="91b15-118">Hiermee definieert u de .NET-typen die gebruikmaken van deze brede vermelding of de voor waarde die moet bestaan voor deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="91b15-118">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="91b15-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="91b15-119">Text Value</span></span>

<span data-ttu-id="91b15-120">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="91b15-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="91b15-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="91b15-121">Remarks</span></span>

<span data-ttu-id="91b15-122">Elke uitgebreide vermelding moet een of meer .NET-typen, een selectieset of de selectie voorwaarde opgeven die moet bestaan voor de definitie die u wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="91b15-122">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="91b15-123">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="91b15-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="91b15-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="91b15-124">See Also</span></span>

[<span data-ttu-id="91b15-125">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="91b15-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="91b15-126">Het element EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="91b15-126">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="91b15-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="91b15-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
