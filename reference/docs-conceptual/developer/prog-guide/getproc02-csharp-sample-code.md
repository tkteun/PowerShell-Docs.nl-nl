---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc02-codevoorbeeld (C#)
description: GetProc02-codevoorbeeld (C#)
ms.openlocfilehash: 17fd0d0c0829ed21ef955fd2e62e9ee089d62190
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355609"
---
# <a name="getproc02-c-sample-code"></a>GetProc02-codevoorbeeld (C#)

De volgende code toont de implementatie van een `Get-Process` cmdlet die opdracht regel invoer accepteert. In deze implementatie wordt een `Name` para meter gedefinieerd voor het toestaan van opdracht regel invoer en wordt de methode [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) gebruikt als uitvoer mechanisme voor het verzenden van uitvoer objecten naar de pijp lijn.

## <a name="code-sample"></a>Code voorbeeld

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs" range="11-76":::

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)
