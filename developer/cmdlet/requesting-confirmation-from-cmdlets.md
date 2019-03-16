---
title: Aanvragen van bevestiging van Cmdlets | Microsoft Docs
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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057398"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Bevestiging vragen vanuit cmdlets

Cmdlets moet bevestiging vragen wanneer ze worden uitgevoerd over op een wijziging aanbrengt in het systeem die buiten de Windows PowerShell-omgeving. Bijvoorbeeld, als een cmdlet is een gebruikersaccount toevoegen of een proces beëindigen, moet de cmdlet vragen om bevestiging van de gebruiker voordat deze wordt voortgezet. Daarentegen als een cmdlet is gewijzigd van een Windows PowerShell-variabele, hoeft de cmdlet niet te vragen om bevestiging.

Als u wilt een bevestiging indienen, de cmdlet moet erop wijzen dat deze bevestiging aanvragen ondersteunt, en moet worden aangeroepen de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (optioneel) methoden om een aanvraag bevestigingsbericht weer te geven.

## <a name="supporting-confirmation-requests"></a>Ondersteunende bevestiging aanvragen

Ter ondersteuning van bevestiging aanvragen, de cmdlet moet instellen de `SupportsShouldProcess` parameter van het kenmerk Cmdlet `true`. Hierdoor kunnen de `Confirm` en `WhatIf` cmdlet-parameters die worden geleverd door Windows PowerShell. De `Confirm` parameter zorgt ervoor dat de gebruiker om te bepalen of de gebeurtenisbevestigingsaanvraag wordt weergegeven. De `WhatIf` parameter zorgt ervoor dat de gebruiker om te bepalen of de cmdlet moet een bericht weergegeven of de bijbehorende actie uitvoeren. Niet handmatig toevoegt de `Confirm` en `WhatIf` parameters aan een cmdlet.

Het volgende voorbeeld ziet de declaratie van een Cmdlet-kenmerk die ondersteuning biedt voor bevestiging aanvragen.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>Aanroepen van de methoden van de aanvraag voor bevestiging

In de code van de cmdlet, aanroepen de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode voordat de bewerking die het systeem wordt uitgevoerd. Ontwerp van de cmdlet zo dat als de aanroep een waarde van retourneert `false`, de bewerking is niet uitgevoerd en de volgende bewerking door de cmdlet wordt verwerkt.

## <a name="calling-the-shouldcontinue-method"></a>Aanroepen van de methode ShouldContinue

De meeste cmdlets aanvragen bevestiging met alleen de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode. Sommige gevallen mogelijk echter extra bevestiging. Voor deze gevallen vormen een aanvulling op de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aanroepen met een aanroep naar de [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methode. Hiermee wordt de cmdlet of de provider voor het beheren van meer fijn het bereik van de **Ja op Alles** reactie op de bevestiging wordt gevraagd.

Als een cmdlet roept de [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methode, de cmdlet moet ook beschikken over een `Force` overschakelen van de parameter. Als de gebruiker opgeeft `Force` wanneer de gebruiker de cmdlet, er nog steeds de cmdlet moet aanroepen [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), maar deze moet de aanroep van overslaan [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) een uitzondering genereert wanneer deze wordt aangeroepen vanuit een niet-interactieve omgeving waar de gebruiker kan niet worden gevraagd. Toevoegen van een `Force` parameter zorgt ervoor dat de opdracht nog steeds kan worden uitgevoerd wanneer deze wordt aangeroepen in een niet-interactieve omgeving.

Het volgende voorbeeld laat zien hoe u aan te roepen [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

Het gedrag van een [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aanroep kan variëren afhankelijk van de omgeving waarin de cmdlet wordt aangeroepen. Met de vorige richtlijnen helpt ervoor te zorgen dat de cmdlet gedrag consistent met andere cmdlets, ongeacht de hostomgeving.

Voor een voorbeeld van aanroepen de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode, Zie [hoe aanvragen bevestigingen](./how-to-request-confirmations.md).

## <a name="specify-the-impact-level"></a>Geef het niveau van Impact

Wanneer u de cmdlet maakt, geeft u het niveau van impact (ernst) van de wijziging. Om dit te doen, stel de waarde van de `ConfirmImpact` parameter van het kenmerk Cmdlet te hoog, Gemiddeld of laag. U kunt een waarde opgeven voor `ConfirmImpact` alleen wanneer u ook opgeven de `SupportsShouldProcess` parameter voor de cmdlet.

Voor de meeste cmdlets, u geen expliciet opgeven `ConfirmImpact`.  In plaats daarvan gebruik de standaardinstelling van de parameter, dit is normaal. Als u `ConfirmImpact` in hoog, zal de bewerking worden bevestigd standaard. Deze instelling voor maximaal verstorende acties, zoals een harde schijf formatteren reserveren.

## <a name="calling-non-confirmation-methods"></a>Aanroepen van methoden van niet-bevestiging

Als de cmdlet of de provider moet een bericht verzenden, maar geen bevestiging wordt gevraagd, kan de volgende drie methoden aanroepen. Vermijd het gebruik van de [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) methode voor het verzenden van berichten van de volgende typen omdat [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) uitvoer wordt weergegeven met de normale uitvoer van de cmdlet of de provider waardoor script schrijven lastig.

- De gebruiker waarschuwen en doorgaan met de bewerking, de cmdlet of de provider kunt aanroepen de [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) methode.

- Voor aanvullende informatie die de gebruiker kunt ophalen met de `Verbose` parameter, de cmdlet of de provider kunt aanroepen de [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) methode.

- Voor foutopsporing op serverniveau details voor andere ontwikkelaars of voor ondersteuning voor het product, de cmdlet of de provider kunt aanroepen de [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) methode. De gebruiker kunt ophalen met deze informatie met behulp van de `Debug` parameter.

Aanroepen de volgende methoden om bevestiging wordt gevraagd voordat ze proberen om uit te voeren een bewerking die een systeem buiten Windows PowerShell-cmdlets en providers:

- [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

Zij dit doen door het aanroepen van de [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode, waarbij u wordt gevraagd de gebruikers om bevestiging van de bewerking op basis van hoe de gebruiker de opdracht aangeroepen.

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
