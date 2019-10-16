---
title: Bevestiging aanvragen bij cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: 0c0517ef7fbd5ae6434773a2dfe276f3a8c35f39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359238"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Bevestiging vragen vanuit cmdlets

Cmdlets moeten een bevestiging aanvragen wanneer ze een wijziging aanbrengen in het systeem dat zich buiten de Windows Power shell-omgeving bevindt. Als een cmdlet bijvoorbeeld gaat om een gebruikers account toe te voegen of een proces te stoppen, moet de cmdlet bevestiging van de gebruiker vereisen voordat deze wordt uitgevoerd. Als een cmdlet daarentegen een Windows Power shell-variabele wijzigt, hoeft de cmdlet geen bevestiging te vereisen.

Als u een aanvraag wilt indienen, moet de cmdlet aangeven dat er bevestigings aanvragen worden ondersteund en moet het [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation.-app. ShouldContinue worden aangeroepen. ](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)(optioneel) methoden om een bericht met een bevestigings aanvraag weer te geven.

## <a name="supporting-confirmation-requests"></a>Bevestigings aanvragen ondersteunen

Ter ondersteuning van bevestigings aanvragen moet de cmdlet de para meter `SupportsShouldProcess` van het kenmerk cmdlet instellen op `true`. Hiermee worden de para meters voor de `Confirm` en de `WhatIf`-cmdlet ingeschakeld die worden meegeleverd met Windows Power shell. Met de para meter `Confirm` kan de gebruiker bepalen of de bevestigings aanvraag wordt weer gegeven. Met de para meter `WhatIf` kan de gebruiker bepalen of de cmdlet een bericht moet weer geven of de actie kan uitvoeren. Voeg de para meters `Confirm` en `WhatIf` niet hand matig toe aan een cmdlet.

In het volgende voor beeld ziet u een cmdlet-kenmerk declaratie die ondersteuning biedt voor bevestigings aanvragen.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>De bevestigings aanvraag methoden aanroepen

Roep in de cmdlet-code de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aan voordat de bewerking wordt uitgevoerd die het systeem wijzigt. Ontwerp de cmdlet zodanig dat als de aanroep een waarde van `false` retourneert, de bewerking niet wordt uitgevoerd en de cmdlet de volgende bewerking verwerkt.

## <a name="calling-the-shouldcontinue-method"></a>De ShouldContinue-methode aanroepen

De meeste cmdlets vragen om bevestiging met alleen de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . In sommige gevallen is mogelijk echter extra bevestiging vereist. Voor deze gevallen moet u de aanroep [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aanvullen met een aanroep van de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . Hierdoor kan de cmdlet of provider het bereik van de **Ja-naar-alle** -antwoorden op de bevestigings prompt nauw keuriger beheren.

Als een cmdlet de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aanroept, moet de cmdlet ook een para meter van de `Force`-switch opgeven. Als de gebruiker `Force` opgeeft wanneer de gebruiker de cmdlet aanroept, moet de cmdlet [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)wel aanroepen, maar moet de aanroep naar [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)worden omzeild.

[System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) genereert een uitzonde ring wanneer deze wordt aangeroepen vanuit een niet-interactieve omgeving waar de gebruiker niet kan worden gevraagd. Als u een `Force`-para meter toevoegt, zorgt u ervoor dat de opdracht nog steeds kan worden uitgevoerd wanneer deze wordt aangeroepen in een niet-interactieve omgeving.

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

Wanneer u de cmdlet maakt, geeft u het impact niveau (de ernst) van de wijziging op. Als u dit wilt doen, stelt u de waarde van de para meter `ConfirmImpact` van het kenmerk cmdlet in op hoog, gemiddeld of laag. U kunt alleen een waarde voor `ConfirmImpact` opgeven wanneer u ook de para meter `SupportsShouldProcess` voor de cmdlet opgeeft.

Voor de meeste cmdlets hoeft u niet expliciet `ConfirmImpact` op te geven.  Gebruik in plaats daarvan de standaard instelling van de para meter, die gemiddeld is. Als u `ConfirmImpact` instelt op hoog, wordt de bewerking standaard bevestigd. Reserveer deze instelling voor zeer storende acties, zoals het opnieuw Format teren van een harde schijf volume.

## <a name="calling-non-confirmation-methods"></a>Niet-bevestigings methoden aanroepen

Als de cmdlet of provider een bericht wil verzenden, maar niet de aanvraag moet worden bevestigd, kan dit de volgende drie methoden aanroepen. Vermijd het gebruik van de methode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) voor het verzenden van berichten van deze typen omdat [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) uitvoer vermengd is met de normale uitvoer van uw cmdlet of provider , waardoor het schrijven van scripts lastig wordt.

- De cmdlet of provider kan de methode [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) aanroepen om de gebruiker ervan op de opdracht te zorgen en de bewerking voort te zetten.

- Om aanvullende informatie te bieden die de gebruiker kan ophalen met behulp van de para meter `Verbose`, kan de cmdlet of provider de methode [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) aanroepen.

- Om details over fout opsporing op te geven voor andere ontwikkel aars of voor product ondersteuning, kan de cmdlet of provider de methode [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) aanroepen. De gebruiker kan deze gegevens ophalen met behulp van de para meter `Debug`.

Cmdlets en providers roepen eerst de volgende methoden aan om bevestiging aan te vragen voordat ze een bewerking proberen uit te voeren die een systeem buiten Windows Power shell wijzigt:

- [System. Management. Automation. cmdlet. Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System. Management. Automation. provider. Cmdletprovider. Shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

Dit doet u door de methode [System. Management. Automation. cmdlet. Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aan te roepen, waarmee de gebruiker wordt gevraagd de bewerking te bevestigen op basis van de manier waarop de gebruiker de opdracht heeft aangeroepen.

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
