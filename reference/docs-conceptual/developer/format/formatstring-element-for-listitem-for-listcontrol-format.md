---
title: Element formats Tring voor lijst item voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354535"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="07528-102">Het element FormatString voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="07528-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="07528-103">Geeft een opmaak patroon aan dat definieert hoe de eigenschap of script waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="07528-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="07528-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) element (Format) List item voor ListControl (indeling) element entry View voor ListControl (Format) List items element voor ListControl Lijst item-element voor ListControl (Format) formats-element voor lijst item voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="07528-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="07528-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="07528-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="07528-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="07528-106">Attributes and Elements</span></span>

<span data-ttu-id="07528-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `FormatString` beschreven.</span><span class="sxs-lookup"><span data-stu-id="07528-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="07528-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="07528-108">Attributes</span></span>

<span data-ttu-id="07528-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="07528-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="07528-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="07528-110">Child Elements</span></span>

<span data-ttu-id="07528-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="07528-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="07528-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="07528-112">Parent Elements</span></span>

|<span data-ttu-id="07528-113">Element</span><span class="sxs-lookup"><span data-stu-id="07528-113">Element</span></span>|<span data-ttu-id="07528-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="07528-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07528-115">Lijst item-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="07528-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="07528-116">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="07528-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="07528-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="07528-117">Text Value</span></span>

<span data-ttu-id="07528-118">Geef het patroon op dat wordt gebruikt om de gegevens op te maken.</span><span class="sxs-lookup"><span data-stu-id="07528-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="07528-119">U kunt dit patroon bijvoorbeeld gebruiken om de waarde van een eigenschap van het type [System. time span](/dotnet/api/System.TimeSpan): {0: mmm} {0: dd} {0: uu}: {0: mm} in te delen.</span><span class="sxs-lookup"><span data-stu-id="07528-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="07528-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="07528-120">Remarks</span></span>

<span data-ttu-id="07528-121">Opmaak teken reeksen kunnen worden gebruikt bij het maken van tabel weergaven, lijst weergaven, brede weer gaven of aangepaste weer gaven.</span><span class="sxs-lookup"><span data-stu-id="07528-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="07528-122">Zie voor meer informatie over het opmaken van een waarde die wordt weer gegeven in een weer gave, [weer gegeven gegevens opmaken](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="07528-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="07528-123">Zie [lijst weergave maken](./creating-a-list-view.md)voor meer informatie over het gebruik van opmaak teken reeksen in lijst weergaven.</span><span class="sxs-lookup"><span data-stu-id="07528-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="07528-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="07528-124">Example</span></span>

<span data-ttu-id="07528-125">In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de eigenschap `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="07528-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="07528-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="07528-126">See Also</span></span>

[<span data-ttu-id="07528-127">Een lijst weergave maken</span><span class="sxs-lookup"><span data-stu-id="07528-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="07528-128">Lijst item-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="07528-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="07528-129">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="07528-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
