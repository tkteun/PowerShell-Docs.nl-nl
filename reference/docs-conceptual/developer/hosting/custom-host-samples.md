---
title: Voor beelden van aangepaste host | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357678"
---
# <a name="custom-host-samples"></a><span data-ttu-id="75108-102">Voorbeelden van aangepaste hosts</span><span class="sxs-lookup"><span data-stu-id="75108-102">Custom Host Samples</span></span>

<span data-ttu-id="75108-103">Deze sectie bevat voorbeeld code voor het schrijven van een aangepaste host.</span><span class="sxs-lookup"><span data-stu-id="75108-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="75108-104">U kunt micro soft Visual Studio gebruiken om een console toepassing te maken en vervolgens de code uit de onderwerpen in deze sectie naar uw host-toepassing te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="75108-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="75108-105">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="75108-105">In This Section</span></span>

 <span data-ttu-id="75108-106">[Host01](./host01-sample.md) -voor beeld In dit voor beeld ziet u hoe u een host-toepassing implementeert die gebruikmaakt van een eenvoudige aangepaste host.</span><span class="sxs-lookup"><span data-stu-id="75108-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="75108-107">[Host02](./host02-sample.md) -voor beeld In dit voor beeld ziet u hoe u een host-toepassing schrijft die gebruikmaakt van de Windows Power shell-runtime samen met een aangepaste implementatie van de host.</span><span class="sxs-lookup"><span data-stu-id="75108-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="75108-108">Met de hosttoepassing wordt de host-cultuur ingesteld op Duits, wordt de cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) uitgevoerd en worden de resultaten weer gegeven zoals u deze zou zien met behulp van pwrsh. exe, waarna de huidige gegevens en tijd in het Duits worden afgedrukt.</span><span class="sxs-lookup"><span data-stu-id="75108-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="75108-109">[Host03](./host03-sample.md) -voor beeld Dit voor beeld laat zien hoe u een interactieve op een console gebaseerde host-toepassing bouwt waarmee opdrachten worden gelezen vanaf de opdracht regel, de opdrachten worden uitgevoerd en de resultaten vervolgens worden weer gegeven in de console.</span><span class="sxs-lookup"><span data-stu-id="75108-109">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="75108-110">[Host04](./host04-sample.md) -voor beeld Dit voor beeld laat zien hoe u een interactieve op een console gebaseerde host-toepassing bouwt waarmee opdrachten worden gelezen vanaf de opdracht regel, de opdrachten worden uitgevoerd en de resultaten vervolgens worden weer gegeven in de console.</span><span class="sxs-lookup"><span data-stu-id="75108-110">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="75108-111">Deze hosttoepassing biedt ook ondersteuning voor het weer geven van prompts waarmee de gebruiker meerdere keuzes kan opgeven.</span><span class="sxs-lookup"><span data-stu-id="75108-111">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="75108-112">[Host05](./host05-sample.md) -voor beeld Dit voor beeld laat zien hoe u een interactieve op een console gebaseerde host-toepassing bouwt waarmee opdrachten worden gelezen vanaf de opdracht regel, de opdrachten worden uitgevoerd en de resultaten vervolgens worden weer gegeven in de console.</span><span class="sxs-lookup"><span data-stu-id="75108-112">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="75108-113">Deze hosttoepassing ondersteunt ook aanroepen naar externe computers met behulp van de cmdlets [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) en [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession)</span><span class="sxs-lookup"><span data-stu-id="75108-113">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="75108-114">[Host06](./host06-sample.md) -voor beeld Dit voor beeld laat zien hoe u een interactieve op een console gebaseerde host-toepassing bouwt waarmee opdrachten worden gelezen vanaf de opdracht regel, de opdrachten worden uitgevoerd en de resultaten vervolgens worden weer gegeven in de console.</span><span class="sxs-lookup"><span data-stu-id="75108-114">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="75108-115">Daarnaast gebruikt dit voor beeld de Tokenizer-Api's om de kleur van de tekst op te geven die door de gebruiker wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="75108-115">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="75108-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="75108-116">See Also</span></span>
