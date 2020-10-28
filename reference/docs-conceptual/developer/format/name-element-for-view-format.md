---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Naam voor Weergave (opmaak)
description: Het element Naam voor Weergave (opmaak)
ms.openlocfilehash: 5781bcdf7a0e1eb5e9c7e97bb6acc0a383dc0262
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666451"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="2fa6a-103">Het element Naam voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2fa6a-103">Name Element for View (Format)</span></span>

<span data-ttu-id="2fa6a-104">Hiermee geeft u de naam op die wordt gebruikt om de weer gave te identificeren.</span><span class="sxs-lookup"><span data-stu-id="2fa6a-104">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="2fa6a-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element (indeling) naam element (indeling)</span><span class="sxs-lookup"><span data-stu-id="2fa6a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2fa6a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2fa6a-106">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2fa6a-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="2fa6a-107">Attributes and Elements</span></span>

<span data-ttu-id="2fa6a-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Name` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="2fa6a-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="2fa6a-109">`Name`Voor elke weer gave is slechts één element toegestaan.</span><span class="sxs-lookup"><span data-stu-id="2fa6a-109">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="2fa6a-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2fa6a-110">Attributes</span></span>

<span data-ttu-id="2fa6a-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="2fa6a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2fa6a-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2fa6a-112">Child Elements</span></span>

<span data-ttu-id="2fa6a-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="2fa6a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2fa6a-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2fa6a-114">Parent Elements</span></span>

|<span data-ttu-id="2fa6a-115">Element</span><span class="sxs-lookup"><span data-stu-id="2fa6a-115">Element</span></span>|<span data-ttu-id="2fa6a-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2fa6a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2fa6a-117">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2fa6a-117">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="2fa6a-118">Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om de leden van een of meer .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="2fa6a-118">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2fa6a-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="2fa6a-119">Text Value</span></span>

<span data-ttu-id="2fa6a-120">Geef een unieke beschrijvende naam op voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="2fa6a-120">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="2fa6a-121">Deze naam kan een verwijzing bevatten naar het type weer gave (zoals een tabel weergave of lijst weergave), welk object of welke verzameling objecten de weer gave gebruiken, welke opdracht de objecten retourneert of een combi natie hiervan.</span><span class="sxs-lookup"><span data-stu-id="2fa6a-121">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="2fa6a-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2fa6a-122">Remarks</span></span>

<span data-ttu-id="2fa6a-123">Voor meer informatie over de verschillende typen weer gaven raadpleegt u de volgende onderwerpen: [tabel weergave](./creating-a-table-view.md), [lijst weergave](./creating-a-list-view.md), [brede weer](./creating-a-wide-view.md) [gave en aangepaste weer](./creating-custom-controls.md)gaven.</span><span class="sxs-lookup"><span data-stu-id="2fa6a-123">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="2fa6a-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="2fa6a-124">Example</span></span>

<span data-ttu-id="2fa6a-125">In het volgende voor beeld ziet u een- `View` element dat een tabel weergave definieert voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="2fa6a-125">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="2fa6a-126">De naam van de weer gave is ' service '.</span><span class="sxs-lookup"><span data-stu-id="2fa6a-126">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="2fa6a-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2fa6a-127">See Also</span></span>

[<span data-ttu-id="2fa6a-128">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="2fa6a-128">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2fa6a-129">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="2fa6a-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2fa6a-130">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="2fa6a-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2fa6a-131">Aangepaste besturingselementen maken</span><span class="sxs-lookup"><span data-stu-id="2fa6a-131">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="2fa6a-132">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2fa6a-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="2fa6a-133">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="2fa6a-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
