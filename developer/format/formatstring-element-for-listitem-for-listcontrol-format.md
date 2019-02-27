---
title: FormatString-Element voor ListItem voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849845"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="6de3f-102">Het element FormatString voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6de3f-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="6de3f-103">Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="6de3f-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="6de3f-104">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries Element voor ListControl (indeling) ListEntry-Element voor ListControl (indeling) ListItems Element voor ListControl (indeling) Lijstitem-Element voor ListControl (indeling) FormatString-Element voor ListItem voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="6de3f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6de3f-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6de3f-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6de3f-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="6de3f-106">Attributes and Elements</span></span>

<span data-ttu-id="6de3f-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `FormatString` element.</span><span class="sxs-lookup"><span data-stu-id="6de3f-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6de3f-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="6de3f-108">Attributes</span></span>

<span data-ttu-id="6de3f-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="6de3f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6de3f-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6de3f-110">Child Elements</span></span>

<span data-ttu-id="6de3f-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="6de3f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6de3f-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6de3f-112">Parent Elements</span></span>

|<span data-ttu-id="6de3f-113">Element</span><span class="sxs-lookup"><span data-stu-id="6de3f-113">Element</span></span>|<span data-ttu-id="6de3f-114">Description</span><span class="sxs-lookup"><span data-stu-id="6de3f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6de3f-115">ListItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="6de3f-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="6de3f-116">Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in een rij in de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="6de3f-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6de3f-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="6de3f-117">Text Value</span></span>

<span data-ttu-id="6de3f-118">Geef het patroon dat wordt gebruikt om de opmaak van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="6de3f-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="6de3f-119">Bijvoorbeeld, kunt u dit patroon om de waarde van elke eigenschap die is van het type [System.DateTime](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="6de3f-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="6de3f-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6de3f-120">Remarks</span></span>

<span data-ttu-id="6de3f-121">Opmaaktekenreeksen kunnen worden gebruikt bij het maken van tabelweergaven, lijst met weergaven, breed weergaven of aangepaste weergaven.</span><span class="sxs-lookup"><span data-stu-id="6de3f-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="6de3f-122">Zie voor meer informatie over het opmaken van een waarde die wordt weergegeven in een weergave [weergegeven gegevens opmaak](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="6de3f-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="6de3f-123">Zie voor meer informatie over het gebruik van opmaaktekenreeksen in lijstweergaven [lijstweergave maken](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="6de3f-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6de3f-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="6de3f-124">Example</span></span>

<span data-ttu-id="6de3f-125">Het volgende voorbeeld ziet u hoe u een opmaaktekenreeks voor de waarde van de `StartTime` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="6de3f-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="6de3f-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6de3f-126">See Also</span></span>

[<span data-ttu-id="6de3f-127">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="6de3f-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="6de3f-128">ListItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="6de3f-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="6de3f-129">Schrijven van een Windows PowerShell opmaak en het bestand van het type</span><span class="sxs-lookup"><span data-stu-id="6de3f-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
