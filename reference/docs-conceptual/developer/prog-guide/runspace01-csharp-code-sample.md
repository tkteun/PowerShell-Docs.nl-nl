---
title: Code voorbeeld van Runspace01 (C#) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 418162731b4a98989642e1c61c655fdb0f002698
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787051"
---
# <a name="runspace01-c-code-sample"></a>Runspace01-codevoorbeeld (C#)

Hier volgen de code voorbeelden voor de runs Pace die wordt beschreven in [een console toepassing maken die een opgegeven opdracht uitvoert](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).
Hiervoor roept de toepassing een runs Pace aan en roept hij een opdracht aan. (Houd er rekening mee dat met deze toepassing geen runs Pace-configuratie gegevens worden opgegeven, noch expliciet een pijp lijn wordt gemaakt. De opdracht die wordt aangeroepen, is de `Get-Process` cmdlet.

> [!NOTE]
> U kunt het C#-bron bestand (runspace01.cs) voor deze runs Pace downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.
> Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
> De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.

## <a name="code-sample"></a>Code voorbeeld

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs" range="11-62":::

## <a name="see-also"></a>Zie ook

[Handleiding voor Windows PowerShell-programmeurs](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
