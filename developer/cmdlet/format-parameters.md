---
title: Parameters opmaken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251180"
---
# <a name="format-parameters"></a><span data-ttu-id="697bc-102">Opmaakparameters</span><span class="sxs-lookup"><span data-stu-id="697bc-102">Format Parameters</span></span>

<span data-ttu-id="697bc-103">De volgende tabel bevat de namen van de aanbevolen en de functionaliteit voor parameters die worden gebruikt om te maken of om gegevens te genereren.</span><span class="sxs-lookup"><span data-stu-id="697bc-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="697bc-104">Parameter</span><span class="sxs-lookup"><span data-stu-id="697bc-104">Parameter</span></span>|<span data-ttu-id="697bc-105">Functionaliteit</span><span class="sxs-lookup"><span data-stu-id="697bc-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="697bc-106">**Als**</span><span class="sxs-lookup"><span data-stu-id="697bc-106">**As**</span></span><br><span data-ttu-id="697bc-107">Gegevenstype: Trefwoord</span><span class="sxs-lookup"><span data-stu-id="697bc-107">Data type: Keyword</span></span>|<span data-ttu-id="697bc-108">Implementeer deze parameter om op te geven van de indeling van de cmdlet-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="697bc-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="697bc-109">Mogelijke waarden zijn mogelijk tekst of Script.</span><span class="sxs-lookup"><span data-stu-id="697bc-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="697bc-110">**Binary**</span><span class="sxs-lookup"><span data-stu-id="697bc-110">**Binary**</span></span><br><span data-ttu-id="697bc-111">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="697bc-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="697bc-112">Deze parameter om aan te geven dat de binaire waarden worden verwerkt door de cmdlet worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="697bc-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="697bc-113">**Codering**</span><span class="sxs-lookup"><span data-stu-id="697bc-113">**Encoding**</span></span><br><span data-ttu-id="697bc-114">Gegevenstype: Trefwoord</span><span class="sxs-lookup"><span data-stu-id="697bc-114">Data type: Keyword</span></span>|<span data-ttu-id="697bc-115">Implementeer deze parameter om op te geven van het type codering die wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="697bc-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="697bc-116">Mogelijke waarden zijn mogelijk ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte en tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="697bc-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="697bc-117">**NewLine**</span><span class="sxs-lookup"><span data-stu-id="697bc-117">**NewLine**</span></span><br><span data-ttu-id="697bc-118">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="697bc-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="697bc-119">Implementeer deze parameter zodat de nieuwe regeltekens worden ondersteund wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="697bc-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="697bc-120">**Korte naam**</span><span class="sxs-lookup"><span data-stu-id="697bc-120">**ShortName**</span></span><br><span data-ttu-id="697bc-121">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="697bc-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="697bc-122">Implementeer deze parameter zodat korte namen worden ondersteund wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="697bc-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="697bc-123">**Breedte**</span><span class="sxs-lookup"><span data-stu-id="697bc-123">**Width**</span></span><br><span data-ttu-id="697bc-124">Gegevenstype: Int32</span><span class="sxs-lookup"><span data-stu-id="697bc-124">Data type: Int32</span></span>|<span data-ttu-id="697bc-125">Implementeer deze parameter zodat de gebruiker kan de breedte van het uitvoerapparaat opgeven.</span><span class="sxs-lookup"><span data-stu-id="697bc-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="697bc-126">**Wrap**</span><span class="sxs-lookup"><span data-stu-id="697bc-126">**Wrap**</span></span><br><span data-ttu-id="697bc-127">Gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="697bc-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="697bc-128">Implementeer deze parameter zodat tekstterugloop wordt ondersteund wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="697bc-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="697bc-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="697bc-129">See Also</span></span>

[<span data-ttu-id="697bc-130">Cmdlet-Parameters</span><span class="sxs-lookup"><span data-stu-id="697bc-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="697bc-131">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="697bc-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="697bc-132">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="697bc-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
