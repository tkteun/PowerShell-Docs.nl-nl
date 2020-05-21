---
title: Voor beelden toevoegen aan een Help-onderwerp over cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: 82bee7b7bb0ef49203636f2a293075f3db924ce4
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557087"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Voorbeelden toevoegen aan een Help-onderwerp voor cmdlets

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Wat u moet weten over voor beelden in cmdlet Help

- Een lijst met alle parameter namen in de opdracht, zelfs wanneer de parameter namen optioneel zijn. Op deze manier kan de gebruiker de opdracht eenvoudig interpreteren.

- Vermijd aliassen en gedeeltelijke parameter namen, zelfs als ze werken in Windows Power shell®.

- In het voor beeld wordt de rationele uitleg uitgelegd voor het bouwen van de opdracht. Leg uit waarom u specifieke para meters en waarden hebt gekozen en hoe u variabelen gebruikt.

- Als de opdracht expressies gebruikt, moet u deze gedetailleerd uitleggen.

- Als de opdracht Eigenschappen en methoden van objecten gebruikt, met name eigenschappen die niet worden weer gegeven in de standaard weergave, kunt u het voor beeld gebruiken om de gebruiker over het object te informeren.

## <a name="help-views-that-display-examples"></a>Help-weer gaven waarin voor beelden worden weer gegeven

Voor beelden worden alleen weer gegeven in de gedetailleerde en volledige weer gave van de Help van de cmdlet.

## <a name="adding-an-examples-node"></a>Een voor beeld-knoop punt toevoegen

In het volgende XML-bestand ziet u hoe u een knoop punt voor beelden kunt toevoegen die één voorbeeld knooppunt bevat. Voeg extra voorbeeld knooppunten toe voor elk voor beeld dat u wilt toevoegen in het onderwerp.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>Een voorbeeld titel toevoegen

In het volgende XML-bestand ziet u hoe u een titel kunt toevoegen voor het voor beeld. De titel wordt gebruikt om het voor beeld uit te stellen uit andere voor beelden. Windows Power shell® gebruikt een standaard header die een opeenvolgend voorbeeld nummer bevat.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Voorafgaande tekens toevoegen

In het volgende XML-bestand ziet u hoe u tekens kunt toevoegen, zoals de Windows Power shell-prompt, die direct vóór de voor beeld-opdracht worden weer gegeven (zonder tussenliggende spaties). Windows Power Shell® maakt gebruik van de Windows Power shell-prompt: C:\PS>.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a>De opdracht toevoegen

In het volgende XML-bestand ziet u hoe u de werkelijke opdracht van het voor beeld kunt toevoegen. Wanneer u de opdracht toevoegt, typt u de volledige naam (geen alias gebruiken) van cmdlets en para meters. Gebruik waar mogelijk kleine letters.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a>Een beschrijving toevoegen

In het volgende XML-bestand ziet u hoe u een beschrijving voor het voor beeld kunt toevoegen. Windows Power shell® gebruikt één set \< maml: para> Tags voor de beschrijving, zelfs als er meerdere \< maml: para codes> Tags kunnen worden gebruikt.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a>Voorbeeld uitvoer toevoegen

In het volgende XML-bestand ziet u hoe de uitvoer van de opdracht kan worden toegevoegd. De gegevens van de opdracht resultaten zijn optioneel, maar in sommige gevallen is het handig om te demonstreren wat het effect is van het gebruik van specifieke para meters. Windows Power shell® gebruikt twee sets lege \< maml: para codes> om de uitvoer van de opdracht van de opdracht te scheiden.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```
