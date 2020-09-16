---
title: SelectionSetName-element voor SelectionCondition voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c7fdd92475ba24d27e61371d1c6b54fa1a55647c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787509"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="946ff-102">Het element SelectionSetName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="946ff-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="946ff-103">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="946ff-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="946ff-104">Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object met dit besturings element weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="946ff-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="946ff-105">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="946ff-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="946ff-106">Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) EntrySelectedBy element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="946ff-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="946ff-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="946ff-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="946ff-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="946ff-108">Attributes and Elements</span></span>

<span data-ttu-id="946ff-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="946ff-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="946ff-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="946ff-110">Attributes</span></span>

<span data-ttu-id="946ff-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="946ff-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="946ff-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="946ff-112">Child Elements</span></span>

<span data-ttu-id="946ff-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="946ff-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="946ff-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="946ff-114">Parent Elements</span></span>

|<span data-ttu-id="946ff-115">Element</span><span class="sxs-lookup"><span data-stu-id="946ff-115">Element</span></span>|<span data-ttu-id="946ff-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="946ff-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="946ff-117">SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="946ff-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="946ff-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="946ff-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="946ff-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="946ff-119">Text Value</span></span>

<span data-ttu-id="946ff-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="946ff-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="946ff-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="946ff-121">Remarks</span></span>

<span data-ttu-id="946ff-122">Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="946ff-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="946ff-123">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="946ff-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="946ff-124">Met de selectie voorwaarde kan een selectieset of .NET-type worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="946ff-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="946ff-125">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="946ff-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="946ff-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="946ff-126">See Also</span></span>

[<span data-ttu-id="946ff-127">SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="946ff-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="946ff-128">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="946ff-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="946ff-129">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="946ff-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="946ff-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="946ff-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
