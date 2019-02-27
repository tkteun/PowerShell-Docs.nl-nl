---
title: Het maken van Runspaces | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848144"
---
# <a name="creating-runspaces"></a><span data-ttu-id="9e3c9-102">Runspaces maken</span><span class="sxs-lookup"><span data-stu-id="9e3c9-102">Creating Runspaces</span></span>

<span data-ttu-id="9e3c9-103">Een runspace is de operationele omgeving voor de opdrachten die worden aangeroepen door een hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="9e3c9-104">Deze omgeving omvat de opdrachten en gegevens die momenteel aanwezig zijn en de taal-beperkingen die momenteel van toepassing.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="9e3c9-105">Hosting van toepassingen kunnen gebruiken de standaard-runspace die wordt geleverd door Windows PowerShell, waaronder alle beschikbare core opdrachten, of maak een aangepaste runspace met slechts een subset van de beschikbare opdrachten.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="9e3c9-106">Voor het maken van een aangepaste runspace, maakt u een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object en wijs deze toe aan uw runspace.</span><span class="sxs-lookup"><span data-stu-id="9e3c9-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="9e3c9-107">Runspace taken</span><span class="sxs-lookup"><span data-stu-id="9e3c9-107">Runspace tasks</span></span>

1. [<span data-ttu-id="9e3c9-108">Het maken van een InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="9e3c9-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="9e3c9-109">Het maken van een beperkte runspace</span><span class="sxs-lookup"><span data-stu-id="9e3c9-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="9e3c9-110">Het maken van meerdere runspaces</span><span class="sxs-lookup"><span data-stu-id="9e3c9-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="9e3c9-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9e3c9-111">See Also</span></span>
