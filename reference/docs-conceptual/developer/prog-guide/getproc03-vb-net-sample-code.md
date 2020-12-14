---
ms.date: 09/12/2016
ms.topic: reference
title: GetProc03-codevoorbeeld (VB.NET)
description: GetProc03-codevoorbeeld (VB.NET)
ms.openlocfilehash: fc70496178c85e101b380e68aacd64c8d1f350e9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355558"
---
# <a name="getproc03-vbnet-sample-code"></a>GetProc03-codevoorbeeld (VB.NET)

De volgende code toont de implementatie van een `Get-Process` cmdlet die de invoer van een pijp lijn kan accepteren. Met deze implementatie wordt een `Name` para meter gedefinieerd die de invoer van de pijp lijn accepteert, worden proces gegevens van de lokale computer opgehaald op basis van de opgegeven namen. vervolgens wordt de methode [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) gebruikt als uitvoer mechanisme voor het verzenden van objecten naar de pijp lijn.

## <a name="code-sample"></a>Code voorbeeld

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
