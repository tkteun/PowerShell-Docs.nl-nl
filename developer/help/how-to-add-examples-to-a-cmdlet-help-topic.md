---
title: Voorbeelden van een Cmdlet Help-onderwerp toevoegen | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855114"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Voorbeelden toevoegen aan een Help-onderwerp voor cmdlets

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Om te weten over de voorbeelden in de Help van Cmdlet

- De lijst alle van de namen van parameters in de opdracht, zelfs wanneer de namen van parameters optioneel zijn. Hiermee wordt de gebruiker de opdracht eenvoudig interpreteren.

- Vermijd aliassen en gedeeltelijke parameternamen, zelfs als ze in Windows PowerShell® werken.

- Leg uit de rationele voor het samenstellen van de opdracht in de beschrijving van het voorbeeld. Wordt uitgelegd waarom u bepaalde parameters en waarden, en hoe u variabelen gebruiken.

- Als de opdracht gebruikmaakt van expressies, kunt u ze in detail uitgelegd.

- Als de opdracht gebruikt eigenschappen en methoden van objecten, met name de eigenschappen die niet in de standaard weer te geven verschijnen, gebruikt u het voorbeeld als een verkoopkans vertelt de gebruiker over het object.

## <a name="help-views-that-display-examples"></a>Help-weergaven die voorbeelden weergeven

Voorbeelden weergegeven alleen in de gedetailleerde en volledige weergaven van de cmdlet Help.

## <a name="adding-an-examples-node"></a>Toevoegen van een knooppunt voorbeelden

De volgende XML-code laat zien hoe een voorbeelden-knooppunt dat één voorbeeldknooppunt bevat toevoegen. Voorbeeld van de aanvullende knooppunten toevoegen voor elke voorbeelden die u wilt opnemen in het onderwerp.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>De titel van een voorbeeld toevoegen

De volgende XML-code laat zien hoe een titel voor het voorbeeld. De titel wordt gebruikt om in te stellen in het voorbeeld naast andere voorbeelden. Windows PowerShell® maakt gebruik van een standard-header die een aantal opeenvolgende voorbeeld bevatten.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Toe te voegen vóór tekens

De volgende XML-code laat zien hoe om toe te voegen tekens, zoals de Windows PowerShell-prompt die direct vóór de opdracht (zonder spaties) worden weergegeven. Windows PowerShell® maakt gebruik van de Windows PowerShell-prompt: C:\PS>.

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

## <a name="adding-the-command"></a>De opdracht toe te voegen

De volgende XML-code laat zien hoe de werkelijke opdracht van het voorbeeld toe te voegen. Bij het toevoegen van de opdracht, typt u de volledige naam (gebruik geen alias) van de cmdlets en -parameters. Kleine letters indien mogelijk ook gebruiken.

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

Het volgende XML-bestand ziet hoe u een beschrijving op voor het voorbeeld toevoegen. Windows PowerShell® maakt gebruik van een enkele set \<maml:para > tags voor de beschrijving, zelfs als meerdere \<maml:para > tags kunnen worden gebruikt.

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

## <a name="adding-example-output"></a>Voorbeeld van uitvoer toevoegen

De volgende XML-code laat zien hoe de uitvoer van de opdracht toevoegen. Informatie over de opdracht is optioneel, maar in sommige gevallen is het handig om te demonstreren het effect van het gebruik van bepaalde parameters. Windows PowerShell® maakt gebruik van twee sets met lege \<maml:para > tags voor het scheiden van de opdrachtuitvoer vanaf de opdrachtregel.

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