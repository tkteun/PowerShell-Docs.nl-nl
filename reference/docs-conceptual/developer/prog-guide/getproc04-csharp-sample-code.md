---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc04-codevoorbeeld (C#)
description: GetProc04-codevoorbeeld (C#)
ms.openlocfilehash: 80020b60a7ab34caec0c856b9b7d12021f4276b9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654386"
---
# <a name="getproc04-c-sample-code"></a>GetProc04-codevoorbeeld (C#)

De volgende code toont de implementatie van een `Get-Process` cmdlet die niet-afsluit fouten rapporteert. Met deze implementatie wordt de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aangeroepen om niet-afsluit fouten te rapporteren.

> [!NOTE]
> U kunt het C#-bron bestand (getprov04.cs) voor deze Get-Proc-cmdlet downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
> De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.

## <a name="code-sample"></a>Code voorbeeld

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs" range="11-98":::

## <a name="see-also"></a>Zie ook

[Handleiding voor Windows PowerShell-programmeurs](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
