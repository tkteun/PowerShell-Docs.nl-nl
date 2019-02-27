---
title: Retour toevoegen aan een Cmdlet Help-onderwerp waarden | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849215"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Retourwaarden toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u een uitvoersectie toevoegen aan een Windows PowerShell® cmdlet Help-onderwerp. De uitvoer-sectie vindt u de .NET-klassen van objecten die de cmdlet retourneert of geeft u de pijplijn.

Er is geen limiet voor het aantal klassen die u aan de sectie uitvoer toevoegen kunt. De typen retourneren die van een cmdlet zijn ingesloten in een \<opdracht: returnValues > knooppunt, waarbij elke klasse die is ingesloten in een \<opdracht: returnValue > element.

Als een cmdlet wordt geen uitvoer gegenereerd, gebruikt u deze sectie om aan te geven dat er geen uitvoer. Bijvoorbeeld, in plaats van de naam van de klasse schrijven 'None' en geef een korte uitleg. Als de cmdlet voorwaardelijk uitvoer genereert, gebruik dit knooppunt te leggen van de voorwaarden en de voorwaardelijke uitvoer te beschrijven.

Het schema bevat twee \<maml:description > elementen in elk \<opdracht: returnValue > element. Echter, de `Get-Help` cmdlet wordt alleen de inhoud van de \<opdracht: returnValue > /\<maml:description > element.

Vanaf Windows PowerShell 3.0, de `Get-Help` cmdlet wordt de inhoud van de \<maml:uri > element. Dit element kunt u gebruikers naar onderwerpen waarin wordt beschreven van de .NET-klasse.

De volgende XML bevat de \<maml:returnValues > knooppunt.

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

Het volgende XML-bestand toont een voorbeeld van het gebruik van de \<maml:returnValues > knooppunt aan het document een uitvoertype.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



