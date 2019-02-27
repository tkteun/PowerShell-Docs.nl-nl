---
title: Invoertypen toevoegen aan een Cmdlet Help-onderwerp | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850174"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Invoertypen toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u een sectie invoer toevoegen aan een Windows PowerShell® cmdlet Help-onderwerp. De invoer-sectie vindt u de .NET-klassen van objecten die de cmdlet als invoer van de pijplijn door de waarde of door de naam van eigenschap accepteert.

Er is geen limiet voor het aantal klassen die u aan een sectie invoer toevoegen kunt. De invoertypen zijn ingesloten in een \<opdracht: inputTypes > knooppunt, waarbij elke klasse die is ingesloten in een \<opdracht: inputType > element.

Het schema bevat twee \<maml:description > elementen in elk \<opdracht: inputType > element. Echter, de `Get-Help` cmdlet wordt alleen de inhoud van de \<opdracht: inputType > /\<maml:description >) element.

Vanaf Windows PowerShell 3.0, de `Get-Help` cmdlet wordt de inhoud van de \<maml:uri > element. Dit element kunt u gebruikers naar onderwerpen waarin wordt beschreven van de .NET-klasse.

De volgende XML bevat de \<maml:inputTypes > knooppunt.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

Het volgende XML-bestand toont een voorbeeld van het gebruik van de \<maml:inputTypes > knooppunt vastleggen van een type gebruikersinvoer.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```