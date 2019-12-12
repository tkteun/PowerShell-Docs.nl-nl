---
title: Het Help-bestand voor de cmdlet maken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353261"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Het Help-bestand voor cmdlets maken

In deze sectie wordt beschreven hoe u een geldig XML-bestand maakt dat inhoud bevat voor Help-onderwerpen over de Windows Power shell-cmdlet. In deze sectie wordt beschreven hoe u het Help-bestand kunt benoemen, hoe u de juiste XML-headers kunt toevoegen en hoe u knoop punten kunt toevoegen die de verschillende secties van de cmdlet Help-inhoud bevatten.

> [!NOTE]
> Voor een volledig overzicht van een Help-bestand opent u een van de dll-Help. XML-bestanden die zich in de installatiemap van Windows Power shell bevinden. Het bestand micro soft. Power shell. commands. Management. dll-Help. XML bevat bijvoorbeeld inhoud voor verschillende Windows Power shell-cmdlets.

### <a name="how-to-create-a-cmdlet-help-file"></a>Een Help-bestand voor cmdlets maken

1. Maak een tekst bestand en sla dit op met UTF8-code ring. De bestands naam moet de volgende indeling hebben, zodat deze door Windows Power shell kan worden gedetecteerd als een cmdlet-Help-bestand.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. Voeg de volgende XML-headers toe aan het tekst bestand. Houd er rekening mee dat het bestand wordt gevalideerd op basis van het MAML-schema (multi-agent Modeling Language). Windows Power shell biedt momenteel geen hulpprogram ma's om het bestand te valideren.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. Voeg een opdracht knooppunt toe aan het Help-bestand van de cmdlet voor elke cmdlet in de assembly. Elk knoop punt in het opdracht knooppunt heeft betrekking op de verschillende secties van het Help-onderwerp van de cmdlet.

   De volgende tabel bevat het XML-element voor elk knoop punt, gevolgd door een beschrijving van elk knoop punt.

   |Knooppunt|Beschrijving|
   |----------|-----------------|
   |`<details>`|Hiermee voegt u inhoud toe voor de secties naam en samen VATTING van het Help-onderwerp van de cmdlet. Zie [de naam en samen vatting van de cmdlet toevoegen](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)voor meer informatie.|
   |`<maml:description>`|Hiermee voegt u inhoud toe voor de sectie Beschrijving van het Help-onderwerp van de cmdlet. Zie [de gedetailleerde beschrijving toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-a-cmdlet-description.md)voor meer informatie.|
   |`<command:syntax>`|Hiermee voegt u inhoud toe voor de sectie syntaxis van het Help-onderwerp van de cmdlet. Zie [syntaxis toevoegen aan een Help-onderwerp](./how-to-add-syntax-to-a-cmdlet-help-topic.md)voor meer informatie.|
   |`<command:parameters>`|Voegt inhoud toe aan de sectie para METERs van het Help-onderwerp van de cmdlet. Zie [para meters toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-parameter-information.md)voor meer informatie.|
   |`<command:inputTypes>`|Hiermee voegt u inhoud toe voor de sectie invoer van het Help-onderwerp van de cmdlet. Zie [invoer typen toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-input-types-to-a-cmdlet-help-topic.md)voor meer informatie.|
   |`<command:returnValues>`|Hiermee voegt u inhoud toe voor de sectie OUTPUTs van het Help-onderwerp van de cmdlet. Zie [retour waarden toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-return-values-to-a-cmdlet-help-topic.md)voor meer informatie.|
   |`<maml:alertset>`|Hiermee voegt u inhoud toe aan de sectie Notities van het Help-onderwerp van de cmdlet. Zie [opmerkingen toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-notes-to-a-cmdlet-help-topic.md)voor meer informatie.|
   |`<command:examples>`|Hiermee voegt u inhoud toe voor de sectie voor beelden van het Help-onderwerp van de cmdlet. Zie voor meer informatie voor [beelden toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-examples-to-a-cmdlet-help-topic.md).|
   |`<maml:relatedLinks>`|Hiermee voegt u inhoud toe aan de sectie verwante koppelingen van het Help-onderwerp van de cmdlet. Zie voor meer informatie [Verwante koppelingen toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-related-links-to-a-cmdlet-help-topic.md).|

## <a name="example"></a>Voorbeeld

 Hier volgt een voor beeld van een opdracht knooppunt waarin de knoop punten voor de verschillende secties van het Help-onderwerp van de cmdlet zijn opgenomen.

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

 [De naam en samen vatting van de cmdlet toevoegen](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [De gedetailleerde beschrijving toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-a-cmdlet-description.md)

 [De syntaxis van een Help-onderwerp toevoegen aan een cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Para meters toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-parameter-information.md)

 [Invoer typen toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Retour waarden toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Opmerkingen toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Voor beelden toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Verwante koppelingen toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows Power shell SDK](../windows-powershell-reference.md)