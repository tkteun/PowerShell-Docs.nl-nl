---
title: SelectionSetName-element voor ViewSelectedBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358815"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="6fdf0-102">Het element SelectionSetName voor ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6fdf0-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="6fdf0-103">Hiermee geeft u een set .NET-objecten op die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="6fdf0-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="6fdf0-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) ViewSelectedBy element (Format) SelectionSetName element voor ViewSelectedBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="6fdf0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6fdf0-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6fdf0-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6fdf0-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="6fdf0-106">Attributes and Elements</span></span>

<span data-ttu-id="6fdf0-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionSetName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="6fdf0-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6fdf0-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="6fdf0-108">Attributes</span></span>

<span data-ttu-id="6fdf0-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="6fdf0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6fdf0-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6fdf0-110">Child Elements</span></span>

<span data-ttu-id="6fdf0-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="6fdf0-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6fdf0-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6fdf0-112">Parent Elements</span></span>

|<span data-ttu-id="6fdf0-113">Element</span><span class="sxs-lookup"><span data-stu-id="6fdf0-113">Element</span></span>|<span data-ttu-id="6fdf0-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6fdf0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6fdf0-115">ViewSelectedBy-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="6fdf0-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="6fdf0-116">Hiermee worden de .NET-objecten gedefinieerd die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="6fdf0-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6fdf0-117">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="6fdf0-117">Text Value</span></span>

<span data-ttu-id="6fdf0-118">Geef de naam op van de selectieset die is gedefinieerd door het element `Name` voor de selectieset.</span><span class="sxs-lookup"><span data-stu-id="6fdf0-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="6fdf0-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6fdf0-119">Remarks</span></span>

<span data-ttu-id="6fdf0-120">U kunt selectie sets gebruiken wanneer u een set verwante objecten hebt waarnaar u wilt verwijzen met behulp van één naam, zoals een set objecten die zijn gerelateerd aan overname.</span><span class="sxs-lookup"><span data-stu-id="6fdf0-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="6fdf0-121">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren en verwijzen van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="6fdf0-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="6fdf0-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="6fdf0-122">Example</span></span>

<span data-ttu-id="6fdf0-123">In het volgende voor beeld ziet u hoe u een selectieset kunt opgeven voor een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="6fdf0-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="6fdf0-124">Hetzelfde schema wordt gebruikt voor tabel-, brede en aangepaste weer gaven.</span><span class="sxs-lookup"><span data-stu-id="6fdf0-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="6fdf0-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6fdf0-125">See Also</span></span>

[<span data-ttu-id="6fdf0-126">Selectie sets definiëren</span><span class="sxs-lookup"><span data-stu-id="6fdf0-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="6fdf0-127">ViewSelectedBy-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="6fdf0-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="6fdf0-128">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="6fdf0-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
