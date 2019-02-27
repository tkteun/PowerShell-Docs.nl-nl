---
title: FirstLineIndent-Element voor kader voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec63f4f9-8858-4529-8646-ffbbc278f83e
caps.latest.revision: 7
ms.openlocfilehash: 694c5baaa5e90a772257276ba139d90acf7ec0e3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845631"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="871e9-102">Het element FirstLineIndent voor Frame voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="871e9-102">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="871e9-103">Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de rechterkant.</span><span class="sxs-lookup"><span data-stu-id="871e9-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="871e9-104">Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.</span><span class="sxs-lookup"><span data-stu-id="871e9-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="871e9-105">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) CustomItem Element voor CustomEntry voor besturingselementen voor weergave (indeling) Frame-Element voor CustomItem voor besturingselementen voor weergave (indeling) FirstLineIndent Element van het Frame besturingselementen van weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="871e9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineIndent Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="871e9-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="871e9-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="871e9-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="871e9-107">Attributes and Elements</span></span>

<span data-ttu-id="871e9-108">De volgende secties worden de kenmerken en onderliggende elementen bovenliggend element van de `FirstLineIndent` element.</span><span class="sxs-lookup"><span data-stu-id="871e9-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="871e9-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="871e9-109">Attributes</span></span>

<span data-ttu-id="871e9-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="871e9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="871e9-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="871e9-111">Child Elements</span></span>

<span data-ttu-id="871e9-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="871e9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="871e9-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="871e9-113">Parent Elements</span></span>

|<span data-ttu-id="871e9-114">Element</span><span class="sxs-lookup"><span data-stu-id="871e9-114">Element</span></span>|<span data-ttu-id="871e9-115">Description</span><span class="sxs-lookup"><span data-stu-id="871e9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="871e9-116">Frame-Element voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="871e9-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="871e9-117">Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts.</span><span class="sxs-lookup"><span data-stu-id="871e9-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="871e9-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="871e9-118">Text Value</span></span>

<span data-ttu-id="871e9-119">Geef het aantal tekens dat u wilt verplaatsen van de eerste regel van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="871e9-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="871e9-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="871e9-120">Remarks</span></span>

<span data-ttu-id="871e9-121">Als dit element is opgegeven, kunt u niet opgeven de [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="871e9-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="871e9-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="871e9-122">See Also</span></span>

[<span data-ttu-id="871e9-123">FirstLineHanging-Element voor kader voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="871e9-123">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="871e9-124">Frame-Element voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="871e9-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="871e9-125">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="871e9-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
