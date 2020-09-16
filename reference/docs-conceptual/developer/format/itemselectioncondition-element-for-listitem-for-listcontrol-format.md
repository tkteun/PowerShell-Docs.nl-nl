---
title: ItemSelectionCondition-element voor lijst item voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f5c388928668e03b96923130fb5849f637548f12
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783616"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="0b609-102">Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0b609-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="0b609-103">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit lijst item.</span><span class="sxs-lookup"><span data-stu-id="0b609-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="0b609-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) item type-element (indeling) van het element list item (Format) voor de ListControl (indeling) element list item voor ListControl (Format) List items element voor List entry voor ListControl (Format) lijst item element voor de ListControl (indeling) ItemSelectionCondition-element</span><span class="sxs-lookup"><span data-stu-id="0b609-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0b609-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0b609-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0b609-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="0b609-106">Attributes and Elements</span></span>

<span data-ttu-id="0b609-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ItemSelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="0b609-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0b609-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="0b609-108">Attributes</span></span>

<span data-ttu-id="0b609-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="0b609-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0b609-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0b609-110">Child Elements</span></span>

|<span data-ttu-id="0b609-111">Element</span><span class="sxs-lookup"><span data-stu-id="0b609-111">Element</span></span>|<span data-ttu-id="0b609-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0b609-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0b609-113">Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0b609-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="0b609-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="0b609-114">Optional element.</span></span><br /><br /> <span data-ttu-id="0b609-115">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="0b609-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="0b609-116">Het element ScriptBlock voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0b609-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="0b609-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="0b609-117">Optional element.</span></span><br /><br /> <span data-ttu-id="0b609-118">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="0b609-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0b609-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0b609-119">Parent Elements</span></span>

|<span data-ttu-id="0b609-120">Element</span><span class="sxs-lookup"><span data-stu-id="0b609-120">Element</span></span>|<span data-ttu-id="0b609-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0b609-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0b609-122">Het element ListItem voor ListItems voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0b609-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="0b609-123">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="0b609-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0b609-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0b609-124">Remarks</span></span>

<span data-ttu-id="0b609-125">U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="0b609-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b609-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0b609-126">See Also</span></span>

[<span data-ttu-id="0b609-127">Het element ListItem voor ListItems voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0b609-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="0b609-128">Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0b609-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="0b609-129">Het element ScriptBlock voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0b609-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="0b609-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="0b609-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
