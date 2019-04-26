---
title: FirstLineIndent-Element voor kader voor controles voor configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065985"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="dccee-102">Het element FirstLineIndent voor Frame voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dccee-102">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="dccee-103">Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de rechterkant.</span><span class="sxs-lookup"><span data-stu-id="dccee-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="dccee-104">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="dccee-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="dccee-105">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) CustomItem-Element voor CustomEntry voor besturingselementen voor het kader, configuratie-Element voor CustomItem controles voor configuratie (-indeling) FirstLineIndent-Element voor Frame voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="dccee-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dccee-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="dccee-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dccee-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="dccee-107">Attributes and Elements</span></span>

<span data-ttu-id="dccee-108">De volgende secties worden de kenmerken en onderliggende elementen bovenliggend element van de `FirstLineIndent` element.</span><span class="sxs-lookup"><span data-stu-id="dccee-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dccee-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="dccee-109">Attributes</span></span>

<span data-ttu-id="dccee-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="dccee-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dccee-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="dccee-111">Child Elements</span></span>

<span data-ttu-id="dccee-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="dccee-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dccee-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="dccee-113">Parent Elements</span></span>

|<span data-ttu-id="dccee-114">Element</span><span class="sxs-lookup"><span data-stu-id="dccee-114">Element</span></span>|<span data-ttu-id="dccee-115">Description</span><span class="sxs-lookup"><span data-stu-id="dccee-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dccee-116">Frame-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="dccee-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="dccee-117">Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts.</span><span class="sxs-lookup"><span data-stu-id="dccee-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dccee-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="dccee-118">Text Value</span></span>

<span data-ttu-id="dccee-119">Geef het aantal tekens dat u wilt verplaatsen van de eerste regel van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="dccee-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="dccee-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="dccee-120">Remarks</span></span>

<span data-ttu-id="dccee-121">Als dit element is opgegeven, kunt u niet opgeven de [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="dccee-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="dccee-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="dccee-122">See Also</span></span>

[<span data-ttu-id="dccee-123">FirstLineHanging-Element voor kader voor controles voor configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="dccee-123">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="dccee-124">Frame-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="dccee-124">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="dccee-125">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="dccee-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
