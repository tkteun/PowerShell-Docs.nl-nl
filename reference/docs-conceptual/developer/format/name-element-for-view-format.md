---
title: Naam element voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354269"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="bbea6-102">Het element Naam voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="bbea6-102">Name Element for View (Format)</span></span>

<span data-ttu-id="bbea6-103">Hiermee geeft u de naam op die wordt gebruikt om de weer gave te identificeren.</span><span class="sxs-lookup"><span data-stu-id="bbea6-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="bbea6-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element (indeling) naam element (indeling)</span><span class="sxs-lookup"><span data-stu-id="bbea6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bbea6-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="bbea6-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bbea6-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="bbea6-106">Attributes and Elements</span></span>

<span data-ttu-id="bbea6-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `Name` beschreven.</span><span class="sxs-lookup"><span data-stu-id="bbea6-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="bbea6-108">Voor elke weer gave is slechts één `Name` element toegestaan.</span><span class="sxs-lookup"><span data-stu-id="bbea6-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="bbea6-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="bbea6-109">Attributes</span></span>

<span data-ttu-id="bbea6-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="bbea6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bbea6-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="bbea6-111">Child Elements</span></span>

<span data-ttu-id="bbea6-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="bbea6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bbea6-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="bbea6-113">Parent Elements</span></span>

|<span data-ttu-id="bbea6-114">Element</span><span class="sxs-lookup"><span data-stu-id="bbea6-114">Element</span></span>|<span data-ttu-id="bbea6-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bbea6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bbea6-116">Element weer geven (indeling)</span><span class="sxs-lookup"><span data-stu-id="bbea6-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="bbea6-117">Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om de leden van een of meer .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="bbea6-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bbea6-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="bbea6-118">Text Value</span></span>

<span data-ttu-id="bbea6-119">Geef een unieke beschrijvende naam op voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="bbea6-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="bbea6-120">Deze naam kan een verwijzing bevatten naar het type weer gave (zoals een tabel weergave of lijst weergave), welk object of welke verzameling objecten de weer gave gebruiken, welke opdracht de objecten retourneert of een combi natie hiervan.</span><span class="sxs-lookup"><span data-stu-id="bbea6-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="bbea6-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="bbea6-121">Remarks</span></span>

<span data-ttu-id="bbea6-122">Voor meer informatie over de verschillende typen weer gaven raadpleegt u de volgende onderwerpen: [tabel weergave](./creating-a-table-view.md), [lijst weergave](./creating-a-list-view.md), [brede weer](./creating-a-wide-view.md) [gave en aangepaste weer](./creating-custom-controls.md)gaven.</span><span class="sxs-lookup"><span data-stu-id="bbea6-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="bbea6-123">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="bbea6-123">Example</span></span>

<span data-ttu-id="bbea6-124">In het volgende voor beeld ziet u een `View`-element dat een tabel weergave definieert voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="bbea6-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="bbea6-125">De naam van de weer gave is ' service '.</span><span class="sxs-lookup"><span data-stu-id="bbea6-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="bbea6-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bbea6-126">See Also</span></span>

[<span data-ttu-id="bbea6-127">Een lijst weergave maken</span><span class="sxs-lookup"><span data-stu-id="bbea6-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="bbea6-128">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="bbea6-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="bbea6-129">Een brede weer gave maken</span><span class="sxs-lookup"><span data-stu-id="bbea6-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="bbea6-130">Aangepaste besturings elementen maken</span><span class="sxs-lookup"><span data-stu-id="bbea6-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="bbea6-131">Element weer geven (indeling)</span><span class="sxs-lookup"><span data-stu-id="bbea6-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="bbea6-132">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="bbea6-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
