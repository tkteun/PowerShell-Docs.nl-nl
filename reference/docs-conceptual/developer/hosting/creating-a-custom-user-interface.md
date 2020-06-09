---
title: Een aangepaste gebruikers interface maken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7286443-eed4-43d5-b809-50cdcdcba088
caps.latest.revision: 4
ms.openlocfilehash: 23518c625fe1138e1bd2bcc895274cb21d7daf8a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "84514839"
---
# <a name="creating-a-custom-user-interface"></a>Een aangepaste gebruikersinterface maken

Windows Power shell biedt abstracte klassen en interfaces waarmee u een aangepaste interactieve gebruikers interface kunt maken die als host fungeert voor de Windows Power shell-engine. Als u een aangepaste gebruikers interface wilt maken, moet u de klasse [System. Management. Automation. host. PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) implementeren. U kunt ook de klassen [System. Management. Automation. host. Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)en [System. Management. Automation](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) . host. Pshostuserinterface, en System [. Management. Automation. host. Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) en [System. Management](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) . Automation. host. Ihostuisupportsmultiplechoiceselection implementeren.
