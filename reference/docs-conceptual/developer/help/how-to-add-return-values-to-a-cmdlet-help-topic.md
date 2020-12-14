---
ms.date: 09/12/2016
ms.topic: reference
title: Retourwaarden toevoegen aan een Help-onderwerp voor cmdlets
description: Retourwaarden toevoegen aan een Help-onderwerp voor cmdlets
ms.openlocfilehash: 8c556821a257451a320916231cb20fc82e75ebb4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "94389739"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Retourwaarden toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u een uitvoer sectie kunt toevoegen aan het Help-onderwerp van een Power shell-cmdlet. De sectie **outputs** geeft een lijst van de .net-klassen van objecten die de cmdlet retourneert of de pijp lijn wordt door gegeven.

Er is geen limiet voor het aantal klassen dat u kunt toevoegen aan de sectie **outputs** . De retour typen van een cmdlet bevinden zich in een `<command:returnValues>` knoop punt, waarbij elke klasse wordt Inge sloten in een- `<command:returnValue>` element.

Als een cmdlet geen uitvoer genereert, gebruikt u deze sectie om aan te geven dat er geen uitvoer is. Schrijf bijvoorbeeld in plaats van de naam van de klasse **geen** en geef een korte uitleg. Als de cmdlet uitvoer voorwaarde genereert, gebruikt u dit knoop punt om de voor waarden uit te leggen en de voorwaardelijke uitvoer te beschrijven.

Het schema bevat twee `<maml:description>` elementen in elk- `<command:returnValue>` element.
`Get-Help`Met de cmdlet wordt echter alleen de inhoud van het `<command:returnValue>/<maml:description>` element weer gegeven.

Vanaf Power Shell 3,0 wordt de `Get-Help` inhoud van het element weer gegeven met de cmdlet `<maml:uri>` .
Met dit element kunt u gebruikers omleiden naar onderwerpen waarin de .NET-klasse wordt beschreven.

Het knoop punt wordt weer gegeven in de volgende XML-code `<maml:returnValues>` .

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

De volgende XML-code toont een voor beeld van het gebruik van het `<maml:returnValues>` knoop punt om een uitvoer type te documenteren.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://docs.microsoft.com/dotnet/api/system.datetime </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```
