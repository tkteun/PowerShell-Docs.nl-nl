---
title: TypeName-element voor ViewSelectedBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353429"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="610de-102">Het element TypeName voor ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="610de-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="610de-103">Hiermee geeft u een .NET-object op dat wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="610de-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="610de-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) ViewSelectedBy element (Format) voor ViewSelectedBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="610de-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="610de-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="610de-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="610de-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="610de-106">Attributes and Elements</span></span>

<span data-ttu-id="610de-107">In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het element `TypeName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="610de-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="610de-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="610de-108">Attributes</span></span>

<span data-ttu-id="610de-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="610de-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="610de-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="610de-110">Child Elements</span></span>

<span data-ttu-id="610de-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="610de-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="610de-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="610de-112">Parent Elements</span></span>

|<span data-ttu-id="610de-113">Element</span><span class="sxs-lookup"><span data-stu-id="610de-113">Element</span></span>|<span data-ttu-id="610de-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="610de-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="610de-115">ViewSelectedBy-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="610de-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="610de-116">Hiermee worden de .NET-objecten gedefinieerd die worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="610de-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="610de-117">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="610de-117">Text Value</span></span>

<span data-ttu-id="610de-118">Geef de volledig gekwalificeerde naam van het .NET-type op, bijvoorbeeld `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="610de-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="610de-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="610de-119">Remarks</span></span>

<span data-ttu-id="610de-120">Zie [een tabel weergave maken](./creating-a-table-view.md), een [lijst weergave](./creating-a-list-view.md)maken, [een brede weer gave](./creating-a-wide-view.md)en [aangepaste weergave onderdelen](./creating-custom-controls.md)maken voor meer informatie over hoe dit element wordt gebruikt in verschillende weer gaven.</span><span class="sxs-lookup"><span data-stu-id="610de-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="610de-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="610de-121">Example</span></span>

<span data-ttu-id="610de-122">In het volgende voor beeld ziet u hoe u het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) opgeeft voor een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="610de-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="610de-123">Hetzelfde schema wordt gebruikt voor tabel-, brede en aangepaste weer gaven.</span><span class="sxs-lookup"><span data-stu-id="610de-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="610de-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="610de-124">See Also</span></span>

[<span data-ttu-id="610de-125">Een lijst weergave maken</span><span class="sxs-lookup"><span data-stu-id="610de-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="610de-126">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="610de-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="610de-127">Een brede weer gave maken</span><span class="sxs-lookup"><span data-stu-id="610de-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="610de-128">Aangepaste besturings elementen maken</span><span class="sxs-lookup"><span data-stu-id="610de-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="610de-129">ViewSelectedBy-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="610de-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="610de-130">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="610de-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
