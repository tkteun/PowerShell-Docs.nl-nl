---
title: Voorbeeld code voor GetProc03 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: a0a88ca517347a94fc81534caace6efa0f13fdd7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352631"
---
# <a name="getproc03-vbnet-sample-code"></a>GetProc03-codevoorbeeld (VB.NET)

De volgende code toont de implementatie van een `Get-Process`-cmdlet waarmee de invoer van een pijp lijn kan worden geaccepteerd. Deze implementatie definieert een `Name` para meter die de invoer van de pijp lijn accepteert, haalt proces gegevens van de lokale computer op op basis van de opgegeven namen, en gebruikt vervolgens de methode [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) als uitvoer mechanisme voor het verzenden van objecten naar de pijp lijn.

## <a name="code-sample"></a>Code voorbeeld

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
