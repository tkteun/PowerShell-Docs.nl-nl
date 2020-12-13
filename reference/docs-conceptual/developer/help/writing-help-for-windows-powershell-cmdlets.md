---
ms.date: 09/13/2016
ms.topic: reference
title: Help voor PowerShell-cmdlets schrijven
description: Help voor PowerShell-cmdlets schrijven
ms.openlocfilehash: b1deaa5998dbc54add93764db785d57afcc0a779
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658098"
---
# <a name="writing-help-for-powershell-cmdlets"></a>Help voor PowerShell-cmdlets schrijven

Power shell-cmdlets kunnen nuttig zijn, maar tenzij in uw Help-onderwerpen duidelijk wordt uitgelegd wat de cmdlet doet en hoe u deze kunt gebruiken, kan de cmdlet mogelijk niet worden gebruikt of, zelfs als dit niet mogelijk is, kan de gebruiker de gegevens weer geven. De Help-indeling van het XML-cmdlet-bestand verbetert de consistentie, maar er is veel meer hulp nodig.

Als u de Help-informatie over de cmdlet nooit hebt geschreven, raadpleegt u de volgende richt lijnen. Het XML-schema dat is vereist voor het schrijven van het Help-onderwerp van de cmdlet wordt beschreven in de volgende sectie. Begin met [het maken van het Help-bestand voor de cmdlet](./how-to-create-the-cmdlet-help-file.md). Dit onderwerp bevat een beschrijving van de XML-knoop punten op het hoogste niveau.

## <a name="writing-guidelines-for-cmdlet-help"></a>Richt lijnen voor het schrijven van cmdlets

### <a name="write-well"></a>Goed schrijven

Er wordt geen goed geschreven onderwerp vervangen. Als u geen professionele schrijver bent, kunt u een schrijver of redacteur vinden om u te helpen. U kunt ook de Help-tekst kopiëren naar micro soft Word en de grammatica-en spelling controle gebruiken om uw werk te verbeteren.

### <a name="write-simply"></a>Schrijf eenvoudigweg

Gebruik eenvoudige woorden en zinsdelen. Vermijd jargon. Houd er rekening mee dat veel lezers alleen zijn uitgerust met een woorden lijst in een vreemde taal en het Help-onderwerp.

### <a name="write-consistently"></a>Consistent schrijven

Help voor gerelateerde cmdlets moet vergelijkbaar zijn (bijvoorbeeld Get-x en set-x). Gebruik de standaard beschrijvingen voor standaard parameters, zoals **Force** en **input object**. (Kopieer ze in de Help voor de kern-cmdlets.) Gebruik standaard termen. Gebruik bijvoorbeeld "para meter", niet "argument" en gebruik "cmdlet" niet "opdracht" of "opdracht-Let".

### <a name="start-the-synopsis-with-a-verb"></a>De samen vatting starten met een werk woord

In het veld samen vatting wordt de gebruiker geïnformeerd wat de cmdlet doet, niet wat het is of hoe deze werkt. Met werk woorden maakt u een op taken gebaseerde instructie waarmee gebruikers worden geïnformeerd als deze cmdlet voldoet aan de vereisten. Gebruik eenvoudige werk woorden zoals ' Get ', ' maken ' en ' wijzigen '. Vermijd ' set '. Dit kan vague en decoratieve woorden als ' Modify ' zijn.

### <a name="focus-on-objects"></a>Focus op objecten

Met de meeste Get-cmdlets wordt iets weer gegeven, maar de primaire functie is om een object op te halen. Focus op het object in uw Help, zodat gebruikers weten dat de standaard weergave een van de vele is en dat ze de methoden en eigenschappen van het object kunnen gebruiken dat u op verschillende manieren hebt opgehaald.

### <a name="write-detailed-descriptions"></a>Gedetailleerde beschrijvingen schrijven

Geef een kort overzicht van alles wat met de cmdlet kan worden uitgevoerd in de gedetailleerde beschrijving. Als de hoofd functie één eigenschap wijzigt, maar de cmdlet alle eigenschappen kan wijzigen, vermeldt u deze in de gedetailleerde beschrijving.

### <a name="use-conventional-syntax"></a>Conventionele syntaxis gebruiken

Gebruik de standaard Backus-Naur indeling die gebruikelijk is voor Windows-en UNIX-opdracht regel Help.

### <a name="use-microsoft-net-types-for-parameter-values"></a>Microsoft .NET typen voor parameter waarden gebruiken

De tijdelijke aanduidingen voor parameter waarden (in de syntaxis en parameter beschrijvingen) tonen de .NET Framework typen van de objecten die door de para meter worden geaccepteerd. Het Power shell-team heeft deze Conventie ontwikkeld om gebruikers over de .NET Framework te leren.

### <a name="write-complete-parameter-descriptions"></a>Volledige beschrijvingen van de para meters schrijven

Parameter beschrijvingen moeten gebruikers van twee dingen informeren: wat de para meter doet (het effect) en wat ze moeten typen voor de parameter waarden.

### <a name="write-practical-examples"></a>Praktijk voorbeelden schrijven

In de voor beelden ziet u hoe u alle para meters kunt gebruiken, maar het belangrijkste is om te laten zien hoe u de cmdlet in Real-World-taken kunt gebruiken. Begin met een eenvoudig voor beeld en schrijf steeds complexe voor beelden. In het laatste voor beeld laat zien hoe u de cmdlet in een pijp lijn kunt gebruiken.

### <a name="use-the-notes-field"></a>Het notitie veld gebruiken

Gebruik het veld opmerkingen om concepten uit te leggen die gebruikers nodig hebben om de cmdlet te begrijpen. U kunt ook notities gebruiken om gebruikers te helpen veelvoorkomende fouten te voor komen. Vermijd Url's wanneer ze worden gewijzigd. Geef in plaats daarvan de gebruikers voorwaarden op die u wilt zoeken.

### <a name="test-your-help"></a>Uw Help testen

Test de Help op dezelfde manier als bij het testen van uw code. Laat vrienden en collega's uw Help-inhoud lezen en feedback geven. U kunt ook feedback van nieuws groepen aanvragen.

## <a name="see-also"></a>Zie ook

 [Het Help-bestand voor cmdlets maken](./how-to-create-the-cmdlet-help-file.md)

 [De cmdlet-naam en het cmdlet-overzicht toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [De gedetailleerde beschrijving toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-a-cmdlet-description.md)

 [Syntaxis toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Para meters toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-parameter-information.md)

 [Invoer typen toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Retourwaarden toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Notities toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Voorbeelden toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Gerelateerde koppelingen toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)
