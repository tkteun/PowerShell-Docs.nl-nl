---
title: Selectionset-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358871"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="ff2ba-102">Het element SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ff2ba-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="ff2ba-103">Hiermee wordt een set .NET-objecten gedefinieerd waarnaar kan worden verwezen door de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="ff2ba-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="ff2ba-104">Configuratie-element (indeling) SelectionSets element (indeling) element verzameling (indeling)</span><span class="sxs-lookup"><span data-stu-id="ff2ba-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ff2ba-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ff2ba-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ff2ba-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ff2ba-106">Attributes and Elements</span></span>

<span data-ttu-id="ff2ba-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionSet` beschreven.</span><span class="sxs-lookup"><span data-stu-id="ff2ba-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="ff2ba-108">Elke selectie reeks moet een naam hebben en moet de .NET-objecten van de set opgeven.</span><span class="sxs-lookup"><span data-stu-id="ff2ba-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="ff2ba-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ff2ba-109">Attributes</span></span>

<span data-ttu-id="ff2ba-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="ff2ba-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ff2ba-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ff2ba-111">Child Elements</span></span>

|<span data-ttu-id="ff2ba-112">Element</span><span class="sxs-lookup"><span data-stu-id="ff2ba-112">Element</span></span>|<span data-ttu-id="ff2ba-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ff2ba-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff2ba-114">Naam element voor Selectieset (indeling)</span><span class="sxs-lookup"><span data-stu-id="ff2ba-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="ff2ba-115">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="ff2ba-115">Required element.</span></span><br /><br /> <span data-ttu-id="ff2ba-116">Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar de selectieset.</span><span class="sxs-lookup"><span data-stu-id="ff2ba-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="ff2ba-117">Type-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="ff2ba-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="ff2ba-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="ff2ba-118">Required element.</span></span><br /><br /> <span data-ttu-id="ff2ba-119">Hiermee definieert u de .NET-objecten die zich in de selectieset bevinden.</span><span class="sxs-lookup"><span data-stu-id="ff2ba-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ff2ba-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ff2ba-120">Parent Elements</span></span>

|<span data-ttu-id="ff2ba-121">Element</span><span class="sxs-lookup"><span data-stu-id="ff2ba-121">Element</span></span>|<span data-ttu-id="ff2ba-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ff2ba-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff2ba-123">SelectionSets element indeling</span><span class="sxs-lookup"><span data-stu-id="ff2ba-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="ff2ba-124">Hiermee worden de algemene sets van .NET-objecten gedefinieerd die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="ff2ba-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ff2ba-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ff2ba-125">Remarks</span></span>

<span data-ttu-id="ff2ba-126">U kunt selectie sets gebruiken wanneer u een set verwante objecten hebt waarnaar u wilt verwijzen met behulp van één naam, zoals een set objecten die zijn gerelateerd aan overname.</span><span class="sxs-lookup"><span data-stu-id="ff2ba-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="ff2ba-127">Wanneer u uw weer gaven definieert, kunt u de set met objecten opgeven door de naam van de selectieset te gebruiken in plaats van alle objecten in elke weer gave te vermelden.</span><span class="sxs-lookup"><span data-stu-id="ff2ba-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="ff2ba-128">Algemene selectie sets worden opgegeven met hun naam bij het definiëren van de weer gaven van het opmaak bestand of de definities van de weer gaven.</span><span class="sxs-lookup"><span data-stu-id="ff2ba-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="ff2ba-129">In dergelijke gevallen wordt in het onderliggende `SelectionSetName`-element van de `ViewSelectedBy`-en `EntrySelectedBy`-elementen de set opgegeven die moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ff2ba-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="ff2ba-130">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.</span><span class="sxs-lookup"><span data-stu-id="ff2ba-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="ff2ba-131">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ff2ba-131">Example</span></span>

<span data-ttu-id="ff2ba-132">In het volgende voor beeld ziet u een `SelectionSet`-element dat vier .NET-typen definieert.</span><span class="sxs-lookup"><span data-stu-id="ff2ba-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ff2ba-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ff2ba-133">See Also</span></span>

[<span data-ttu-id="ff2ba-134">Selectie sets definiëren</span><span class="sxs-lookup"><span data-stu-id="ff2ba-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="ff2ba-135">Element naam van de Selectieset (indeling)</span><span class="sxs-lookup"><span data-stu-id="ff2ba-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="ff2ba-136">SelectionSets-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="ff2ba-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="ff2ba-137">Type-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="ff2ba-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="ff2ba-138">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="ff2ba-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
