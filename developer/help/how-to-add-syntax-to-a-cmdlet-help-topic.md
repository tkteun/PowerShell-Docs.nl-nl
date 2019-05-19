---
title: Syntaxis toevoegen aan een Cmdlet Help-onderwerp | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 0210b5ed3104777541692a0e78e7d3b16f9c8256
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855136"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Syntaxis toevoegen aan een Help-onderwerp voor cmdlets

Voordat u begint met de code van het XML-bestand voor het syntaxisschema in de cmdlet Help-bestand, lees deze sectie als u een helder beeld van het type van de gegevens die u moet opgeven, zoals de parameterkenmerken en hoe die gegevens wordt weergegeven in het syntaxisschema...

### <a name="parameter-attributes"></a>Parameterkenmerken

- Vereist

  - Indien waar, kan de parameter moet worden weergegeven in alle opdrachten die gebruikmaken van de parameter is ingesteld.

  - Indien onwaar, wordt de parameter is optioneel in alle opdrachten die gebruikmaken van de parameter is ingesteld.

- Positie

  - Als de naam, is de parameternaam is vereist.

  - Als positionele, is de parameternaam van de is optioneel. Wanneer deze wordt weggelaten, wordt de waarde van parameter moet in de opgegeven positie in de opdracht. Bijvoorbeeld, als de waarde positie = "1", de parameterwaarde moet het eerste of de enige naamloze parameterwaarde in de opdracht.

- Pijpleidinginvoer

  - Als de waarde true (ByValue), kunt u invoer voor de parameter doorgeven. De invoer is gekoppeld met ("gebonden aan") met de parameter, zelfs als de naam van de eigenschap het objecttype komt niet overeen met het verwachte type. De Windows PowerShell? onderdelen van de parameter-binding probeert te converteren van de invoer naar het juiste type en mislukt de opdracht alleen als het type kan niet worden geconverteerd. Slechts één parameter in een parameterset kan worden gekoppeld met de waarde.

  - Als de waarde true (ByPropertyName), kunt u invoer voor de parameter doorgeven. De invoer is gekoppeld aan de parameter alleen als de parameternaam overeenkomt met de naam van een eigenschap van het invoerobject. Bijvoorbeeld, als de parameternaam is `Path`, doorgesluisd naar de cmdlet objecten zijn gekoppeld aan deze parameter alleen als het object een eigenschap met de naam pad heeft.

  - Als true (ByValue, ByPropertyName), u kunt de invoer voor de parameter doorgeven door de naam van de eigenschap of door de waarde. Slechts één parameter in een parameterset kan worden gekoppeld met de waarde.

  - Als het ONWAAR is, kunt u kunt geen invoer voor deze parameter doorsluizen.

- Bij globbing

  - Indien waar, kan de tekst dat de gebruiker van het type voor de waarde van parameter mag jokertekens bevatten.

  - Als het ONWAAR is, kan niet de tekst dat de gebruiker van het type voor de waarde van parameter jokertekens bevatten.

### <a name="parameter-value-attributes"></a>Parameter Waardekenmerken

- Vereist

  - Indien waar, kan de opgegeven waarde moet worden gebruikt wanneer u gebruikmaakt van de parameter in een opdracht.

  - Indien onwaar, wordt de waarde van parameter is optioneel. Een waarde is doorgaans optioneel alleen wanneer deze een van verschillende geldige waarden voor een parameter, zoals een opsommingstype.

Het vereiste kenmerk van een parameterwaarde wijkt af van het vereiste kenmerk van een parameter.

Het vereiste kenmerk van een parameter geeft aan of de parameter (en de waarde ervan) inbegrepen zijn moeten bij het aanroepen van de cmdlet. Het vereiste kenmerk van een parameterwaarde wordt daarentegen gebruikt alleen wanneer de parameter is opgenomen in de opdracht. Hiermee wordt aangegeven of de betreffende waarde moet worden gebruikt met de parameter.

Normaal gesproken parameterwaarden die tijdelijke aanduidingen zijn zijn vereist en parameterwaarden die letterlijke zijn zijn niet vereist, omdat ze een van verschillende waarden die kunnen worden gebruikt met de parameter.

### <a name="gathering-syntax-information"></a>Verzamelen van informatie over syntaxis

1. Beginnen met de cmdletnaam van de.

   ```
   SYNTAX
       Get-Tech
   ```

