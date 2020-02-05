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
ms.openlocfilehash: ad0fe5c63b145c681f14328d5ef5a8784a035e26
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995936"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Retourwaarden toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u een sectie OUTPUTs toevoegt aan een Help-onderwerp voor Windows Power shell®-cmdlet. De sectie OUTPUTs geeft een lijst van de .NET-klassen van objecten die de cmdlet retourneert of de pijp lijn wordt door gegeven.

Er is geen limiet voor het aantal klassen dat u kunt toevoegen aan de sectie OUTPUTs. De retour typen van een cmdlet bevinden zich in een \<opdracht: returnValues > knoop punt, waarbij elke klasse wordt Inge sloten in een \<opdracht: returnValue > element.

Als een cmdlet geen uitvoer genereert, gebruikt u deze sectie om aan te geven dat er geen uitvoer is. Schrijf bijvoorbeeld ' geen ' in plaats van de naam van de klasse en geef een korte uitleg. Als de cmdlet uitvoer voorwaarde genereert, gebruikt u dit knoop punt om de voor waarden uit te leggen en de voorwaardelijke uitvoer te beschrijven.

Het schema bevat twee \<maml: Beschrijving > elementen in elke \<opdracht: returnValue > element. Met de cmdlet `Get-Help` wordt echter alleen de inhoud van de \<opdracht weer gegeven: returnValue >/\<maml: Description > element.

Vanaf Windows Power Shell 3,0 wordt met de cmdlet `Get-Help` de inhoud van het element \<maml: URI > weer gegeven. Met dit element kunt u gebruikers omleiden naar onderwerpen waarin de .NET-klasse wordt beschreven.

In het volgende XML-bestand worden de \<maml: returnValues > knoop punt weer gegeven.

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

In het volgende XML-bestand ziet u een voor beeld van het gebruik van de \<maml: returnValues > knoop punt om een uitvoer type te documenteren.

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



