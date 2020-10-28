---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace07-codevoorbeeld
description: Runspace07-codevoorbeeld
ms.openlocfilehash: 6e8c9f48a6e9c5a642ecf93bca8a85003b3cfbf8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647401"
---
# <a name="runspace07-code-sample"></a>Runspace07-codevoorbeeld

Dit is de bron code voor het Runspace07-voor beeld dat wordt beschreven in [een console toepassing maken waarmee opdrachten worden toegevoegd aan een pijp lijn](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).
Met deze voorbeeld toepassing maakt u een runs Pace, maakt u een pijp lijn, voegt u twee opdrachten aan de pijp lijn toe en voert u de pijp lijn uit. De opdrachten die zijn toegevoegd aan de pijp lijn zijn de `Get-Process` `Measure-Object` cmdlets en.

> [!NOTE]
> U kunt het C#-bron bestand (runspace07.cs) downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
> De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.

## <a name="code-sample"></a>Code voorbeeld

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs" range="11-108":::

## <a name="see-also"></a>Zie ook

[Handleiding voor Windows PowerShell-programmeurs](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
