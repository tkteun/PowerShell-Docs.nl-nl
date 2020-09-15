---
title: Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ca2106dbbd8da345e71e83a3ead3cf7a1cb44cb4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773110"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="7408b-102">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7408b-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="7408b-103">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="7408b-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="7408b-104">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7408b-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="7408b-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionCondition element voor EntrySelectedBy voor WideEntry (Format) voor SelectionCondition voor EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7408b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7408b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7408b-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="7408b-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7408b-107">Attributes and Elements</span></span>

<span data-ttu-id="7408b-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="7408b-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7408b-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7408b-109">Attributes</span></span>

<span data-ttu-id="7408b-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="7408b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7408b-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7408b-111">Child Elements</span></span>

<span data-ttu-id="7408b-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="7408b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7408b-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7408b-113">Parent Elements</span></span>

|<span data-ttu-id="7408b-114">Element</span><span class="sxs-lookup"><span data-stu-id="7408b-114">Element</span></span>|<span data-ttu-id="7408b-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7408b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7408b-116">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="7408b-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="7408b-117">Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7408b-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7408b-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="7408b-118">Text Value</span></span>

<span data-ttu-id="7408b-119">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="7408b-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="7408b-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7408b-120">Remarks</span></span>

<span data-ttu-id="7408b-121">Voor de selectie voorwaarde moet ten minste één eigenschaps naam of een script worden opgegeven om te evalueren, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="7408b-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="7408b-122">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="7408b-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7408b-123">Zie [brede weer gave](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="7408b-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7408b-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7408b-124">See Also</span></span>

[<span data-ttu-id="7408b-125">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="7408b-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7408b-126">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="7408b-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7408b-127">Script block-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="7408b-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7408b-128">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="7408b-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7408b-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="7408b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
