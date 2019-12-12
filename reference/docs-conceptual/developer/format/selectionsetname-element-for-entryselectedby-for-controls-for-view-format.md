---
title: SelectionSetName-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358866"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="b9f6a-102">Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b9f6a-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="b9f6a-103">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="b9f6a-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="b9f6a-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="b9f6a-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b9f6a-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor besturings elementen voor weer gave (indeling) CustomEntry element voor CustomEntries voor besturings elementen voor de weer gave (Format) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de weer gave (Format) SelectionSetName-element voor EntrySelectedBy for Controls ( Formatteer</span><span class="sxs-lookup"><span data-stu-id="b9f6a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b9f6a-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b9f6a-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b9f6a-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b9f6a-107">Attributes and Elements</span></span>

<span data-ttu-id="b9f6a-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionSetName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="b9f6a-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b9f6a-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b9f6a-109">Attributes</span></span>

<span data-ttu-id="b9f6a-110">Geen</span><span class="sxs-lookup"><span data-stu-id="b9f6a-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="b9f6a-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b9f6a-111">Child Elements</span></span>

<span data-ttu-id="b9f6a-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="b9f6a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b9f6a-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b9f6a-113">Parent Elements</span></span>

|<span data-ttu-id="b9f6a-114">Element</span><span class="sxs-lookup"><span data-stu-id="b9f6a-114">Element</span></span>|<span data-ttu-id="b9f6a-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b9f6a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9f6a-116">EntrySelectedBy-element voor CustomEntry voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="b9f6a-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="b9f6a-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b9f6a-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b9f6a-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="b9f6a-118">Text Value</span></span>

<span data-ttu-id="b9f6a-119">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="b9f6a-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9f6a-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b9f6a-120">Remarks</span></span>

<span data-ttu-id="b9f6a-121">Voor elke controle definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b9f6a-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="b9f6a-122">Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven.</span><span class="sxs-lookup"><span data-stu-id="b9f6a-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="b9f6a-123">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="b9f6a-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b9f6a-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b9f6a-124">See Also</span></span>

[<span data-ttu-id="b9f6a-125">EntrySelectedBy-element voor CustomEntry voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="b9f6a-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="b9f6a-126">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b9f6a-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
