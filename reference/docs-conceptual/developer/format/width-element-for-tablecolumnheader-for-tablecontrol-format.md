---
title: Width-element voor TableColumnHeader voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "84514853"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="07f2e-102">Het element Breedte voor TableColumnHeader voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="07f2e-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="07f2e-103">Hiermee wordt de breedte (in tekens) van een kolom gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="07f2e-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="07f2e-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableHeaders element voor TableControl (indeling) TableColumnHeader element TableHeaders voor TableControl (indeling) breedte-element voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="07f2e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="07f2e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="07f2e-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="07f2e-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="07f2e-106">Attributes and Elements</span></span>

<span data-ttu-id="07f2e-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Width` element beschreven die worden gebruikt bij het definiëren van kolom koppen.</span><span class="sxs-lookup"><span data-stu-id="07f2e-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="07f2e-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="07f2e-108">Attributes</span></span>

<span data-ttu-id="07f2e-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="07f2e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="07f2e-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="07f2e-110">Child Elements</span></span>

<span data-ttu-id="07f2e-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="07f2e-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="07f2e-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="07f2e-112">Parent Elements</span></span>

|<span data-ttu-id="07f2e-113">Element</span><span class="sxs-lookup"><span data-stu-id="07f2e-113">Element</span></span>|<span data-ttu-id="07f2e-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="07f2e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07f2e-115">TableColumnHeader-element voor TableHeaders voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="07f2e-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="07f2e-116">Hiermee definieert u een label, breedte en uitlijning van de gegevens voor een kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="07f2e-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="07f2e-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="07f2e-117">Text Value</span></span>

<span data-ttu-id="07f2e-118">Als dat mogelijk is, geeft u een breedte (in tekens) op die groter is dan de lengte van de weer gegeven eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="07f2e-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="07f2e-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="07f2e-119">Remarks</span></span>

<span data-ttu-id="07f2e-120">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="07f2e-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="07f2e-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="07f2e-121">Example</span></span>

<span data-ttu-id="07f2e-122">In het volgende voor beeld ziet u een `TableColumnHeader` element waarvan de breedte 16 tekens is.</span><span class="sxs-lookup"><span data-stu-id="07f2e-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="07f2e-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="07f2e-123">See Also</span></span>

[<span data-ttu-id="07f2e-124">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="07f2e-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="07f2e-125">TableColumnHeader-element voor TableHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="07f2e-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="07f2e-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="07f2e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
