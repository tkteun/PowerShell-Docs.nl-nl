---
title: Het toevoegen van parameterinformatie | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851938"
---
# <a name="how-to-add-parameter-information"></a>Parametergegevens toevoegen

In deze sectie wordt beschreven hoe u inhoud die wordt weergegeven in de sectie PARAMETERS van de cmdlet Help-onderwerp toevoegen. De sectie PARAMETERS van het Help-onderwerp geeft een lijst van elk van de parameters van de cmdlet en biedt een gedetailleerde beschrijving van elke parameter.

De inhoud van de sectie PARAMETERS moet consistent zijn met de inhoud van de sectie syntaxis van het Help-onderwerp. Het is de verantwoordelijkheid van de Help-auteur om ervoor te zorgen dat zowel de syntaxis en Parameters knooppunt dezelfde XML-elementen bevatten.

> [!NOTE]
> Voor een volledige weergave van een Help-bestand, open een van de dll-Help.xml-bestanden zich in de installatiemap van Windows PowerShell. Bijvoorbeeld, worden de inhoud van het bestand Microsoft.PowerShell.Commands.Management.dll Help.xml bevat voor verschillende van de Windows PowerShell-cmdlets.

### <a name="to-add-parameters"></a>Parameters toevoegen

1. Open het cmdlet Help-bestand en zoek het knooppunt van de opdracht voor de cmdlet die u documenteert. Als u een nieuwe cmdlet die u moet maken van een nieuwe opdracht knooppunt toevoegt. Het Help-bestand bevat een knooppunt van de opdracht voor elke cmdlet die u Help-inhoud voor biedt. Hier volgt een voorbeeld van een lege opdracht-knooppunt.

    ```xml
    <command:command>
    </command:command>
    ```

2. Zoek het knooppunt beschrijving en toevoegen van een knooppunt Parameters zoals hieronder wordt weergegeven in het knooppunt opdracht. Slechts één knooppunt van de Parameters is toegestaan en dan onmiddellijk het knooppunt syntaxis moet volgen.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. In het knooppunt Parameters toevoegen een parameterknooppunt voor alle parameters van de cmdlet, zoals hieronder weergegeven.

   In dit voorbeeld wordt een parameterknooppunt toegevoegd voor de drie parameters.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Omdat dit de dezelfde XML-labels die worden gebruikt in het knooppunt syntaxis en omdat de parameters die hier is opgegeven moeten overeenkomen met de parameters die zijn opgegeven door de syntaxis van knooppunt zijn, kunt u de Parameter-knooppunten van het knooppunt syntaxis kopiëren en plak deze in het knooppunt Parameters. Echter, moet u slechts één exemplaar van een parameterknooppunt kopiëren, zelfs als de parameter is opgegeven meerdere parametersets, in de syntaxis.

4. Stel de kenmerkwaarden weer die de eigenschappen van elke parameter definiëren voor elk knooppunt Parameter. Deze kenmerken zijn onder andere het volgende: Bij globbing, pipelineinput en positie nodig.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

5. Voeg de naam van de parameter voor elk knooppunt Parameter. Hier volgt een voorbeeld van de naam van de parameter toegevoegd aan de Parameter-knooppunt.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. Voor elk knooppunt Parameter, de beschrijving van de parameter toevoegen Hier volgt een voorbeeld van de beschrijving van de parameter toegevoegd aan de Parameter-knooppunt.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

7. Voor elk knooppunt Parameter toevoegen het .NET Framework-type van de parameter. Het parametertype wordt weergegeven, samen met de naam van de parameter.

   Hier volgt een voorbeeld van het parametertype van de .NET Framework toegevoegd aan de Parameter-knooppunt.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

8. Voor elk knooppunt Parameter toevoegen de standaardwaarde van de parameter. De volgende zin is toegevoegd aan de beschrijving van de parameter wanneer de inhoud wordt weergegeven: "DefaultValue" is de standaardinstelling.

   Hier volgt een voorbeeld van de standaardwaarde voor de parameter wordt toegevoegd aan de Parameter-knooppunt.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

