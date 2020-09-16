---
title: ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3bfd3efe916b4d88c024de8f959482cab515f777
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781219"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="1d344-102">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1d344-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="1d344-103">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="1d344-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="1d344-104">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="1d344-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="1d344-105">Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor CustomControl voor Configuration (Format) CustomEntry element voor het CustomItem-element van de configuratie (indeling) voor CustomEntry voor besturings elementen voor de configuratie ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling) ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d344-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1d344-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1d344-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1d344-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1d344-107">Attributes and Elements</span></span>

<span data-ttu-id="1d344-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ItemSelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="1d344-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1d344-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1d344-109">Attributes</span></span>

<span data-ttu-id="1d344-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="1d344-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1d344-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1d344-111">Child Elements</span></span>

|<span data-ttu-id="1d344-112">Element</span><span class="sxs-lookup"><span data-stu-id="1d344-112">Element</span></span>|<span data-ttu-id="1d344-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1d344-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1d344-114">Het element PropertyName voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d344-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="1d344-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="1d344-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1d344-116">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="1d344-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="1d344-117">Script block-element voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d344-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="1d344-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="1d344-118">Optional element.</span></span><br /><br /> <span data-ttu-id="1d344-119">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="1d344-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1d344-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1d344-120">Parent Elements</span></span>

|<span data-ttu-id="1d344-121">Element</span><span class="sxs-lookup"><span data-stu-id="1d344-121">Element</span></span>|<span data-ttu-id="1d344-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1d344-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1d344-123">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1d344-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="1d344-124">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1d344-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1d344-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1d344-125">Remarks</span></span>

<span data-ttu-id="1d344-126">U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="1d344-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d344-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1d344-127">See Also</span></span>

[<span data-ttu-id="1d344-128">Het element PropertyName voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d344-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="1d344-129">Script block-element voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d344-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="1d344-130">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1d344-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="1d344-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="1d344-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
