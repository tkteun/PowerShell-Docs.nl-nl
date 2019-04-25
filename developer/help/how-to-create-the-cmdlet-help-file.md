---
title: Over het maken van de Cmdlet Help-bestand | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083243"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Het Help-bestand voor cmdlets maken

Deze sectie beschrijft het maken van een geldig XML-bestand die inhoud van Help-onderwerpen voor Windows PowerShell-cmdlets bevat. In deze sectie wordt beschreven hoe het Help-bestand een naam, de juiste XML-headers toevoegen, en het toevoegen van knooppunten die de verschillende secties van de cmdlet Help-inhoud bevat.

> [!NOTE]
> Voor een volledige weergave van een Help-bestand, open een van de dll-Help.xml-bestanden zich in de installatiemap van Windows PowerShell. Bijvoorbeeld, worden de inhoud van het bestand Microsoft.PowerShell.Commands.Management.dll Help.xml bevat voor verschillende van de Windows PowerShell-cmdlets.

### <a name="how-to-create-a-cmdlet-help-file"></a>Over het maken van een Cmdlet Help-bestand

1. Maak een tekstbestand en sla deze met UTF8-codering. Naam van het bestand moet de volgende indeling hebben, zodat Windows PowerShell kunnen worden gedetecteerd als een cmdlet Help-bestand.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. De volgende XML-headers toevoegen aan het tekstbestand. Let erop dat het bestand worden gevalideerd op basis van het schema voor meerdere Agent Modeling Language (MAML). Windows PowerShell biedt op dit moment geen alle hulpprogramma's voor het valideren van het bestand.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. Een knooppunt van de opdracht toevoegen aan de cmdlet Help-bestand voor elke cmdlet in de assembly. Elk knooppunt in het knooppunt van de opdracht is gekoppeld aan de verschillende secties van de cmdlet Help-onderwerp.

   De volgende tabel bevat de XML-element voor elk knooppunt, gevolgd door een beschrijvingen van elk knooppunt.

   |Knooppunt|Description|
   |----------|-----------------|
   |`<details>`|Inhoud voor de naam en de samenvatting secties van de cmdlet Help-onderwerp toevoegen Zie voor meer informatie, [toevoegen van de Cmdlet-naam en de samenvatting](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).|
   |`<maml:description>`|Adds content for the DESCRIPTION section of the cmdlet Help topic. Zie voor meer informatie, [de gedetailleerde beschrijving toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-a-cmdlet-description.md).|
   |`<command:syntax>`|Inhoud voor de sectie syntaxis van de cmdlet Help-onderwerp toevoegen Zie voor meer informatie, [over het toevoegen van de syntaxis voor een Cmdlet Help-onderwerp](./how-to-add-syntax-to-a-cmdlet-help-topic.md).|
   |`<command:parameters>`|Inhoud voor de PARAMETERS-sectie van de cmdlet Help-onderwerp toevoegen Zie voor meer informatie, [hoe u Parameters toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-parameter-information.md).|
   |`<command:inputTypes>`|Inhoud voor de invoer-sectie van de cmdlet Help-onderwerp toevoegen Zie voor meer informatie, [over het toevoegen van de invoertypen voor een Cmdlet Help-onderwerp](./how-to-add-input-types-to-a-cmdlet-help-topic.md).|
   |`<command:returnValues>`|Inhoud voor de sectie uitvoer van de cmdlet Help-onderwerp toevoegen Zie voor meer informatie, [toevoegen retourneren waarden aan een Cmdlet Help-onderwerp hoe u](./how-to-add-return-values-to-a-cmdlet-help-topic.md).|
   |`<maml:alertset>`|Inhoud toevoegen aan de sectie met opmerkingen van de cmdlet Help-onderwerp Zie voor meer informatie, [toevoegen aan een Cmdlet Help-onderwerp notities](./how-to-add-notes-to-a-cmdlet-help-topic.md).|
   |`<command:examples>`|Inhoud voor de sectie met voorbeelden van de cmdlet Help-onderwerp toevoegen Zie voor meer informatie, [over het toevoegen van de voorbeelden aan een Cmdlet Help-onderwerp](./how-to-add-examples-to-a-cmdlet-help-topic.md).|
   |`<maml:relatedLinks>`|Inhoud voor de verwante koppelingen-sectie van de cmdlet Help-onderwerp toevoegen Zie voor meer informatie, [hoe u verwante koppelingen toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-related-links-to-a-cmdlet-help-topic.md).|

## <a name="example"></a>Voorbeeld

 Hier volgt een voorbeeld van een opdracht-knooppunt met de knooppunten voor de verschillende secties van de cmdlet Help-onderwerp.

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a>Zie ook

 [Het toevoegen van de Cmdlet-naam en de samenvatting](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [De gedetailleerde beschrijving toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-a-cmdlet-description.md)

 [Syntaxis toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Parameters toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-parameter-information.md)

 [Invoertypen toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Geretourneerde waarden toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Het toevoegen van notities aan een Cmdlet Help-onderwerp](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Voorbeelden van een Cmdlet Help-onderwerp toevoegen](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Verwante koppelingen toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)