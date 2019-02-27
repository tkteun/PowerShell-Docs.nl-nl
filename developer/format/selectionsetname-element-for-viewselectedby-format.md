---
title: SelectionSetName-Element voor ViewSelectedBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848445"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="46281-102">Het element SelectionSetName voor ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="46281-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="46281-103">Hiermee geeft u een set van .NET-objecten die worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="46281-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="46281-104">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ViewSelectedBy-Element (indeling) SelectionSetName Element voor ViewSelectedBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="46281-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="46281-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="46281-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="46281-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="46281-106">Attributes and Elements</span></span>

<span data-ttu-id="46281-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="46281-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="46281-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="46281-108">Attributes</span></span>

<span data-ttu-id="46281-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="46281-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="46281-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="46281-110">Child Elements</span></span>

<span data-ttu-id="46281-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="46281-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="46281-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="46281-112">Parent Elements</span></span>

|<span data-ttu-id="46281-113">Element</span><span class="sxs-lookup"><span data-stu-id="46281-113">Element</span></span>|<span data-ttu-id="46281-114">Description</span><span class="sxs-lookup"><span data-stu-id="46281-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="46281-115">ViewSelectedBy-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="46281-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="46281-116">Hiermee definieert u de .NET-objecten die worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="46281-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="46281-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="46281-117">Text Value</span></span>

<span data-ttu-id="46281-118">Geef de naam van de van selectieset die wordt gedefinieerd door de `Name` -element voor de selectieset.</span><span class="sxs-lookup"><span data-stu-id="46281-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="46281-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="46281-119">Remarks</span></span>

<span data-ttu-id="46281-120">U kunt selectiesets gebruiken wanneer u een set van gerelateerde objecten die u verwijzen wilt met behulp van één naam, zoals een set objecten die via overname verwant zijn hebt.</span><span class="sxs-lookup"><span data-stu-id="46281-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="46281-121">Zie voor meer informatie over het definiëren en verwijst naar een selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="46281-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="46281-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="46281-122">Example</span></span>

<span data-ttu-id="46281-123">Het volgende voorbeeld ziet hoe u een selectie instellen voor een lijst weergeven.</span><span class="sxs-lookup"><span data-stu-id="46281-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="46281-124">Hetzelfde schema wordt gebruikt voor de tabel, breed en aangepaste weergaven.</span><span class="sxs-lookup"><span data-stu-id="46281-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="46281-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="46281-125">See Also</span></span>

[<span data-ttu-id="46281-126">Selectiesets definiëren</span><span class="sxs-lookup"><span data-stu-id="46281-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="46281-127">ViewSelectedBy-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="46281-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="46281-128">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="46281-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
