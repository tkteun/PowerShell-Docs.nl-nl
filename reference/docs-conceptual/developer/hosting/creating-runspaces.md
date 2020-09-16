---
title: Runspaces maken | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0c27e2bf54e16a3bdc93c4b91629893bb1cc1e3e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779570"
---
# <a name="creating-runspaces"></a><span data-ttu-id="a4d59-102">Runspaces maken</span><span class="sxs-lookup"><span data-stu-id="a4d59-102">Creating Runspaces</span></span>

<span data-ttu-id="a4d59-103">Een runs Pace is de besturings omgeving voor de opdrachten die worden aangeroepen door een hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="a4d59-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="a4d59-104">Deze omgeving bevat de opdrachten en gegevens die momenteel aanwezig zijn en de taal beperkingen die momenteel van toepassing zijn.</span><span class="sxs-lookup"><span data-stu-id="a4d59-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="a4d59-105">Hosttoepassingen kunnen gebruikmaken van de standaard runs Pace van Windows Power shell, die alle beschik bare kern opdrachten bevat, of een aangepaste runs Pace maken die alleen een subset van de beschik bare opdrachten bevat.</span><span class="sxs-lookup"><span data-stu-id="a4d59-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="a4d59-106">Als u een aangepaste runs Pace wilt maken, maakt u een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object en wijst u dit toe aan uw runs Pace.</span><span class="sxs-lookup"><span data-stu-id="a4d59-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="a4d59-107">Runs Pace-taken</span><span class="sxs-lookup"><span data-stu-id="a4d59-107">Runspace tasks</span></span>

1. [<span data-ttu-id="a4d59-108">Een InitialSessionState maken</span><span class="sxs-lookup"><span data-stu-id="a4d59-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="a4d59-109">Een beperkte runspace maken</span><span class="sxs-lookup"><span data-stu-id="a4d59-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="a4d59-110">Meerdere runspaces maken</span><span class="sxs-lookup"><span data-stu-id="a4d59-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="a4d59-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a4d59-111">See Also</span></span>
