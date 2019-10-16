---
title: GetProc02 (C#) voorbeeld code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 5989b1e7030375b1bacdd9b82c25c1a8288fd637
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352673"
---
# <a name="getproc02-c-sample-code"></a>GetProc02-codevoorbeeld (C#)

De volgende code toont de implementatie van een cmdlet `Get-Process` die opdracht regel invoer accepteert. U ziet dat deze implementatie een `Name`-para meter definieert om opdracht regel invoer toe te staan en gebruikt de methode [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) als uitvoer mechanisme voor het verzenden van uitvoer objecten naar de pijp lijn.

## <a name="code-sample"></a>Code voorbeeld

[!code-csharp[GetProcessSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a>Zie ook

[Windows Power shell SDK](../windows-powershell-reference.md)
