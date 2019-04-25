---
title: SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064132"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="9e360-102">Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9e360-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="9e360-103">De voorwaarde die moet aanwezig zijn om uit te breiden, de verzameling objecten van deze definitie wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="9e360-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="9e360-104">Configuratie van Element (indeling) DefaultSettings-Element (indeling) EnumerableExpansions-Element (indeling) EnumerableExpansion-Element (indeling) EntrySelectedBy Element voor EnumerableExpansion (indeling) SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="9e360-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9e360-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="9e360-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9e360-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="9e360-106">Attributes and Elements</span></span>

<span data-ttu-id="9e360-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="9e360-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="9e360-108">U moet een enkel `PropertyName` of `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="9e360-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="9e360-109">De `SelectionSetName` en `TypeName` elementen zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="9e360-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="9e360-110">U kunt een van beide element opgeven.</span><span class="sxs-lookup"><span data-stu-id="9e360-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9e360-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="9e360-111">Attributes</span></span>

<span data-ttu-id="9e360-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="9e360-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9e360-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9e360-113">Child Elements</span></span>

|<span data-ttu-id="9e360-114">Element</span><span class="sxs-lookup"><span data-stu-id="9e360-114">Element</span></span>|<span data-ttu-id="9e360-115">Description</span><span class="sxs-lookup"><span data-stu-id="9e360-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9e360-116">PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="9e360-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="9e360-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="9e360-117">Optional element.</span></span><br /><br /> <span data-ttu-id="9e360-118">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="9e360-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="9e360-119">ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="9e360-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="9e360-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="9e360-120">Optional element.</span></span><br /><br /> <span data-ttu-id="9e360-121">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="9e360-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="9e360-122">SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="9e360-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="9e360-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="9e360-123">Optional element.</span></span><br /><br /> <span data-ttu-id="9e360-124">Hiermee geeft u de set van .NET-typen die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="9e360-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="9e360-125">TypeName-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="9e360-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="9e360-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="9e360-126">Optional element.</span></span><br /><br /> <span data-ttu-id="9e360-127">Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="9e360-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9e360-128">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9e360-128">Parent Elements</span></span>

|<span data-ttu-id="9e360-129">Element</span><span class="sxs-lookup"><span data-stu-id="9e360-129">Element</span></span>|<span data-ttu-id="9e360-130">Description</span><span class="sxs-lookup"><span data-stu-id="9e360-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9e360-131">EntrySelectedBy-Element voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="9e360-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="9e360-132">Hiermee definieert u welke .NET verzameling objecten worden uitgebreid door deze definitie.</span><span class="sxs-lookup"><span data-stu-id="9e360-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9e360-133">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9e360-133">Remarks</span></span>

<span data-ttu-id="9e360-134">Elke definitie moet hebben ten minste één naam, selectie instellen of selectievoorwaarde gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="9e360-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="9e360-135">Wanneer u een selectievoorwaarde definieert, wordt de volgende vereisten gelden:</span><span class="sxs-lookup"><span data-stu-id="9e360-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="9e360-136">De selectievoorwaarde moet de naam van een minimaal één eigenschap of een scriptblok opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="9e360-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="9e360-137">De selectievoorwaarde een willekeurig aantal .NET-typen kunt opgeven of de selectie wordt ingesteld, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="9e360-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="9e360-138">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [voorwaarden definiëren voor Diplaying gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9e360-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9e360-139">Zie voor meer informatie over andere onderdelen van een brede weergave [brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="9e360-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9e360-140">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9e360-140">See Also</span></span>

[<span data-ttu-id="9e360-141">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="9e360-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9e360-142">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="9e360-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
