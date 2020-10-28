---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor EntrySelectedBy voor CustomEntry voor Weergave (opmaak)
description: Het element TypeName voor EntrySelectedBy voor CustomEntry voor Weergave (opmaak)
ms.openlocfilehash: 72bb88bccc2bbd62f7ed160b820cf9169cb69341
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645741"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="81c67-103">Het element TypeName voor EntrySelectedBy voor CustomEntry voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="81c67-103">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="81c67-104">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="81c67-104">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="81c67-105">Er is geen limiet voor het aantal typen dat voor een definitie kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="81c67-105">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="81c67-106">Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) EntrySelectedBy element voor CustomEntry voor weer gave (Format) voor EntrySelectedBy voor CustomEntry</span><span class="sxs-lookup"><span data-stu-id="81c67-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="81c67-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="81c67-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="81c67-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="81c67-108">Attributes and Elements</span></span>

<span data-ttu-id="81c67-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="81c67-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="81c67-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="81c67-110">Attributes</span></span>

<span data-ttu-id="81c67-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="81c67-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="81c67-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="81c67-112">Child Elements</span></span>

<span data-ttu-id="81c67-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="81c67-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="81c67-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="81c67-114">Parent Elements</span></span>

|<span data-ttu-id="81c67-115">Element</span><span class="sxs-lookup"><span data-stu-id="81c67-115">Element</span></span>|<span data-ttu-id="81c67-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="81c67-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="81c67-117">EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="81c67-117">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="81c67-118">Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste besturings element weergave definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="81c67-118">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="81c67-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="81c67-119">Text Value</span></span>

<span data-ttu-id="81c67-120">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="81c67-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="81c67-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="81c67-121">Remarks</span></span>

<span data-ttu-id="81c67-122">Voor elke aangepaste controle weergave definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="81c67-122">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="81c67-123">Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="81c67-123">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="81c67-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="81c67-124">See Also</span></span>

[<span data-ttu-id="81c67-125">Aangepaste besturingselementen maken</span><span class="sxs-lookup"><span data-stu-id="81c67-125">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="81c67-126">EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="81c67-126">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="81c67-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="81c67-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
