---
title: Een aangepaste gebruikers interface maken | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ebbaba4231b54d42cdcdef07a3ff665bd207d696
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779774"
---
# <a name="creating-a-custom-user-interface"></a>Een aangepaste gebruikersinterface maken

Windows Power shell biedt abstracte klassen en interfaces waarmee u een aangepaste interactieve gebruikers interface kunt maken die als host fungeert voor de Windows Power shell-engine. Als u een aangepaste gebruikers interface wilt maken, moet u de klasse [System. Management. Automation. host. PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) implementeren. U kunt ook de klassen [System. Management. Automation. host. Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)en [System. Management. Automation](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) . host. Pshostuserinterface, en System [. Management. Automation. host. Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) en [System. Management](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) . Automation. host. Ihostuisupportsmultiplechoiceselection implementeren.
