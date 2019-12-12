---
title: PropertyName-element voor ItemSelectionCondition voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354094"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="70538-102">Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="70538-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="70538-103">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="70538-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="70538-104">Wanneer deze eigenschap aanwezig is of wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt de weer gave gebruikt.</span><span class="sxs-lookup"><span data-stu-id="70538-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="70538-105">Dit element wordt gebruikt bij het definiëren van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="70538-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="70538-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) item type-element (indeling) List item (Format) List items-element Element voor list items voor ListControl (Format) ItemSelectionCondition-element voor lijst item voor ListControls PropertyName-element voor ItemSelectionCondition voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="70538-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70538-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="70538-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70538-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="70538-108">Attributes and Elements</span></span>

<span data-ttu-id="70538-109">In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het element `PropertyName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="70538-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70538-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="70538-110">Attributes</span></span>

<span data-ttu-id="70538-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="70538-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70538-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="70538-112">Child Elements</span></span>

<span data-ttu-id="70538-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="70538-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="70538-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="70538-114">Parent Elements</span></span>

|<span data-ttu-id="70538-115">Element</span><span class="sxs-lookup"><span data-stu-id="70538-115">Element</span></span>|<span data-ttu-id="70538-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="70538-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70538-117">ItemSelectionCondition-element voor lijst item voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="70538-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="70538-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="70538-118">Text Value</span></span>

<span data-ttu-id="70538-119">Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="70538-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="70538-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="70538-120">Remarks</span></span>

<span data-ttu-id="70538-121">Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.</span><span class="sxs-lookup"><span data-stu-id="70538-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="70538-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="70538-122">See Also</span></span>

[<span data-ttu-id="70538-123">Script block-element voor ItemSelectionCondition voor ListIControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="70538-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="70538-124">ItemSelectionCondition-element voor lijst item voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="70538-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="70538-125">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="70538-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
