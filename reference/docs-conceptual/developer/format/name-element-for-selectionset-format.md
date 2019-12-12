---
title: Naam element voor Selectieset (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354290"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="7dfb5-102">Het element Naam voor SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7dfb5-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="7dfb5-103">Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar de selectieset.</span><span class="sxs-lookup"><span data-stu-id="7dfb5-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="7dfb5-104">Configuratie-element (indeling) SelectionSets element (Format) element van de verzameling (indeling) naam element van de Selectieset (indeling)</span><span class="sxs-lookup"><span data-stu-id="7dfb5-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7dfb5-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7dfb5-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7dfb5-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7dfb5-106">Attributes and Elements</span></span>

<span data-ttu-id="7dfb5-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Name` beschreven.</span><span class="sxs-lookup"><span data-stu-id="7dfb5-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7dfb5-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7dfb5-108">Attributes</span></span>

<span data-ttu-id="7dfb5-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="7dfb5-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7dfb5-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7dfb5-110">Child Elements</span></span>

<span data-ttu-id="7dfb5-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="7dfb5-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7dfb5-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7dfb5-112">Parent Elements</span></span>

|<span data-ttu-id="7dfb5-113">Element</span><span class="sxs-lookup"><span data-stu-id="7dfb5-113">Element</span></span>|<span data-ttu-id="7dfb5-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7dfb5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7dfb5-115">Selectie verzamelings element (indeling)</span><span class="sxs-lookup"><span data-stu-id="7dfb5-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="7dfb5-116">Hiermee wordt één set .NET-objecten gedefinieerd waarnaar kan worden verwezen met de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="7dfb5-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7dfb5-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="7dfb5-117">Text Value</span></span>

<span data-ttu-id="7dfb5-118">Geef de naam op om te verwijzen naar de selectieset.</span><span class="sxs-lookup"><span data-stu-id="7dfb5-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="7dfb5-119">Er zijn geen beperkingen met betrekking tot welke tekens kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7dfb5-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="7dfb5-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7dfb5-120">Remarks</span></span>

<span data-ttu-id="7dfb5-121">De naam die u hier opgeeft, wordt gebruikt in het element `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="7dfb5-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="7dfb5-122">De selectieset die kan worden gebruikt door een weer gave, door een definitie van een weer gave (weer gaven kunnen meerdere definities hebben) of wanneer een selectie voorwaarde wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="7dfb5-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="7dfb5-123">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.</span><span class="sxs-lookup"><span data-stu-id="7dfb5-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="7dfb5-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="7dfb5-124">Example</span></span>

<span data-ttu-id="7dfb5-125">Dit voor beeld toont een `SelectionSet`-element waarmee vier .NET-typen worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="7dfb5-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="7dfb5-126">De naam van de selectieset is ' FileSystemTypes '.</span><span class="sxs-lookup"><span data-stu-id="7dfb5-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7dfb5-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7dfb5-127">See Also</span></span>

[<span data-ttu-id="7dfb5-128">Selectie sets definiëren</span><span class="sxs-lookup"><span data-stu-id="7dfb5-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="7dfb5-129">Selectie verzamelings element (indeling)</span><span class="sxs-lookup"><span data-stu-id="7dfb5-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="7dfb5-130">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="7dfb5-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
