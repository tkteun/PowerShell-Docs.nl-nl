---
title: Codevoorbeeld RunSpace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: abf19d848f6150d005c63bb0fc2ffbe1de405e2a
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734967"
---
# <a name="runspace05-code-sample"></a>Runspace05-codevoorbeeld

Hier volgt de broncode voor het voorbeeld Runspace05 die wordt beschreven in [configureren van een Runspace met behulp van RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2). In dit voorbeeld laat zien hoe de configuratiegegevens runspace maken, een runspace maken, een pijplijn maken met één opdracht en uitvoeren van de pijplijn. De opdracht die wordt uitgevoerd, is de `Get-Process` cmdlet.

> [!NOTE]
> U kunt downloaden de C# bronbestand (runspace05.cs) met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3.0 Runtime-onderdelen. Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.

## <a name="code-sample"></a>Voorbeeld van code

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a>Zie ook

[Windows PowerShell-programmeergids](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)