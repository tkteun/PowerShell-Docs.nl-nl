---
title: ItemSelectionCondition-Element voor ListItem voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850916"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="4183b-102">Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4183b-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="4183b-103">Hiermee definieert u de voorwaarde die moet bestaan voor dit item in de lijst moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4183b-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="4183b-104">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries Element voor ListControl (indeling) ListEntry-Element voor ListEntries voor ListControl (indeling) ListItems Element voor ListEntry voor ListControl (indeling) ListItem Element voor ListItems voor ListControl (indeling) ItemSelectionCondition Element voor ListItem voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="4183b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4183b-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="4183b-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4183b-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="4183b-106">Attributes and Elements</span></span>

<span data-ttu-id="4183b-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ItemSelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="4183b-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4183b-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="4183b-108">Attributes</span></span>

<span data-ttu-id="4183b-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="4183b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4183b-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4183b-110">Child Elements</span></span>

|<span data-ttu-id="4183b-111">Element</span><span class="sxs-lookup"><span data-stu-id="4183b-111">Element</span></span>|<span data-ttu-id="4183b-112">Description</span><span class="sxs-lookup"><span data-stu-id="4183b-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4183b-113">PropertyName-Element voor ItemSelectionCondition voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="4183b-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="4183b-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4183b-114">Optional element.</span></span><br /><br /> <span data-ttu-id="4183b-115">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="4183b-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="4183b-116">ScriptBlock-Element voor ItemSelectionCondition voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="4183b-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="4183b-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4183b-117">Optional element.</span></span><br /><br /> <span data-ttu-id="4183b-118">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="4183b-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4183b-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4183b-119">Parent Elements</span></span>

|<span data-ttu-id="4183b-120">Element</span><span class="sxs-lookup"><span data-stu-id="4183b-120">Element</span></span>|<span data-ttu-id="4183b-121">Description</span><span class="sxs-lookup"><span data-stu-id="4183b-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4183b-122">Lijstitem-Element voor ListItems voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="4183b-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="4183b-123">Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in een rij in de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="4183b-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4183b-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="4183b-124">Remarks</span></span>

<span data-ttu-id="4183b-125">U kunt een naam van eigenschap of een script voor deze voorwaarde opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="4183b-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="4183b-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4183b-126">See Also</span></span>

[<span data-ttu-id="4183b-127">Lijstitem-Element voor ListItems voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="4183b-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="4183b-128">PropertyName-Element voor ItemSelectionCondition voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="4183b-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="4183b-129">ScriptBlock-Element voor ItemSelectionCondition voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="4183b-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="4183b-130">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="4183b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
