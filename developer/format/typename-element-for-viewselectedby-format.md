---
title: TypeName-Element voor ViewSelectedBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083753"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="5d03f-102">Het element TypeName voor ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5d03f-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="5d03f-103">Hiermee geeft u een .NET-object dat door de weergave wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="5d03f-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="5d03f-104">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ViewSelectedBy-Element (indeling) TypeName Element voor ViewSelectedBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="5d03f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5d03f-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5d03f-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5d03f-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="5d03f-106">Attributes and Elements</span></span>

<span data-ttu-id="5d03f-107">De volgende secties beschrijven kenmerken, onderliggende elementen en de bovenliggende elementen van de `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="5d03f-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5d03f-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="5d03f-108">Attributes</span></span>

<span data-ttu-id="5d03f-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="5d03f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5d03f-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5d03f-110">Child Elements</span></span>

<span data-ttu-id="5d03f-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="5d03f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5d03f-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5d03f-112">Parent Elements</span></span>

|<span data-ttu-id="5d03f-113">Element</span><span class="sxs-lookup"><span data-stu-id="5d03f-113">Element</span></span>|<span data-ttu-id="5d03f-114">Description</span><span class="sxs-lookup"><span data-stu-id="5d03f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5d03f-115">ViewSelectedBy-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="5d03f-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="5d03f-116">Hiermee definieert u de .NET-objecten die worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="5d03f-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5d03f-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="5d03f-117">Text Value</span></span>

<span data-ttu-id="5d03f-118">Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="5d03f-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5d03f-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5d03f-119">Remarks</span></span>

<span data-ttu-id="5d03f-120">Zie voor meer informatie over hoe dit element wordt gebruikt in verschillende weergaven, [het maken van een tabelweergave](./creating-a-table-view.md), [het maken van een lijstweergave](./creating-a-list-view.md), [het maken van een brede weergave](./creating-a-wide-view.md), en [ Onderdelen van de aangepaste weergave](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="5d03f-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="5d03f-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="5d03f-121">Example</span></span>

<span data-ttu-id="5d03f-122">Het volgende voorbeeld ziet u hoe u de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) -object voor een lijst weergeven.</span><span class="sxs-lookup"><span data-stu-id="5d03f-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="5d03f-123">Hetzelfde schema wordt gebruikt voor de tabel, breed en aangepaste weergaven.</span><span class="sxs-lookup"><span data-stu-id="5d03f-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="5d03f-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5d03f-124">See Also</span></span>

[<span data-ttu-id="5d03f-125">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="5d03f-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5d03f-126">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="5d03f-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="5d03f-127">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="5d03f-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="5d03f-128">Het maken van aangepaste besturingselementen</span><span class="sxs-lookup"><span data-stu-id="5d03f-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="5d03f-129">ViewSelectedBy-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="5d03f-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="5d03f-130">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d03f-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
