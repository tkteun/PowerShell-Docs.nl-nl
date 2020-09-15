---
title: Naam element voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 670b089f850fa4b39b7b100ca1e1ce45b05ea72d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773229"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="72ebf-102">Het element Naam voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="72ebf-102">Name Element for View (Format)</span></span>

<span data-ttu-id="72ebf-103">Hiermee geeft u de naam op die wordt gebruikt om de weer gave te identificeren.</span><span class="sxs-lookup"><span data-stu-id="72ebf-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="72ebf-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element (indeling) naam element (indeling)</span><span class="sxs-lookup"><span data-stu-id="72ebf-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="72ebf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="72ebf-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="72ebf-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="72ebf-106">Attributes and Elements</span></span>

<span data-ttu-id="72ebf-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Name` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="72ebf-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="72ebf-108">`Name`Voor elke weer gave is slechts één element toegestaan.</span><span class="sxs-lookup"><span data-stu-id="72ebf-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="72ebf-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="72ebf-109">Attributes</span></span>

<span data-ttu-id="72ebf-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="72ebf-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="72ebf-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="72ebf-111">Child Elements</span></span>

<span data-ttu-id="72ebf-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="72ebf-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="72ebf-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="72ebf-113">Parent Elements</span></span>

|<span data-ttu-id="72ebf-114">Element</span><span class="sxs-lookup"><span data-stu-id="72ebf-114">Element</span></span>|<span data-ttu-id="72ebf-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="72ebf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="72ebf-116">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="72ebf-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="72ebf-117">Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om de leden van een of meer .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="72ebf-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="72ebf-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="72ebf-118">Text Value</span></span>

<span data-ttu-id="72ebf-119">Geef een unieke beschrijvende naam op voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="72ebf-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="72ebf-120">Deze naam kan een verwijzing bevatten naar het type weer gave (zoals een tabel weergave of lijst weergave), welk object of welke verzameling objecten de weer gave gebruiken, welke opdracht de objecten retourneert of een combi natie hiervan.</span><span class="sxs-lookup"><span data-stu-id="72ebf-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="72ebf-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="72ebf-121">Remarks</span></span>

<span data-ttu-id="72ebf-122">Voor meer informatie over de verschillende typen weer gaven raadpleegt u de volgende onderwerpen: [tabel weergave](./creating-a-table-view.md), [lijst weergave](./creating-a-list-view.md), [brede weer](./creating-a-wide-view.md) [gave en aangepaste weer](./creating-custom-controls.md)gaven.</span><span class="sxs-lookup"><span data-stu-id="72ebf-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="72ebf-123">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="72ebf-123">Example</span></span>

<span data-ttu-id="72ebf-124">In het volgende voor beeld ziet u een- `View` element dat een tabel weergave definieert voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="72ebf-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="72ebf-125">De naam van de weer gave is ' service '.</span><span class="sxs-lookup"><span data-stu-id="72ebf-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="72ebf-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="72ebf-126">See Also</span></span>

[<span data-ttu-id="72ebf-127">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="72ebf-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="72ebf-128">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="72ebf-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="72ebf-129">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="72ebf-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="72ebf-130">Aangepaste besturingselementen maken</span><span class="sxs-lookup"><span data-stu-id="72ebf-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="72ebf-131">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="72ebf-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="72ebf-132">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="72ebf-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
