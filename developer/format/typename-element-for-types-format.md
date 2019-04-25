---
title: TypeName-Element voor typen die zijn (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083787"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="78f7c-102">Het element TypeName voor Typen (opmaak)</span><span class="sxs-lookup"><span data-stu-id="78f7c-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="78f7c-103">Hiermee geeft u de .NET-type van een object dat bij de selectieset hoort.</span><span class="sxs-lookup"><span data-stu-id="78f7c-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="78f7c-104">Configuratie Element (indeling) SelectionSets-Element (indeling) SelectionSet-Element (indeling) van het type Element (indeling) TypeName Element van de typen (indeling)</span><span class="sxs-lookup"><span data-stu-id="78f7c-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="78f7c-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="78f7c-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="78f7c-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="78f7c-106">Attributes and Elements</span></span>

<span data-ttu-id="78f7c-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="78f7c-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="78f7c-108">Ten minste één `TypeName` element moet worden opgenomen in de selectieset.</span><span class="sxs-lookup"><span data-stu-id="78f7c-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="78f7c-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="78f7c-109">Attributes</span></span>

<span data-ttu-id="78f7c-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="78f7c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="78f7c-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="78f7c-111">Child Elements</span></span>

<span data-ttu-id="78f7c-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="78f7c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="78f7c-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="78f7c-113">Parent Elements</span></span>

|<span data-ttu-id="78f7c-114">Element</span><span class="sxs-lookup"><span data-stu-id="78f7c-114">Element</span></span>|<span data-ttu-id="78f7c-115">Description</span><span class="sxs-lookup"><span data-stu-id="78f7c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="78f7c-116">Typen Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="78f7c-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="78f7c-117">Hiermee definieert u de .NET-objecten die in de selectie.</span><span class="sxs-lookup"><span data-stu-id="78f7c-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="78f7c-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="78f7c-118">Text Value</span></span>

<span data-ttu-id="78f7c-119">Geef de volledig gekwalificeerde naam voor het .NET-type.</span><span class="sxs-lookup"><span data-stu-id="78f7c-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="78f7c-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="78f7c-120">Remarks</span></span>

<span data-ttu-id="78f7c-121">U kunt selectiesets gebruiken wanneer u een set van gerelateerde objecten die u verwijzen wilt met behulp van één naam, zoals een set objecten die via overname verwant zijn hebt.</span><span class="sxs-lookup"><span data-stu-id="78f7c-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="78f7c-122">Bij het definiëren van uw weergaven, kunt u de set objecten opgeven met behulp van de naam van de selectie instellen in plaats van de lijst van alle objecten in elke weergave.</span><span class="sxs-lookup"><span data-stu-id="78f7c-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="78f7c-123">Algemene selectiesets worden opgegeven door de naam bij het definiëren van de weergaven van de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="78f7c-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="78f7c-124">In dergelijke gevallen de `SelectionSetName` onderliggend element van de `ViewSelectedBy` -element voor de weergave bevat de set.</span><span class="sxs-lookup"><span data-stu-id="78f7c-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="78f7c-125">Verschillende vermeldingen van een weergave kunnen echter ook een selectie instellen die van toepassing op alleen die vermelding van de weergave opgeven.</span><span class="sxs-lookup"><span data-stu-id="78f7c-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="78f7c-126">Zie voor meer informatie over selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="78f7c-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="78f7c-127">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="78f7c-127">Example</span></span>

<span data-ttu-id="78f7c-128">Het volgende voorbeeld wordt een `SelectionSet` element waarin vier .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="78f7c-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```
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

## <a name="see-also"></a><span data-ttu-id="78f7c-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="78f7c-129">See Also</span></span>

[<span data-ttu-id="78f7c-130">Selectiesets definiëren</span><span class="sxs-lookup"><span data-stu-id="78f7c-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="78f7c-131">SelectionSet-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="78f7c-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="78f7c-132">SelectionSets-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="78f7c-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="78f7c-133">Typen Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="78f7c-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="78f7c-134">Een Windows PowerShell opmaak bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="78f7c-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
