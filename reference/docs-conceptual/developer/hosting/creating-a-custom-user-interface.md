---
ms.date: 09/13/2016
ms.topic: reference
title: Een aangepaste gebruikersinterface maken
description: Een aangepaste gebruikersinterface maken
ms.openlocfilehash: 411165f868cd524c0cef0ba9cce3188c60a7dbdf
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645398"
---
# <a name="creating-a-custom-user-interface"></a><span data-ttu-id="8e786-103">Een aangepaste gebruikersinterface maken</span><span class="sxs-lookup"><span data-stu-id="8e786-103">Creating a custom user interface</span></span>

<span data-ttu-id="8e786-104">Windows Power shell biedt abstracte klassen en interfaces waarmee u een aangepaste interactieve gebruikers interface kunt maken die als host fungeert voor de Windows Power shell-engine.</span><span class="sxs-lookup"><span data-stu-id="8e786-104">Windows PowerShell provides abstract classes and interfaces that allow you to create a custom interactive UI that hosts the Windows PowerShell engine.</span></span> <span data-ttu-id="8e786-105">Als u een aangepaste gebruikers interface wilt maken, moet u de klasse [System. Management. Automation. host. PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) implementeren.</span><span class="sxs-lookup"><span data-stu-id="8e786-105">To create a custom UI, you must implement the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class.</span></span> <span data-ttu-id="8e786-106">U kunt ook de klassen [System. Management. Automation. host. Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)en [System. Management. Automation](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) . host. Pshostuserinterface, en System [. Management. Automation. host. Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) en [System. Management](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) . Automation. host. Ihostuisupportsmultiplechoiceselection implementeren.</span><span class="sxs-lookup"><span data-stu-id="8e786-106">Optionally, you can also implement the [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)and [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) classes, and the [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) and [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfaces.</span></span>
