---
title: FormatString-Element voor TableColumnItem voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845638"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="5da71-102">Het element FormatString voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5da71-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="5da71-103">Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script van de tabel wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="5da71-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="5da71-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries-Element (indeling) TableRowEntry-Element (indeling) TableColumnItems-Element (indeling) TableColumnItem-Element (indeling) FormatString-Element voor TableColumnItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="5da71-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5da71-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5da71-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5da71-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="5da71-106">Attributes and Elements</span></span>

<span data-ttu-id="5da71-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `FormatString` element.</span><span class="sxs-lookup"><span data-stu-id="5da71-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5da71-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="5da71-108">Attributes</span></span>

<span data-ttu-id="5da71-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="5da71-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5da71-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5da71-110">Child Elements</span></span>

<span data-ttu-id="5da71-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="5da71-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5da71-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5da71-112">Parent Elements</span></span>

|<span data-ttu-id="5da71-113">Element</span><span class="sxs-lookup"><span data-stu-id="5da71-113">Element</span></span>|<span data-ttu-id="5da71-114">Description</span><span class="sxs-lookup"><span data-stu-id="5da71-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5da71-115">TableColumnItem-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="5da71-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="5da71-116">Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="5da71-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5da71-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="5da71-117">Text Value</span></span>

<span data-ttu-id="5da71-118">Geef het patroon dat wordt gebruikt om de opmaak van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="5da71-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="5da71-119">Dit patroon kan bijvoorbeeld worden gebruikt om de waarde van elke eigenschap die is van het type [System.DateTime](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="5da71-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="5da71-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5da71-120">Remarks</span></span>

<span data-ttu-id="5da71-121">Opmaaktekenreeksen kunnen worden gebruikt bij het maken van tabelweergaven, lijst met weergaven, breed weergaven of aangepaste weergaven.</span><span class="sxs-lookup"><span data-stu-id="5da71-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="5da71-122">Zie voor meer informatie over het opmaken van een waarde die wordt weergegeven in een weergave [weergegeven gegevens opmaak](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="5da71-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="5da71-123">Zie voor meer informatie over de onderdelen van een tabelweergave [tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="5da71-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5da71-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="5da71-124">Example</span></span>

<span data-ttu-id="5da71-125">Het volgende voorbeeld ziet u hoe u een opmaaktekenreeks voor de waarde van de `StartTime` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="5da71-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="5da71-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5da71-126">See Also</span></span>

[<span data-ttu-id="5da71-127">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="5da71-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="5da71-128">Opmaak gegevens weergegeven</span><span class="sxs-lookup"><span data-stu-id="5da71-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="5da71-129">TableColumnItem-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="5da71-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="5da71-130">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="5da71-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
