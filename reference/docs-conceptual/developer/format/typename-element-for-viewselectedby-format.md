---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor ViewSelectedBy (opmaak)
description: Het element TypeName voor ViewSelectedBy (opmaak)
ms.openlocfilehash: 62edc2fe4b4c1c5f1b17dd2f8b0943f28ff5dfb7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667722"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="e647b-103">Het element TypeName voor ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e647b-103">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="e647b-104">Hiermee geeft u een .NET-object op dat wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="e647b-104">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="e647b-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) ViewSelectedBy element (Format) voor ViewSelectedBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e647b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e647b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e647b-106">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e647b-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e647b-107">Attributes and Elements</span></span>

<span data-ttu-id="e647b-108">In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="e647b-108">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e647b-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e647b-109">Attributes</span></span>

<span data-ttu-id="e647b-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="e647b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e647b-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e647b-111">Child Elements</span></span>

<span data-ttu-id="e647b-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="e647b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e647b-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e647b-113">Parent Elements</span></span>

|<span data-ttu-id="e647b-114">Element</span><span class="sxs-lookup"><span data-stu-id="e647b-114">Element</span></span>|<span data-ttu-id="e647b-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e647b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e647b-116">Het element ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e647b-116">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="e647b-117">Hiermee worden de .NET-objecten gedefinieerd die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="e647b-117">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e647b-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="e647b-118">Text Value</span></span>

<span data-ttu-id="e647b-119">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="e647b-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e647b-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e647b-120">Remarks</span></span>

<span data-ttu-id="e647b-121">Zie [een tabel weergave maken](./creating-a-table-view.md), een [lijst weergave](./creating-a-list-view.md)maken, [een brede weer gave](./creating-a-wide-view.md)en [aangepaste weergave onderdelen](./creating-custom-controls.md)maken voor meer informatie over hoe dit element wordt gebruikt in verschillende weer gaven.</span><span class="sxs-lookup"><span data-stu-id="e647b-121">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="e647b-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e647b-122">Example</span></span>

<span data-ttu-id="e647b-123">In het volgende voor beeld ziet u hoe u het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) opgeeft voor een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="e647b-123">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="e647b-124">Hetzelfde schema wordt gebruikt voor tabel-, brede en aangepaste weer gaven.</span><span class="sxs-lookup"><span data-stu-id="e647b-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="e647b-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e647b-125">See Also</span></span>

[<span data-ttu-id="e647b-126">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="e647b-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e647b-127">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="e647b-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e647b-128">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="e647b-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e647b-129">Aangepaste besturingselementen maken</span><span class="sxs-lookup"><span data-stu-id="e647b-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="e647b-130">Het element ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e647b-130">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="e647b-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e647b-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
