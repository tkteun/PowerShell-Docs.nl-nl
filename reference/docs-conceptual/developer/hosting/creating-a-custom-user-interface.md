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
# <a name="creating-a-custom-user-interface"></a>Een aangepaste gebruikersinterface maken

Windows Power shell biedt abstracte klassen en interfaces waarmee u een aangepaste interactieve gebruikers interface kunt maken die als host fungeert voor de Windows Power shell-engine. Als u een aangepaste gebruikers interface wilt maken, moet u de klasse [System. Management. Automation. host. PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) implementeren. U kunt ook de klassen [System. Management. Automation. host. Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)en [System. Management. Automation](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) . host. Pshostuserinterface, en System [. Management. Automation. host. Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) en [System. Management](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) . Automation. host. Ihostuisupportsmultiplechoiceselection implementeren.
