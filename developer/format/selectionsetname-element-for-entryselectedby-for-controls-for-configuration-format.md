---
title: SelectionSetName-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063970"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="4435c-102">Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4435c-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="4435c-103">Hiermee geeft u een set van .NET-typen die gebruikmaken van deze definitie van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="4435c-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="4435c-104">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="4435c-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="4435c-105">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) EntrySelectedBy-Element voor CustomEntry controles voor configuratie (-indeling) SelectionSetName-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="4435c-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4435c-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="4435c-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4435c-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="4435c-107">Attributes and Elements</span></span>

<span data-ttu-id="4435c-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="4435c-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4435c-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="4435c-109">Attributes</span></span>

<span data-ttu-id="4435c-110">Geen</span><span class="sxs-lookup"><span data-stu-id="4435c-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="4435c-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4435c-111">Child Elements</span></span>

<span data-ttu-id="4435c-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="4435c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4435c-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4435c-113">Parent Elements</span></span>

|<span data-ttu-id="4435c-114">Element</span><span class="sxs-lookup"><span data-stu-id="4435c-114">Element</span></span>|<span data-ttu-id="4435c-115">Description</span><span class="sxs-lookup"><span data-stu-id="4435c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4435c-116">EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="4435c-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="4435c-117">Hiermee definieert u de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4435c-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4435c-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="4435c-118">Text Value</span></span>

<span data-ttu-id="4435c-119">Geef de naam van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="4435c-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="4435c-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="4435c-120">Remarks</span></span>

<span data-ttu-id="4435c-121">De besturingselementdefinitie van elk moet ten minste één naam, selectie instellen of selectievoorwaarde gedefinieerd hebben.</span><span class="sxs-lookup"><span data-stu-id="4435c-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="4435c-122">Selectiesets worden meestal gebruikt wanneer u wilt definiëren van een groep objecten die worden gebruikt in meerdere weergaven.</span><span class="sxs-lookup"><span data-stu-id="4435c-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="4435c-123">Zie voor meer informatie over het definiëren van selectiesets [definiëren voor de selectie wordt ingesteld](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="4435c-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4435c-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4435c-124">See Also</span></span>

[<span data-ttu-id="4435c-125">EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="4435c-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="4435c-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="4435c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
