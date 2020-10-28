---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor EntrySelectedBy voor GroupBy (opmaak)
description: Het element TypeName voor EntrySelectedBy voor GroupBy (opmaak)
ms.openlocfilehash: 07cc92e9c501aa0eb2d219e416851be0fcd80f47
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645714"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="2b857-103">Het element TypeName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2b857-103">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="2b857-104">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het aangepaste besturings element.</span><span class="sxs-lookup"><span data-stu-id="2b857-104">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="2b857-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2b857-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="2b857-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry-element voor CustomControl voor het element GroupBy (Format) voor CustomEntry voor het object GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2b857-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b857-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="2b857-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b857-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="2b857-108">Attributes and Elements</span></span>

<span data-ttu-id="2b857-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="2b857-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b857-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2b857-110">Attributes</span></span>

<span data-ttu-id="2b857-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="2b857-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2b857-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2b857-112">Child Elements</span></span>

<span data-ttu-id="2b857-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="2b857-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2b857-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2b857-114">Parent Elements</span></span>

|<span data-ttu-id="2b857-115">Element</span><span class="sxs-lookup"><span data-stu-id="2b857-115">Element</span></span>|<span data-ttu-id="2b857-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2b857-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b857-117">Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2b857-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="2b857-118">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2b857-118">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2b857-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="2b857-119">Text Value</span></span>

<span data-ttu-id="2b857-120">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="2b857-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b857-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2b857-121">Remarks</span></span>

<span data-ttu-id="2b857-122">Voor elke controle definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="2b857-122">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="2b857-123">Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="2b857-123">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b857-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2b857-124">See Also</span></span>

[<span data-ttu-id="2b857-125">Aangepaste besturingselementen maken</span><span class="sxs-lookup"><span data-stu-id="2b857-125">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="2b857-126">Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2b857-126">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="2b857-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="2b857-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
