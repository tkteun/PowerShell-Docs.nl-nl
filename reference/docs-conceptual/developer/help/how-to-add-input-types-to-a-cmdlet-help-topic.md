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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353289"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Invoertypen toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u een invoer sectie toevoegt aan een Help-onderwerp voor Windows Power shell®-cmdlet. De sectie invoer geeft een lijst van de .NET-klassen van objecten die de cmdlet accepteert als invoer van de pijp lijn, hetzij op waarde hetzij op basis van eigenschaps naam.

Er is geen limiet voor het aantal klassen dat u kunt toevoegen aan een invoer sectie. De invoer typen bevinden zich in een \<command: inputTypes > knoop punt, waarbij elke klasse wordt Inge sloten in een \<command: input type >-element.

Het schema bevat twee \<maml: Description >-elementen in elk element \<command: input type >. De `Get-Help`-cmdlet geeft echter alleen de inhoud weer van het element \<command: input type >/\<maml: Description >).

Vanaf Windows Power Shell 3,0 geeft de cmdlet `Get-Help` de inhoud van het \<maml: URI >-element weer. Met dit element kunt u gebruikers omleiden naar onderwerpen waarin de .NET-klasse wordt beschreven.

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