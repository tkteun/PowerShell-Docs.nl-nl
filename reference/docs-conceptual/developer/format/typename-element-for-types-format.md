---
title: TypeName-element voor typen (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358737"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="d28fa-102">Het element TypeName voor Typen (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d28fa-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="d28fa-103">Hiermee geeft u het .NET-type op van een object dat tot de selectieset behoort.</span><span class="sxs-lookup"><span data-stu-id="d28fa-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="d28fa-104">Configuratie-element (indeling) SelectionSets element (Format) element van het type Selectionset (indeling)-element (Format) elementen van het type TypeName-element van typen (indeling)</span><span class="sxs-lookup"><span data-stu-id="d28fa-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d28fa-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d28fa-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d28fa-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d28fa-106">Attributes and Elements</span></span>

<span data-ttu-id="d28fa-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `TypeName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="d28fa-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="d28fa-108">Ten minste één `TypeName`-element moet worden opgenomen in de selectieset.</span><span class="sxs-lookup"><span data-stu-id="d28fa-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="d28fa-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d28fa-109">Attributes</span></span>

<span data-ttu-id="d28fa-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="d28fa-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d28fa-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d28fa-111">Child Elements</span></span>

<span data-ttu-id="d28fa-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="d28fa-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d28fa-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d28fa-113">Parent Elements</span></span>

|<span data-ttu-id="d28fa-114">Element</span><span class="sxs-lookup"><span data-stu-id="d28fa-114">Element</span></span>|<span data-ttu-id="d28fa-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d28fa-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d28fa-116">Type-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="d28fa-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="d28fa-117">Hiermee definieert u de .NET-objecten die zich in de selectieset bevinden.</span><span class="sxs-lookup"><span data-stu-id="d28fa-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d28fa-118">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="d28fa-118">Text Value</span></span>

<span data-ttu-id="d28fa-119">Geef de volledig gekwalificeerde naam voor het .NET-type op.</span><span class="sxs-lookup"><span data-stu-id="d28fa-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="d28fa-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d28fa-120">Remarks</span></span>

<span data-ttu-id="d28fa-121">U kunt selectie sets gebruiken wanneer u een set verwante objecten hebt waarnaar u wilt verwijzen met behulp van één naam, zoals een set objecten die zijn gerelateerd aan overname.</span><span class="sxs-lookup"><span data-stu-id="d28fa-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="d28fa-122">Wanneer u uw weer gaven definieert, kunt u de set met objecten opgeven door de naam van de selectieset te gebruiken in plaats van alle objecten in elke weer gave te vermelden.</span><span class="sxs-lookup"><span data-stu-id="d28fa-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="d28fa-123">Algemene selectie sets worden opgegeven met hun naam bij het definiëren van de weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="d28fa-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="d28fa-124">In dergelijke gevallen specificeert het onderliggende `SelectionSetName` van het element `ViewSelectedBy` voor de weer gave de set.</span><span class="sxs-lookup"><span data-stu-id="d28fa-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="d28fa-125">Met verschillende vermeldingen in een weer gave kunt u echter ook een selectie reeks opgeven die alleen van toepassing is op die vermelding van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="d28fa-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="d28fa-126">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.</span><span class="sxs-lookup"><span data-stu-id="d28fa-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="d28fa-127">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="d28fa-127">Example</span></span>

<span data-ttu-id="d28fa-128">In het volgende voor beeld ziet u een `SelectionSet`-element dat vier .NET-typen definieert.</span><span class="sxs-lookup"><span data-stu-id="d28fa-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d28fa-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d28fa-129">See Also</span></span>

[<span data-ttu-id="d28fa-130">Selectie sets definiëren</span><span class="sxs-lookup"><span data-stu-id="d28fa-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d28fa-131">Selectie verzamelings element (indeling)</span><span class="sxs-lookup"><span data-stu-id="d28fa-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="d28fa-132">SelectionSets-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="d28fa-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="d28fa-133">Type-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="d28fa-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="d28fa-134">Een Windows Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d28fa-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