9. Voor elke Parameter die meerdere waarden heeft, moet u een mogelijke waarden-knooppunt toevoegen.

   Hier volgt een voorbeeld van de van een knooppunt mogelijke waarden die twee mogelijke waarden voor de parameter definieert

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

Hier volgen enkele dingen om te onthouden wanneer parameters toe te voegen.

- De kenmerken van de parameter worden niet weergegeven in alle weergaven van de cmdlet Help-onderwerp. Echter, worden deze weergegeven in een tabel die de parameter-omschrijving te volgen wanneer de gebruiker wordt gevraagd voor de volledige (Get-Help \<cmdletname >-volledige) of Parameter (Get-Help \<cmdletname >-parameter) weergave van het onderwerp.

- De beschrijving van de parameter is een van de belangrijkste onderdelen van een cmdlet Help-onderwerp. De beschrijving moet kort, evenals grondig. Vergeet ook niet als de beschrijving van de parameter te lang is, zoals wanneer twee parameters met elkaar communiceren, u meer inhoud in de sectie met opmerkingen van de cmdlet Help-onderwerp toevoegen kunt.

  De beschrijving van de parameter biedt twee soorten informatie.

- Wat de cmdlet doet wanneer de parameter wordt gebruikt.

- Welke een geldige waarde is voor de parameter.

- Omdat de parameterwaarden worden uitgedrukt als .NET Framework-objecten, moeten gebruikers meer informatie over deze waarden dan ze net als in een traditionele Help voor de opdrachtregel. De gebruiker zien welk type gegevens dat de parameter is ontworpen om te accepteren en voorbeelden.

De standaardwaarde van de parameter is de waarde die wordt gebruikt als de parameter niet is opgegeven op de opdrachtregel. Houd er rekening mee dat de standaardwaarde optioneel is en is niet nodig voor bepaalde parameters, zoals vereiste parameters. U moet echter een standaardwaarde voor de meeste optionele parameters opgeven.

De standaardwaarde helpt de gebruiker om het effect van het gebruik van de parameter niet te begrijpen. De standaardwaarde zeer specifiek, beschrijven, zoals het 'huidige directory' of de 'Windows PowerShell installatiemap ($pshome)' voor een pad zijn optioneel. U kunt ook een zin dat de standaard, zoals de volgende zin gebruikt beschrijft voor het schrijven de `PassThru` parameter: "Als PassThru gebruikt, niet opgegeven is, de cmdlet geeft niet de objecten in de pijplijn."  Ook, omdat de waarde wordt weergegeven naast de naam van het veld '**standaardwaarde**", hoeft u niet de term 'standaardwaarde' in de vermelding opnemen.

De standaardwaarde van de parameter wordt niet weergegeven in alle weergaven van de cmdlet Help-onderwerp. Maar deze wordt weergegeven in een tabel (samen met de parameterkenmerken) de beschrijving van de parameter wanneer de gebruiker wordt gevraagd voor de volledige (Get-Help \<cmdletname >-volledige) of Parameter (Get-Help \<cmdletname >-parameter) weergeven in het onderwerp.

Het volgende XML-bestand bevat een combinatie van een `<dev:defaultValue>` tags toegevoegd aan de `<command:parameter>` knooppunt. U ziet dat de standaardwaarde onmiddellijk na de afsluitende volgt `</command:parameterValue>` tag (als de waarde van parameter is opgegeven) of de afsluitende `</maml:description>` code van de beschrijving van de parameter. de naam.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

Voeg waarden toe voor typen die zijn geïnventariseerd

Als de parameter meerdere waarden of van een opsommingstype heeft, kunt u een optionele \<dev:possibleValues > knooppunt. Dit knooppunt kunt u een naam en beschrijving voor meerdere waarden opgeven.

Houd er rekening mee dat de beschrijvingen van de opsommingswaarden niet in een van de standaard Help weergaven die worden weergegeven weergegeven worden door de `Get-Help` cmdlet, maar andere viewers Help kunnen deze inhoud weergeven in hun visie.

De volgende XML bevat een `<dev:possibleValues>` knooppunt met twee waarden die zijn opgegeven.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```