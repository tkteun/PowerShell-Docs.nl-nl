---
title: Naam van Element voor SelectionSet (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065149"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="07d6e-102">Het element Naam voor SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="07d6e-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="07d6e-103">Hiermee geeft u de naam die wordt gebruikt om te verwijzen naar de selectieset.</span><span class="sxs-lookup"><span data-stu-id="07d6e-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="07d6e-104">Configuratie-Element (indeling) SelectionSets-Element (indeling) SelectionSet-Element (indeling) de naam van Element van SelectionSet (indeling)</span><span class="sxs-lookup"><span data-stu-id="07d6e-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="07d6e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="07d6e-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="07d6e-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="07d6e-106">Attributes and Elements</span></span>

<span data-ttu-id="07d6e-107">De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `Name` Element.</span><span class="sxs-lookup"><span data-stu-id="07d6e-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="07d6e-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="07d6e-108">Attributes</span></span>

<span data-ttu-id="07d6e-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="07d6e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="07d6e-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="07d6e-110">Child Elements</span></span>

<span data-ttu-id="07d6e-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="07d6e-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="07d6e-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="07d6e-112">Parent Elements</span></span>

|<span data-ttu-id="07d6e-113">Element</span><span class="sxs-lookup"><span data-stu-id="07d6e-113">Element</span></span>|<span data-ttu-id="07d6e-114">Description</span><span class="sxs-lookup"><span data-stu-id="07d6e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07d6e-115">SelectionSet-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="07d6e-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="07d6e-116">Definieert één set met .NET-objecten die kan worden verwezen door de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="07d6e-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="07d6e-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="07d6e-117">Text Value</span></span>

<span data-ttu-id="07d6e-118">Geef de naam om te verwijzen naar de selectieset.</span><span class="sxs-lookup"><span data-stu-id="07d6e-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="07d6e-119">Er zijn geen beperkingen voor welke tekens kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="07d6e-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="07d6e-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="07d6e-120">Remarks</span></span>

<span data-ttu-id="07d6e-121">De naam die u hier opgeeft, wordt gebruikt in de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="07d6e-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="07d6e-122">De van selectieset die door een weergave kan worden gebruikt door een definitie van een weergave (weergaven kunnen meerdere definities hebben), of wanneer een selectievoorwaarde op te geven.</span><span class="sxs-lookup"><span data-stu-id="07d6e-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="07d6e-123">Zie voor meer informatie over selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="07d6e-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="07d6e-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="07d6e-124">Example</span></span>

<span data-ttu-id="07d6e-125">In dit voorbeeld ziet u een `SelectionSet` element waarin vier .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="07d6e-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="07d6e-126">De naam van de selectieset is 'FileSystemTypes'.</span><span class="sxs-lookup"><span data-stu-id="07d6e-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="07d6e-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="07d6e-127">See Also</span></span>

[<span data-ttu-id="07d6e-128">Selectiesets definiëren</span><span class="sxs-lookup"><span data-stu-id="07d6e-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="07d6e-129">SelectionSet-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="07d6e-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="07d6e-130">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="07d6e-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
