---
title: Breedte van Element voor TableColumnHeader voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055186"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="b33e7-102">Het element Breedte voor TableColumnHeader voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b33e7-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="b33e7-103">Hiermee definieert u de breedte (in tekens) van een kolom.</span><span class="sxs-lookup"><span data-stu-id="b33e7-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="b33e7-104">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableHeaders Element voor TableControl (indeling) TableColumnHeader Element TableHeaders voor TableControl (indeling) breedte van Element voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="b33e7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b33e7-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b33e7-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b33e7-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b33e7-106">Attributes and Elements</span></span>

<span data-ttu-id="b33e7-107">De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `Width` element dat wordt gebruikt bij het definiëren van kolomkoppen.</span><span class="sxs-lookup"><span data-stu-id="b33e7-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="b33e7-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b33e7-108">Attributes</span></span>

<span data-ttu-id="b33e7-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="b33e7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b33e7-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b33e7-110">Child Elements</span></span>

<span data-ttu-id="b33e7-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="b33e7-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b33e7-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b33e7-112">Parent Elements</span></span>

|<span data-ttu-id="b33e7-113">Element</span><span class="sxs-lookup"><span data-stu-id="b33e7-113">Element</span></span>|<span data-ttu-id="b33e7-114">Description</span><span class="sxs-lookup"><span data-stu-id="b33e7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b33e7-115">TableColumnHeader-Element voor TableHeaders voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="b33e7-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="b33e7-116">Een label, de breedte en de uitlijning van de gegevens voor een kolom van de tabel definieert.</span><span class="sxs-lookup"><span data-stu-id="b33e7-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b33e7-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="b33e7-117">Text Value</span></span>

<span data-ttu-id="b33e7-118">Wanneer op alle mogelijke een breedte (in tekens) die groter is dan de lengte van de weergegeven waarden wilt opgeven.</span><span class="sxs-lookup"><span data-stu-id="b33e7-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="b33e7-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b33e7-119">Remarks</span></span>

<span data-ttu-id="b33e7-120">Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b33e7-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b33e7-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="b33e7-121">Example</span></span>

<span data-ttu-id="b33e7-122">Het volgende voorbeeld wordt een `TableColumnHeader` element waarvan u de breedte 16 tekens is.</span><span class="sxs-lookup"><span data-stu-id="b33e7-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="b33e7-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b33e7-123">See Also</span></span>

[<span data-ttu-id="b33e7-124">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="b33e7-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b33e7-125">TableColumnHeader-Element voor TableHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="b33e7-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="b33e7-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="b33e7-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
