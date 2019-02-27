---
title: Eigenschappen als Parameters declareren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850573"
---
# <a name="declaring-properties-as-parameters"></a>Eigenschappen declareren als parameters

Dit onderwerp bevat algemene informatie die u begrijpen moet voordat u de parameters van een cmdlet declareren.

U declareert de parameters van een cmdlet uit binnen de klasse van de cmdlet, definiëren van de openbare eigenschappen die staan voor elke parameter en vervolgens een of meer kenmerken van de Parameter toevoegen aan elke eigenschap. De Windows PowerShell-runtime maakt gebruik van de Parameter-kenmerken voor het identificeren van de eigenschap als cmdlet-parameter. De syntaxis van de basis voor de Parameter-kenmerk declareren is `[Parameter()]`.

Hier volgt een voorbeeld van een eigenschap die is gedefinieerd als een vereiste parameter.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Hier volgen enkele dingen om te weten over parameters.

- Een parameter moet expliciet gemarkeerd als openbaar. Parameters die niet zijn gemarkeerd als openbare standaard naar interne en wordt niet worden gevonden door de Windows PowerShell-runtime.

- Parameters moeten worden gedefinieerd als Microsoft .NET Framework-typen voor betere validatie van de parameter. Parameters die beperkt tot één waarde uit een set waarden zijn moeten bijvoorbeeld worden gedefinieerd als een opsommingstype. Parameters die een Uniform Resource Identifier (URI)-waarde moet van het type [System.Uri](/dotnet/api/System.Uri).

- Vermijd basic queryreeksparameters voor eigenschappen van alle vrije tekst.

- U kunt een parameter toevoegen aan een willekeurig aantal parametersets. Zie voor meer informatie over parametersets [Cmdlet-Parameter stelt](./cmdlet-parameter-sets.md).

Windows PowerShell biedt ook een aantal gemeenschappelijke parameters die automatisch beschikbaar voor elke cmdlet zijn. Zie voor meer informatie over deze parameters en hun aliassen, [algemene Parameters van de Cmdlet](./common-parameter-names.md).

## <a name="see-also"></a>Zie ook

[Algemene cmdlet-Parameters](./common-parameter-names.md)

[Typen van de Cmdlet-Parameter](./types-of-cmdlet-parameters.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
