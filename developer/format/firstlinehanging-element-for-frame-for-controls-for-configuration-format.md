---
title: FirstLineHanging-Element voor kader voor controles voor configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 679c8bcb-b49d-4bb4-91f5-ea1af6c217e3
caps.latest.revision: 8
ms.openlocfilehash: 4553f95e48a2b1440c00b4951bea56376b00628a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850545"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="3e373-102">Het element FirstLineHanging voor Frame voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3e373-102">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3e373-103">Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de linkerkant.</span><span class="sxs-lookup"><span data-stu-id="3e373-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="3e373-104">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="3e373-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3e373-105">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) CustomItem-Element voor CustomEntry voor besturingselementen voor het kader, configuratie-Element voor CustomItem controles voor configuratie (-indeling) FirstLineHanging-Element voor Frame voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="3e373-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3e373-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="3e373-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3e373-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="3e373-107">Attributes and Elements</span></span>

<span data-ttu-id="3e373-108">De volgende secties worden de kenmerken en onderliggende elementen bovenliggend element van de `FirstLineHanging` element.</span><span class="sxs-lookup"><span data-stu-id="3e373-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3e373-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="3e373-109">Attributes</span></span>

<span data-ttu-id="3e373-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="3e373-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3e373-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3e373-111">Child Elements</span></span>

<span data-ttu-id="3e373-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="3e373-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3e373-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3e373-113">Parent Elements</span></span>

|<span data-ttu-id="3e373-114">Element</span><span class="sxs-lookup"><span data-stu-id="3e373-114">Element</span></span>|<span data-ttu-id="3e373-115">Description</span><span class="sxs-lookup"><span data-stu-id="3e373-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3e373-116">Frame-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="3e373-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="3e373-117">Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts.</span><span class="sxs-lookup"><span data-stu-id="3e373-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3e373-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="3e373-118">Text Value</span></span>

<span data-ttu-id="3e373-119">Geef het aantal tekens dat u wilt verplaatsen van de eerste regel van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="3e373-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e373-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3e373-120">Remarks</span></span>

<span data-ttu-id="3e373-121">Als dit element is opgegeven, kunt u niet opgeven de `FirstLineIndent` element.</span><span class="sxs-lookup"><span data-stu-id="3e373-121">If this element is specified, you cannot specify the `FirstLineIndent` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e373-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3e373-122">See Also</span></span>

[<span data-ttu-id="3e373-123">Frame-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="3e373-123">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="3e373-124">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="3e373-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
