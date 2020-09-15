---
title: EntrySelectedBy-element voor CustomEntry voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5c82e02d23b1694d05f7a32578ccc5d33686f13f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774249"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="03d39-102">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="03d39-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="03d39-103">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="03d39-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="03d39-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="03d39-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="03d39-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element (indeling) Controls-element (opmaak) Control element (Format) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor de weer gave (Format) CustomEntries-element voor object voor weer gave (Format) voor de weer gave (Format) voor het EntrySelectedBy-element voor Controls (indeling)</span><span class="sxs-lookup"><span data-stu-id="03d39-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="03d39-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="03d39-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="03d39-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="03d39-107">Attributes and Elements</span></span>

<span data-ttu-id="03d39-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="03d39-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="03d39-109">U moet ten minste één type, selectieset of selectie voorwaarde voor een definitie opgeven.</span><span class="sxs-lookup"><span data-stu-id="03d39-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="03d39-110">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="03d39-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="03d39-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="03d39-111">Attributes</span></span>

<span data-ttu-id="03d39-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="03d39-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="03d39-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="03d39-113">Child Elements</span></span>

|<span data-ttu-id="03d39-114">Element</span><span class="sxs-lookup"><span data-stu-id="03d39-114">Element</span></span>|<span data-ttu-id="03d39-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="03d39-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="03d39-116">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="03d39-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="03d39-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="03d39-117">Optional element.</span></span><br /><br /> <span data-ttu-id="03d39-118">Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="03d39-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="03d39-119">Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="03d39-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="03d39-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="03d39-120">Optional element.</span></span><br /><br /> <span data-ttu-id="03d39-121">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="03d39-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="03d39-122">Het element TypeName voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="03d39-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="03d39-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="03d39-123">Optional element.</span></span><br /><br /> <span data-ttu-id="03d39-124">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="03d39-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="03d39-125">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="03d39-125">Parent Elements</span></span>

|<span data-ttu-id="03d39-126">Element</span><span class="sxs-lookup"><span data-stu-id="03d39-126">Element</span></span>|<span data-ttu-id="03d39-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="03d39-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="03d39-128">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="03d39-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="03d39-129">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="03d39-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="03d39-130">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="03d39-130">Remarks</span></span>

<span data-ttu-id="03d39-131">Selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of wanneer een specifieke eigenschaps waarde of script wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="03d39-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="03d39-132">Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="03d39-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="03d39-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="03d39-133">See Also</span></span>

[<span data-ttu-id="03d39-134">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="03d39-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="03d39-135">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="03d39-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
