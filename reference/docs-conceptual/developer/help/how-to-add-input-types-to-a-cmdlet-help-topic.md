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
ms.openlocfilehash: 58b908be3149376547b075320b021421351b881e
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557057"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Invoertypen toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u een invoer sectie toevoegt aan een Help-onderwerp voor Windows Power shell®-cmdlet. De sectie invoer geeft een lijst van de .NET-klassen van objecten die de cmdlet accepteert als invoer van de pijp lijn, hetzij op waarde hetzij op basis van eigenschaps naam.

Er is geen limiet voor het aantal klassen dat u kunt toevoegen aan een invoer sectie. De invoer typen bevinden zich in een \< opdracht: inputTypes> knoop punt, waarbij elke klasse wordt Inge sloten in een \< opdracht: input type> element.

Het schema bevat twee \< maml: beschrijving> elementen in elke \< opdracht: input type> element. Met de `Get-Help` cmdlet wordt echter alleen de inhoud van de \< opdracht: input type>/ \< maml: Description>) weer gegeven.

Vanaf Windows Power Shell 3,0 geeft de `Get-Help` cmdlet de inhoud van het \< element maml: URI>. Met dit element kunt u gebruikers omleiden naar onderwerpen waarin de .NET-klasse wordt beschreven.

Het volgende XML-bestand bevat het \<> knoop punt maml: inputTypes.

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

In het volgende XML-bestand ziet u een voor beeld van het gebruik van het \< maml: inputTypes>-knoop punt om een invoer type te documenteren.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```
