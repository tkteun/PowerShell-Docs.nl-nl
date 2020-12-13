---
ms.date: 09/13/2016
ms.topic: reference
title: Declaratie van het kenmerk Referentie
description: Declaratie van het kenmerk Referentie
ms.openlocfilehash: fb826d9a46cadc021fe0c667091bbc7a9251aaa8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648601"
---
# <a name="credential-attribute-declaration"></a>Declaratie van het kenmerk Referentie

Het referentie kenmerk is een optioneel kenmerk dat kan worden gebruikt met referentie parameters van het type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , zodat een teken reeks ook als argument kan worden door gegeven aan de para meter. Wanneer dit kenmerk wordt toegevoegd aan een parameter declaratie, wordt de invoer van de teken reeks door Windows Power shell geconverteerd naar een [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object. De cmdlet [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) gebruikt dit kenmerk bijvoorbeeld om Windows Power shell het [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object te laten genereren dat door de cmdlet wordt geretourneerd.

## <a name="syntax"></a>Syntax

```csharp
[Credential]
```

## <a name="remarks"></a>Opmerkingen

- Dit kenmerk wordt doorgaans gebruikt door para meters van het type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , zodat een teken reeks ook als argument kan worden door gegeven aan de para meter. Wanneer een [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object wordt door gegeven aan de para meter, doet Windows Power shell niets.

- Bij het maken van het [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object gebruikt Windows Power shell de huidige host om de juiste prompts voor de gebruiker weer te geven. De standaard host geeft bijvoorbeeld een vraag naar een gebruikers naam en wacht woord wanneer dit kenmerk wordt gebruikt. Als er echter een aangepaste host wordt gebruikt die een andere prompt definieert, wordt de prompt weer gegeven.

- Dit kenmerk wordt gebruikt met het parameter kenmerk. Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over dat kenmerk.

- Het referentie kenmerk wordt gedefinieerd door de klasse [System. Management. Automation. Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) .

## <a name="see-also"></a>Zie ook

[Parameteraliassen](./parameter-aliases.md)

[Declaratie van het kenmerk Parameter](./parameter-attribute-declaration.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
