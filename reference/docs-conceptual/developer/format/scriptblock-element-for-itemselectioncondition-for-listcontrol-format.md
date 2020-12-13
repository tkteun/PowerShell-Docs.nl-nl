---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor ItemSelectionCondition voor ListControl (opmaak)
description: Het element ScriptBlock voor ItemSelectionCondition voor ListControl (opmaak)
ms.openlocfilehash: 1e518f898e0e1e62ca64f9897b1323cc6dd89ae9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665055"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="675f4-103">Het element ScriptBlock voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="675f4-103">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="675f4-104">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="675f4-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="675f4-105">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het lijst item gebruikt.</span><span class="sxs-lookup"><span data-stu-id="675f4-105">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="675f4-106">Dit element wordt gebruikt bij het definiëren van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="675f4-106">This element is used when defining a list view.</span></span>

<span data-ttu-id="675f4-107">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling). element van ListControl element (Format) voor ListControl (indeling) element List entry voor List Entries (Format) List items element voor List entry voor ListControl (Format) lijst item-element voor de list items voor listing Control (Format) ItemSelectionCondition element voor ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="675f4-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="675f4-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="675f4-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="675f4-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="675f4-109">Attributes and Elements</span></span>

<span data-ttu-id="675f4-110">In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="675f4-110">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="675f4-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="675f4-111">Attributes</span></span>

<span data-ttu-id="675f4-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="675f4-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="675f4-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="675f4-113">Child Elements</span></span>

<span data-ttu-id="675f4-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="675f4-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="675f4-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="675f4-115">Parent Elements</span></span>

|<span data-ttu-id="675f4-116">Element</span><span class="sxs-lookup"><span data-stu-id="675f4-116">Element</span></span>|<span data-ttu-id="675f4-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="675f4-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="675f4-118">Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="675f4-118">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="675f4-119">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit lijst item.</span><span class="sxs-lookup"><span data-stu-id="675f4-119">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="675f4-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="675f4-120">Text Value</span></span>

<span data-ttu-id="675f4-121">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="675f4-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="675f4-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="675f4-122">Remarks</span></span>

<span data-ttu-id="675f4-123">Als dit element wordt gebruikt, kunt u het element niet opgeven `PropertyName` bij het definiëren van de selectie voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="675f4-123">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="675f4-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="675f4-124">See Also</span></span>

[<span data-ttu-id="675f4-125">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="675f4-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
