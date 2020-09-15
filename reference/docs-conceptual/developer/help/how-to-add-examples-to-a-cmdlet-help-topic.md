---
title: Voorbeelden toevoegen aan een Help-onderwerp voor cmdlets
ms.date: 09/12/2016
ms.openlocfilehash: 33a1726f9d52b5a368d5df7962cc17ba9c45246a
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893438"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Voorbeelden toevoegen aan een Help-onderwerp voor cmdlets

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Wat u moet weten over voor beelden in cmdlet Help

- Een lijst met alle parameter namen in de opdracht, zelfs wanneer de parameter namen optioneel zijn. Op deze manier kan de gebruiker de opdracht eenvoudig interpreteren.

- Vermijd aliassen en gedeeltelijke parameter namen, ook al werken ze in Power shell.

- In het voor beeld wordt de rationele uitleg uitgelegd voor het bouwen van de opdracht. Leg uit waarom u specifieke para meters en waarden hebt gekozen en hoe u variabelen gebruikt.

- Als de opdracht expressies gebruikt, moet u deze gedetailleerd uitleggen.

- Als de opdracht Eigenschappen en methoden van objecten gebruikt, met name eigenschappen die niet worden weer gegeven in de standaard weergave, kunt u het voor beeld gebruiken om de gebruiker over het object te informeren.

## <a name="help-views-that-display-examples"></a>Help-weer gaven waarin voor beelden worden weer gegeven

Voor beelden worden alleen weer gegeven in de gedetailleerde en volledige weer gave van de Help van de cmdlet.

## <a name="adding-an-examples-node"></a>Een voor beeld-knoop punt toevoegen

In het volgende XML-bestand ziet u hoe u een knoop punt **voor beelden** kunt toevoegen die één **voorbeeld** knooppunt bevat. Voeg extra voorbeeld knooppunten toe voor elk voor beeld dat u wilt toevoegen in het onderwerp.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>Een voorbeeld titel toevoegen

In het volgende XML-bestand ziet u hoe u een **titel** kunt toevoegen voor het voor beeld. De **titel** wordt gebruikt om het voor beeld uit te stellen uit andere voor beelden. Power shell gebruikt een standaard header die een opeenvolgend voorbeeld nummer bevat.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Voorafgaande tekens toevoegen

In het volgende XML-bestand ziet u hoe u tekens kunt toevoegen, zoals de Windows Power shell-prompt, die direct vóór de voor beeld-opdracht worden weer gegeven (zonder tussenliggende spaties). Power Shell maakt gebruik van de Windows Power shell-prompt: `C:\PS>` .

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

In het volgende XML-bestand ziet u hoe u een beschrijving voor het voor beeld kunt toevoegen. Power shell gebruikt één set `<maml:para>` Tags voor de beschrijving, zelfs als er meerdere `<maml:para>` Tags kunnen worden gebruikt.

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

In het volgende XML-bestand ziet u hoe de uitvoer van de opdracht kan worden toegevoegd. De gegevens van de opdracht resultaten zijn optioneel, maar in sommige gevallen is het handig om te demonstreren wat het effect is van het gebruik van specifieke para meters.
Power shell gebruikt twee sets lege `<maml:para>` Tags voor het scheiden van de uitvoer van de opdracht van de opdracht.

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
