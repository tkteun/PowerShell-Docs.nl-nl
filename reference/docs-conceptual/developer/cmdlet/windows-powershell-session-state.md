---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell-sessiestatus
description: Windows PowerShell-sessiestatus
ms.openlocfilehash: 51de92f1f392f708cf49c7ccb4a6808fd628076c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668130"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="26f17-103">Windows PowerShell-sessiestatus</span><span class="sxs-lookup"><span data-stu-id="26f17-103">Windows PowerShell Session State</span></span>

<span data-ttu-id="26f17-104">Sessie status verwijst naar de huidige configuratie van een Windows Power shell-sessie of-module.</span><span class="sxs-lookup"><span data-stu-id="26f17-104">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="26f17-105">Een Windows Power shell-sessie is de operationele omgeving die interactief wordt gebruikt door de opdracht regel gebruiker of via een programma door een hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="26f17-105">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="26f17-106">De sessie status voor een sessie wordt de status van de globale sessie genoemd.</span><span class="sxs-lookup"><span data-stu-id="26f17-106">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="26f17-107">Vanuit een oogpunt van ontwikkel aars verwijst een Windows Power shell-sessie naar de tijd tussen het moment waarop een hosttoepassing een Windows Power shell-runs Pace opent en wanneer de runs Pace wordt gesloten.</span><span class="sxs-lookup"><span data-stu-id="26f17-107">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="26f17-108">Op een andere manier is de sessie de levens duur van een exemplaar van de Windows Power shell-engine die wordt aangeroepen terwijl de runs Pace bestaat.</span><span class="sxs-lookup"><span data-stu-id="26f17-108">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="26f17-109">Sessie status van de module</span><span class="sxs-lookup"><span data-stu-id="26f17-109">Module Session State</span></span>

<span data-ttu-id="26f17-110">De sessie status van de module wordt gemaakt wanneer de module of een van de geneste modules in de sessie wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="26f17-110">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="26f17-111">Wanneer een module een element, zoals een cmdlet, functie of script, exporteert, wordt een verwijzing naar dat element toegevoegd aan de algemene sessie status van de sessie.</span><span class="sxs-lookup"><span data-stu-id="26f17-111">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="26f17-112">Wanneer het element echter wordt uitgevoerd, wordt het uitgevoerd binnen de sessie status van de module.</span><span class="sxs-lookup"><span data-stu-id="26f17-112">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="26f17-113">Session-State gegevens</span><span class="sxs-lookup"><span data-stu-id="26f17-113">Session-State Data</span></span>

<span data-ttu-id="26f17-114">Sessie status gegevens kunnen openbaar of privé zijn.</span><span class="sxs-lookup"><span data-stu-id="26f17-114">Session state data can be public or private.</span></span> <span data-ttu-id="26f17-115">Open bare gegevens zijn beschikbaar voor aanroepen buiten de sessie status terwijl privé gegevens alleen beschikbaar zijn voor aanroepen vanuit de sessie status.</span><span class="sxs-lookup"><span data-stu-id="26f17-115">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="26f17-116">Een module kan bijvoorbeeld een persoonlijke functie hebben die alleen door de module kan worden aangeroepen of alleen intern door een openbaar element dat is geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="26f17-116">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="26f17-117">Dit is vergelijkbaar met de persoonlijke en open bare leden van een .NET Framework type.</span><span class="sxs-lookup"><span data-stu-id="26f17-117">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="26f17-118">Sessie status gegevens worden opgeslagen door het huidige exemplaar van de uitvoerings engine binnen de context van de huidige Windows Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="26f17-118">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="26f17-119">De sessie status gegevens bestaan uit de volgende items:</span><span class="sxs-lookup"><span data-stu-id="26f17-119">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="26f17-120">Padgegevens</span><span class="sxs-lookup"><span data-stu-id="26f17-120">Path information</span></span>

- <span data-ttu-id="26f17-121">Informatie over station</span><span class="sxs-lookup"><span data-stu-id="26f17-121">Drive information</span></span>

- <span data-ttu-id="26f17-122">Informatie over Windows Power shell-provider</span><span class="sxs-lookup"><span data-stu-id="26f17-122">Windows PowerShell provider information</span></span>

- <span data-ttu-id="26f17-123">Informatie over de geïmporteerde modules en verwijzingen naar de module-elementen (zoals cmdlets, functies en scripts) die worden geëxporteerd door de module.</span><span class="sxs-lookup"><span data-stu-id="26f17-123">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="26f17-124">Deze informatie en deze verwijzingen gelden alleen voor de status van de globale sessie.</span><span class="sxs-lookup"><span data-stu-id="26f17-124">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="26f17-125">Informatie over sessie status variabele</span><span class="sxs-lookup"><span data-stu-id="26f17-125">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="26f17-126">Toegang tot Session-State gegevens in cmdlets</span><span class="sxs-lookup"><span data-stu-id="26f17-126">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="26f17-127">-Cmdlets kunnen indirect toegang krijgen tot sessie status gegevens via de eigenschap [System. Management. Automation. PSCmdlet. sessionState \*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) van de cmdlet-klasse of rechtstreeks via de klasse [System. Management. Automation. sessionState](/dotnet/api/System.Management.Automation.SessionState) .</span><span class="sxs-lookup"><span data-stu-id="26f17-127">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="26f17-128">De klasse [System. Management. Automation. sessionState](/dotnet/api/System.Management.Automation.SessionState) biedt eigenschappen die kunnen worden gebruikt om verschillende soorten sessie status gegevens te onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="26f17-128">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="26f17-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="26f17-129">See Also</span></span>

[<span data-ttu-id="26f17-130">System. Management. Automation. PSCmdlet. sessionState</span><span class="sxs-lookup"><span data-stu-id="26f17-130">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="26f17-131">System. Management. Automation. sessionState? Displayproperty = FullName</span><span class="sxs-lookup"><span data-stu-id="26f17-131">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="26f17-132">Windows Power shell-cmdlets</span><span class="sxs-lookup"><span data-stu-id="26f17-132">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="26f17-133">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="26f17-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="26f17-134">Windows Power shell shell SDK</span><span class="sxs-lookup"><span data-stu-id="26f17-134">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
