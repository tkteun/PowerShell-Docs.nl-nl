---
ms.date: 09/12/2016
ms.topic: reference
title: Invoertypen toevoegen aan een Help-onderwerp voor cmdlets
description: Invoertypen toevoegen aan een Help-onderwerp voor cmdlets
ms.openlocfilehash: f2ad87c54230bcdd7e0ea708e9a1869daef7495f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "94391099"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Invoertypen toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u een **invoer** sectie kunt toevoegen aan het Help-onderwerp van een Power shell-cmdlet. De sectie **invoer** geeft een lijst van de .net-klassen van objecten die de cmdlet accepteert als invoer van de pijp lijn, hetzij op waarde hetzij op basis van eigenschaps naam.

Er is geen limiet voor het aantal klassen dat u kunt toevoegen aan een **invoer** sectie. De invoer typen bevinden zich in een `<command:inputTypes>` knoop punt, waarbij elke klasse wordt Inge sloten in een- `<command:inputType>` element.

Het schema bevat twee `<maml:description>` elementen in elk- `<command:inputType>` element.
`Get-Help`Met de cmdlet wordt echter alleen de inhoud van het `<command:inputType>/<maml:description>` element weer gegeven.

Vanaf Power Shell 3,0 wordt de `Get-Help` inhoud van het element weer gegeven met de cmdlet `<maml:uri>` .
Met dit element kunt u gebruikers omleiden naar onderwerpen waarin de .NET-klasse wordt beschreven.

Het knoop punt wordt weer gegeven in de volgende XML-code `<maml:inputTypes>` .

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

De volgende XML-code toont een voor beeld van het gebruik van het `<maml:inputTypes>` knoop punt om een invoer type te documenteren.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name>System.DateTime</maml:name>
      <maml:uri>https://docs.microsoft.com/dotnet/api/system.datetime</maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```
