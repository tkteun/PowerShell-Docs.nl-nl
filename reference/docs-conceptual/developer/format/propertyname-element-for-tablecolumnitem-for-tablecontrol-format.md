---
title: Het element PropertyName voor TableColumnItem voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353996"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="a82ff-102">Het element PropertyName voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a82ff-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="a82ff-103">Hiermee geeft u de eigenschap op waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="a82ff-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="a82ff-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) TableColumnItems element (indeling) TableColumnItem element (indeling) Het element PropertyName voor TableColumnItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="a82ff-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a82ff-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a82ff-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a82ff-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a82ff-106">Attributes and Elements</span></span>

<span data-ttu-id="a82ff-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `PropertyName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="a82ff-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a82ff-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a82ff-108">Attributes</span></span>

<span data-ttu-id="a82ff-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="a82ff-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a82ff-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a82ff-110">Child Elements</span></span>

<span data-ttu-id="a82ff-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="a82ff-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a82ff-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a82ff-112">Parent Elements</span></span>

|<span data-ttu-id="a82ff-113">Element</span><span class="sxs-lookup"><span data-stu-id="a82ff-113">Element</span></span>|<span data-ttu-id="a82ff-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a82ff-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a82ff-115">TableColumnItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a82ff-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="a82ff-116">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="a82ff-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a82ff-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="a82ff-117">Text Value</span></span>

<span data-ttu-id="a82ff-118">Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a82ff-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="a82ff-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a82ff-119">Remarks</span></span>

<span data-ttu-id="a82ff-120">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="a82ff-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a82ff-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="a82ff-121">Example</span></span>

<span data-ttu-id="a82ff-122">Dit voor beeld toont een `TableColumnItem`-element waarmee de eigenschap `Status` van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a82ff-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="a82ff-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a82ff-123">See Also</span></span>

[<span data-ttu-id="a82ff-124">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="a82ff-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a82ff-125">TableColumnItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a82ff-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="a82ff-126">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="a82ff-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
