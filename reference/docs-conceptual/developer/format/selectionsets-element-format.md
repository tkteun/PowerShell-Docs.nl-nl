---
title: SelectionSets-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353730"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="95068-102">Het element SelectionSets (opmaak)</span><span class="sxs-lookup"><span data-stu-id="95068-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="95068-103">Hiermee worden de algemene sets van .NET-objecten gedefinieerd die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="95068-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="95068-104">De weer gaven en besturings elementen van het opmaak bestand kunnen verwijzen naar de volledige set met objecten door alleen de naam van de selectieset te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="95068-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="95068-105">SelectionSets element indeling van configuratie-element</span><span class="sxs-lookup"><span data-stu-id="95068-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="95068-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="95068-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="95068-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="95068-107">Attributes and Elements</span></span>

<span data-ttu-id="95068-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionSets` beschreven.</span><span class="sxs-lookup"><span data-stu-id="95068-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="95068-109">Elk onderliggend element definieert een set objecten waarnaar kan worden verwezen door de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="95068-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="95068-110">De volg orde van de onderliggende elementen is niet significant.</span><span class="sxs-lookup"><span data-stu-id="95068-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="95068-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="95068-111">Attributes</span></span>

<span data-ttu-id="95068-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="95068-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="95068-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="95068-113">Child Elements</span></span>

|<span data-ttu-id="95068-114">Element</span><span class="sxs-lookup"><span data-stu-id="95068-114">Element</span></span>|<span data-ttu-id="95068-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="95068-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95068-116">Selectie verzamelings element (indeling)</span><span class="sxs-lookup"><span data-stu-id="95068-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="95068-117">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="95068-117">Required element.</span></span><br /><br /> <span data-ttu-id="95068-118">Hiermee wordt één set .NET-objecten gedefinieerd waarnaar kan worden verwezen met de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="95068-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="95068-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="95068-119">Parent Elements</span></span>

|<span data-ttu-id="95068-120">Element</span><span class="sxs-lookup"><span data-stu-id="95068-120">Element</span></span>|<span data-ttu-id="95068-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="95068-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95068-122">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="95068-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="95068-123">Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="95068-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="95068-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="95068-124">Remarks</span></span>

<span data-ttu-id="95068-125">U kunt selectie sets gebruiken wanneer u een set verwante objecten hebt waarnaar u wilt verwijzen met behulp van één naam, zoals een set objecten die zijn gerelateerd aan overname.</span><span class="sxs-lookup"><span data-stu-id="95068-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="95068-126">Wanneer u uw weer gaven definieert, kunt u de set met objecten opgeven door de naam van de selectieset te gebruiken in plaats van alle objecten in elke weer gave te vermelden.</span><span class="sxs-lookup"><span data-stu-id="95068-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="95068-127">Algemene selectie sets worden opgegeven met hun naam bij het definiëren van de weer gaven van het opmaak bestand of de definities van de weer gaven.</span><span class="sxs-lookup"><span data-stu-id="95068-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="95068-128">In dergelijke gevallen specificeert het `SelectionSetName` onderliggende element van de `ViewSelectedBy` en `EntrySelectedBy` elementen de set die moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="95068-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="95068-129">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.</span><span class="sxs-lookup"><span data-stu-id="95068-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="95068-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="95068-130">See Also</span></span>

[<span data-ttu-id="95068-131">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="95068-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="95068-132">Selectie sets definiëren</span><span class="sxs-lookup"><span data-stu-id="95068-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="95068-133">Selectie verzamelings element (indeling)</span><span class="sxs-lookup"><span data-stu-id="95068-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="95068-134">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="95068-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
