---
title: Element naam voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 109f3a40606dbe82322decf0c69d2367c75175f6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781083"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="083ff-102">Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="083ff-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="083ff-103">Hiermee geeft u de naam van het besturings element op.</span><span class="sxs-lookup"><span data-stu-id="083ff-103">Specifies the name of the control.</span></span>

<span data-ttu-id="083ff-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (indeling) voor besturings elementen voor weer gave (Format) naam element voor besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="083ff-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="083ff-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="083ff-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="083ff-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="083ff-106">Attributes and Elements</span></span>

<span data-ttu-id="083ff-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Name` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="083ff-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="083ff-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="083ff-108">Attributes</span></span>

<span data-ttu-id="083ff-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="083ff-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="083ff-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="083ff-110">Child Elements</span></span>

<span data-ttu-id="083ff-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="083ff-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="083ff-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="083ff-112">Parent Elements</span></span>

|<span data-ttu-id="083ff-113">Element</span><span class="sxs-lookup"><span data-stu-id="083ff-113">Element</span></span>|<span data-ttu-id="083ff-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="083ff-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="083ff-115">Besturings element voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="083ff-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="083ff-116">Hiermee wordt een besturings element gedefinieerd dat kan worden gebruikt door de weer gave en de naam die wordt gebruikt om te verwijzen naar het besturings element.</span><span class="sxs-lookup"><span data-stu-id="083ff-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="083ff-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="083ff-117">Text Value</span></span>

<span data-ttu-id="083ff-118">Geef de naam op die wordt gebruikt om te verwijzen naar het besturings element.</span><span class="sxs-lookup"><span data-stu-id="083ff-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="083ff-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="083ff-119">Remarks</span></span>

<span data-ttu-id="083ff-120">De naam die u hier opgeeft, kan worden gebruikt in de volgende elementen om te verwijzen naar dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="083ff-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="083ff-121">Bij het maken van een tabel, lijst, brede of aangepaste beheer weergave kan het besturings element worden opgegeven door het volgende element: element [GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="083ff-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="083ff-122">Wanneer u een ander besturings element maakt dat door een weer gave kan worden gebruikt, kan dit besturings element worden opgegeven met het volgende element: [ExpressionBinding element voor CustomItem voor besturings elementen voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="083ff-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="083ff-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="083ff-123">See Also</span></span>

[<span data-ttu-id="083ff-124">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="083ff-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="083ff-125">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="083ff-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="083ff-126">Besturings element voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="083ff-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="083ff-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="083ff-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
