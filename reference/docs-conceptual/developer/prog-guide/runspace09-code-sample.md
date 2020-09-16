---
title: Voor beeld van RunSpace09-code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fc5d8d4d182cca6bfc42d63c68a14a7a5e5f9c97
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784670"
---
# <a name="runspace09-code-sample"></a>Runspace09-codevoorbeeld

Dit is de bron code voor het Runspace09-voor beeld dat wordt beschreven in [een console toepassing maken die een pijp lijn asynchroon aanroept](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).
Met deze voorbeeld toepassing wordt een runs Pace gemaakt en geopend, wordt een pijp lijn gemaakt en asynchroon aangeroepen en worden vervolgens pijplijn gebeurtenissen gebruikt om het script asynchroon te verwerken. Het script dat door deze toepassing wordt uitgevoerd, maakt de gehele getallen 1 tot en met 10 in intervallen van 0,5 seconden (500 MS).

## <a name="code-sample"></a>Code voorbeeld

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)
