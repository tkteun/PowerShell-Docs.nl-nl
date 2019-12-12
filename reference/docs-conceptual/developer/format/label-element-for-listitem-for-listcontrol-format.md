---
title: Element label voor lijst item voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354444"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="a06dd-102">Het element Label voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a06dd-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="a06dd-103">Hiermee geeft u het label op dat links van de eigenschap of script waarde in de rij wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a06dd-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="a06dd-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling). element (Format) List item voor ListControl (indeling) Format) lijst item-element voor list items voor ListControl (Format) label-element voor lijst item voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="a06dd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a06dd-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a06dd-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a06dd-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a06dd-106">Attributes and Elements</span></span>

<span data-ttu-id="a06dd-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Label` beschreven.</span><span class="sxs-lookup"><span data-stu-id="a06dd-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a06dd-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a06dd-108">Attributes</span></span>

<span data-ttu-id="a06dd-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="a06dd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a06dd-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a06dd-110">Child Elements</span></span>

<span data-ttu-id="a06dd-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="a06dd-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a06dd-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a06dd-112">Parent Elements</span></span>

|<span data-ttu-id="a06dd-113">Element</span><span class="sxs-lookup"><span data-stu-id="a06dd-113">Element</span></span>|<span data-ttu-id="a06dd-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a06dd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a06dd-115">Lijst item-element voor list items voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="a06dd-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="a06dd-116">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="a06dd-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a06dd-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="a06dd-117">Text Value</span></span>

<span data-ttu-id="a06dd-118">Geef het label op dat links van de eigenschap of script waarde moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a06dd-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="a06dd-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a06dd-119">Remarks</span></span>

<span data-ttu-id="a06dd-120">Als er geen label is opgegeven, wordt de naam van de eigenschap of het script weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a06dd-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="a06dd-121">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over het gebruik van labels in een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="a06dd-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a06dd-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="a06dd-122">Example</span></span>

<span data-ttu-id="a06dd-123">In het volgende voor beeld ziet u hoe u een label aan een rij toevoegt.</span><span class="sxs-lookup"><span data-stu-id="a06dd-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="a06dd-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a06dd-124">See Also</span></span>

[<span data-ttu-id="a06dd-125">Een lijst weergave maken</span><span class="sxs-lookup"><span data-stu-id="a06dd-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="a06dd-126">Lijst item-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a06dd-126">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="a06dd-127">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="a06dd-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
