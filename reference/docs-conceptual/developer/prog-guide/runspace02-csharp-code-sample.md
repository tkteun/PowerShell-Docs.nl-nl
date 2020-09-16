---
title: Code voorbeeld van Runspace02 (C#) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1e58f035f20baa7443d9031499062a45beae01b9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778449"
---
# <a name="runspace02-c-code-sample"></a>Runspace02-codevoorbeeld (C#)

Dit is de C#-bron code voor het Runspace02-voor beeld. In dit voor beeld wordt de klasse [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) gebruikt om de cmdlet synchroon uit te voeren `Get-Process` . Windows Forms en gegevens binding worden vervolgens gebruikt om de resultaten in een DataGridView-besturings element weer te geven

## <a name="code-sample"></a>Code voorbeeld

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs" range="11-82":::

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)
