---
ms.date: 09/13/2016
ms.topic: reference
title: Het element FormatString voor TableColumnItem voor TableControl (opmaak)
description: Het element FormatString voor TableColumnItem voor TableControl (opmaak)
ms.openlocfilehash: 3d386e61ac321c05e0b298019c2298f76b391b21
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667892"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="7d3bd-103">Het element FormatString voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7d3bd-103">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="7d3bd-104">Hiermee geeft u een indelings patroon op dat definieert hoe de eigenschap of script waarde van de tabel wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7d3bd-104">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="7d3bd-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) TableColumnItems element (indeling) TableColumnItem element (opmaak) formats element voor TableColumnItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="7d3bd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7d3bd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7d3bd-106">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d3bd-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7d3bd-107">Attributes and Elements</span></span>

<span data-ttu-id="7d3bd-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `FormatString` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="7d3bd-108">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7d3bd-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7d3bd-109">Attributes</span></span>

<span data-ttu-id="7d3bd-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="7d3bd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7d3bd-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7d3bd-111">Child Elements</span></span>

<span data-ttu-id="7d3bd-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="7d3bd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7d3bd-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7d3bd-113">Parent Elements</span></span>

|<span data-ttu-id="7d3bd-114">Element</span><span class="sxs-lookup"><span data-stu-id="7d3bd-114">Element</span></span>|<span data-ttu-id="7d3bd-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7d3bd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d3bd-116">TableColumnItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="7d3bd-116">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="7d3bd-117">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="7d3bd-117">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7d3bd-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="7d3bd-118">Text Value</span></span>

<span data-ttu-id="7d3bd-119">Geef het patroon op dat wordt gebruikt om de gegevens op te maken.</span><span class="sxs-lookup"><span data-stu-id="7d3bd-119">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="7d3bd-120">Dit patroon kan bijvoorbeeld worden gebruikt voor het opmaken van de waarde van een eigenschap van het type [System. time span](/dotnet/api/System.TimeSpan): {0: mmm} {0: dd} {0: uu}: {0: mm}.</span><span class="sxs-lookup"><span data-stu-id="7d3bd-120">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="7d3bd-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7d3bd-121">Remarks</span></span>

<span data-ttu-id="7d3bd-122">Opmaak teken reeksen kunnen worden gebruikt bij het maken van tabel weergaven, lijst weergaven, brede weer gaven of aangepaste weer gaven.</span><span class="sxs-lookup"><span data-stu-id="7d3bd-122">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="7d3bd-123">Zie voor meer informatie over het opmaken van een waarde die wordt weer gegeven in een weer gave, [weer gegeven gegevens opmaken](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="7d3bd-123">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="7d3bd-124">Zie [tabel weergave](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="7d3bd-124">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7d3bd-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="7d3bd-125">Example</span></span>

<span data-ttu-id="7d3bd-126">In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de `StartTime` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="7d3bd-126">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="7d3bd-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7d3bd-127">See Also</span></span>

[<span data-ttu-id="7d3bd-128">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="7d3bd-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7d3bd-129">Weergegeven gegevens opmaken</span><span class="sxs-lookup"><span data-stu-id="7d3bd-129">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="7d3bd-130">TableColumnItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="7d3bd-130">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="7d3bd-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="7d3bd-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
