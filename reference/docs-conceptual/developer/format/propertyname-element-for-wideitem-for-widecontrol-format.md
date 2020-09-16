---
title: Het element PropertyName voor WideItem voor WideControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7728f960a67faa99eaafb4a4934674e119b8af27
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780471"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="2d731-102">Het element PropertyName voor WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2d731-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="2d731-103">Hiermee geeft u de eigenschap op van het object waarvan de waarde wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="2d731-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="2d731-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) WideItem element (indeling) eigenschap Naam element voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="2d731-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2d731-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2d731-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2d731-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="2d731-106">Attributes and Elements</span></span>

<span data-ttu-id="2d731-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="2d731-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2d731-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2d731-108">Attributes</span></span>

<span data-ttu-id="2d731-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="2d731-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2d731-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2d731-110">Child Elements</span></span>

<span data-ttu-id="2d731-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="2d731-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2d731-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2d731-112">Parent Elements</span></span>

|<span data-ttu-id="2d731-113">Element</span><span class="sxs-lookup"><span data-stu-id="2d731-113">Element</span></span>|<span data-ttu-id="2d731-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2d731-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2d731-115">WideItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="2d731-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="2d731-116">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="2d731-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2d731-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="2d731-117">Text Value</span></span>

<span data-ttu-id="2d731-118">Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2d731-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="2d731-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2d731-119">Remarks</span></span>

<span data-ttu-id="2d731-120">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="2d731-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2d731-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="2d731-121">Example</span></span>

<span data-ttu-id="2d731-122">In dit voor beeld ziet u een breed overzicht waarin de waarde van de eigenschap proces naam van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2d731-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2d731-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2d731-123">See Also</span></span>

[<span data-ttu-id="2d731-124">WideItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="2d731-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="2d731-125">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="2d731-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2d731-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="2d731-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
