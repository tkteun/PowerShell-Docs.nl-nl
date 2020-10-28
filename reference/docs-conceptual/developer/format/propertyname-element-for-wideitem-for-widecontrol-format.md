---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor WideItem voor WideControl (opmaak)
description: Het element PropertyName voor WideItem voor WideControl (opmaak)
ms.openlocfilehash: 1d4d5eaf7708dfbd7997122fac156a36487538ea
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665614"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="c1963-103">Het element PropertyName voor WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1963-103">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="c1963-104">Hiermee geeft u de eigenschap op van het object waarvan de waarde wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="c1963-104">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="c1963-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) WideItem element (indeling) eigenschap Naam element voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="c1963-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c1963-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c1963-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1963-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c1963-107">Attributes and Elements</span></span>

<span data-ttu-id="c1963-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="c1963-108">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1963-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c1963-109">Attributes</span></span>

<span data-ttu-id="c1963-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="c1963-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c1963-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c1963-111">Child Elements</span></span>

<span data-ttu-id="c1963-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="c1963-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c1963-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c1963-113">Parent Elements</span></span>

|<span data-ttu-id="c1963-114">Element</span><span class="sxs-lookup"><span data-stu-id="c1963-114">Element</span></span>|<span data-ttu-id="c1963-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c1963-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1963-116">WideItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c1963-116">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="c1963-117">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="c1963-117">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c1963-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="c1963-118">Text Value</span></span>

<span data-ttu-id="c1963-119">Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c1963-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1963-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c1963-120">Remarks</span></span>

<span data-ttu-id="c1963-121">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="c1963-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c1963-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c1963-122">Example</span></span>

<span data-ttu-id="c1963-123">In dit voor beeld ziet u een breed overzicht waarin de waarde van de eigenschap proces naam van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c1963-123">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c1963-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c1963-124">See Also</span></span>

[<span data-ttu-id="c1963-125">WideItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c1963-125">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="c1963-126">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="c1963-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c1963-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c1963-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
