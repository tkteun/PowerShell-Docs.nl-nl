---
title: Script block-element voor ItemSelectionCondition voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 38dc952bfadd6aed24bae8cbef05adcd22e61dd4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787628"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="711ba-102">Het element ScriptBlock voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="711ba-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="711ba-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="711ba-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="711ba-104">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het lijst item gebruikt.</span><span class="sxs-lookup"><span data-stu-id="711ba-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="711ba-105">Dit element wordt gebruikt bij het definiëren van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="711ba-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="711ba-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling). element van ListControl element (Format) voor ListControl (indeling) element List entry voor List Entries (Format) List items element voor List entry voor ListControl (Format) lijst item-element voor de list items voor listing Control (Format) ItemSelectionCondition element voor ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="711ba-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="711ba-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="711ba-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="711ba-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="711ba-108">Attributes and Elements</span></span>

<span data-ttu-id="711ba-109">In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="711ba-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="711ba-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="711ba-110">Attributes</span></span>

<span data-ttu-id="711ba-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="711ba-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="711ba-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="711ba-112">Child Elements</span></span>

<span data-ttu-id="711ba-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="711ba-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="711ba-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="711ba-114">Parent Elements</span></span>

|<span data-ttu-id="711ba-115">Element</span><span class="sxs-lookup"><span data-stu-id="711ba-115">Element</span></span>|<span data-ttu-id="711ba-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="711ba-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="711ba-117">Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="711ba-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="711ba-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit lijst item.</span><span class="sxs-lookup"><span data-stu-id="711ba-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="711ba-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="711ba-119">Text Value</span></span>

<span data-ttu-id="711ba-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="711ba-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="711ba-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="711ba-121">Remarks</span></span>

<span data-ttu-id="711ba-122">Als dit element wordt gebruikt, kunt u het element niet opgeven `PropertyName` bij het definiëren van de selectie voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="711ba-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="711ba-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="711ba-123">See Also</span></span>

[<span data-ttu-id="711ba-124">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="711ba-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
