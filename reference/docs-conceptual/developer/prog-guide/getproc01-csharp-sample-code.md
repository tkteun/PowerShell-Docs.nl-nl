---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc01-codevoorbeeld (C#)
description: GetProc01-codevoorbeeld (C#)
ms.openlocfilehash: 79509ff12afb32c907058f4ddb0c707f3823857a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654478"
---
# <a name="getproc01-c-sample-code"></a>GetProc01-codevoorbeeld (C#)

De volgende code toont de implementatie van de voor beeld-cmdlet GetProc01. U ziet dat de cmdlet wordt vereenvoudigd door de werkelijke hoeveelheid werk van het ophalen van het proces aan de methode [System. Diagnostics. process. GetProcesses *](/dotnet/api/System.Diagnostics.Process.GetProcesses) te laten staan.

> [!NOTE]
> U kunt het C#-bron bestand (getproc01.cs) voor deze Get-Proc-cmdlet downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
> De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.

## <a name="code-sample"></a>Code voorbeeld

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a>Zie ook

[Handleiding voor Windows PowerShell-programmeurs](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
