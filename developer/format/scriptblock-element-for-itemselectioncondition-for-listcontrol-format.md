---
title: ScriptBlock-Element voor ItemSelectionCondition voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064404"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="fc827-102">Het element ScriptBlock voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fc827-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="fc827-103">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="fc827-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="fc827-104">Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en dat het item wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fc827-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="fc827-105">Dit element wordt gebruikt bij het definiëren van een lijst weergeven.</span><span class="sxs-lookup"><span data-stu-id="fc827-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="fc827-106">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries Element voor ListControl (indeling) ListEntry-Element voor ListEntries voor ListControl (indeling) ListItems Element voor ListEntry voor ListControl (indeling) ListItem Element voor ListItems voor lijst beheer (indeling) ItemSelectionCondition Element voor ListItem voor ListControl (indeling) ScriptBlock Element voor ItemSelectionCondition voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="fc827-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fc827-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="fc827-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fc827-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="fc827-108">Attributes and Elements</span></span>

<span data-ttu-id="fc827-109">De volgende secties beschrijven kenmerken, onderliggende elementen en de bovenliggende elementen van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="fc827-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fc827-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="fc827-110">Attributes</span></span>

<span data-ttu-id="fc827-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="fc827-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fc827-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fc827-112">Child Elements</span></span>

<span data-ttu-id="fc827-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="fc827-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fc827-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fc827-114">Parent Elements</span></span>

|<span data-ttu-id="fc827-115">Element</span><span class="sxs-lookup"><span data-stu-id="fc827-115">Element</span></span>|<span data-ttu-id="fc827-116">Description</span><span class="sxs-lookup"><span data-stu-id="fc827-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fc827-117">ItemSelectionCondition-Element voor ListItem voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="fc827-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="fc827-118">Hiermee definieert u de voorwaarde die moet bestaan voor dit item in de lijst moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fc827-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fc827-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="fc827-119">Text Value</span></span>

<span data-ttu-id="fc827-120">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="fc827-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc827-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="fc827-121">Remarks</span></span>

<span data-ttu-id="fc827-122">Als dit element wordt gebruikt, kunt u niet opgeven de `PropertyName` element bij het definiëren van de selectievoorwaarde.</span><span class="sxs-lookup"><span data-stu-id="fc827-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc827-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fc827-123">See Also</span></span>

[<span data-ttu-id="fc827-124">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc827-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
