---
ms.date: 09/13/2016
ms.topic: reference
title: Bevestiging vragen vanuit cmdlets
description: Bevestiging vragen vanuit cmdlets
ms.openlocfilehash: fd869d50b185cb4d38269640df58ec284a32da50
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646412"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Bevestiging vragen vanuit cmdlets

Cmdlets moeten een bevestiging aanvragen wanneer ze een wijziging aanbrengen in het systeem dat zich buiten de Windows Power shell-omgeving bevindt. Als een cmdlet bijvoorbeeld gaat om een gebruikers account toe te voegen of een proces te stoppen, moet de cmdlet bevestiging van de gebruiker vereisen voordat deze wordt uitgevoerd. Als een cmdlet daarentegen een Windows Power shell-variabele wijzigt, hoeft de cmdlet geen bevestiging te vereisen.

Als u een aanvraag wilt indienen, moet de cmdlet aangeven dat deze bevestigings aanvragen ondersteunt en moet deze de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . cmdlet. ShouldContinue (optioneel) aanroepen om een bevestigings aanvraag bericht weer te geven.

## <a name="supporting-confirmation-requests"></a>Bevestigings aanvragen ondersteunen

Ter ondersteuning van bevestigings aanvragen moet de cmdlet de `SupportsShouldProcess` para meter van het cmdlet-kenmerk instellen op `true` . Hierdoor worden de `Confirm` `WhatIf` para meters en cmdlets van Windows Power shell ingeschakeld. `Confirm`Met de para meter kan de gebruiker bepalen of de bevestigings aanvraag wordt weer gegeven. `WhatIf`Met de para meter kan de gebruiker bepalen of de cmdlet een bericht moet weer geven of de actie kan uitvoeren. Voeg de `Confirm` para meters en niet hand matig toe `WhatIf` aan een cmdlet.

In het volgende voor beeld ziet u een cmdlet-kenmerk declaratie die ondersteuning biedt voor bevestigings aanvragen.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>De bevestigings aanvraag methoden aanroepen

Roep in de cmdlet-code de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aan voordat de bewerking wordt uitgevoerd die het systeem wijzigt. Ontwerp de cmdlet zodanig dat als de aanroep een waarde van retourneert `false` , de bewerking niet wordt uitgevoerd en de cmdlet de volgende bewerking verwerkt.

## <a name="calling-the-shouldcontinue-method"></a>De ShouldContinue-methode aanroepen

De meeste cmdlets vragen om bevestiging met alleen de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . In sommige gevallen is mogelijk echter extra bevestiging vereist. Voor deze gevallen moet u de aanroep [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aanvullen met een aanroep van de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . Hierdoor kan de cmdlet of provider het bereik van de **Ja-naar-alle** -antwoorden op de bevestigings prompt nauw keuriger beheren.

Als een cmdlet de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aanroept, moet de cmdlet ook een `Force` Switch parameter opgeven. Als de gebruiker opgeeft `Force` wanneer de gebruiker de cmdlet aanroept, moet de cmdlet [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)wel aanroepen, maar moet de aanroep naar [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)worden omzeild.

[System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) genereert een uitzonde ring wanneer deze wordt aangeroepen vanuit een niet-interactieve omgeving waar de gebruiker niet kan worden gevraagd. Door een `Force` para meter toe te voegen, zorgt u ervoor dat de opdracht nog steeds kan worden uitgevoerd wanneer deze wordt aangeroepen in een niet-interactieve omgeving.

In het volgende voor beeld ziet u hoe [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)wordt aangeroepen.

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

Het gedrag van de aanroep [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) kan variëren, afhankelijk van de omgeving waarin de cmdlet is aangeroepen. Met de vorige richt lijnen kunt u ervoor zorgen dat de cmdlet consistent werkt met andere cmdlets, ongeacht de hostomgeving.

Zie [bevestigingen aanvragen](./how-to-request-confirmations.md)voor een voor beeld van het aanroepen van de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .

## <a name="specify-the-impact-level"></a>Het niveau van de impact opgeven

Wanneer u de cmdlet maakt, geeft u het impact niveau (de ernst) van de wijziging op. Als u dit wilt doen, stelt u de waarde van de `ConfirmImpact` para meter van het cmdlet-kenmerk in op hoog, gemiddeld of laag. U kunt alleen een waarde opgeven voor `ConfirmImpact` Wanneer u ook de `SupportsShouldProcess` para meter voor de cmdlet opgeeft.

Voor de meeste cmdlets hoeft u niet expliciet op te geven `ConfirmImpact` .  Gebruik in plaats daarvan de standaard instelling van de para meter, die gemiddeld is. Als u `ConfirmImpact` op hoog instelt, wordt de bewerking standaard bevestigd. Reserveer deze instelling voor zeer storende acties, zoals het opnieuw Format teren van een harde schijf volume.

## <a name="calling-non-confirmation-methods"></a>Niet-bevestigings methoden aanroepen

Als de cmdlet of provider een bericht wil verzenden, maar niet de aanvraag moet worden bevestigd, kan dit de volgende drie methoden aanroepen. Vermijd het gebruik van de methode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) voor het verzenden van berichten van deze typen omdat de uitvoer van [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is vermengd met de normale uitvoer van uw cmdlet of provider, waardoor het schrijven van scripts wordt gelastigt.

- De cmdlet of provider kan de methode [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) aanroepen om de gebruiker ervan op de opdracht te zorgen en de bewerking voort te zetten.

- Om aanvullende informatie te bieden die de gebruiker kan ophalen met behulp van de `Verbose` para meter, kan de cmdlet of provider de methode [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) aanroepen.

- Om details over fout opsporing op te geven voor andere ontwikkel aars of voor product ondersteuning, kan de cmdlet of provider de methode [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) aanroepen. De gebruiker kan deze gegevens ophalen met behulp van de `Debug` para meter.

Cmdlets en providers roepen eerst de volgende methoden aan om bevestiging aan te vragen voordat ze een bewerking proberen uit te voeren die een systeem buiten Windows Power shell wijzigt:

- [System. Management. Automation. cmdlet. Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System. Management. Automation. provider. Cmdletprovider. Shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

Dit doet u door de methode [System. Management. Automation. cmdlet. Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aan te roepen, waarmee de gebruiker wordt gevraagd de bewerking te bevestigen op basis van de manier waarop de gebruiker de opdracht heeft aangeroepen.

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
