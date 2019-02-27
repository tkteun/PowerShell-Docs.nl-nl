---
title: Element een label voor ListItem voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845953"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="07798-102">Het element Label voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="07798-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="07798-103">Hiermee geeft u het label dat wordt weergegeven aan de linkerkant van de waarde voor eigenschap of het script in de rij.</span><span class="sxs-lookup"><span data-stu-id="07798-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="07798-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries Element voor ListControl (indeling) ListEntry-Element voor ListItems voor ListEntry voor ListControl Element (ListControl (indeling) -Indeling) ListItem Element voor ListItems voor ListControl (indeling) Label-Element voor ListItem voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="07798-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="07798-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="07798-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="07798-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="07798-106">Attributes and Elements</span></span>

<span data-ttu-id="07798-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `Label` element.</span><span class="sxs-lookup"><span data-stu-id="07798-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="07798-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="07798-108">Attributes</span></span>

<span data-ttu-id="07798-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="07798-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="07798-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="07798-110">Child Elements</span></span>

<span data-ttu-id="07798-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="07798-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="07798-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="07798-112">Parent Elements</span></span>

|<span data-ttu-id="07798-113">Element</span><span class="sxs-lookup"><span data-stu-id="07798-113">Element</span></span>|<span data-ttu-id="07798-114">Description</span><span class="sxs-lookup"><span data-stu-id="07798-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07798-115">Lijstitem-Element voor ListItems voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="07798-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="07798-116">Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in een rij in de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="07798-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="07798-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="07798-117">Text Value</span></span>

<span data-ttu-id="07798-118">Geef het label om te worden weergegeven aan de linkerkant van de waarde voor eigenschap of script.</span><span class="sxs-lookup"><span data-stu-id="07798-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="07798-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="07798-119">Remarks</span></span>

<span data-ttu-id="07798-120">Als een label niet opgegeven is, wordt de naam van de eigenschap of het script wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="07798-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="07798-121">Zie voor meer informatie over het gebruik van de labels in een lijst weergeven [het maken van een lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="07798-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="07798-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="07798-122">Example</span></span>

<span data-ttu-id="07798-123">Het volgende voorbeeld ziet hoe u een label toevoegen aan een rij.</span><span class="sxs-lookup"><span data-stu-id="07798-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="07798-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="07798-124">See Also</span></span>

[<span data-ttu-id="07798-125">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="07798-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="07798-126">ListItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="07798-126">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="07798-127">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="07798-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
