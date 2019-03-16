---
title: Referentie-kenmerkdeclaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059249"
---
# <a name="credential-attribute-declaration"></a>Declaratie van het kenmerk Referentie

De referentie-kenmerk is een optioneel kenmerk die kan worden gebruikt met de parameters van het type referentie [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) zodat een tekenreeks kan ook als een argument worden doorgegeven aan de parameter. Wanneer dit kenmerk wordt toegevoegd aan een parameterdeclaratie, Windows PowerShell converteert de tekenreeksinvoer van de in een [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object. Bijvoorbeeld, de [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet maakt gebruik van dit kenmerk moet Windows PowerShell, genereren de [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object dat wordt geretourneerd door de cmdlet.

## <a name="syntax"></a>Syntaxis

```csharp
[Credential]
```

## <a name="remarks"></a>Opmerkingen

- Meestal dit kenmerk wordt gebruikt door de parameters van het type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) zodat een tekenreeks kan ook als een argument worden doorgegeven aan de parameter. Wanneer een [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object doorgegeven aan de parameter, de Windows PowerShell, gebeurt er niets.

- Bij het maken van de [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object, Windows PowerShell maakt gebruik van de huidige Host om de juiste aanwijzingen voor de gebruiker weer te geven. Bijvoorbeeld, de standaard Host een prompt weergegeven voor een gebruikersnaam en wachtwoord wanneer dit kenmerk wordt gebruikt. Als een aangepaste host wordt gebruikt die een verschillende prompt definieert en deze prompt zou worden weergegeven.

- Dit kenmerk wordt gebruikt met de Parameter-kenmerk. Zie voor meer informatie over dat kenmerk [kenmerk parameterdeclaratie](./parameter-attribute-declaration.md).

- De referentie-kenmerk wordt gedefinieerd door de [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) klasse.

## <a name="see-also"></a>Zie ook

[Parameter Aliases](./parameter-aliases.md)

[Kenmerk parameterdeclaratie](./parameter-attribute-declaration.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
