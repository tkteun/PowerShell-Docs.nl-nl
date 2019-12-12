---
title: Een Windows Power shell-hosttoepassing schrijven | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: b44708b3bbcb974a6178323dff2302b7da121af6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357517"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="1d0c2-102">Een Windows PowerShell-hosttoepassing schrijven</span><span class="sxs-lookup"><span data-stu-id="1d0c2-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="1d0c2-103">U kunt Windows Power shell in uw toepassing hosten.</span><span class="sxs-lookup"><span data-stu-id="1d0c2-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="1d0c2-104">De hosttoepassing kan de runs Pace definiëren waar opdrachten worden uitgevoerd, sessies openen op een lokale of externe computer en de opdrachten synchroon of asynchroon aanroepen op basis van de behoeften van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="1d0c2-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="1d0c2-105">In de volgende onderwerpen wordt uitgelegd hoe u een toepassing maakt die als host fungeert voor Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="1d0c2-105">The following topics explain how to create an application that hosts Windows PowerShell.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1d0c2-106">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="1d0c2-106">In This Section</span></span>

<span data-ttu-id="1d0c2-107">[Snelstartgids voor Windows Power shell-host](./windows-powershell-host-quickstart.md) Biedt instructies en code voorbeelden om u te helpen bij het maken van hosttoepassingen.</span><span class="sxs-lookup"><span data-stu-id="1d0c2-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="1d0c2-108">[Runspaces maken](./creating-runspaces.md) Een reeks onderwerpen waarin wordt uitgelegd hoe u runspaces maakt om Windows Power shell-opdracht uit te voeren in een hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="1d0c2-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="1d0c2-109">[Opdrachten toevoegen en aanroepen](./adding-and-invoking-commands.md) Hierin wordt uitgelegd hoe u een opdracht pijplijn maakt en uitvoert in uw host-toepassing.</span><span class="sxs-lookup"><span data-stu-id="1d0c2-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="1d0c2-110">[Externe Runspaces maken](./creating-remote-runspaces.md) Hierin wordt uitgelegd hoe u een runs Pace verbindt met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="1d0c2-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="1d0c2-111">[Een aangepaste gebruikers interface maken](./creating-a-custom-user-interface.md) Hierin worden aangepaste gebruikers interfaces geïntroduceerd en vindt u koppelingen naar voor beelden.</span><span class="sxs-lookup"><span data-stu-id="1d0c2-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="1d0c2-112">Voor [beelden van hosttoepassingen](./host-application-samples.md) Deze sectie bevat voor beelden van complete host-toepassingen.</span><span class="sxs-lookup"><span data-stu-id="1d0c2-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d0c2-113">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1d0c2-113">See Also</span></span>

[<span data-ttu-id="1d0c2-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1d0c2-114">Windows PowerShell</span></span>](https://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)
