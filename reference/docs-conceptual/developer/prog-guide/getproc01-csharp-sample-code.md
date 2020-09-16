---
title: GetProc01 (C#) voorbeeld code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 883beb9dd1328a1897b9b61656a98cf515a21be7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778888"
---
# <a name="getproc01-c-sample-code"></a>GetProc01-codevoorbeeld (C#)

De volgende code toont de implementatie van de voor beeld-cmdlet GetProc01. U ziet dat de cmdlet wordt vereenvoudigd door de werkelijke hoeveelheid werk van het ophalen van het proces aan de methode [System. Diagnostics. process. GetProcesses *](/dotnet/api/System.Diagnostics.Process.GetProcesses) te laten staan.

> [!NOTE]
> U kunt het C#-bron bestand (getproc01.cs) voor deze Get-proc-cmdlet downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
> De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.

## <a name="code-sample"></a>Code voorbeeld

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a>Zie ook

[Handleiding voor Windows PowerShell-programmeurs](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
