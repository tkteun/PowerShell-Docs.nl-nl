---
ms.date: 09/12/2016
ms.topic: reference
title: Syntaxis toevoegen aan een Help-onderwerp voor cmdlets
description: Syntaxis toevoegen aan een Help-onderwerp voor cmdlets
ms.openlocfilehash: bcc037d22051c162cd0f70702da17afe7ed9c01a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659065"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Syntaxis toevoegen aan een Help-onderwerp voor cmdlets

Voordat u begint met het coderen van de XML voor het syntaxis diagram in het Help-bestand van de cmdlet, leest u deze sectie om een duidelijk beeld te krijgen van het soort gegevens dat u moet opgeven, zoals de parameter kenmerken en hoe die gegevens worden weer gegeven in het syntaxis diagram.

## <a name="parameter-attributes"></a>Parameter kenmerken

- Vereist
  - Als deze eigenschap waar is, moet de para meter worden weer gegeven in alle opdrachten die gebruikmaken van de para meter set.
  - Als false is ingesteld, is de para meter optioneel in alle opdrachten die gebruikmaken van de parameterset.
- Positie
  - Als u een naam opgeeft, is de parameter naam vereist.
  - Als positioneel is, is de naam van de para meter optioneel. Wanneer deze is wegge laten, moet de waarde van de para meter in de opgegeven positie in de opdracht staan. Als de waarde bijvoorbeeld position = "1" is, moet de waarde van de para meter de eerste of enige niet-genaamde parameter waarde in de opdracht zijn.
- Pijplijn invoer
  - Indien waar (ByValue), kunt u invoer door sluizen naar de para meter. De invoer is gekoppeld aan (' gebonden aan ') de para meter, zelfs als de naam van de eigenschap en het object type niet overeenkomen met het verwachte type.
    De Power shell-parameter bindings onderdelen proberen de invoer om te zetten naar het juiste type en de opdracht wordt alleen uitgevoerd als het type niet kan worden geconverteerd. Er kan slechts één para meter in een parameterset worden gekoppeld door een waarde.
  - Indien waar (ByPropertyName), kunt u invoer door sluizen naar de para meter. De invoer wordt echter alleen gekoppeld aan de para meter als de parameter naam overeenkomt met de naam van een eigenschap van het invoer object. Als de parameter naam bijvoorbeeld is `Path` , worden objecten die naar de cmdlet zijn geleid, alleen aan die para meter gekoppeld wanneer het object een eigenschap met de naam pad heeft.
  - Indien waar (ByValue, ByPropertyName), kunt u de invoer van een pipe naar de para meter door geven door de naam van de eigenschap of de waarde. Er kan slechts één para meter in een parameterset worden gekoppeld door een waarde.
  - Als deze eigenschap onwaar is, kunt u geen invoer van de sluis naar deze para meter.
- Globbing
  - Als deze eigenschap waar is, kan de tekst die de gebruiker voor de parameter waarde typt joker tekens bevatten.
  - Indien onwaar, kan de tekst die de gebruiker voor de parameter waarde typt geen joker tekens bevatten.

### <a name="parameter-value-attributes"></a>Kenmerken van parameter waarden

- Vereist
  - Indien waar, moet de opgegeven waarde worden gebruikt wanneer u de para meter in een opdracht gebruikt.
  - Als false is ingesteld, is de waarde van de para meter optioneel. Normaal gesp roken is een waarde alleen optioneel wanneer het een van de geldige waarden voor een para meter is, zoals in een opgesomd type.

Het **vereiste** kenmerk van een parameter waarde wijkt af van het **vereiste** kenmerk van een para meter.

Het vereiste kenmerk van een para meter geeft aan of de para meter (en de bijbehorende waarde) moet worden opgenomen bij het aanroepen van de cmdlet. Daarentegen wordt het vereiste kenmerk van een parameter waarde alleen gebruikt wanneer de para meter in de opdracht wordt opgenomen. Hiermee wordt aangegeven of de desbetreffende waarde moet worden gebruikt met de para meter.

Normaal gesp roken zijn parameter waarden die tijdelijke aanduidingen zijn vereist en parameter waarden die letterlijk zijn, niet vereist, omdat ze een van verschillende waarden zijn die kunnen worden gebruikt met de para meter.

### <a name="gathering-syntax-information"></a>Syntaxis informatie verzamelen

1. Begin met de naam van de cmdlet.

   ```
   SYNTAX
       Get-Tech
   ```

