---
ms.date: 09/13/2016
ms.topic: reference
title: Het Help-bestand voor cmdlets maken
description: Het Help-bestand voor cmdlets maken
ms.openlocfilehash: 40259c8f9496b10380805a78f3711aed6f1bf2e5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659090"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Het Help-bestand voor cmdlets maken

In deze sectie wordt beschreven hoe u een geldig XML-bestand maakt dat inhoud bevat voor Help-onderwerpen over de Windows Power shell-cmdlet. In deze sectie wordt beschreven hoe u het Help-bestand kunt benoemen, hoe u de juiste XML-headers kunt toevoegen en hoe u knoop punten kunt toevoegen die de verschillende secties van de cmdlet Help-inhoud bevatten.

> [!NOTE]
> Als u een volledig overzicht van een Help-bestand wilt weer geven, opent u een van de `dll-Help.xml` bestanden die zich in de installatiemap van Windows Power shell bevinden. Het `Microsoft.PowerShell.Commands.Management.dll-Help.xml` bestand bevat bijvoorbeeld inhoud voor verschillende Power shell-cmdlets.

### <a name="how-to-create-a-cmdlet-help-file"></a>Een Help-bestand voor cmdlets maken

1. Maak een tekst bestand en sla dit op met UTF8-code ring. De bestands naam moet de volgende indeling hebben, zodat deze door Windows Power shell kan worden gedetecteerd als een cmdlet-Help-bestand.

   `<PSSnapInAssemblyName>.dll-Help.xml`

1. Voeg de volgende XML-headers toe aan het tekst bestand. Houd er rekening mee dat het bestand wordt gevalideerd op basis van het MAML-schema (micro soft Assistance Markup Language). Power shell biedt momenteel geen hulpprogram ma's om het bestand te valideren.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

1. Voeg een **opdracht** knooppunt toe aan het Help-bestand van de cmdlet voor elke cmdlet in de assembly. Elk knoop punt in het **opdracht** knooppunt heeft betrekking op de verschillende secties van het Help-onderwerp van de cmdlet.

   De volgende tabel bevat het XML-element voor elk knoop punt, gevolgd door een beschrijving van elk knoop punt.

   |           Knooppunt           |                                                                                                     Beschrijving                                                                                                     |
   | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | `<details>`              | Hiermee voegt u inhoud toe voor de secties naam en samen VATTING van het Help-onderwerp van de cmdlet. Zie [de naam en samen vatting van de cmdlet toevoegen](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)voor meer informatie. |
   | `<maml:description>`     | Hiermee voegt u inhoud toe voor de sectie Beschrijving van het Help-onderwerp van de cmdlet. Zie [de gedetailleerde beschrijving toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-a-cmdlet-description.md)voor meer informatie.                    |
   | `<command:syntax>`       | Hiermee voegt u inhoud toe voor de sectie syntaxis van het Help-onderwerp van de cmdlet. Zie [syntaxis toevoegen aan een Help-onderwerp](./how-to-add-syntax-to-a-cmdlet-help-topic.md)voor meer informatie.                                  |
   | `<command:parameters>`   | Voegt inhoud toe aan de sectie para METERs van het Help-onderwerp van de cmdlet. Zie [para meters toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-parameter-information.md)voor meer informatie.                                  |
   | `<command:inputTypes>`   | Hiermee voegt u inhoud toe voor de sectie invoer van het Help-onderwerp van de cmdlet. Zie [invoer typen toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-input-types-to-a-cmdlet-help-topic.md)voor meer informatie.                        |
   | `<command:returnValues>` | Hiermee voegt u inhoud toe voor de sectie OUTPUTs van het Help-onderwerp van de cmdlet. Zie [retour waarden toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-return-values-to-a-cmdlet-help-topic.md)voor meer informatie.                   |
   | `<maml:alertset>`        | Hiermee voegt u inhoud toe voor de sectie Notities van het Help-onderwerp van de cmdlet. Zie [opmerkingen toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-notes-to-a-cmdlet-help-topic.md)voor meer informatie.                                      |
   | `<command:examples>`     | Hiermee voegt u inhoud toe voor de sectie voor beelden van het Help-onderwerp van de cmdlet. Zie voor meer informatie voor [beelden toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-examples-to-a-cmdlet-help-topic.md).                            |
   | `<maml:relatedLinks>`    | Hiermee voegt u inhoud toe aan de sectie verwante koppelingen van het Help-onderwerp van de cmdlet. Zie voor meer informatie [Verwante koppelingen toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-related-links-to-a-cmdlet-help-topic.md).             |

## <a name="example"></a>Voorbeeld

 Hier volgt een voor beeld van een **opdracht** knooppunt waarin de knoop punten voor de verschillende secties van het Help-onderwerp van de cmdlet zijn opgenomen.

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

 [Syntaxis toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Para meters toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-parameter-information.md)

 [Invoertypen toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Retourwaarden toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Opmerkingen toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Voorbeelden toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Gerelateerde koppelingen toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)
