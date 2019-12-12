---
title: Invoer typen toevoegen aan een Help-onderwerp over cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353289"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Invoertypen toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u een invoer sectie toevoegt aan een Help-onderwerp voor Windows Power shell®-cmdlet. De sectie invoer geeft een lijst van de .NET-klassen van objecten die de cmdlet accepteert als invoer van de pijp lijn, hetzij op waarde hetzij op basis van eigenschaps naam.

Er is geen limiet voor het aantal klassen dat u kunt toevoegen aan een invoer sectie. De invoer typen bevinden zich in een \<opdracht: inputTypes > knoop punt, waarbij elke klasse wordt Inge sloten in een \<opdracht: input type > element.

Het schema bevat twee \<maml: Beschrijving > elementen in elke \<opdracht: input type > element. Met de cmdlet `Get-Help` wordt echter alleen de inhoud van de \<opdracht weer gegeven: input type >/\<maml: Description >-element.

Vanaf Windows Power Shell 3,0 wordt met de cmdlet `Get-Help` de inhoud van het element \<maml: URI > weer gegeven. Met dit element kunt u gebruikers omleiden naar onderwerpen waarin de .NET-klasse wordt beschreven.

Het volgende XML-bestand bevat het \<maml: inputTypes >-knoop punt.

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

In het volgende XML-bestand ziet u een voor beeld van het gebruik van het knoop punt \<maml: inputTypes > om een invoer type te documenteren.

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