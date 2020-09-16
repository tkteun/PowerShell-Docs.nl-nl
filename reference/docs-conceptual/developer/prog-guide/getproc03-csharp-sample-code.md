---
title: GetProc03 (C#) voorbeeld code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 278c3f36bb975f9ea195978853e6539c0bd15084
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787118"
---
# <a name="getproc03-c-sample-code"></a>GetProc03-codevoorbeeld (C#)

De volgende code toont de implementatie van een `Get-Process` cmdlet die de invoer van een pijp lijn kan accepteren. Met deze implementatie wordt een `Name` para meter gedefinieerd die de invoer van de pijp lijn accepteert, worden proces gegevens van de lokale computer opgehaald op basis van de opgegeven namen. vervolgens wordt de methode [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) gebruikt als uitvoer mechanisme voor het verzenden van objecten naar de pijp lijn.

> [!NOTE]
> U kunt het C#-bron bestand (getprov03.cs) voor deze Get-proc-cmdlet downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
> De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.

## <a name="code-sample"></a>Code voorbeeld

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="11-78":::

## <a name="see-also"></a>Zie ook

[Handleiding voor Windows PowerShell-programmeurs](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