2. Lijst met alle parameters van de cmdlet. Typ een streepje (ook wel bekend als een 'dash' of 'min-teken' (45 ASCII) voordat u de parameternaam van elke. Tussen de parameters in parametersets (sommige cmdlets hebben slechts één parameter ingesteld). In dit voorbeeld de Get-Tech heeft cmdlet twee parametersets.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Elke parameter is ingesteld met de cmdletnaam van de start.

   Lijst met de eerste standaardparameter. De standaardparameter is opgegeven door de cmdlet-klasse.

   Voor elke parameter is ingesteld, eerst een lijst met de unieke parameter, tenzij er positionele parameters die moeten worden eerst weergegeven. In het vorige voorbeeld, de naam en ID-parameters zijn unieke parameters voor de twee parametersets (elke parameterset moet hebben één parameter die uniek is voor deze parameter is ingesteld). Dit maakt het gemakkelijker voor gebruikers om te bepalen wat ze nodig hebben om op te geven voor de parameter parameter ingesteld.

   Worden de parameters in de volgorde waarin ze moeten worden weergegeven in de opdracht. Als de volgorde niet van belang, worden gerelateerde parameters beschreven die samen of eerst een lijst met de meest gebruikte parameters.

   Zorg ervoor dat u de parameters WhatIf en Bevestig als de cmdlet shouldprocess wordt overgeslagen ondersteunt.

   De algemene parameters (zoals uitgebreid, foutopsporing en ErrorAction) in het diagram syntaxis niet aanbieden. De `Get-Help` cmdlet toegevoegd die informatie voor u, wanneer deze wordt weergegeven het Help-onderwerp.

3. De parameterwaarden toevoegen. In Windows PowerShell?, parameterwaarden worden vertegenwoordigd door hun .NET-type. Echter, de naam van het worden afgekort, zoals 'tekenreeks' voor System.String.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Typen afkorten, zolang de betekenis daarvan uitgeschakeld, zoals 'tekenreeks' voor System.String en 'integer' voor System.Int32 is.

   Lijst van alle waarden van inventarisaties, zoals de - parameter van het type in het vorige voorbeeld, dat kan worden ingesteld op 'basic' of 'Geavanceerd'.

   Verwissel de parameters, zoals - lijst in het vorige voorbeeld, bevatten geen waarden.

4. Punthaken toevoegen aan parameterwaarden die tijdelijke aanduiding, in vergelijking met de parameterwaarden die letterlijke tekenreeksen zijn.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. Zet de volgende optionele parameters en hun waarden tussen vierkante haken.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. Tussen de namen van de volgende optionele parameters (voor positionele parameters) tussen vierkante haken. De naam op voor parameters die positionele, zoals de parameter Name in het volgende voorbeeld zijn, hoeft niet te worden opgenomen in de opdracht.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. Als een parameterwaarde meerdere waarden, zoals een lijst met namen in de parameter Name van een set van vierkante haken meteen volgt op de waarde van parameter toevoegen bevatten kan.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. Als de gebruiker uit parameters of parameterwaarden kiezen kan, plaats, zoals het typeparameter, de keuze tussen accolades en scheidt u deze met de exclusieve OR symbol(;).

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. Als de parameterwaarde bepaalde opmaak gebruiken moet, zoals aanhalingstekens of haakjes weergegeven in de indeling in de syntaxis.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>Het Syntaxisschema XML-code

Het knooppunt van de syntaxis van het XML-bestand begint onmiddellijk na het knooppunt beschrijving, dat eindigt op de \</maml:description > tag. Zie voor meer informatie over het verzamelen van de gegevens die worden gebruikt in het syntaxisschema [verzamelen van informatie over de syntaxis](#gathering-syntax-information).

### <a name="adding-a-syntax-node"></a>Toevoegen van een knooppunt syntaxis

Het syntaxisschema weergegeven in de cmdlet Help-onderwerp is gegenereerd op basis van de gegevens in het knooppunt van de syntaxis van het XML-bestand. Het knooppunt syntaxis is ingesloten in een paar als \<opdrachtsyntaxis: > tags. Met elke parameter ingesteld van de ingesloten in een paar van de cmdlet \<opdracht: syntaxitem > tags. Er is geen limiet voor het aantal \<opdracht: syntaxitem > tags die u kunt toevoegen.

Het volgende voorbeeld ziet een knooppunt syntaxis met de syntaxis van de item-knooppunten gedurende twee parametersets.

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>De Cmdlet-naam toe te voegen aan de Parameter instellen gegevens

Elke parameterset van de cmdlet is opgegeven in een knooppunt van het item syntaxis. Elk knooppunt van het item syntaxis begint met een paar \<maml:name >-labels die de naam van de cmdlet bevatten.

Het volgende voorbeeld bevat een knooppunt syntaxis met de syntaxis van de item-knooppunten gedurende twee parametersets.

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

### <a name="adding-parameters"></a>Parameters toe te voegen

Elke parameter toegevoegd aan de syntaxis van de item-knooppunt is opgegeven in een paar \<opdrachtparameter: > tags. U moet een tweetal \<opdrachtparameter: > tags voor elke parameter die is opgenomen in de parameter is ingesteld, met uitzondering van de algemene parameters die worden geleverd door Windows PowerShell?

De kenmerken van het openen \<opdrachtparameter: > tag te bepalen hoe de parameter in het syntaxisschema wordt weergegeven. Zie voor informatie over de parameterkenmerken, [Parameterkenmerken](#parameter-attributes).

> [!NOTE]
> De \<opdrachtparameter: > tag ondersteunt een onderliggend element \<maml:description > waarvan de inhoud wordt nooit weergegeven. De beschrijvingen van de parameters zijn opgegeven in de parameterknooppunt van het XML-bestand. Om te voorkomen dat inconsistenties tussen de informatie in de syntaxis van de instanties en de parameterknooppunt, laat de (\<maml:description > of laat het veld leeg.

Het volgende voorbeeld bevat een knooppunt van het item syntaxis voor een parameter met twee parameters instellen.

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
