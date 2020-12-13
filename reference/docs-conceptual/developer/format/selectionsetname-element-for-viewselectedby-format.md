---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor ViewSelectedBy (opmaak)
description: Het element SelectionSetName voor ViewSelectedBy (opmaak)
ms.openlocfilehash: a1a1816761715a138bcb3c2bd4cb9dbbb2f9cb92
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654905"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="8effa-103">Het element SelectionSetName voor ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8effa-103">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="8effa-104">Hiermee geeft u een set .NET-objecten op die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="8effa-104">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="8effa-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) ViewSelectedBy element (Format) SelectionSetName element voor ViewSelectedBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="8effa-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8effa-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8effa-106">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8effa-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="8effa-107">Attributes and Elements</span></span>

<span data-ttu-id="8effa-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="8effa-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8effa-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="8effa-109">Attributes</span></span>

<span data-ttu-id="8effa-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="8effa-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8effa-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8effa-111">Child Elements</span></span>

<span data-ttu-id="8effa-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="8effa-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8effa-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8effa-113">Parent Elements</span></span>

|<span data-ttu-id="8effa-114">Element</span><span class="sxs-lookup"><span data-stu-id="8effa-114">Element</span></span>|<span data-ttu-id="8effa-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8effa-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8effa-116">Het element ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8effa-116">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="8effa-117">Hiermee worden de .NET-objecten gedefinieerd die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="8effa-117">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8effa-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="8effa-118">Text Value</span></span>

<span data-ttu-id="8effa-119">Geef de naam op van de selectieset die is gedefinieerd door het `Name` element voor de selectieset.</span><span class="sxs-lookup"><span data-stu-id="8effa-119">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="8effa-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="8effa-120">Remarks</span></span>

<span data-ttu-id="8effa-121">U kunt selectie sets gebruiken wanneer u een set verwante objecten hebt waarnaar u wilt verwijzen met behulp van één naam, zoals een set objecten die zijn gerelateerd aan overname.</span><span class="sxs-lookup"><span data-stu-id="8effa-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="8effa-122">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="8effa-122">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="8effa-123">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="8effa-123">Example</span></span>

<span data-ttu-id="8effa-124">In het volgende voor beeld ziet u hoe u een selectieset kunt opgeven voor een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="8effa-124">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="8effa-125">Hetzelfde schema wordt gebruikt voor tabel-, brede en aangepaste weer gaven.</span><span class="sxs-lookup"><span data-stu-id="8effa-125">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="8effa-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8effa-126">See Also</span></span>

[<span data-ttu-id="8effa-127">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="8effa-127">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="8effa-128">Het element ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8effa-128">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="8effa-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="8effa-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
