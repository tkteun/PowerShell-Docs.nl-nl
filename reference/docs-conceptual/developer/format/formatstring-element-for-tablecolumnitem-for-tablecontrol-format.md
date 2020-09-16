---
title: Element formats Tring voor TableColumnItem voor TableControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 848583e697d0ab7bd5b017c14c47aba3c51a3c17
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781542"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="420c0-102">Het element FormatString voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="420c0-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="420c0-103">Hiermee geeft u een indelings patroon op dat definieert hoe de eigenschap of script waarde van de tabel wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="420c0-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="420c0-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) TableColumnItems element (indeling) TableColumnItem element (opmaak) formats element voor TableColumnItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="420c0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="420c0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="420c0-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="420c0-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="420c0-106">Attributes and Elements</span></span>

<span data-ttu-id="420c0-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `FormatString` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="420c0-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="420c0-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="420c0-108">Attributes</span></span>

<span data-ttu-id="420c0-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="420c0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="420c0-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="420c0-110">Child Elements</span></span>

<span data-ttu-id="420c0-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="420c0-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="420c0-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="420c0-112">Parent Elements</span></span>

|<span data-ttu-id="420c0-113">Element</span><span class="sxs-lookup"><span data-stu-id="420c0-113">Element</span></span>|<span data-ttu-id="420c0-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="420c0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="420c0-115">TableColumnItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="420c0-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="420c0-116">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="420c0-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="420c0-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="420c0-117">Text Value</span></span>

<span data-ttu-id="420c0-118">Geef het patroon op dat wordt gebruikt om de gegevens op te maken.</span><span class="sxs-lookup"><span data-stu-id="420c0-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="420c0-119">Dit patroon kan bijvoorbeeld worden gebruikt voor het opmaken van de waarde van een eigenschap van het type [System. time span](/dotnet/api/System.TimeSpan): {0: mmm} {0: dd} {0: uu}: {0: mm}.</span><span class="sxs-lookup"><span data-stu-id="420c0-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="420c0-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="420c0-120">Remarks</span></span>

<span data-ttu-id="420c0-121">Opmaak teken reeksen kunnen worden gebruikt bij het maken van tabel weergaven, lijst weergaven, brede weer gaven of aangepaste weer gaven.</span><span class="sxs-lookup"><span data-stu-id="420c0-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="420c0-122">Zie voor meer informatie over het opmaken van een waarde die wordt weer gegeven in een weer gave, [weer gegeven gegevens opmaken](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="420c0-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="420c0-123">Zie [tabel weergave](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="420c0-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="420c0-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="420c0-124">Example</span></span>

<span data-ttu-id="420c0-125">In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de `StartTime` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="420c0-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="420c0-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="420c0-126">See Also</span></span>

[<span data-ttu-id="420c0-127">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="420c0-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="420c0-128">Weergegeven gegevens opmaken</span><span class="sxs-lookup"><span data-stu-id="420c0-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="420c0-129">TableColumnItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="420c0-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="420c0-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="420c0-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
