---
title: Retour waarden toevoegen aan een Help-onderwerp over cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: a5618b72827d8ef70201437c4a99ea8bf68cdfd3
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565540"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Retourwaarden toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u een sectie OUTPUTs toevoegt aan een Help-onderwerp voor Windows Power shell®-cmdlet. De sectie OUTPUTs geeft een lijst van de .NET-klassen van objecten die de cmdlet retourneert of de pijp lijn wordt door gegeven.

Er is geen limiet voor het aantal klassen dat u kunt toevoegen aan de sectie OUTPUTs. De retour typen van een cmdlet bevinden zich in een \< opdracht: returnvalues> knoop punt, waarbij elke klasse wordt Inge sloten in een \< opdracht: returnValue> element.

Als een cmdlet geen uitvoer genereert, gebruikt u deze sectie om aan te geven dat er geen uitvoer is. Schrijf bijvoorbeeld ' geen ' in plaats van de naam van de klasse en geef een korte uitleg. Als de cmdlet uitvoer voorwaarde genereert, gebruikt u dit knoop punt om de voor waarden uit te leggen en de voorwaardelijke uitvoer te beschrijven.

Het schema bevat twee \< maml: beschrijving> elementen in elke \< opdracht: returnValue> element. `Get-Help`Met de cmdlet wordt echter alleen de inhoud van de \< opdracht weer gegeven: returnValue>/ \< maml: Description> element.

Vanaf Windows Power Shell 3,0 geeft de `Get-Help` cmdlet de inhoud van het \< element maml: URI>. Met dit element kunt u gebruikers omleiden naar onderwerpen waarin de .NET-klasse wordt beschreven.

Het volgende XML-bestand bevat de \< maml: returnvalues> knoop punt.

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

De volgende XML-code toont een voor beeld van het gebruik van de \< maml: returnvalues> knoop punt om een uitvoer type te documenteren.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```
