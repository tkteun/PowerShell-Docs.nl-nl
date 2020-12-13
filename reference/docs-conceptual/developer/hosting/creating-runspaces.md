---
ms.date: 09/13/2016
ms.topic: reference
title: Runspaces maken
description: Runspaces maken
ms.openlocfilehash: c6b2c577e435ec88364b189a0c3d065f54f02525
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649346"
---
# <a name="creating-runspaces"></a><span data-ttu-id="00d33-103">Runspaces maken</span><span class="sxs-lookup"><span data-stu-id="00d33-103">Creating Runspaces</span></span>

<span data-ttu-id="00d33-104">Een runs Pace is de besturings omgeving voor de opdrachten die worden aangeroepen door een hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="00d33-104">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="00d33-105">Deze omgeving bevat de opdrachten en gegevens die momenteel aanwezig zijn en de taal beperkingen die momenteel van toepassing zijn.</span><span class="sxs-lookup"><span data-stu-id="00d33-105">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="00d33-106">Hosttoepassingen kunnen gebruikmaken van de standaard runs Pace van Windows Power shell, die alle beschik bare kern opdrachten bevat, of een aangepaste runs Pace maken die alleen een subset van de beschik bare opdrachten bevat.</span><span class="sxs-lookup"><span data-stu-id="00d33-106">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="00d33-107">Als u een aangepaste runs Pace wilt maken, maakt u een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object en wijst u dit toe aan uw runs Pace.</span><span class="sxs-lookup"><span data-stu-id="00d33-107">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="00d33-108">Runs Pace-taken</span><span class="sxs-lookup"><span data-stu-id="00d33-108">Runspace tasks</span></span>

1. [<span data-ttu-id="00d33-109">Een InitialSessionState maken</span><span class="sxs-lookup"><span data-stu-id="00d33-109">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="00d33-110">Een beperkte runspace maken</span><span class="sxs-lookup"><span data-stu-id="00d33-110">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="00d33-111">Meerdere runspaces maken</span><span class="sxs-lookup"><span data-stu-id="00d33-111">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="00d33-112">Zie ook</span><span class="sxs-lookup"><span data-stu-id="00d33-112">See Also</span></span>
