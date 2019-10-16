---
title: Verwijzing kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359421"
---
# <a name="credential-attribute-declaration"></a>Declaratie van het kenmerk Referentie

Het referentie kenmerk is een optioneel kenmerk dat kan worden gebruikt met referentie parameters van het type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , zodat een teken reeks ook als argument kan worden door gegeven aan de para meter. Wanneer dit kenmerk wordt toegevoegd aan een parameter declaratie, wordt de invoer van de teken reeks door Windows Power shell geconverteerd naar een [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object. De cmdlet [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) gebruikt dit kenmerk bijvoorbeeld om Windows Power shell het [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object te laten genereren dat door de cmdlet wordt geretourneerd.

## <a name="syntax"></a>Syntaxis

```csharp
[Credential]
```

## <a name="remarks"></a>Opmerkingen

- Dit kenmerk wordt doorgaans gebruikt door para meters van het type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , zodat een teken reeks ook als argument kan worden door gegeven aan de para meter. Wanneer een [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object wordt door gegeven aan de para meter, doet Windows Power shell niets.

- Bij het maken van het [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object gebruikt Windows Power shell de huidige host om de juiste prompts voor de gebruiker weer te geven. De standaard host geeft bijvoorbeeld een vraag naar een gebruikers naam en wacht woord wanneer dit kenmerk wordt gebruikt. Als er echter een aangepaste host wordt gebruikt die een andere prompt definieert, wordt de prompt weer gegeven.

- Dit kenmerk wordt gebruikt met het parameter kenmerk. Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over dat kenmerk.

- Het referentie kenmerk wordt gedefinieerd door de klasse [System. Management. Automation. Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) .

## <a name="see-also"></a>Zie ook

[Parameter aliassen](./parameter-aliases.md)

[Parameter kenmerk declaratie](./parameter-attribute-declaration.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
