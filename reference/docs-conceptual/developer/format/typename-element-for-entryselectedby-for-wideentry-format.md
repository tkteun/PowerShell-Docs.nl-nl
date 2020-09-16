---
title: TypeName-element voor EntrySelectedBy voor WideEntry (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9af443067467f590df824b28636f57b807a4fc94
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780182"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="31415-102">Het element TypeName voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="31415-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="31415-103">Hiermee geeft u een .NET-type voor de definitie op.</span><span class="sxs-lookup"><span data-stu-id="31415-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="31415-104">De definitie wordt gebruikt wanneer dit object wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="31415-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="31415-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (indeling) element-TypeName voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="31415-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="31415-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="31415-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="31415-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="31415-107">Attributes and Elements</span></span>

<span data-ttu-id="31415-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="31415-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="31415-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="31415-109">Attributes</span></span>

<span data-ttu-id="31415-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="31415-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="31415-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="31415-111">Child Elements</span></span>

<span data-ttu-id="31415-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="31415-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="31415-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="31415-113">Parent Elements</span></span>

|<span data-ttu-id="31415-114">Element</span><span class="sxs-lookup"><span data-stu-id="31415-114">Element</span></span>|<span data-ttu-id="31415-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="31415-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="31415-116">Het element EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="31415-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="31415-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze brede vermelding of de voor waarde die moet bestaan voor deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="31415-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="31415-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="31415-118">Text Value</span></span>

<span data-ttu-id="31415-119">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="31415-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="31415-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="31415-120">Remarks</span></span>

<span data-ttu-id="31415-121">Elke uitgebreide vermelding moet een of meer .NET-typen, een selectieset of de selectie voorwaarde opgeven die moet bestaan voor de definitie die u wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="31415-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="31415-122">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="31415-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="31415-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="31415-123">See Also</span></span>

[<span data-ttu-id="31415-124">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="31415-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="31415-125">Het element EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="31415-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="31415-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="31415-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
