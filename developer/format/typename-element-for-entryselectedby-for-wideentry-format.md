---
title: TypeName-Element voor EntrySelectedBy voor WideEntry (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083923"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="bdf7b-102">Het element TypeName voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="bdf7b-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="bdf7b-103">Hiermee geeft u een .NET-type voor de definitie.</span><span class="sxs-lookup"><span data-stu-id="bdf7b-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="bdf7b-104">De definitie wordt gebruikt wanneer dit object wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bdf7b-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="bdf7b-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) EntrySelectedBy Element voor WideEntry (indeling) TypeName-Element voor WideEntry ( -Indeling)</span><span class="sxs-lookup"><span data-stu-id="bdf7b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bdf7b-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="bdf7b-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bdf7b-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="bdf7b-107">Attributes and Elements</span></span>

<span data-ttu-id="bdf7b-108">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="bdf7b-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bdf7b-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="bdf7b-109">Attributes</span></span>

<span data-ttu-id="bdf7b-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="bdf7b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bdf7b-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="bdf7b-111">Child Elements</span></span>

<span data-ttu-id="bdf7b-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="bdf7b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bdf7b-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="bdf7b-113">Parent Elements</span></span>

|<span data-ttu-id="bdf7b-114">Element</span><span class="sxs-lookup"><span data-stu-id="bdf7b-114">Element</span></span>|<span data-ttu-id="bdf7b-115">Description</span><span class="sxs-lookup"><span data-stu-id="bdf7b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bdf7b-116">EntrySelectedBy-Element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="bdf7b-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="bdf7b-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze vermelding breed of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bdf7b-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bdf7b-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="bdf7b-118">Text Value</span></span>

<span data-ttu-id="bdf7b-119">Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="bdf7b-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="bdf7b-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="bdf7b-120">Remarks</span></span>

<span data-ttu-id="bdf7b-121">Elk item wide moet opgeven voor een of meer .NET-typen, een selectie instellen of de selectievoorwaarde moet bestaan voor de definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bdf7b-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="bdf7b-122">Zie voor meer informatie over andere onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="bdf7b-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bdf7b-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bdf7b-123">See Also</span></span>

[<span data-ttu-id="bdf7b-124">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="bdf7b-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="bdf7b-125">EntrySelectedBy-Element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="bdf7b-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="bdf7b-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="bdf7b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
