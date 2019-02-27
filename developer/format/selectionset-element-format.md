---
title: SelectionSet-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850419"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="06795-102">Het element SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="06795-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="06795-103">Hiermee definieert een set van .NET-objecten die kan worden verwezen door de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="06795-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="06795-104">Configuratie Element (indeling) SelectionSets-Element (indeling) SelectionSet-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="06795-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="06795-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="06795-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="06795-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="06795-106">Attributes and Elements</span></span>

<span data-ttu-id="06795-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSet` element.</span><span class="sxs-lookup"><span data-stu-id="06795-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="06795-108">Elke selectieset moet een naam hebben en deze de .NET-objecten van de set moet opgeven.</span><span class="sxs-lookup"><span data-stu-id="06795-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="06795-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="06795-109">Attributes</span></span>

<span data-ttu-id="06795-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="06795-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="06795-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="06795-111">Child Elements</span></span>

|<span data-ttu-id="06795-112">Element</span><span class="sxs-lookup"><span data-stu-id="06795-112">Element</span></span>|<span data-ttu-id="06795-113">Description</span><span class="sxs-lookup"><span data-stu-id="06795-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06795-114">De van naamelement voor SelectionSet (indeling)</span><span class="sxs-lookup"><span data-stu-id="06795-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="06795-115">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="06795-115">Required element.</span></span><br /><br /> <span data-ttu-id="06795-116">Hiermee geeft u de naam die wordt gebruikt om te verwijzen naar de selectieset.</span><span class="sxs-lookup"><span data-stu-id="06795-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="06795-117">Typen Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="06795-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="06795-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="06795-118">Required element.</span></span><br /><br /> <span data-ttu-id="06795-119">Hiermee definieert u de .NET-objecten die in de selectie.</span><span class="sxs-lookup"><span data-stu-id="06795-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="06795-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="06795-120">Parent Elements</span></span>

|<span data-ttu-id="06795-121">Element</span><span class="sxs-lookup"><span data-stu-id="06795-121">Element</span></span>|<span data-ttu-id="06795-122">Description</span><span class="sxs-lookup"><span data-stu-id="06795-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06795-123">SelectionSets Element opmaken</span><span class="sxs-lookup"><span data-stu-id="06795-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="06795-124">Hiermee definieert u de algemene sets met .NET-objecten die kunnen worden gebruikt door alle weergaven van de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="06795-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="06795-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="06795-125">Remarks</span></span>

<span data-ttu-id="06795-126">U kunt selectiesets gebruiken wanneer u een set van gerelateerde objecten die u verwijzen wilt met behulp van één naam, zoals een set objecten die via overname verwant zijn hebt.</span><span class="sxs-lookup"><span data-stu-id="06795-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="06795-127">Bij het definiëren van uw weergaven, kunt u de set objecten opgeven met behulp van de naam van de selectie instellen in plaats van de lijst van alle objecten in elke weergave.</span><span class="sxs-lookup"><span data-stu-id="06795-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="06795-128">Algemene selectiesets worden opgegeven door de naam bij het definiëren van de weergaven van de opmaak bestand of de definities van de weergaven.</span><span class="sxs-lookup"><span data-stu-id="06795-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="06795-129">In dergelijke gevallen de `SelectionSetName` onderliggend element van de `ViewSelectedBy` en `EntrySelectedBy` elementen Hiermee geeft u de set moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="06795-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="06795-130">Zie voor meer informatie over selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="06795-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="06795-131">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="06795-131">Example</span></span>

<span data-ttu-id="06795-132">Het volgende voorbeeld wordt een `SelectionSet` element waarin vier .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="06795-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="06795-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="06795-133">See Also</span></span>

[<span data-ttu-id="06795-134">Selectiesets definiëren</span><span class="sxs-lookup"><span data-stu-id="06795-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="06795-135">De van naamelement van SelectionSet (indeling)</span><span class="sxs-lookup"><span data-stu-id="06795-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="06795-136">SelectionSets-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="06795-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="06795-137">Typen Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="06795-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="06795-138">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="06795-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
