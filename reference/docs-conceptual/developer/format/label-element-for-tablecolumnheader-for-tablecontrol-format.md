---
title: Label element voor TableColumnHeader voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356040"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="2c583-102">Het element Label voor TableColumnHeader voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2c583-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="2c583-103">Hiermee wordt het label gedefinieerd dat boven aan een kolom wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2c583-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="2c583-104">Dit element wordt gebruikt bij het definiëren van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="2c583-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="2c583-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) TableControl element (Format) TableHeaders element voor TableControl (Format) TableColumnHeader-element voor TableHeaders voor TableControl (Format) voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="2c583-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2c583-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="2c583-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="2c583-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="2c583-107">Attributes and Elements</span></span>

<span data-ttu-id="2c583-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Label` beschreven.</span><span class="sxs-lookup"><span data-stu-id="2c583-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="2c583-109">Voor elke kolom is slechts één label toegestaan.</span><span class="sxs-lookup"><span data-stu-id="2c583-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="2c583-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2c583-110">Attributes</span></span>

<span data-ttu-id="2c583-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="2c583-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2c583-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2c583-112">Child Elements</span></span>

<span data-ttu-id="2c583-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="2c583-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2c583-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2c583-114">Parent Elements</span></span>

|<span data-ttu-id="2c583-115">Element</span><span class="sxs-lookup"><span data-stu-id="2c583-115">Element</span></span>|<span data-ttu-id="2c583-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2c583-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2c583-117">TableColumnHeader-element voor TableHeaders voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="2c583-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="2c583-118">Hiermee definieert u een label, de breedte en de uitlijning van de gegevens voor een kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="2c583-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2c583-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="2c583-119">Text Value</span></span>

<span data-ttu-id="2c583-120">Geef de tekst op die boven aan de kolom van de tabel wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2c583-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="2c583-121">Er zijn geen beperkte tekens voor het kolom Label.</span><span class="sxs-lookup"><span data-stu-id="2c583-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="2c583-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2c583-122">Remarks</span></span>

<span data-ttu-id="2c583-123">Als er geen label is opgegeven, wordt de naam van de eigenschap waarvan de waarde wordt weer gegeven in de rijen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2c583-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="2c583-124">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="2c583-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2c583-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="2c583-125">Example</span></span>

<span data-ttu-id="2c583-126">In dit voor beeld ziet u een `TableColumnHeader` element waarvan het label ' kolom 1 ' is.</span><span class="sxs-lookup"><span data-stu-id="2c583-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="2c583-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2c583-127">See Also</span></span>

[<span data-ttu-id="2c583-128">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="2c583-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2c583-129">TableColumnHeader-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="2c583-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="2c583-130">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="2c583-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
