---
title: Parameter informatie toevoegen | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353282"
---
# <a name="how-to-add-parameter-information"></a>Parametergegevens toevoegen

In deze sectie wordt beschreven hoe u inhoud kunt toevoegen die wordt weer gegeven in de sectie para METERs van het Help-onderwerp van de cmdlet. De sectie para METERs van het Help-onderwerp bevat een lijst met alle para meters van de cmdlet en een gedetailleerde beschrijving van elke para meter.

De inhoud van de para METERs sectie moet consistent zijn met de inhoud van de sectie syntaxis van het Help-onderwerp. Het is de verantwoordelijkheid van de Help-auteur om ervoor te zorgen dat zowel de syntaxis als het para meters-knoop punt vergelijk bare XML-elementen bevatten.

> [!NOTE]
> Voor een volledig overzicht van een Help-bestand opent u een van de dll-Help. XML-bestanden die zich in de installatiemap van Windows Power shell bevinden. Het bestand micro soft. Power shell. commands. Management. dll-Help. XML bevat bijvoorbeeld inhoud voor verschillende Windows Power shell-cmdlets.

### <a name="to-add-parameters"></a>Para meters toevoegen

1. Open het Help-bestand van de cmdlet en zoek het knoop punt opdracht voor de cmdlet die u wilt documenteren. Als u een nieuwe cmdlet toevoegt, moet u een nieuw opdracht knooppunt maken. Uw Help-bestand bevat een opdracht knooppunt voor elke cmdlet waarvoor u Help-inhoud voor maakt. Hier volgt een voor beeld van een leeg opdracht knooppunt.

    ```xml
    <command:command>
    </command:command>
    ```

2. Zoek in het opdracht knooppunt het knoop punt beschrijving en voeg een para meters-knoop punt toe, zoals hieronder wordt weer gegeven. Er is slechts één para meters-knoop punt toegestaan en het moet onmiddellijk volgen op het syntaxis knooppunt.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. Voeg binnen het knoop punt para meters een parameter knooppunt toe voor elke para meter van de cmdlet, zoals hieronder wordt weer gegeven.

   In dit voor beeld wordt een parameter knooppunt toegevoegd voor drie para meters.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Omdat dit dezelfde XML-tags zijn die worden gebruikt in het syntaxis knooppunt, en omdat de para meters die hier zijn opgegeven, moeten overeenkomen met de para meters die zijn opgegeven door het syntaxis knooppunt, kunt u de parameter knooppunten van het syntaxis knooppunt kopiëren en plakken in het knoop punt para meters. Zorg er echter voor dat u slechts één exemplaar van een parameter knooppunt kopieert, zelfs als de para meter in meerdere parameter sets in de syntaxis is opgegeven.

4. Stel voor elk parameter knooppunt de kenmerk waarden in waarmee de kenmerken van elke para meter worden gedefinieerd. Deze kenmerken bevatten het volgende: vereist, globbing, pipelineinput en positie.

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

5. Voeg voor elk parameter knooppunt de naam van de para meter toe. Hier volgt een voor beeld van de parameter naam die is toegevoegd aan het parameter knooppunt.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. Voeg voor elk parameter knooppunt de beschrijving van de para meter toe. Hier volgt een voor beeld van de parameter beschrijving die wordt toegevoegd aan het parameter knooppunt.

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

7. Voeg voor elk parameter knooppunt het .NET Framework type van de para meter toe. Het parameter type wordt samen met de parameter naam weer gegeven.

   Hier volgt een voor beeld van de para meter .NET Framework type dat is toegevoegd aan het parameter knooppunt.

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

8. Voeg voor elk parameter knooppunt de standaard waarde van de para meter toe. De volgende zin wordt toegevoegd aan de parameter beschrijving wanneer de inhoud wordt weer gegeven: ' DefaultValue ' is de standaard waarde.

   Hier volgt een voor beeld van de standaard waarde voor de para meter wordt toegevoegd aan het knoop punt para meter.

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

