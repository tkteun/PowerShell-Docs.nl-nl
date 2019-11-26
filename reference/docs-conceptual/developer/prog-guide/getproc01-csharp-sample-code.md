---
title: GetProc01 (C#) voorbeeld code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 499a688ce5e8daa78baff58c454ad237836bbe48
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416172"
---
# <a name="getproc01-c-sample-code"></a>GetProc01-codevoorbeeld (C#)

De volgende code toont de implementatie van de voor beeld-cmdlet GetProc01. U ziet dat de cmdlet wordt vereenvoudigd door de werkelijke hoeveelheid werk van het ophalen van het proces aan de methode [System. Diagnostics. process. GetProcesses *](/dotnet/api/System.Diagnostics.Process.GetProcesses) te laten staan.

> [!NOTE]
> U kunt het C# bron bestand (getproc01.cs) voor deze Get-proc-cmdlet downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
>
> De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map.

## <a name="code-sample"></a>Code voorbeeld

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a>Zie ook

[Hand leiding voor Windows Power shell-programmeurs](./windows-powershell-programmer-s-guide.md)

[Windows Power shell SDK](../windows-powershell-reference.md)
