---
title: Gebruikers die aanvragen bevestiging | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067212"
---
# <a name="users-requesting-confirmation"></a>Gebruikers die bevestiging vragen

Wanneer u een waarde opgeeft `true` voor de `SupportsShouldProcess` parameter van de Cmdlet kenmerk verklaring die gebruikers kunnen opgeven de `Confirm` parameter bij de opdrachtprompt.

In de standaardomgeving, kunnen gebruikers opgeven de `Confirm` parameter of `"-Confirm:$true` zodat bevestiging wordt gevraagd wanneer de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode wordt aangeroepen. Dit omzeilt [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) bevestiging aanvragen, zelfs voor invloedrijke bewerkingen.

Als `Confirm` niet is opgegeven, de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aanroep vraagt om bevestiging als de `$ConfirmPreference` voorkeursvariabele is gelijk aan of groter is dan de `ConfirmImpact` instellen van de cmdlet of -provider. De standaardinstelling van `$ConfirmPreference` is hoog. Daarom in de standaardomgeving aanvraag alleen-cmdlets en providers die een grote impact-actie opgeeft bevestigen.

Als `Confirm` false is of als `"-Confirm:$false` is opgegeven, wordt de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aanroep vraagt om bevestiging van de gebruiker en de `$ConfirmPreference` shell-variabele wordt genegeerd.

## <a name="remarks"></a>Opmerkingen

- Voor cmdlets en providers die opgeeft `SupportsShouldProcess`, maar niet `ConfirmImpact`, deze acties worden behandeld als 'normale impact' acties en ze niet standaard wordt gevraagd. Het niveau van de impact is kleiner dan de standaardinstelling van de `$ConfirmPreference` voorkeursvariabele.

- Als de gebruiker Hiermee geeft u de `Verbose` parameter, krijgen ze het bericht van de bewerking, zelfs als ze niet om bevestiging wordt gevraagd.

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
