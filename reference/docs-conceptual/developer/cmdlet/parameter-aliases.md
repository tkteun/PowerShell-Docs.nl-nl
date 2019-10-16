---
title: Parameter aliassen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359261"
---
# <a name="parameter-aliases"></a>Parameteraliassen

Cmdlet-para meters kunnen ook aliassen hebben. U kunt de aliassen gebruiken in plaats van de parameter namen wanneer u de para meter in een opdracht typt of opgeeft.

## <a name="benefits-of-using-aliases"></a>Voor delen van het gebruik van aliassen

Het toevoegen van aliassen aan para meters biedt de volgende voor delen.

- U kunt een snelkoppeling opgeven zodat de gebruiker de volledige parameter naam niet hoeft te gebruiken wanneer de cmdlet wordt aangeroepen. U kunt bijvoorbeeld de alias ' CN ' gebruiken in plaats van de parameter naam ' ComputerName '.

- U kunt meerdere aliassen definiëren als u verschillende namen voor dezelfde para meter wilt opgeven. Mogelijk wilt u meerdere aliassen definiëren als u moet werken met meerdere gebruikers groepen die naar dezelfde gegevens op verschillende manieren verwijzen.

- U kunt achterwaartse compatibiliteit voor bestaande scripts bieden als de naam van een para meter wordt gewijzigd.

- Door gebruik te maken van het alias kenmerk samen met het kenmerk ValueFromPipelineByName, kunt u een para meter definiëren waarmee de cmdlet kan worden gebonden aan verschillende object typen. Stel dat u twee objecten van verschillende typen hebt en het eerste object heeft een eigenschap Writer en het tweede object heeft een editor-eigenschap. Als uw cmdlet een para meter heeft met schrijver-en redacteur-aliassen en de door de cmdlet geaccepteerde invoer van de pijp lijn is gebaseerd op eigenschapnamen, kan de cmdlet met de twee parameter aliassen aan beide objecten worden gebonden.

Zie [common para meter names](./common-parameter-names.md)(Engelstalig) voor meer informatie over aliassen die kunnen worden gebruikt met specifieke para meters.

## <a name="defining-parameter-aliases"></a>Parameter aliassen definiëren

Als u een alias voor een para meter wilt definiëren, declareert u het alias kenmerk, zoals wordt weer gegeven in de volgende parameter declaratie. In dit voor beeld worden meerdere aliassen gedefinieerd voor dezelfde para meter. (Zie[cmdlet-para meters declareren](./how-to-declare-cmdlet-parameters.md)voor meer informatie.)

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

[Algemene parameter namen](./common-parameter-names.md)

[Cmdlet-para meters declareren](./how-to-declare-cmdlet-parameters.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
