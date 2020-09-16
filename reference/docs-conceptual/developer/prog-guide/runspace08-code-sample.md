---
title: Voor beeld van RunSpace08-code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 67172a0f8d6daf2f5b9965d1a18f7698daddbe1a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784687"
---
# <a name="runspace08-code-sample"></a>Runspace08-codevoorbeeld

Dit is de bron code voor het Runspace08-voor beeld dat wordt beschreven in [een console toepassing maken die para meters toevoegt aan een opdracht](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).
Met deze voorbeeld toepassing maakt u een runs Pace, maakt u een pijp lijn, voegt u twee opdrachten aan de pijp lijn toe, voegt u twee para meters toe aan de tweede opdracht en voert u de pijp lijn uit. De opdrachten die worden toegevoegd aan de pijp lijn zijn de `Get-Process` `Sort-Object` cmdlets en.

## <a name="code-sample"></a>Code voorbeeld

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs" range="11-86":::

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)
