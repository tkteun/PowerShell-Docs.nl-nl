---
title: Element een label voor TableColumnHeader voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065747"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="0955b-102">Het element Label voor TableColumnHeader voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0955b-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="0955b-103">Hiermee definieert u het label dat wordt weergegeven aan de bovenkant van een kolom.</span><span class="sxs-lookup"><span data-stu-id="0955b-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="0955b-104">Dit element wordt gebruikt bij het definiëren van een tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="0955b-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="0955b-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableHeaders Element voor TableControl (indeling) TableColumnHeader-Element voor TableHeaders voor TableControl (indeling) Label-Element voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="0955b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0955b-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="0955b-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="0955b-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="0955b-107">Attributes and Elements</span></span>

<span data-ttu-id="0955b-108">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `Label` element.</span><span class="sxs-lookup"><span data-stu-id="0955b-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="0955b-109">Slechts één label is toegestaan voor elke kolom.</span><span class="sxs-lookup"><span data-stu-id="0955b-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="0955b-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="0955b-110">Attributes</span></span>

<span data-ttu-id="0955b-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="0955b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0955b-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0955b-112">Child Elements</span></span>

<span data-ttu-id="0955b-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="0955b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0955b-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0955b-114">Parent Elements</span></span>

|<span data-ttu-id="0955b-115">Element</span><span class="sxs-lookup"><span data-stu-id="0955b-115">Element</span></span>|<span data-ttu-id="0955b-116">Description</span><span class="sxs-lookup"><span data-stu-id="0955b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0955b-117">TableColumnHeader-Element voor TableHeaders voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="0955b-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="0955b-118">Een label, de breedte en de uitlijning van de gegevens voor een kolom van de tabel definieert.</span><span class="sxs-lookup"><span data-stu-id="0955b-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0955b-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="0955b-119">Text Value</span></span>

<span data-ttu-id="0955b-120">Geef de tekst die wordt weergegeven aan de bovenkant van de kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="0955b-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="0955b-121">Er zijn geen tekens voor het label van de kolom.</span><span class="sxs-lookup"><span data-stu-id="0955b-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="0955b-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0955b-122">Remarks</span></span>

<span data-ttu-id="0955b-123">Als u geen naam opgeeft, wordt de naam van de eigenschap waarvan de waarde wordt weergegeven in de rijen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0955b-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="0955b-124">Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="0955b-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0955b-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="0955b-125">Example</span></span>

<span data-ttu-id="0955b-126">In dit voorbeeld ziet u een `TableColumnHeader` element waarvan het label 'Kolom 1' is.</span><span class="sxs-lookup"><span data-stu-id="0955b-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="0955b-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0955b-127">See Also</span></span>

[<span data-ttu-id="0955b-128">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="0955b-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0955b-129">TableColumnHeader-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="0955b-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="0955b-130">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="0955b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
