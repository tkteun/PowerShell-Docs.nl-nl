---
title: EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 75a0f42e7722b54791a873200a35c8fcbbd665b1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774130"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="448ee-102">Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="448ee-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="448ee-103">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="448ee-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="448ee-104">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="448ee-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="448ee-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor het object CustomControl voor GroupBy (Format) EntrySelectedBy voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="448ee-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="448ee-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="448ee-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="448ee-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="448ee-107">Attributes and Elements</span></span>

<span data-ttu-id="448ee-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="448ee-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="448ee-109">U moet ten minste één type, selectieset of selectie voorwaarde voor een definitie opgeven.</span><span class="sxs-lookup"><span data-stu-id="448ee-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="448ee-110">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="448ee-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="448ee-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="448ee-111">Attributes</span></span>

<span data-ttu-id="448ee-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="448ee-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="448ee-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="448ee-113">Child Elements</span></span>

|<span data-ttu-id="448ee-114">Element</span><span class="sxs-lookup"><span data-stu-id="448ee-114">Element</span></span>|<span data-ttu-id="448ee-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="448ee-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="448ee-116">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="448ee-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="448ee-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="448ee-117">Optional element.</span></span><br /><br /> <span data-ttu-id="448ee-118">Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="448ee-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="448ee-119">Het element SelectionSetName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="448ee-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="448ee-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="448ee-120">Optional element.</span></span><br /><br /> <span data-ttu-id="448ee-121">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="448ee-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="448ee-122">Het element TypeName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="448ee-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="448ee-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="448ee-123">Optional element.</span></span><br /><br /> <span data-ttu-id="448ee-124">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="448ee-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="448ee-125">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="448ee-125">Parent Elements</span></span>

|<span data-ttu-id="448ee-126">Element</span><span class="sxs-lookup"><span data-stu-id="448ee-126">Element</span></span>|<span data-ttu-id="448ee-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="448ee-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="448ee-128">Het element CustomEntry voor CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="448ee-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="448ee-129">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="448ee-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="448ee-130">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="448ee-130">Remarks</span></span>

<span data-ttu-id="448ee-131">Selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of wanneer een specifieke eigenschaps waarde of script wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="448ee-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="448ee-132">Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="448ee-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="448ee-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="448ee-133">See Also</span></span>

[<span data-ttu-id="448ee-134">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="448ee-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="448ee-135">Het element SelectionSetName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="448ee-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="448ee-136">Het element TypeName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="448ee-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="448ee-137">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="448ee-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="448ee-138">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="448ee-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
