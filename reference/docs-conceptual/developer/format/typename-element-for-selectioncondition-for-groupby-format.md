---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor SelectionCondition voor GroupBy (opmaak)
description: Het element TypeName voor SelectionCondition voor GroupBy (opmaak)
ms.openlocfilehash: 096d2355e113a7e44cc6ae31ea23efc3f01080a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664639"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="c9274-103">Het element TypeName voor SelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c9274-103">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="c9274-104">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="c9274-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="c9274-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c9274-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c9274-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) voor SelectionCondition voor GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c9274-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c9274-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="c9274-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9274-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c9274-108">Attributes and Elements</span></span>

<span data-ttu-id="c9274-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="c9274-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9274-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c9274-110">Attributes</span></span>

<span data-ttu-id="c9274-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="c9274-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c9274-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c9274-112">Child Elements</span></span>

<span data-ttu-id="c9274-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="c9274-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c9274-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c9274-114">Parent Elements</span></span>

|<span data-ttu-id="c9274-115">Element</span><span class="sxs-lookup"><span data-stu-id="c9274-115">Element</span></span>|<span data-ttu-id="c9274-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c9274-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9274-117">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c9274-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="c9274-118">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="c9274-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c9274-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="c9274-119">Text Value</span></span>

<span data-ttu-id="c9274-120">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="c9274-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9274-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c9274-121">Remarks</span></span>

<span data-ttu-id="c9274-122">Als dit element is opgegeven, kunt u het element niet opgeven `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="c9274-122">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="c9274-123">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het definiëren van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="c9274-123">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c9274-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c9274-124">See Also</span></span>

[<span data-ttu-id="c9274-125">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c9274-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="c9274-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c9274-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
