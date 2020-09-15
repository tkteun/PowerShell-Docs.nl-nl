---
title: TypeName-element voor SelectionCondition voor EntrySelectedBy voor TableControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b9367f0ea659b9dce8fe200a5a08873d53bc03a8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772583"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="3ee99-102">Het element TypeName voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3ee99-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="3ee99-103">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="3ee99-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="3ee99-104">Wanneer dit type aanwezig is, wordt voldaan aan de voor waarde en wordt de tabelrij gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3ee99-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="3ee99-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element voor TableRowEntry (Format) SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (Format) voor SelectionCondition voor EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3ee99-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3ee99-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3ee99-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3ee99-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="3ee99-107">Attributes and Elements</span></span>

<span data-ttu-id="3ee99-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="3ee99-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3ee99-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="3ee99-109">Attributes</span></span>

<span data-ttu-id="3ee99-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="3ee99-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3ee99-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3ee99-111">Child Elements</span></span>

<span data-ttu-id="3ee99-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="3ee99-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3ee99-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3ee99-113">Parent Elements</span></span>

|<span data-ttu-id="3ee99-114">Element</span><span class="sxs-lookup"><span data-stu-id="3ee99-114">Element</span></span>|<span data-ttu-id="3ee99-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3ee99-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ee99-116">SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="3ee99-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="3ee99-117">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze tabelrij.</span><span class="sxs-lookup"><span data-stu-id="3ee99-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3ee99-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="3ee99-118">Text Value</span></span>

<span data-ttu-id="3ee99-119">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="3ee99-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ee99-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3ee99-120">Remarks</span></span>

<span data-ttu-id="3ee99-121">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3ee99-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="3ee99-122">Zie voor [waarden definiëren voor wanneer een weergave vermelding of-item wordt gebruikt](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="3ee99-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="3ee99-123">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="3ee99-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3ee99-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3ee99-124">See Also</span></span>

[<span data-ttu-id="3ee99-125">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="3ee99-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="3ee99-126">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="3ee99-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3ee99-127">SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="3ee99-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="3ee99-128">SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="3ee99-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="3ee99-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="3ee99-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
