---
title: Notatie parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359323"
---
# <a name="format-parameters"></a><span data-ttu-id="e8682-102">Opmaakparameters</span><span class="sxs-lookup"><span data-stu-id="e8682-102">Format Parameters</span></span>

<span data-ttu-id="e8682-103">De volgende tabel bevat de aanbevolen namen en functionaliteit voor para meters die worden gebruikt om gegevens te Format teren of te genereren.</span><span class="sxs-lookup"><span data-stu-id="e8682-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="e8682-104">Parameter</span><span class="sxs-lookup"><span data-stu-id="e8682-104">Parameter</span></span>|<span data-ttu-id="e8682-105">Functionaliteit</span><span class="sxs-lookup"><span data-stu-id="e8682-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="e8682-106">**Alsook**</span><span class="sxs-lookup"><span data-stu-id="e8682-106">**As**</span></span><br><span data-ttu-id="e8682-107">Gegevens type: tref woord</span><span class="sxs-lookup"><span data-stu-id="e8682-107">Data type: Keyword</span></span>|<span data-ttu-id="e8682-108">Implementeer deze para meter om de cmdlet-uitvoer indeling op te geven.</span><span class="sxs-lookup"><span data-stu-id="e8682-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="e8682-109">Mogelijke waarden kunnen bijvoorbeeld tekst of script zijn.</span><span class="sxs-lookup"><span data-stu-id="e8682-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="e8682-110">**Waarde**</span><span class="sxs-lookup"><span data-stu-id="e8682-110">**Binary**</span></span><br><span data-ttu-id="e8682-111">Gegevens type: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e8682-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="e8682-112">Implementeer deze para meter om aan te geven dat de cmdlet binaire waarden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="e8682-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="e8682-113">**Gecodeerd**</span><span class="sxs-lookup"><span data-stu-id="e8682-113">**Encoding**</span></span><br><span data-ttu-id="e8682-114">Gegevens type: tref woord</span><span class="sxs-lookup"><span data-stu-id="e8682-114">Data type: Keyword</span></span>|<span data-ttu-id="e8682-115">Implementeer deze para meter om het type code ring op te geven dat wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="e8682-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="e8682-116">Mogelijke waarden zijn bijvoorbeeld ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, byte en string.</span><span class="sxs-lookup"><span data-stu-id="e8682-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="e8682-117">**Regels**</span><span class="sxs-lookup"><span data-stu-id="e8682-117">**NewLine**</span></span><br><span data-ttu-id="e8682-118">Gegevens type: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e8682-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="e8682-119">Implementeer deze para meter zodat de tekens voor de nieuwe regel worden ondersteund wanneer de para meter wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e8682-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="e8682-120">**Korte naam**</span><span class="sxs-lookup"><span data-stu-id="e8682-120">**ShortName**</span></span><br><span data-ttu-id="e8682-121">Gegevens type: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e8682-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="e8682-122">Implementeer deze para meter zodat korte namen worden ondersteund wanneer de para meter wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e8682-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="e8682-123">**Breedte**</span><span class="sxs-lookup"><span data-stu-id="e8682-123">**Width**</span></span><br><span data-ttu-id="e8682-124">Gegevens type: Int32</span><span class="sxs-lookup"><span data-stu-id="e8682-124">Data type: Int32</span></span>|<span data-ttu-id="e8682-125">Implementeer deze para meter zodat de gebruiker de breedte van het uitvoer apparaat kan opgeven.</span><span class="sxs-lookup"><span data-stu-id="e8682-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="e8682-126">**Verpakt**</span><span class="sxs-lookup"><span data-stu-id="e8682-126">**Wrap**</span></span><br><span data-ttu-id="e8682-127">Gegevens type: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e8682-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="e8682-128">Implementeer deze para meter zodat tekst terugloop wordt ondersteund wanneer de para meter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e8682-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="e8682-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e8682-129">See Also</span></span>

[<span data-ttu-id="e8682-130">Cmdlet-para meters</span><span class="sxs-lookup"><span data-stu-id="e8682-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="e8682-131">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="e8682-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="e8682-132">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="e8682-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
