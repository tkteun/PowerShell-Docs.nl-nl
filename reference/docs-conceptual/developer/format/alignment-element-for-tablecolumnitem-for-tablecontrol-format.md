---
title: Alignment-element voor TableColumnItem voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359122"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="1c912-102">Het element Uitlijning voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1c912-102">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="1c912-103">Bepaalt hoe de gegevens in een kolom van de rij worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1c912-103">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="1c912-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) TableColumnItems element (indeling) TableColumnItem element (indeling) Alignment-element voor TableColumnItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="1c912-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1c912-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1c912-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1c912-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1c912-106">Attributes and Elements</span></span>

<span data-ttu-id="1c912-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Alignment` beschreven.</span><span class="sxs-lookup"><span data-stu-id="1c912-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1c912-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1c912-108">Attributes</span></span>

<span data-ttu-id="1c912-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="1c912-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1c912-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1c912-110">Child Elements</span></span>

<span data-ttu-id="1c912-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="1c912-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1c912-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1c912-112">Parent Elements</span></span>

|<span data-ttu-id="1c912-113">Element</span><span class="sxs-lookup"><span data-stu-id="1c912-113">Element</span></span>|<span data-ttu-id="1c912-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1c912-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1c912-115">TableColumnItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="1c912-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="1c912-116">Hiermee definieert u een label, de breedte en de uitlijning van de gegevens voor een kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="1c912-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1c912-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="1c912-117">Text Value</span></span>

<span data-ttu-id="1c912-118">Geef een van de volgende waarden op.</span><span class="sxs-lookup"><span data-stu-id="1c912-118">Specify one of the following values.</span></span> <span data-ttu-id="1c912-119">(Deze waarden zijn niet hoofdletter gevoelig.)</span><span class="sxs-lookup"><span data-stu-id="1c912-119">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="1c912-120">Hiermee worden de gegevens die worden weer gegeven in de kolom links verplaatst.</span><span class="sxs-lookup"><span data-stu-id="1c912-120">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="1c912-121">(Dit is de standaard waarde als dit element niet is opgegeven.)</span><span class="sxs-lookup"><span data-stu-id="1c912-121">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="1c912-122">Hiermee worden de gegevens die worden weer gegeven in de kolom rechts verplaatst.</span><span class="sxs-lookup"><span data-stu-id="1c912-122">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="1c912-123">Centreert de gegevens die in de kolom worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1c912-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c912-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1c912-124">Remarks</span></span>

<span data-ttu-id="1c912-125">Zie [tabel weergave](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="1c912-125">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c912-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1c912-126">See Also</span></span>

[<span data-ttu-id="1c912-127">Tabel weergave</span><span class="sxs-lookup"><span data-stu-id="1c912-127">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1c912-128">TableColumnItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="1c912-128">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
