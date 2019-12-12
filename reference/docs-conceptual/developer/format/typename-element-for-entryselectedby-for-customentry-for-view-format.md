---
title: TypeName-element voor EntrySelectedBy voor CustomEntry voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358757"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="29d2d-102">Het element TypeName voor EntrySelectedBy voor CustomEntry voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="29d2d-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="29d2d-103">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="29d2d-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="29d2d-104">Er is geen limiet voor het aantal typen dat voor een definitie kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="29d2d-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="29d2d-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (indeling) EntrySelectedBy Element voor CustomEntry voor View (Format) TypeName-element voor EntrySelectedBy voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="29d2d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="29d2d-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="29d2d-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="29d2d-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="29d2d-107">Attributes and Elements</span></span>

<span data-ttu-id="29d2d-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `TypeName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="29d2d-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="29d2d-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="29d2d-109">Attributes</span></span>

<span data-ttu-id="29d2d-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="29d2d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="29d2d-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="29d2d-111">Child Elements</span></span>

<span data-ttu-id="29d2d-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="29d2d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="29d2d-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="29d2d-113">Parent Elements</span></span>

|<span data-ttu-id="29d2d-114">Element</span><span class="sxs-lookup"><span data-stu-id="29d2d-114">Element</span></span>|<span data-ttu-id="29d2d-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="29d2d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="29d2d-116">EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="29d2d-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="29d2d-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste besturings element weergave definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="29d2d-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="29d2d-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="29d2d-118">Text Value</span></span>

<span data-ttu-id="29d2d-119">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="29d2d-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="29d2d-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="29d2d-120">Remarks</span></span>

<span data-ttu-id="29d2d-121">Voor elke aangepaste controle weergave definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="29d2d-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="29d2d-122">Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="29d2d-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="29d2d-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="29d2d-123">See Also</span></span>

[<span data-ttu-id="29d2d-124">Aangepaste besturings elementen maken</span><span class="sxs-lookup"><span data-stu-id="29d2d-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="29d2d-125">EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="29d2d-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="29d2d-126">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="29d2d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
