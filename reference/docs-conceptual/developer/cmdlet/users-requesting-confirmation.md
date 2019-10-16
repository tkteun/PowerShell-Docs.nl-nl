---
title: Gebruikers vragen om bevestiging | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359154"
---
# <a name="users-requesting-confirmation"></a>Gebruikers die bevestiging vragen

Wanneer u de waarde `true` opgeeft voor de para meter `SupportsShouldProcess` van de kenmerk declaratie van de cmdlet, kunnen gebruikers de para meter `Confirm` opgeven bij de opdracht prompt.

In de standaard omgeving kunnen gebruikers de para meter `Confirm` of `"-Confirm:$true` opgeven, zodat er een bevestiging wordt gevraagd wanneer de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wordt aangeroepen. Dit omzeilt [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -bevestigings aanvragen, zelfs voor bewerkingen met een hoge impact.

Als `Confirm` niet is opgegeven, wordt met de aanroep aangevraagd [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) als de `$ConfirmPreference`-voorkeurs variabele gelijk is aan of groter is dan de `ConfirmImpact`-instelling van de cmdlet of provider. De standaard instelling van `$ConfirmPreference` is hoog. In de standaard omgeving worden alleen cmdlets en providers vermeld waarmee een bevestiging van een actie aanvraag met hoge impact wordt opgegeven.

Als `Confirm` false is of als `"-Confirm:$false` is opgegeven, wordt met de aanroep [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) de bevestiging van de gebruiker aangevraagd en wordt de `$ConfirmPreference`-shell variabele genegeerd.

## <a name="remarks"></a>Opmerkingen

- Voor cmdlets en providers die `SupportsShouldProcess` opgeven, maar niet `ConfirmImpact`, worden deze acties behandeld als ' gemiddelde impact ' acties en worden ze niet standaard gevraagd. Het effect niveau is lager dan de standaard instelling van de voorkeurs variabele `$ConfirmPreference`.

- Als de gebruiker de para meter `Verbose` opgeeft, worden deze op de hoogte gesteld van de bewerking, zelfs als ze niet worden gevraagd om bevestiging.

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
