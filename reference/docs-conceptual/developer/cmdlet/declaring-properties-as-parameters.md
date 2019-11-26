---
title: Eigenschappen declareren als para meters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356446"
---
# <a name="declaring-properties-as-parameters"></a>Eigenschappen declareren als parameters

In dit onderwerp vindt u basis informatie die u moet begrijpen voordat u de para meters van een cmdlet declareert.

Als u de para meters van een cmdlet binnen de cmdlet-klasse wilt declareren, definieert u de open bare eigenschappen die voor elke para meter vertegenwoordigen en voegt u vervolgens een of meer parameter kenmerken toe aan elke eigenschap. De Windows Power shell-runtime maakt gebruik van de parameter kenmerken om de eigenschap te identificeren als een cmdlet-para meter. De basis syntaxis voor het declareren van het parameter kenmerk is `[Parameter()]`.

Hier volgt een voor beeld van een eigenschap die is gedefinieerd als een vereiste para meter.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Hier volgen enkele dingen die u moet weten over para meters.

- Een para meter moet expliciet als openbaar worden gemarkeerd. Para meters die niet zijn gemarkeerd als open bare standaard waarde voor intern en niet worden gevonden door de Windows Power shell-runtime.

- Para meters moeten worden gedefinieerd als Microsoft .NET Framework-typen voor een betere validatie van de para meters. Para meters die zijn beperkt tot één waarde uit een set waarden, moeten bijvoorbeeld worden gedefinieerd als een opsommings type. Para meters die een URI-waarde (Uniform Resource Identifier) volgen, moeten van het type [System. URI](/dotnet/api/System.Uri)zijn.

- Vermijd Basic string-para meters voor alle eigenschappen van een vrije-vorm tekst.

- U kunt een para meter toevoegen aan een wille keurig aantal parameter sets. Zie [cmdlet-parameter sets](./cmdlet-parameter-sets.md)voor meer informatie over parameter sets.

Windows Power shell biedt ook een aantal algemene para meters die automatisch beschikbaar zijn voor elke cmdlet. Zie [algemene cmdlet-para meters](./common-parameter-names.md)voor meer informatie over deze para meters en de bijbehorende aliassen.

## <a name="see-also"></a>Zie ook

[Algemene cmdlet-para meters](./common-parameter-names.md)

[Typen cmdlet-para meter](./types-of-cmdlet-parameters.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)