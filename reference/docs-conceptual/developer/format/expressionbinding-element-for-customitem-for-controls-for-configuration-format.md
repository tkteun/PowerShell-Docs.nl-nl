---
title: ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354654"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="1d0b9-102">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1d0b9-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="1d0b9-103">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="1d0b9-104">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="1d0b9-105">Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het configureren van een configuratie ( Format) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor configuratie ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d0b9-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1d0b9-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1d0b9-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1d0b9-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1d0b9-107">Attributes and Elements</span></span>

<span data-ttu-id="1d0b9-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ExpressionBinding` beschreven.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1d0b9-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1d0b9-109">Attributes</span></span>

<span data-ttu-id="1d0b9-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1d0b9-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1d0b9-111">Child Elements</span></span>

|<span data-ttu-id="1d0b9-112">Element</span><span class="sxs-lookup"><span data-stu-id="1d0b9-112">Element</span></span>|<span data-ttu-id="1d0b9-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1d0b9-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="1d0b9-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-114">Optional element.</span></span><br /><br /> <span data-ttu-id="1d0b9-115">Hiermee wordt een besturings element gedefinieerd dat door dit besturings element wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="1d0b9-116">CustomControlName-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d0b9-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="1d0b9-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-117">Optional element.</span></span><br /><br /> <span data-ttu-id="1d0b9-118">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="1d0b9-119">EnumerateCollection-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d0b9-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="1d0b9-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-120">Optional element.</span></span><br /><br /> <span data-ttu-id="1d0b9-121">Opgegeven dat de elementen van verzamelingen worden weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="1d0b9-122">ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d0b9-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="1d0b9-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-123">Optional element.</span></span><br /><br /> <span data-ttu-id="1d0b9-124">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="1d0b9-125">Het element PropertyName voor ExpressionBinding voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d0b9-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="1d0b9-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-126">Optional element.</span></span><br /><br /> <span data-ttu-id="1d0b9-127">Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="1d0b9-128">Script block-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="1d0b9-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="1d0b9-129">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-129">Optional element.</span></span><br /><br /> <span data-ttu-id="1d0b9-130">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het algemene besturings element.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1d0b9-131">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1d0b9-131">Parent Elements</span></span>

|<span data-ttu-id="1d0b9-132">Element</span><span class="sxs-lookup"><span data-stu-id="1d0b9-132">Element</span></span>|<span data-ttu-id="1d0b9-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1d0b9-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1d0b9-134">CustomItem-element voor CustomEntry voor besturings elementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="1d0b9-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="1d0b9-135">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1d0b9-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1d0b9-136">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1d0b9-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="1d0b9-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1d0b9-137">See Also</span></span>

[<span data-ttu-id="1d0b9-138">CustomItem-element voor CustomEntry voor besturings elementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="1d0b9-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="1d0b9-139">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="1d0b9-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
