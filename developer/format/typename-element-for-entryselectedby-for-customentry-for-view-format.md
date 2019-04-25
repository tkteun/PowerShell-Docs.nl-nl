---
title: TypeName-Element voor EntrySelectedBy voor CustomEntry voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083974"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="9a2d3-102">Het element TypeName voor EntrySelectedBy voor CustomEntry voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9a2d3-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="9a2d3-103">Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie van de weergave van het aangepaste besturingselement.</span><span class="sxs-lookup"><span data-stu-id="9a2d3-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="9a2d3-104">Er is geen limiet voor het aantal typen die kunnen worden opgegeven voor een definitie.</span><span class="sxs-lookup"><span data-stu-id="9a2d3-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="9a2d3-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor EntrySelectedBy weergeven (indeling) Element voor CustomEntry voor weergave (indeling) TypeName Element voor EntrySelectedBy voor CustomEntry voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="9a2d3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9a2d3-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="9a2d3-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a2d3-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="9a2d3-107">Attributes and Elements</span></span>

<span data-ttu-id="9a2d3-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="9a2d3-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a2d3-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="9a2d3-109">Attributes</span></span>

<span data-ttu-id="9a2d3-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="9a2d3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9a2d3-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9a2d3-111">Child Elements</span></span>

<span data-ttu-id="9a2d3-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="9a2d3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9a2d3-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9a2d3-113">Parent Elements</span></span>

|<span data-ttu-id="9a2d3-114">Element</span><span class="sxs-lookup"><span data-stu-id="9a2d3-114">Element</span></span>|<span data-ttu-id="9a2d3-115">Description</span><span class="sxs-lookup"><span data-stu-id="9a2d3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9a2d3-116">EntrySelectedBy-Element voor CustomEntry voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="9a2d3-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="9a2d3-117">Definieert de .NET-typen die gebruikmaken van deze definitie van het aangepaste besturingselement weergeven of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9a2d3-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9a2d3-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="9a2d3-118">Text Value</span></span>

<span data-ttu-id="9a2d3-119">Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="9a2d3-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a2d3-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9a2d3-120">Remarks</span></span>

<span data-ttu-id="9a2d3-121">De weergavedefinitie voor elk aangepast besturingselement moet ten minste één naam, selectie instellen of selectievoorwaarde gedefinieerd hebben.</span><span class="sxs-lookup"><span data-stu-id="9a2d3-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="9a2d3-122">Zie voor meer informatie over de onderdelen van de weergave van een aangepast besturingselement [het maken van aangepaste besturingselementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="9a2d3-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9a2d3-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9a2d3-123">See Also</span></span>

[<span data-ttu-id="9a2d3-124">Het maken van aangepaste besturingselementen</span><span class="sxs-lookup"><span data-stu-id="9a2d3-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="9a2d3-125">EntrySelectedBy-Element voor CustomEntry voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="9a2d3-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9a2d3-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a2d3-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
