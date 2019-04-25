---
title: Codevoorbeeld RunSpace07 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 064e7d7ea2ee173bbcdd75a9f3a6c12582afe17b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081288"
---
# <a name="runspace07-code-sample"></a>Runspace07-codevoorbeeld

Hier volgt de broncode voor het voorbeeld Runspace07 die zijn beschreven [het maken van een toepassing die wordt toegevoegd consoleopdrachten voor een pijplijn](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e). Deze voorbeeldtoepassing maakt een runspace, wordt een pijplijn gemaakt, worden twee opdrachten toegevoegd aan de pijplijn en voert de pijplijn. De opdrachten toegevoegd aan de pijplijn zijn de `Get-Process` en `Measure-Object` cmdlets.

> [!NOTE]
> U kunt downloaden de C# bronbestand (runspace07.cs) met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3.0 Runtime-onderdelen. Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.

## <a name="code-sample"></a>Voorbeeld van code

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a>Zie ook

[Windows PowerShell-programmeergids](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)