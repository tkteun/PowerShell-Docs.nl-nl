---
title: Script block-element voor ItemSelectionCondition voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353891"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="1c64c-102">Het element ScriptBlock voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1c64c-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="1c64c-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="1c64c-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="1c64c-104">Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt het lijst item gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1c64c-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="1c64c-105">Dit element wordt gebruikt bij het definiëren van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="1c64c-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="1c64c-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling). element (Format) voor ListControl voor ListControl (Format) lijst item-element voor list items voor List Control (Format) ItemSelectionCondition-element voor lijst item voor ListControl (Format) script block element voor ListControl (Format) voor ItemSelectionCondition</span><span class="sxs-lookup"><span data-stu-id="1c64c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1c64c-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1c64c-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1c64c-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1c64c-108">Attributes and Elements</span></span>

<span data-ttu-id="1c64c-109">In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het element `ScriptBlock` beschreven.</span><span class="sxs-lookup"><span data-stu-id="1c64c-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1c64c-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1c64c-110">Attributes</span></span>

<span data-ttu-id="1c64c-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="1c64c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1c64c-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1c64c-112">Child Elements</span></span>

<span data-ttu-id="1c64c-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="1c64c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1c64c-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1c64c-114">Parent Elements</span></span>

|<span data-ttu-id="1c64c-115">Element</span><span class="sxs-lookup"><span data-stu-id="1c64c-115">Element</span></span>|<span data-ttu-id="1c64c-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1c64c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c64c-117">ItemSelectionCondition-element voor lijst item voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="1c64c-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="1c64c-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit lijst item.</span><span class="sxs-lookup"><span data-stu-id="1c64c-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1c64c-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="1c64c-119">Text Value</span></span>

<span data-ttu-id="1c64c-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="1c64c-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c64c-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1c64c-121">Remarks</span></span>

<span data-ttu-id="1c64c-122">Als dit element wordt gebruikt, kunt u het `PropertyName`-element niet opgeven wanneer u de selectie voorwaarde definieert.</span><span class="sxs-lookup"><span data-stu-id="1c64c-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c64c-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1c64c-123">See Also</span></span>

[<span data-ttu-id="1c64c-124">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="1c64c-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
