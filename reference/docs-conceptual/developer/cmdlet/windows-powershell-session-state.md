---
title: Windows Power shell-sessie status | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359108"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="0b998-102">Windows PowerShell-sessiestatus</span><span class="sxs-lookup"><span data-stu-id="0b998-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="0b998-103">Sessie status verwijst naar de huidige configuratie van een Windows Power shell-sessie of-module.</span><span class="sxs-lookup"><span data-stu-id="0b998-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="0b998-104">Een Windows Power shell-sessie is de operationele omgeving die interactief wordt gebruikt door de opdracht regel gebruiker of via een programma door een hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="0b998-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="0b998-105">De sessie status voor een sessie wordt de status van de globale sessie genoemd.</span><span class="sxs-lookup"><span data-stu-id="0b998-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="0b998-106">Vanuit een oogpunt van ontwikkel aars verwijst een Windows Power shell-sessie naar de tijd tussen het moment waarop een hosttoepassing een Windows Power shell-runs Pace opent en wanneer de runs Pace wordt gesloten.</span><span class="sxs-lookup"><span data-stu-id="0b998-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="0b998-107">Op een andere manier is de sessie de levens duur van een exemplaar van de Windows Power shell-engine die wordt aangeroepen terwijl de runs Pace bestaat.</span><span class="sxs-lookup"><span data-stu-id="0b998-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="0b998-108">Sessie status van de module</span><span class="sxs-lookup"><span data-stu-id="0b998-108">Module Session State</span></span>

<span data-ttu-id="0b998-109">De sessie status van de module wordt gemaakt wanneer de module of een van de geneste modules in de sessie wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="0b998-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="0b998-110">Wanneer een module een element, zoals een cmdlet, functie of script, exporteert, wordt een verwijzing naar dat element toegevoegd aan de algemene sessie status van de sessie.</span><span class="sxs-lookup"><span data-stu-id="0b998-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="0b998-111">Wanneer het element echter wordt uitgevoerd, wordt het uitgevoerd binnen de sessie status van de module.</span><span class="sxs-lookup"><span data-stu-id="0b998-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="0b998-112">Sessie status gegevens</span><span class="sxs-lookup"><span data-stu-id="0b998-112">Session-State Data</span></span>

<span data-ttu-id="0b998-113">Sessie status gegevens kunnen openbaar of privé zijn.</span><span class="sxs-lookup"><span data-stu-id="0b998-113">Session state data can be public or private.</span></span> <span data-ttu-id="0b998-114">Open bare gegevens zijn beschikbaar voor aanroepen buiten de sessie status terwijl privé gegevens alleen beschikbaar zijn voor aanroepen vanuit de sessie status.</span><span class="sxs-lookup"><span data-stu-id="0b998-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="0b998-115">Een module kan bijvoorbeeld een persoonlijke functie hebben die alleen door de module kan worden aangeroepen of alleen intern door een openbaar element dat is geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="0b998-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="0b998-116">Dit is vergelijkbaar met de persoonlijke en open bare leden van een .NET Framework type.</span><span class="sxs-lookup"><span data-stu-id="0b998-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="0b998-117">Sessie status gegevens worden opgeslagen door het huidige exemplaar van de uitvoerings engine binnen de context van de huidige Windows Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="0b998-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="0b998-118">De sessie status gegevens bestaan uit de volgende items:</span><span class="sxs-lookup"><span data-stu-id="0b998-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="0b998-119">Padgegevens</span><span class="sxs-lookup"><span data-stu-id="0b998-119">Path information</span></span>

- <span data-ttu-id="0b998-120">Informatie over station</span><span class="sxs-lookup"><span data-stu-id="0b998-120">Drive information</span></span>

- <span data-ttu-id="0b998-121">Informatie over Windows Power shell-provider</span><span class="sxs-lookup"><span data-stu-id="0b998-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="0b998-122">Informatie over de geïmporteerde modules en verwijzingen naar de module-elementen (zoals cmdlets, functies en scripts) die worden geëxporteerd door de module.</span><span class="sxs-lookup"><span data-stu-id="0b998-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="0b998-123">Deze informatie en deze verwijzingen gelden alleen voor de status van de globale sessie.</span><span class="sxs-lookup"><span data-stu-id="0b998-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="0b998-124">Informatie over sessie status variabele</span><span class="sxs-lookup"><span data-stu-id="0b998-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="0b998-125">Toegang tot sessie status gegevens in cmdlets</span><span class="sxs-lookup"><span data-stu-id="0b998-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="0b998-126">-Cmdlets kunnen indirect toegang krijgen tot sessie status gegevens via de eigenschap [System. Management. Automation. PSCmdlet. sessionState \*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) van de cmdlet-klasse of rechtstreeks via de klasse [System. Management. Automation. sessionState](/dotnet/api/System.Management.Automation.SessionState) .</span><span class="sxs-lookup"><span data-stu-id="0b998-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="0b998-127">De klasse [System. Management. Automation. sessionState](/dotnet/api/System.Management.Automation.SessionState) biedt eigenschappen die kunnen worden gebruikt om verschillende soorten sessie status gegevens te onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="0b998-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b998-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0b998-128">See Also</span></span>

[<span data-ttu-id="0b998-129">System. Management. Automation. PSCmdlet. sessionState</span><span class="sxs-lookup"><span data-stu-id="0b998-129">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="0b998-130">System. Management. Automation. sessionState? Displayproperty = FullName</span><span class="sxs-lookup"><span data-stu-id="0b998-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="0b998-131">Windows Power shell-cmdlets</span><span class="sxs-lookup"><span data-stu-id="0b998-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="0b998-132">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="0b998-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="0b998-133">Windows Power shell shell SDK</span><span class="sxs-lookup"><span data-stu-id="0b998-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
