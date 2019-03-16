---
title: De status van een Windows PowerShell-sessie | Microsoft Docs
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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059538"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="ef58a-102">Windows PowerShell-sessiestatus</span><span class="sxs-lookup"><span data-stu-id="ef58a-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="ef58a-103">Sessiestatus verwijst naar de huidige configuratie van een Windows PowerShell-sessie of de module.</span><span class="sxs-lookup"><span data-stu-id="ef58a-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="ef58a-104">Een Windows PowerShell-sessie is de operationele omgeving die interactief wordt gebruikt door de gebruiker van de opdrachtregel of via een programma door een hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="ef58a-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="ef58a-105">De sessiestatus voor een sessie wordt aangeduid als de globale sessiestatus.</span><span class="sxs-lookup"><span data-stu-id="ef58a-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="ef58a-106">Vanuit het oogpunt van ontwikkelaars verwijst een Windows PowerShell-sessie naar de tijd tussen wanneer een Windows PowerShell-runspace in een host-toepassing wordt geopend en wanneer deze de runspace wordt gesloten.</span><span class="sxs-lookup"><span data-stu-id="ef58a-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="ef58a-107">De sessie is een andere manier bekeken, is de levensduur van een exemplaar van de Windows PowerShell-engine die wordt aangeroepen terwijl de runspace bestaat.</span><span class="sxs-lookup"><span data-stu-id="ef58a-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="ef58a-108">Module-sessiestatus</span><span class="sxs-lookup"><span data-stu-id="ef58a-108">Module Session State</span></span>

<span data-ttu-id="ef58a-109">Status van de module-sessies worden gemaakt wanneer de module of een van de geneste modules in de sessie is geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="ef58a-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="ef58a-110">Wanneer een module een element, zoals een cmdlet, een functie of een script exporteert, wordt een verwijzing naar dat element wordt toegevoegd aan de globale sessiestatus van de sessie.</span><span class="sxs-lookup"><span data-stu-id="ef58a-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="ef58a-111">Echter, wanneer het element wordt uitgevoerd, deze uitgevoerd in de status van de sessie van de module.</span><span class="sxs-lookup"><span data-stu-id="ef58a-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="ef58a-112">Sessiestatusgegevens</span><span class="sxs-lookup"><span data-stu-id="ef58a-112">Session-State Data</span></span>

<span data-ttu-id="ef58a-113">Gegevens over de sessiestatus kan openbaar of privé zijn.</span><span class="sxs-lookup"><span data-stu-id="ef58a-113">Session state data can be public or private.</span></span> <span data-ttu-id="ef58a-114">Openbare gegevens is beschikbaar voor het aanroepen van buiten de sessiestatus terwijl persoonlijke gegevens alleen beschikbaar voor gesprekken vanuit de sessiestatus is.</span><span class="sxs-lookup"><span data-stu-id="ef58a-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="ef58a-115">Een module kan bijvoorbeeld een privé-functie die alleen door de module of alleen intern kan worden aangeroepen door een openbare-element dat is geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="ef58a-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="ef58a-116">Dit is vergelijkbaar met de persoonlijke en openbare leden van een .NET Framework-type.</span><span class="sxs-lookup"><span data-stu-id="ef58a-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="ef58a-117">Sessiestatus gegevens worden opgeslagen door het huidige exemplaar van de engine voor het uitvoeren in de context van de huidige Windows PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="ef58a-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="ef58a-118">Sessiestatusgegevens bestaat uit de volgende items:</span><span class="sxs-lookup"><span data-stu-id="ef58a-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="ef58a-119">Informatie over het pad</span><span class="sxs-lookup"><span data-stu-id="ef58a-119">Path information</span></span>

- <span data-ttu-id="ef58a-120">Informatie over stations</span><span class="sxs-lookup"><span data-stu-id="ef58a-120">Drive information</span></span>

- <span data-ttu-id="ef58a-121">Informatie over Windows PowerShell-provider</span><span class="sxs-lookup"><span data-stu-id="ef58a-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="ef58a-122">Informatie over de geïmporteerde modules en verwijzingen naar de module-elementen (zoals cmdlets, functies en scripts) die zijn geëxporteerd door de module.</span><span class="sxs-lookup"><span data-stu-id="ef58a-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="ef58a-123">Deze informatie en deze verwijzingen zijn alleen de algemene sessiestatus.</span><span class="sxs-lookup"><span data-stu-id="ef58a-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="ef58a-124">Informatie over de variabele van sessie-status</span><span class="sxs-lookup"><span data-stu-id="ef58a-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="ef58a-125">Toegang tot sessiestatusgegevens binnen Cmdlets</span><span class="sxs-lookup"><span data-stu-id="ef58a-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="ef58a-126">Cmdlets ofwel toegang kunt krijgen tot sessiestatusgegevens indirect via de [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) eigenschap van de cmdlet-klasse of rechtstreeks via de [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) klasse.</span><span class="sxs-lookup"><span data-stu-id="ef58a-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="ef58a-127">De [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) klasse-eigenschappen die kunnen worden gebruikt voor het onderzoeken van verschillende typen sessiestatusgegevens biedt.</span><span class="sxs-lookup"><span data-stu-id="ef58a-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef58a-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ef58a-128">See Also</span></span>

[<span data-ttu-id="ef58a-129">System.Management.Automation.PSCmdlet.Sessionstate</span><span class="sxs-lookup"><span data-stu-id="ef58a-129">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="ef58a-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="ef58a-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="ef58a-131">Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="ef58a-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="ef58a-132">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ef58a-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="ef58a-133">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="ef58a-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
