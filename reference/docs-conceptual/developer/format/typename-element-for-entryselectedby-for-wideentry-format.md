---
title: TypeName-element voor EntrySelectedBy voor WideEntry (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353555"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="b1262-102">Het element TypeName voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b1262-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="b1262-103">Hiermee geeft u een .NET-type voor de definitie op.</span><span class="sxs-lookup"><span data-stu-id="b1262-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="b1262-104">De definitie wordt gebruikt wanneer dit object wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b1262-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="b1262-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) element-TypeName voor WideEntry ( Formatteer</span><span class="sxs-lookup"><span data-stu-id="b1262-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b1262-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b1262-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b1262-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b1262-107">Attributes and Elements</span></span>

<span data-ttu-id="b1262-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `TypeName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="b1262-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b1262-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b1262-109">Attributes</span></span>

<span data-ttu-id="b1262-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="b1262-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b1262-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b1262-111">Child Elements</span></span>

<span data-ttu-id="b1262-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="b1262-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b1262-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b1262-113">Parent Elements</span></span>

|<span data-ttu-id="b1262-114">Element</span><span class="sxs-lookup"><span data-stu-id="b1262-114">Element</span></span>|<span data-ttu-id="b1262-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b1262-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1262-116">EntrySelectedBy-element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="b1262-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="b1262-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze brede vermelding of de voor waarde die moet bestaan voor deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="b1262-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b1262-118">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="b1262-118">Text Value</span></span>

<span data-ttu-id="b1262-119">Geef de volledig gekwalificeerde naam van het .NET-type op, bijvoorbeeld `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="b1262-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="b1262-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b1262-120">Remarks</span></span>

<span data-ttu-id="b1262-121">Elke uitgebreide vermelding moet een of meer .NET-typen, een selectieset of de selectie voorwaarde opgeven die moet bestaan voor de definitie die u wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b1262-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="b1262-122">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="b1262-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b1262-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b1262-123">See Also</span></span>

[<span data-ttu-id="b1262-124">Een brede weer gave maken</span><span class="sxs-lookup"><span data-stu-id="b1262-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b1262-125">EntrySelectedBy-element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="b1262-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="b1262-126">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b1262-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
