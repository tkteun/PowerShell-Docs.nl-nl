---
title: Schrijven van een Windows PowerShell-hosttoepassing | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: 2df5a59833fcdd58c6b2afbb4882111592fb3d76
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082495"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="6e9c8-102">Een Windows PowerShell-hosttoepassing schrijven</span><span class="sxs-lookup"><span data-stu-id="6e9c8-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="6e9c8-103">U kunt Windows PowerShell hosten in uw toepassing.</span><span class="sxs-lookup"><span data-stu-id="6e9c8-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="6e9c8-104">De host-toepassing kunt definiëren de runspace waarin opdrachten zijn uitgevoerd, opent u sessies op een lokale of externe computer en aanroepen van de opdrachten die een synchroon of asynchroon op basis van de behoeften van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="6e9c8-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="6e9c8-105">De volgende onderwerpen wordt uitgelegd hoe u een toepassing maken die als host fungeert</span><span class="sxs-lookup"><span data-stu-id="6e9c8-105">The following topics explain how to create an application that hosts</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6e9c8-106">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="6e9c8-106">In This Section</span></span>

<span data-ttu-id="6e9c8-107">[Quick Start Windows PowerShell-Host](./windows-powershell-host-quickstart.md) bevat instructies en voorbeelden van code om u te helpen aan de slag hosting van toepassingen maken.</span><span class="sxs-lookup"><span data-stu-id="6e9c8-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="6e9c8-108">[Het maken van Runspaces](./creating-runspaces.md) een set onderwerpen waarin wordt uitgelegd hoe u runspaces voor het uitvoeren van Windows PowerShell-opdracht in een host-toepassing maken.</span><span class="sxs-lookup"><span data-stu-id="6e9c8-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="6e9c8-109">[Toe te voegen en aan te roepen opdrachten](./adding-and-invoking-commands.md) wordt uitgelegd hoe u maken en uitvoeren van een pijplijn opdracht in uw hosttoepassing...</span><span class="sxs-lookup"><span data-stu-id="6e9c8-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="6e9c8-110">[Het maken van externe runspaces](./creating-remote-runspaces.md) wordt uitgelegd hoe u een runspace verbinden met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="6e9c8-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="6e9c8-111">[Het maken van een aangepaste gebruikersinterface](./creating-a-custom-user-interface.md) Introduces aangepaste gebruiker interfaces en vindt u koppelingen naar voorbeelden.</span><span class="sxs-lookup"><span data-stu-id="6e9c8-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="6e9c8-112">[Voorbeelden van gebruikerstoepassingen hosten](./host-application-samples.md) in deze sectie bevat voorbeelden van volledige hosting van toepassingen.</span><span class="sxs-lookup"><span data-stu-id="6e9c8-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e9c8-113">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6e9c8-113">See Also</span></span>

[<span data-ttu-id="6e9c8-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e9c8-114">Windows PowerShell</span></span>](http://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)