9. Voeg een mogelijk waarden knooppunt toe voor elke para meter met meerdere waarden.

   Hier volgt een voor beeld van het knoop punt van een mogelijke waarden waarmee twee mogelijke waarden voor de para meter worden gedefinieerd

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

Hier volgen enkele dingen die u moet onthouden wanneer u para meters toevoegt.

- De kenmerken van de para meter worden niet weer gegeven in alle weer gaven van het Help-onderwerp van de cmdlet. Ze worden echter weer gegeven in een tabel die volgt op de parameter beschrijving wanneer de gebruiker de volledige (Get-Help \<cmdletname >-Full) of para meter (Get-Help \<cmdletname >-para meter) van het onderwerp weergeeft.

- De parameter beschrijving is een van de belangrijkste onderdelen van een Help-onderwerp voor cmdlets. De beschrijving moet kort en uitgebreid zijn. Houd er ook rekening mee dat als de parameter beschrijving te lang wordt, bijvoorbeeld wanneer twee para meters met elkaar communiceren, kunt u meer inhoud toevoegen in de sectie Notities van het Help-onderwerp van de cmdlet.

  De parameter beschrijving biedt twee soorten informatie.

- Wat de cmdlet doet wanneer de para meter wordt gebruikt.

- Wat een geldige waarde voor de para meter is.

- Omdat de parameter waarden worden uitgedrukt als .NET Framework objecten, hebben gebruikers meer informatie nodig over deze waarden dan in een traditionele opdracht regel-Help. Vertel de gebruiker welk type gegevens de para meter is ontworpen om te accepteren, en neem voor beelden op.

De standaard waarde van de para meter is de waarde die wordt gebruikt als de para meter niet is opgegeven op de opdracht regel. Houd er rekening mee dat de standaard waarde Optioneel is en niet nodig is voor sommige para meters, zoals de vereiste para meters. U moet echter een standaard waarde opgeven voor de meeste optionele para meters.

De standaard waarde helpt de gebruiker bij het begrijpen van het effect van het gebruik van de para meter. Beschrijf de standaard waarde zeer specifiek, zoals de ' huidige map ' of de ' Windows Power shell-installatiemap ($pshome) ' voor een optioneel pad. U kunt ook een zin schrijven waarin de standaard waarde wordt beschreven, zoals de volgende zin die wordt gebruikt voor de para meter `PassThru`: ' als PassThru niet is opgegeven, geeft de cmdlet geen objecten uit de pijp lijn. '  Omdat de waarde tegenover de veld naam '**standaard waarde**' wordt weer gegeven, hoeft u niet de term ' standaard waarde ' in de vermelding op te geven.

De standaard waarde van de para meter wordt niet weer gegeven in alle weer gaven van het Help-onderwerp van de cmdlet. Het wordt echter weer gegeven in een tabel (samen met de parameter kenmerken) op basis van de parameter beschrijving wanneer de gebruiker de volledige (Get-Help \<cmdletname >-Full) of para meter (Get-Help \<cmdletname >-para meter) van het onderwerp weergeeft.

In het volgende XML-bestand ziet u een paar `<dev:defaultValue>`-tags die zijn toegevoegd aan het knoop punt `<command:parameter>`. U ziet dat de standaard waarde direct na de tag `</command:parameterValue>` wordt gevolgd (wanneer de parameter waarde is opgegeven) of het afsluitende `</maml:description>`-label van de parameter beschrijving. naam.

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

Waarden voor opgesomde typen toevoegen

Als de para meter meerdere waarden of waarden van een opgesomd type heeft, kunt u een optioneel \<dev: possibleValues >-knoop punt gebruiken. Met dit knoop punt kunt u een naam en beschrijving voor meerdere waarden opgeven.

Houd er rekening mee dat de beschrijvingen van de opgesomde waarden niet worden weer gegeven in een van de standaard Help-weer gaven die worden weer gegeven door de cmdlet `Get-Help`, maar andere Help-viewers kunnen deze inhoud in hun weer gaven weer geven.

Het volgende XML-bestand bevat een `<dev:possibleValues>`-knoop punt met twee opgegeven waarden.

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