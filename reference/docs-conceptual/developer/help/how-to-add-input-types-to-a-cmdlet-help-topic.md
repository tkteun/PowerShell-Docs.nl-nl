---
title: Invoertypen toevoegen aan een Help-onderwerp voor cmdlets
ms.date: 09/12/2016
ms.openlocfilehash: d41c49ff48cf361c2ba694d11576e84a9367eef5
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893421"
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
