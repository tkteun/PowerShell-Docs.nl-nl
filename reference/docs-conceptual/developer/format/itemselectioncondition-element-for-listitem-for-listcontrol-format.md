---
title: ItemSelectionCondition-element voor lijst item voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356054"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="0b632-102">Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0b632-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="0b632-103">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit lijst item.</span><span class="sxs-lookup"><span data-stu-id="0b632-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="0b632-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling). element (Format) voor ListControl voor ListControl (Format) lijst item-element voor list items voor ListControl (Format) ItemSelectionCondition-element voor de lijst item voor ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0b632-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0b632-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="0b632-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0b632-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="0b632-106">Attributes and Elements</span></span>

<span data-ttu-id="0b632-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ItemSelectionCondition` beschreven.</span><span class="sxs-lookup"><span data-stu-id="0b632-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0b632-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="0b632-108">Attributes</span></span>

<span data-ttu-id="0b632-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="0b632-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0b632-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0b632-110">Child Elements</span></span>

|<span data-ttu-id="0b632-111">Element</span><span class="sxs-lookup"><span data-stu-id="0b632-111">Element</span></span>|<span data-ttu-id="0b632-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0b632-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0b632-113">PropertyName-element voor ItemSelectionCondition voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="0b632-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="0b632-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="0b632-114">Optional element.</span></span><br /><br /> <span data-ttu-id="0b632-115">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="0b632-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="0b632-116">Script block-element voor ItemSelectionCondition voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="0b632-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="0b632-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="0b632-117">Optional element.</span></span><br /><br /> <span data-ttu-id="0b632-118">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="0b632-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0b632-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0b632-119">Parent Elements</span></span>

|<span data-ttu-id="0b632-120">Element</span><span class="sxs-lookup"><span data-stu-id="0b632-120">Element</span></span>|<span data-ttu-id="0b632-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0b632-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0b632-122">Lijst item-element voor list items voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="0b632-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="0b632-123">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="0b632-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0b632-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0b632-124">Remarks</span></span>

<span data-ttu-id="0b632-125">U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="0b632-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b632-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0b632-126">See Also</span></span>

[<span data-ttu-id="0b632-127">Lijst item-element voor list items voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="0b632-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="0b632-128">PropertyName-element voor ItemSelectionCondition voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="0b632-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="0b632-129">Script block-element voor ItemSelectionCondition voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="0b632-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="0b632-130">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="0b632-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
