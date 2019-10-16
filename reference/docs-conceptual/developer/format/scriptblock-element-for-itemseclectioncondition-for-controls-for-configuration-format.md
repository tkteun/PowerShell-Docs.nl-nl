---
title: Script block-element voor ItemSeclectionCondition voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353905"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="81990-102">Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="81990-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="81990-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="81990-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="81990-104">Wanneer dit script wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="81990-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="81990-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="81990-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="81990-106">Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het configureren van een configuratie ( Format) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor configuratie ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling) ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor de configuratie (indeling) script block-element voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="81990-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="81990-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="81990-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="81990-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="81990-108">Attributes and Elements</span></span>

<span data-ttu-id="81990-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ScriptBlock` beschreven.</span><span class="sxs-lookup"><span data-stu-id="81990-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="81990-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="81990-110">Attributes</span></span>

<span data-ttu-id="81990-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="81990-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="81990-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="81990-112">Child Elements</span></span>

<span data-ttu-id="81990-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="81990-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="81990-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="81990-114">Parent Elements</span></span>

|<span data-ttu-id="81990-115">Element</span><span class="sxs-lookup"><span data-stu-id="81990-115">Element</span></span>|<span data-ttu-id="81990-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="81990-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="81990-117">ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="81990-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="81990-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="81990-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="81990-119">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="81990-119">Text Value</span></span>

<span data-ttu-id="81990-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="81990-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="81990-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="81990-121">Remarks</span></span>

<span data-ttu-id="81990-122">Als dit element wordt gebruikt, kunt u het kenmerk [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) niet opgeven bij het definiëren van de selectie voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="81990-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="81990-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="81990-123">See Also</span></span>

[<span data-ttu-id="81990-124">Het element PropertyName voor ItemSeclectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="81990-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="81990-125">ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="81990-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="81990-126">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="81990-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
