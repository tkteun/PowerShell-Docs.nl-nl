---
title: PropertyName-Element voor WideItem voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064642"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="84c79-102">Het element PropertyName voor WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="84c79-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="84c79-103">Hiermee geeft u de eigenschap van het object waarvan de waarde wordt weergegeven in de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="84c79-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="84c79-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry Element (indeling) WideItem-Element (indeling) PropertyName-Element voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="84c79-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="84c79-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="84c79-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="84c79-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="84c79-106">Attributes and Elements</span></span>

<span data-ttu-id="84c79-107">De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="84c79-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="84c79-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="84c79-108">Attributes</span></span>

<span data-ttu-id="84c79-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="84c79-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="84c79-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="84c79-110">Child Elements</span></span>

<span data-ttu-id="84c79-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="84c79-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="84c79-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="84c79-112">Parent Elements</span></span>

|<span data-ttu-id="84c79-113">Element</span><span class="sxs-lookup"><span data-stu-id="84c79-113">Element</span></span>|<span data-ttu-id="84c79-114">Description</span><span class="sxs-lookup"><span data-stu-id="84c79-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84c79-115">WideItem-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="84c79-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="84c79-116">De eigenschap of het script waarvan de waarde wordt weergegeven in de brede weergave definieert.</span><span class="sxs-lookup"><span data-stu-id="84c79-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="84c79-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="84c79-117">Text Value</span></span>

<span data-ttu-id="84c79-118">Geef de naam van de eigenschap waarvan de waarde wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="84c79-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="84c79-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="84c79-119">Remarks</span></span>

<span data-ttu-id="84c79-120">Zie voor meer informatie over de onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="84c79-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="84c79-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="84c79-121">Example</span></span>

<span data-ttu-id="84c79-122">In dit voorbeeld ziet u een breed overzicht waarin de waarde van de procesnaam-eigenschap van de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span><span class="sxs-lookup"><span data-stu-id="84c79-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="84c79-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="84c79-123">See Also</span></span>

[<span data-ttu-id="84c79-124">WideItem-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="84c79-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="84c79-125">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="84c79-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="84c79-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="84c79-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
