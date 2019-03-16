---
title: DisplayError-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056478"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="0b0a1-102">Het element DisplayError (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0b0a1-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="0b0a1-103">Hiermee geeft u op dat de tekenreeks #ERR wordt weergegeven wanneer er treedt een fout op bij het weergeven van een hoeveelheid gegevens.</span><span class="sxs-lookup"><span data-stu-id="0b0a1-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="0b0a1-104">Configuratie Element (indeling) DefaultSettings-Element (indeling) DisplayError-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="0b0a1-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0b0a1-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="0b0a1-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0b0a1-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="0b0a1-106">Attributes and Elements</span></span>

<span data-ttu-id="0b0a1-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `DisplayError` element.</span><span class="sxs-lookup"><span data-stu-id="0b0a1-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0b0a1-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="0b0a1-108">Attributes</span></span>

<span data-ttu-id="0b0a1-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="0b0a1-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0b0a1-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0b0a1-110">Child Elements</span></span>

<span data-ttu-id="0b0a1-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="0b0a1-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0b0a1-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0b0a1-112">Parent Elements</span></span>

|<span data-ttu-id="0b0a1-113">Element</span><span class="sxs-lookup"><span data-stu-id="0b0a1-113">Element</span></span>|<span data-ttu-id="0b0a1-114">Description</span><span class="sxs-lookup"><span data-stu-id="0b0a1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0b0a1-115">DefaultSettings-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="0b0a1-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="0b0a1-116">Algemene instellingen die betrekking hebben op alle weergaven van de opmaak bestand definieert.</span><span class="sxs-lookup"><span data-stu-id="0b0a1-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0b0a1-117">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0b0a1-117">Remarks</span></span>

<span data-ttu-id="0b0a1-118">Standaard als een fout optreedt tijdens een poging om weer te geven van een hoeveelheid gegevens, is de locatie van de gegevens leeg.</span><span class="sxs-lookup"><span data-stu-id="0b0a1-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="0b0a1-119">Wanneer dit element is ingesteld op true, wordt de tekenreeks #ERR wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="0b0a1-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b0a1-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0b0a1-120">See Also</span></span>

[<span data-ttu-id="0b0a1-121">DefaultSettings-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="0b0a1-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="0b0a1-122">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b0a1-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
