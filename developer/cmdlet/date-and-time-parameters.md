---
title: De datum en tijdparameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 49f6c667b0fd9678586559af39a33f982de0a68c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846709"
---
# <a name="date-and-time-parameters"></a><span data-ttu-id="9eaab-102">Datum- en tijdparameters</span><span class="sxs-lookup"><span data-stu-id="9eaab-102">Date and Time Parameters</span></span>

<span data-ttu-id="9eaab-103">De volgende tabel bevat de namen van de aanbevolen en de functionaliteit voor parameters die werken met gegevens van de datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="9eaab-103">The following table lists recommended names and functionality for parameters that handle date and time information.</span></span> <span data-ttu-id="9eaab-104">Datum en tijd-parameters worden meestal gebruikt om vast te leggen wanneer iets wordt gemaakt of geopend.</span><span class="sxs-lookup"><span data-stu-id="9eaab-104">Date and time parameters are typically used to record when something is created or accessed.</span></span>

<span data-ttu-id="9eaab-105">Gebruikte gegevens typt u: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9eaab-105">Accessed Data type: SwitchParameter</span></span>

<span data-ttu-id="9eaab-106">Deze parameter implementeren, zodat wanneer deze is opgegeven de cmdlet wordt uitgevoerd op de resources die zijn gebruikt op basis van de datum en tijd die is opgegeven door de `Before` en `After` parameters.</span><span class="sxs-lookup"><span data-stu-id="9eaab-106">Implement this parameter so that when it is specified the cmdlet will operate on the resources that have been accessed based on the date and time specified by the `Before` and `After` parameters.</span></span>

<span data-ttu-id="9eaab-107">Als deze parameter is opgegeven, de `Created` en `Modified` parameters moeten niet worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9eaab-107">If this parameter is specified, the `Created` and `Modified` parameters must be not be specified.</span></span>

<span data-ttu-id="9eaab-108">Na het gegevenstype: DateTime</span><span class="sxs-lookup"><span data-stu-id="9eaab-108">After Data type: DateTime</span></span>

<span data-ttu-id="9eaab-109">Implementeer deze parameter om op te geven van de datum en tijd waarna de cmdlet is gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9eaab-109">Implement this parameter to specify the date and time after which the cmdlet was used.</span></span> <span data-ttu-id="9eaab-110">Voor de `After` parameter om te werken, de cmdlet moet ook beschikken over een `Accessed`, `Created`, of `Modified` parameter.</span><span class="sxs-lookup"><span data-stu-id="9eaab-110">For the `After` parameter to work, the cmdlet must also have an `Accessed`, `Created`, or `Modified` parameter.</span></span> <span data-ttu-id="9eaab-111">En deze parameter moet worden ingesteld op `true` wanneer de cmdlet wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="9eaab-111">And, that parameter must be set to `true` when the cmdlet is called.</span></span>

<span data-ttu-id="9eaab-112">Voordat u het gegevenstype: DateTime</span><span class="sxs-lookup"><span data-stu-id="9eaab-112">Before Data type: DateTime</span></span>

<span data-ttu-id="9eaab-113">Implementeer deze parameter om op te geven van de datum en tijd waarbinnen de cmdlet is gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9eaab-113">Implement this parameter to specify the date and time before which the cmdlet was used.</span></span> <span data-ttu-id="9eaab-114">Voor de `Before` parameter om te werken, de cmdlet moet ook beschikken over een `Accessed`, `Created`, of `Modified` parameter.</span><span class="sxs-lookup"><span data-stu-id="9eaab-114">For the `Before` parameter to work, the cmdlet must also have an `Accessed`, `Created`, or `Modified` parameter.</span></span> <span data-ttu-id="9eaab-115">En deze parameter moet worden ingesteld op `true` wanneer de cmdlet wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="9eaab-115">And, that parameter must be set to `true` when the cmdlet is called.</span></span>

<span data-ttu-id="9eaab-116">Gegevens van het type gemaakt: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9eaab-116">Created Data type: SwitchParameter</span></span>

<span data-ttu-id="9eaab-117">Deze parameter implementeren, zodat wanneer deze is opgegeven de cmdlet wordt uitgevoerd op de resources die zijn gemaakt op basis van de datum en tijd die is opgegeven door de `Before` en `After` parameters.</span><span class="sxs-lookup"><span data-stu-id="9eaab-117">Implement this parameter so that when it is specified the cmdlet will operate on the resources that have been created based on the date and time specified by the `Before` and `After` parameters.</span></span>

<span data-ttu-id="9eaab-118">Als deze parameter is opgegeven, de `Accessed` en `Modified` parameters moeten niet worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9eaab-118">If this parameter is specified, the `Accessed` and `Modified` parameters must not be specified.</span></span>

<span data-ttu-id="9eaab-119">Exacte gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9eaab-119">Exact Data type: SwitchParameter</span></span>

<span data-ttu-id="9eaab-120">Implementeer deze parameter zodat wanneer deze de termijn van de resource is opgegeven moet precies overeenkomen met de naam van de resource.</span><span class="sxs-lookup"><span data-stu-id="9eaab-120">Implement this parameter so that when it is specified the resource term must match the resource name exactly.</span></span> <span data-ttu-id="9eaab-121">Als de parameter niet is opgegeven hoeft de termijn van de resource en de naam niet precies.</span><span class="sxs-lookup"><span data-stu-id="9eaab-121">When the parameter is not specified the resource term and name do not need to match exactly.</span></span>

<span data-ttu-id="9eaab-122">Gewijzigde gegevens typt u: DateTime</span><span class="sxs-lookup"><span data-stu-id="9eaab-122">Modified Data type: DateTime</span></span>

<span data-ttu-id="9eaab-123">Deze parameter implementeren, zodat wanneer deze is opgegeven de cmdlet wordt uitgevoerd op resources die zijn gewijzigd op basis van de datum en tijd die is opgegeven door de `Before` en `After` parameters.</span><span class="sxs-lookup"><span data-stu-id="9eaab-123">Implement this parameter so that when it is specified the cmdlet will operate on resources that have been changed based on the date and time specified by the `Before` and `After` parameters.</span></span>

<span data-ttu-id="9eaab-124">Als deze parameter is opgegeven, de `Accessed` en `Created` parameters moeten niet worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9eaab-124">If this parameter is specified, the `Accessed` and `Created` parameters must not be specified.</span></span>

## <a name="see-also"></a><span data-ttu-id="9eaab-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9eaab-125">See Also</span></span>

[<span data-ttu-id="9eaab-126">Cmdlet-Parameters</span><span class="sxs-lookup"><span data-stu-id="9eaab-126">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="9eaab-127">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9eaab-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="9eaab-128">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9eaab-128">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
