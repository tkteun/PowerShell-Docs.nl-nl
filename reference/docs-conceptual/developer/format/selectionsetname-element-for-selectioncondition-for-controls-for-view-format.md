---
title: SelectionSetName-element voor SelectionCondition voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0feb23f860487952344680f75ee674e9e0e6dcc6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787526"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="41944-102">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="41944-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="41944-103">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="41944-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="41944-104">Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object met dit besturings element weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="41944-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="41944-105">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="41944-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="41944-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (indeling) Control element (Format) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings elementen voor het element Control (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor de weer gave (Format) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de weer gave (Format) SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor de weer gave (indeling) SelectionSetName element voor SelectionCondition voor besturings elementen</span><span class="sxs-lookup"><span data-stu-id="41944-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="41944-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="41944-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="41944-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="41944-108">Attributes and Elements</span></span>

<span data-ttu-id="41944-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="41944-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="41944-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="41944-110">Attributes</span></span>

<span data-ttu-id="41944-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="41944-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="41944-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="41944-112">Child Elements</span></span>

<span data-ttu-id="41944-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="41944-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="41944-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="41944-114">Parent Elements</span></span>

|<span data-ttu-id="41944-115">Element</span><span class="sxs-lookup"><span data-stu-id="41944-115">Element</span></span>|<span data-ttu-id="41944-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="41944-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41944-117">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="41944-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="41944-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="41944-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="41944-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="41944-119">Text Value</span></span>

<span data-ttu-id="41944-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="41944-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="41944-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="41944-121">Remarks</span></span>

<span data-ttu-id="41944-122">Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="41944-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="41944-123">Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="41944-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="41944-124">Met de selectie voorwaarde kan een selectieset of .NET-type worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="41944-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="41944-125">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="41944-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="41944-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="41944-126">See Also</span></span>

[<span data-ttu-id="41944-127">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="41944-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="41944-128">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="41944-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="41944-129">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="41944-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="41944-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="41944-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
