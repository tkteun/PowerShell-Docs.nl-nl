---
title: Display error-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355214"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="43973-102">Het element DisplayError (opmaak)</span><span class="sxs-lookup"><span data-stu-id="43973-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="43973-103">Hiermee geeft u op dat de teken reeks #ERR wordt weer gegeven wanneer een fout optreedt bij het weer geven van een stukje gegevens.</span><span class="sxs-lookup"><span data-stu-id="43973-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="43973-104">Configuratie-element (indeling) DefaultSettings element (indeling) Display error element (indeling)</span><span class="sxs-lookup"><span data-stu-id="43973-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="43973-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="43973-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="43973-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="43973-106">Attributes and Elements</span></span>

<span data-ttu-id="43973-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `DisplayError` beschreven.</span><span class="sxs-lookup"><span data-stu-id="43973-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="43973-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="43973-108">Attributes</span></span>

<span data-ttu-id="43973-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="43973-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="43973-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="43973-110">Child Elements</span></span>

<span data-ttu-id="43973-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="43973-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="43973-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="43973-112">Parent Elements</span></span>

|<span data-ttu-id="43973-113">Element</span><span class="sxs-lookup"><span data-stu-id="43973-113">Element</span></span>|<span data-ttu-id="43973-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="43973-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43973-115">DefaultSettings-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="43973-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="43973-116">Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="43973-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="43973-117">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="43973-117">Remarks</span></span>

<span data-ttu-id="43973-118">Wanneer er een fout optreedt tijdens het weer geven van een stukje gegevens, blijft de locatie van de gegevens standaard leeg.</span><span class="sxs-lookup"><span data-stu-id="43973-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="43973-119">Als dit element is ingesteld op True, wordt de #ERR teken reeks weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43973-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="43973-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="43973-120">See Also</span></span>

[<span data-ttu-id="43973-121">DefaultSettings-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="43973-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="43973-122">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="43973-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
