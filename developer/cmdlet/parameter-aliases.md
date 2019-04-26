---
title: Aliassen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067583"
---
# <a name="parameter-aliases"></a>Parameteraliassen

Cmdlet-parameters kunnen ook aliassen hebben. Wanneer u typt of de parameter in een opdracht opgeven, kunt u de aliassen in plaats van de namen van parameters.

## <a name="benefits-of-using-aliases"></a>Voordelen van het gebruik van aliassen

Aliassen aan parameters toe te voegen, biedt de volgende voordelen.

- U kunt een snelkoppeling kunt opgeven, zodat de gebruiker beschikt niet over de volledige parameternaam gebruiken wanneer de cmdlet wordt aangeroepen. U kunt bijvoorbeeld de alias 'CN' gebruiken in plaats van de naam van de parameter "Computernaam".

- U kunt meerdere aliassen definiëren als u wilt dat verschillende namen voor de dezelfde parameter op te geven. Het is raadzaam om te definiëren meerdere aliassen instellen als u wilt werken met meerdere gebruikersgroepen die naar dezelfde gegevens op verschillende manieren verwijzen.

- U kunt zorgen voor compatibiliteit voor bestaande scripts als de naam van een parameter wordt gewijzigd.

- Met behulp van het kenmerk Alias, samen met het kenmerk ValueFromPipelineByName, kunt u een parameter waarmee de cmdlet verbinding maken met verschillende objecttypen definiëren. Stel bijvoorbeeld dat er twee objecten van verschillende typen en het eerste object al een eigenschap schrijver en de tweede object heeft een eigenschap van een editor. Als uw cmdlet heeft een parameter die was met de schrijver en editor aliassen en de cmdlet geaccepteerd pijpleidinginvoer gebaseerd in de namen van eigenschappen, uw cmdlet kan binden aan beide objecten met behulp van de twee parameter-aliassen.

Zie voor meer informatie over aliassen die kunnen worden gebruikt met bepaalde parameters [algemene parameternamen](./common-parameter-names.md).

## <a name="defining-parameter-aliases"></a>Parameter-aliassen definiëren

Declareren voor het definiëren van een alias voor een parameter, de Alias-kenmerk, zoals wordt weergegeven in de volgende parameterdeclaratie. In dit voorbeeld worden meerdere aliassen instellen voor de dezelfde parameter gedefinieerd. (Zie voor meer informatie,[hoe u de Cmdlet-Parameters declareren](./how-to-declare-cmdlet-parameters.md).)

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a>Zie ook

[Namen van algemene parameters](./common-parameter-names.md)

[Hoe om te declareren Cmdlet-Parameters](./how-to-declare-cmdlet-parameters.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
