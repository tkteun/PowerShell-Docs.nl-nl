---
ms.date: 09/13/2016
ms.topic: reference
title: Gebruikers die bevestiging vragen
description: Gebruikers die bevestiging vragen
ms.openlocfilehash: 58dbe27635ca38886b728f585fec063645b3597e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646304"
---
# <a name="users-requesting-confirmation"></a>Gebruikers die bevestiging vragen

Wanneer u een waarde van opgeeft `true` voor de `SupportsShouldProcess` para meter van de cmdlet-kenmerk declaratie, kunnen gebruikers de `Confirm` para meter opgeven bij de opdracht prompt.

In de standaard omgeving kunnen gebruikers de `Confirm` para meter opgeven of `"-Confirm:$true` ervoor zorgen dat er een bevestiging wordt gevraagd wanneer de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wordt aangeroepen. Dit omzeilt [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -bevestigings aanvragen, zelfs voor bewerkingen met een hoge impact.

Als `Confirm` niet is opgegeven, wordt met de aanroep van [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) een bevestiging gevraagd als de `$ConfirmPreference` Voorkeurs variabele gelijk is aan of groter is dan de `ConfirmImpact` instelling van de cmdlet of provider. De standaard instelling `$ConfirmPreference` is hoog. In de standaard omgeving worden alleen cmdlets en providers vermeld waarmee een bevestiging van een actie aanvraag met hoge impact wordt opgegeven.

Als `Confirm` is ingesteld op False of als `"-Confirm:$false` is opgegeven, wordt voor de aanroep van [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) een bevestiging van de gebruiker aangevraagd en `$ConfirmPreference` wordt de shell-variabele genegeerd.

## <a name="remarks"></a>Opmerkingen

- Voor cmdlets en providers die `SupportsShouldProcess` , maar niet worden opgegeven, `ConfirmImpact` worden deze acties verwerkt als ' gemiddelde impact ' acties en worden ze niet standaard gevraagd. Het effect niveau is lager dan de standaard instelling van de `$ConfirmPreference` Voorkeurs variabele.

- Als de gebruiker de `Verbose` para meter opgeeft, wordt deze op de hoogte gesteld van de bewerking, zelfs als ze niet om bevestiging wordt gevraagd.

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