1. Een lijst met alle para meters van de cmdlet. Typ een afbreek streepje ( `-` ) (ASCII 45) voor elke parameter naam.
   De para meters in parameter sets scheiden (sommige cmdlets hebben mogelijk slechts één para meter ingesteld). In dit voor beeld heeft de cmdlet Get-Tech twee parameter sets.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Start elke set para meters met de naam van de cmdlet.

   Geef eerst de standaard parameterset weer. De standaard parameter wordt opgegeven door de cmdlet-klasse.

   Geef voor elke parameterset eerst de unieke para meter weer, tenzij er positionele para meters zijn die eerst moeten worden weer gegeven. In het vorige voor beeld zijn de para meters name en ID unieke para meters voor de twee parameter sets (elke parameterset moet één para meter hebben die uniek is voor die para meter set). Dit maakt het gemakkelijker voor gebruikers om te identificeren welke para meter ze moeten opgeven voor de parameterset.

   Vermeld de para meters in de volg orde waarin ze moeten worden weer gegeven in de opdracht. Als de volg orde niet van belang is, geeft u verwante para meters samen of geeft u de meest gebruikte para meters weer.

   Zorg ervoor dat u de WhatIf en de para meters bevestigt als de cmdlet ShouldProcess ondersteunt.

   Vermeld de algemene para meters (zoals uitgebreid, fout opsporing en error Action) niet in uw syntaxis diagram. De `Get-Help` cmdlet voegt deze informatie voor u toe wanneer het Help-onderwerp wordt weer gegeven.

1. Voeg de parameter waarden toe. In Power shell worden parameter waarden vertegenwoordigd door hun .NET-type.
   De type naam kan echter worden afgekort, zoals "teken reeks" voor System. String.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Kortings typen, zolang ze duidelijk zijn, zoals **teken reeks** voor **System. String** en **int** voor **System. Int32**.

   Alle waarden van opsommingen weer geven, zoals de `-type` para meter in het vorige voor beeld, die kunnen worden ingesteld op **Basic** of **Advanced**.

   Switch-para meters, zoals `-list` in het vorige voor beeld, hebben geen waarden.

1. U kunt punt haken toevoegen aan parameter waarden die een tijdelijke aanduiding zijn, vergeleken met parameter waarden die letterlijke tekens zijn.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

1. Plaats optionele para meters en hun graad tussen vier Kante haken.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. Plaats namen van optionele para meters (voor positionele para meters) tussen vier Kante haken. De naam van para meters die positioneel zijn, zoals de para meter name in het volgende voor beeld, hoeft niet te worden opgenomen in de opdracht.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. Als een parameter waarde meerdere waarden kan bevatten, zoals een lijst met namen in de para meter name, voegt u een paar rechte haken toe direct na de waarde van de para meter.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

1. Als de gebruiker kan kiezen uit para meters of parameter waarden, zoals de type para meter, plaatst u de keuzes tussen accolades en scheidt u deze met de exclusieve of symbool (;).

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

1. Als de parameter waarde specifieke opmaak moet gebruiken, zoals aanhalings tekens of haakjes, geeft u de notatie in de syntaxis weer.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>De XML van het syntaxis diagram coderen

Het syntaxis knooppunt van de XML begint direct na het knoop punt beschrijving, dat eindigt op de `</maml:description>` tag. Zie voor meer informatie over het verzamelen van de gegevens die worden gebruikt in het syntaxis diagram [syntaxis gegevens verzamelen](#gathering-syntax-information).

### <a name="adding-a-syntax-node"></a>Een syntaxis knooppunt toevoegen

Het syntaxis diagram dat in het Help-onderwerp van de cmdlet wordt weer gegeven, wordt gegenereerd op basis van de gegevens in het syntaxis knooppunt van de XML. Het syntaxis knooppunt bevindt zich in een paar `<command:syntax>` Tags als labels. Met elke parameterset van de cmdlet, Inge sloten in een paar `<command:syntaxitem>` Tags. Er is geen limiet voor het aantal `<command:syntaxitem>` Tags dat u kunt toevoegen.

In het volgende voor beeld ziet u een syntaxis knooppunt met syntaxis item knooppunten voor twee parameter sets.

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>De naam van de cmdlet toevoegen aan de para meter set data

Elke parameterset van de cmdlet is opgegeven in een knoop punt syntaxis item. Elk knoop punt met een syntaxis item begint met een paar `<maml:name>` Tags die de naam van de cmdlet bevatten.

Het volgende voor beeld bevat een syntaxis knooppunt met syntaxis item knooppunten voor twee parameter sets.

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a>Para meters toevoegen

Elke para meter die wordt toegevoegd aan het knoop punt syntaxis item, wordt opgegeven in een paar `<command:parameter>` Tags. U hebt een paar `<command:parameter>` Tags nodig voor elke para meter die is opgenomen in de parameterset, met uitzonde ring van de algemene para meters die worden geleverd door Power shell.

De kenmerken van de begin `<command:parameter>` code bepalen hoe de para meter wordt weer gegeven in het syntaxis diagram. Zie [para meter Attributes](#parameter-attributes)(Engelstalig) voor meer informatie over parameter kenmerken.

> [!NOTE]
> Het `<command:parameter>` Label ondersteunt een onderliggend element `<maml:description>` waarvan de inhoud nooit wordt weer gegeven. De parameter beschrijvingen worden opgegeven in het parameter knooppunt van de XML. Als u wilt voor komen dat de gegevens in het syntaxis-item bodes en het parameter knooppunt inconsistenties, laat u de ( `<maml:description>` of laat u het leeg).

Het volgende voor beeld bevat een syntaxis item-knoop punt voor een parameterset met twee para meters.

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
