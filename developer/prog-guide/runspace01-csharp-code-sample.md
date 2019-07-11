---
title: Runspace01 (C#) codevoorbeeld | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: ab067485d70523a16493eb57170615ab300eaa98
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735053"
---
# <a name="runspace01-c-code-sample"></a>Runspace01-codevoorbeeld (C#)

Hier volgen de codevoorbeelden voor de runspace die zijn beschreven [het maken van een Console-toepassing die wordt uitgevoerd een opgegeven opdracht](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program). U doet dit door de toepassing een runspace aanroept en roept vervolgens een opdracht. (Houd er rekening mee dat deze toepassing geen informatie over de configuratie van de runspace geeft, noch worden deze expliciet een pijplijn maken). De opdracht die wordt opgeroepen, is de `Get-Process` cmdlet.

> [!NOTE]
> U kunt downloaden de C# bronbestand (runspace01.cs) voor deze runspace met de Microsoft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3.0 Runtime-onderdelen. Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.

## <a name="code-sample"></a>Voorbeeld van code

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a>Zie ook

[Windows PowerShell-programmeergids](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)