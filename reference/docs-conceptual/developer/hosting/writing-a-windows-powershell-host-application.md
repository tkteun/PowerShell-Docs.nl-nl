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
ms.openlocfilehash: fe0393634a1e5bb1a3d4a98ccf245e199beb0f16
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75869908"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="442da-102">Een Windows PowerShell-hosttoepassing schrijven</span><span class="sxs-lookup"><span data-stu-id="442da-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="442da-103">U kunt Windows Power shell in uw toepassing hosten.</span><span class="sxs-lookup"><span data-stu-id="442da-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="442da-104">De hosttoepassing kan de runs Pace definiëren waar opdrachten worden uitgevoerd, sessies openen op een lokale of externe computer en de opdrachten synchroon of asynchroon aanroepen op basis van de behoeften van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="442da-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="442da-105">In de volgende onderwerpen wordt uitgelegd hoe u een toepassing maakt die als host fungeert voor Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="442da-105">The following topics explain how to create an application that hosts Windows PowerShell.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="442da-106">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="442da-106">In This Section</span></span>

<span data-ttu-id="442da-107">[Snelstartgids voor Windows Power shell-host](./windows-powershell-host-quickstart.md) Biedt instructies en code voorbeelden om u te helpen bij het maken van hosttoepassingen.</span><span class="sxs-lookup"><span data-stu-id="442da-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="442da-108">[Runspaces maken](./creating-runspaces.md) Een reeks onderwerpen waarin wordt uitgelegd hoe u runspaces maakt om Windows Power shell-opdracht uit te voeren in een hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="442da-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="442da-109">[Opdrachten toevoegen en aanroepen](./adding-and-invoking-commands.md) Hierin wordt uitgelegd hoe u een opdracht pijplijn maakt en uitvoert in uw host-toepassing.</span><span class="sxs-lookup"><span data-stu-id="442da-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="442da-110">[Externe Runspaces maken](./creating-remote-runspaces.md) Hierin wordt uitgelegd hoe u een runs Pace verbindt met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="442da-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="442da-111">[Een aangepaste gebruikers interface maken](./creating-a-custom-user-interface.md) Hierin worden aangepaste gebruikers interfaces geïntroduceerd en vindt u koppelingen naar voor beelden.</span><span class="sxs-lookup"><span data-stu-id="442da-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="442da-112">Voor [beelden van hosttoepassingen](./host-application-samples.md) Deze sectie bevat voor beelden van complete host-toepassingen.</span><span class="sxs-lookup"><span data-stu-id="442da-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>
