---
title: PropertyName-Element voor ItemSelectionCondition voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846485"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="ca2fa-102">Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ca2fa-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="ca2fa-103">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="ca2fa-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="ca2fa-104">Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de weergave wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ca2fa-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="ca2fa-105">Dit element wordt gebruikt bij het definiëren van een lijst weergeven.</span><span class="sxs-lookup"><span data-stu-id="ca2fa-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="ca2fa-106">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries-Element (indeling) ListEntry-Element voor ListControl (indeling) ListItems Element voor ListEntry voor ListItem ListControl (indeling) Element voor ListItems voor ListControl (indeling) ItemSelectionCondition Element voor ListItem voor ListControls PropertyName-Element voor ItemSelectionCondition voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ca2fa-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ca2fa-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ca2fa-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ca2fa-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ca2fa-108">Attributes and Elements</span></span>

<span data-ttu-id="ca2fa-109">De volgende secties beschrijven kenmerken, onderliggende elementen en de bovenliggende elementen van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="ca2fa-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca2fa-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ca2fa-110">Attributes</span></span>

<span data-ttu-id="ca2fa-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="ca2fa-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ca2fa-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ca2fa-112">Child Elements</span></span>

<span data-ttu-id="ca2fa-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="ca2fa-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ca2fa-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ca2fa-114">Parent Elements</span></span>

|<span data-ttu-id="ca2fa-115">Element</span><span class="sxs-lookup"><span data-stu-id="ca2fa-115">Element</span></span>|<span data-ttu-id="ca2fa-116">Description</span><span class="sxs-lookup"><span data-stu-id="ca2fa-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca2fa-117">ItemSelectionCondition-Element voor ListItem voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ca2fa-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="ca2fa-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="ca2fa-118">Text Value</span></span>

<span data-ttu-id="ca2fa-119">Geef de naam van de eigenschap waarvan de waarde wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="ca2fa-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="ca2fa-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ca2fa-120">Remarks</span></span>

<span data-ttu-id="ca2fa-121">Als dit element wordt gebruikt, kunt u niet opgeven de [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element bij het definiëren van de selectievoorwaarde.</span><span class="sxs-lookup"><span data-stu-id="ca2fa-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca2fa-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ca2fa-122">See Also</span></span>

[<span data-ttu-id="ca2fa-123">ScriptBlock-Element voor ItemSelectionCondition voor ListIControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ca2fa-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="ca2fa-124">ItemSelectionCondition-Element voor ListItem voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ca2fa-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="ca2fa-125">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca2fa-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
