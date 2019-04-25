---
title: GetProc03 (C#) voorbeeldcode | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 4d921dd62999bc68b80838bafa2a3da8d4df3ebb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081511"
---
# <a name="getproc03-c-sample-code"></a>GetProc03-codevoorbeeld (C#)

De volgende code toont de implementatie van een `Get-Process` cmdlet kan accepteren pipelined invoer. Deze implementatie definieert een `Name` parameter die de invoer van de pijplijn, accepteert procesinformatie opgehaald uit de lokale computer op basis van de opgegeven namen en gebruikt vervolgens de [System.Management.Automation.Cmdlet.WriteObject% 28System.object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) methode als de uitvoer-mechanisme voor het verzenden van objecten aan de pijplijn.

> [!NOTE]
> U kunt downloaden de C# bronbestand (getprov03.cs) voor deze cmdlet Get-Proc is met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en .NET Framework 3.0 Runtime-onderdelen. Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.

## <a name="code-sample"></a>Voorbeeld van code

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a>Zie ook

[Windows PowerShell-programmeergids](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)