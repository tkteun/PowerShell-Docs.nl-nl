---
title: TypeName-element voor EntrySelectedBy voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e62762cf142bd2d20b21ad8f4249285bd3679280
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780262"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="4a370-102">Het element TypeName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4a370-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="4a370-103">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het aangepaste besturings element.</span><span class="sxs-lookup"><span data-stu-id="4a370-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="4a370-104">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4a370-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="4a370-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry-element voor CustomControl voor het element GroupBy (Format) voor CustomEntry voor het object GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4a370-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4a370-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4a370-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4a370-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="4a370-107">Attributes and Elements</span></span>

<span data-ttu-id="4a370-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="4a370-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4a370-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="4a370-109">Attributes</span></span>

<span data-ttu-id="4a370-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="4a370-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4a370-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4a370-111">Child Elements</span></span>

<span data-ttu-id="4a370-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="4a370-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4a370-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4a370-113">Parent Elements</span></span>

|<span data-ttu-id="4a370-114">Element</span><span class="sxs-lookup"><span data-stu-id="4a370-114">Element</span></span>|<span data-ttu-id="4a370-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4a370-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4a370-116">Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4a370-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="4a370-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4a370-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4a370-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="4a370-118">Text Value</span></span>

<span data-ttu-id="4a370-119">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="4a370-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a370-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="4a370-120">Remarks</span></span>

<span data-ttu-id="4a370-121">Voor elke controle definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="4a370-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="4a370-122">Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="4a370-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4a370-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4a370-123">See Also</span></span>

[<span data-ttu-id="4a370-124">Aangepaste besturingselementen maken</span><span class="sxs-lookup"><span data-stu-id="4a370-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="4a370-125">Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4a370-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="4a370-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="4a370-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
