---
title: TypeName-Element voor EntrySelectedBy voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846618"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="f116c-102">Het element TypeName voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f116c-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="f116c-103">Hiermee geeft u een .NET-type dat deze vermelding van de tabelweergave gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f116c-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="f116c-104">Er is geen limiet voor het aantal typen die kunnen worden opgegeven voor de vermelding in een tabel.</span><span class="sxs-lookup"><span data-stu-id="f116c-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="f116c-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries-Element (indeling) TableRowEntry-Element (indeling) EntrySelectedBy Element (indeling) TypeName-Element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="f116c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f116c-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f116c-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f116c-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f116c-107">Attributes and Elements</span></span>

<span data-ttu-id="f116c-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="f116c-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f116c-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f116c-109">Attributes</span></span>

<span data-ttu-id="f116c-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="f116c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f116c-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f116c-111">Child Elements</span></span>

<span data-ttu-id="f116c-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="f116c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f116c-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f116c-113">Parent Elements</span></span>

|<span data-ttu-id="f116c-114">Element</span><span class="sxs-lookup"><span data-stu-id="f116c-114">Element</span></span>|<span data-ttu-id="f116c-115">Description</span><span class="sxs-lookup"><span data-stu-id="f116c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f116c-116">EntrySelectedBy-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="f116c-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="f116c-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze vermelding of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f116c-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f116c-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="f116c-118">Text Value</span></span>

<span data-ttu-id="f116c-119">Geef de naam van het .NET-type.</span><span class="sxs-lookup"><span data-stu-id="f116c-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="f116c-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f116c-120">Remarks</span></span>

<span data-ttu-id="f116c-121">Elk lijstitem moet hebben ten minste één naam, selectie instellen of selectievoorwaarde gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="f116c-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="f116c-122">Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f116c-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f116c-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f116c-123">See Also</span></span>

[<span data-ttu-id="f116c-124">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="f116c-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f116c-125">EntrySelectedBy-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="f116c-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="f116c-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="f116c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
