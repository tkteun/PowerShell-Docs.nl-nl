---
title: Element label voor lijst item voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ad80cc0478e7567b12d264ab661d843248ba48e1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783633"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="08723-102">Het element Label voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="08723-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="08723-103">Hiermee geeft u het label op dat links van de eigenschap of script waarde in de rij wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="08723-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="08723-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling). element (Format) List item voor ListControl (Format) element Entry List voor ListControl (Format) List items voor List entry voor ListControl element (Format) lijst item-element voor list items voor ListControl (Format) label-element (Format)</span><span class="sxs-lookup"><span data-stu-id="08723-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="08723-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="08723-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="08723-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="08723-106">Attributes and Elements</span></span>

<span data-ttu-id="08723-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Label` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="08723-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="08723-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="08723-108">Attributes</span></span>

<span data-ttu-id="08723-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="08723-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="08723-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="08723-110">Child Elements</span></span>

<span data-ttu-id="08723-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="08723-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="08723-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="08723-112">Parent Elements</span></span>

|<span data-ttu-id="08723-113">Element</span><span class="sxs-lookup"><span data-stu-id="08723-113">Element</span></span>|<span data-ttu-id="08723-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="08723-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08723-115">Het element ListItem voor ListItems voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="08723-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="08723-116">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="08723-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="08723-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="08723-117">Text Value</span></span>

<span data-ttu-id="08723-118">Geef het label op dat links van de eigenschap of script waarde moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="08723-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="08723-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="08723-119">Remarks</span></span>

<span data-ttu-id="08723-120">Als er geen label is opgegeven, wordt de naam van de eigenschap of het script weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="08723-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="08723-121">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over het gebruik van labels in een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="08723-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="08723-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="08723-122">Example</span></span>

<span data-ttu-id="08723-123">In het volgende voor beeld ziet u hoe u een label aan een rij toevoegt.</span><span class="sxs-lookup"><span data-stu-id="08723-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="08723-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="08723-124">See Also</span></span>

[<span data-ttu-id="08723-125">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="08723-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="08723-126">Lijst item-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="08723-126">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="08723-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="08723-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
