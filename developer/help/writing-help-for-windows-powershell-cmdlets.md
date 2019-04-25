---
title: Schrijfhulp voor PowerShell-Cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083158"
---
# <a name="writing-help-for-powershell-cmdlets"></a>Schrijven van Help voor PowerShell-Cmdlets

PowerShell-cmdlets kan nuttig zijn, maar, tenzij uw Help-onderwerpen duidelijk wat de cmdlet doet en het gebruik ervan, de cmdlet niet kan ophalen gebruikt, of nog erger, het kan frustrerend kan zijn voor gebruikers.
De indeling op basis van een XML-cmdlet Help verbetert de consistentie, maar erg nuttig vereist veel meer.

Als u nooit cmdlet Help hebt geschreven, raadpleegt u de volgende richtlijnen.
Het XML-schema vereist voor het maken van de cmdlet Help-onderwerp wordt beschreven in de volgende sectie.
Beginnen met [het maken van de Cmdlet Help-bestand](./how-to-create-the-cmdlet-help-file.md).
Dit onderwerp bevat een beschrijving van de op het hoogste niveau XML-knooppunten.

## <a name="writing-guidelines-for-cmdlet-help"></a>Richtlijnen voor de Help van de Cmdlet schrijven

### <a name="write-well"></a>Ook schrijven
Niets wordt vervangen door een goed geschreven onderwerp.
Als u niet een professionele schrijver, vindt u een schrijver of -editor om u te helpen.
Een ander alternatief is om te kopiëren van de Help-tekst in Microsoft Word en gebruiken van de grammatica en spelling controleren ter verbetering van uw werk.

### <a name="write-simply"></a>Alleen schrijven
Gebruik eenvoudige woorden en zinnen.
Vermijd jargon.
Houd rekening met dat veel lezers zijn uitgerust met een woordenlijst vreemde taal en het Help-onderwerp.

### <a name="write-consistently"></a>Consistent schrijven
Help voor verwante cmdlets (voor bijvoorbeeld get-x en set-x) vergelijkbaar zijn.
Gebruik van de beschrijvingen van de standaard voor standard parameters, zoals **Force** en **InputObject**.
(Kopieer deze in de Help voor de core-cmdlets.) Standard gebruiksrechtovereenkomst.
Bijvoorbeeld, gebruik 'parameter', niet 'argument' en gebruik 'cmdlet"niet"opdracht' of 'command-let'.

### <a name="start-the-synopsis-with-a-verb"></a>De samenvatting met een bewerking starten
Het veld Samenvatting wordt de gebruiker geïnformeerd, wat de cmdlet, niet wat dit is of hoe het werkt.
Bewerkingen maken een taakgebaseerde instructie waarmee gebruikers worden geïnformeerd als deze cmdlet voldoet aan de vereisten.
Gebruik eenvoudige woorden als 'ophalen', 'maken' en "wijzigen."
Vermijd 'instellen', wat kan vaag zijn en decoratieve woorden als 'wijzigen' zijn.

### <a name="focus-on-objects"></a>Richt u op objecten
De meeste 'ophalen' cmdlets weergave iets, maar de primaire functie is om op te halen van een object.
In de Help, die zich richten op het object, zodat gebruikers weten dat de standaardweergave is een van de vele en dat ze de methoden en eigenschappen van het object dat u hebt opgehaald voor ze op verschillende manieren kunnen gebruiken.

### <a name="write-detailed-descriptions"></a>Gedetailleerde beschrijvingen schrijven
Geef een korte lijst alles wat de cmdlet in de gedetailleerde beschrijving doen kunt.
Als de main-functie is een eigenschap te wijzigen, maar de cmdlet alle eigenschappen kunt wijzigen, kunt u dit in de gedetailleerde beschrijving van de lijst.

### <a name="use-conventional-syntax"></a>Gebruik de syntaxis van de conventionele
Gebruik de standaard Backus Naur-indeling die gebruikt voor het Windows- en UNIX Help voor de opdrachtregel wordt.

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>Microsoft .NET Framework-typen voor parameterwaarden gebruiken
De tijdelijke aanduidingen voor de parameterwaarden (in de beschrijvingen van de syntaxis en parameteropties) weergeven de .NET Framework-typen van de objecten die de parameter accepteert.
Het PowerShell-team ontwikkeld deze afspraak om te leren van gebruikers over de .NET-Framework.

### <a name="write-complete-parameter-descriptions"></a>Beschrijvingen van de volledige parameters schrijven
Beschrijvingen van de parameters moeten in kennis stellen gebruikers van twee dingen: wat de parameter (het effect ervan) doet en wat ze voor de parameterwaarden moeten typen.

### <a name="write-practical-examples"></a>Praktijkvoorbeelden schrijven
Het gebruik van alle parameters moeten worden weergegeven in de voorbeelden, maar het belangrijkste is om weer te geven over het gebruik van de cmdlet in de praktijk taken.
Beginnen met een eenvoudig voorbeeld en steeds complexer voorbeelden schrijven.
In het laatste voorbeeld te laten zien hoe de cmdlet gebruiken in een pijplijn.

### <a name="use-the-notes-field"></a>Het veld Opmerkingen
Gebruik het veld Notities om uit te leggen van de concepten die gebruikers nodig hebben om te begrijpen van de cmdlet.
U kunt ook notities gebruiken om veelvoorkomende fouten te voorkomen dat gebruikers te helpen.
Vermijd URL's als ze worden gewijzigd.
In plaats daarvan bieden voorwaarden om te zoeken naar gebruikers.

### <a name="test-your-help"></a>Test uw hulp
Test de Help net zoals u bij het testen van uw code.
Vrienden en collega's uw Help-inhoud lezen en feedback geven.
Ook kunt u feedback van nieuwsgroepen krijgen.

## <a name="see-also"></a>Zie ook

 [Over het maken van de Cmdlet Help-bestand](./how-to-create-the-cmdlet-help-file.md)

 [De naam van Cmdlet en samenvatting toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [De gedetailleerde beschrijving toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-a-cmdlet-description.md)

 [Syntaxis toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Parameters toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-parameter-information.md)

 [Invoertypen voor een Cmdlet Help-onderwerp toevoegen](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Geretourneerde waarden toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Opmerkingen bij de toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Voorbeelden van een Cmdlet Help-onderwerp toevoegen](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Verwante koppelingen toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)