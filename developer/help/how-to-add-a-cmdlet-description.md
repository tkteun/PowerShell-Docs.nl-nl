---
title: Hoe u een beschrijving van de Cmdlet toevoegen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851427"
---
# <a name="how-to-add-a-cmdlet-description"></a>Een cmdlet-beschrijving toevoegen

In deze sectie wordt beschreven hoe u inhoud die wordt weergegeven in de sectie Beschrijving van de cmdlet Help toevoegen. In het Help-bestand, wordt deze inhoud toegevoegd aan het knooppunt van de opdracht voor elke cmdlet.

> [!NOTE]
> Voor een volledige weergave van een Help-bestand, open een van de dll-Help.xml-bestanden zich in de installatiemap van Windows PowerShell. Bijvoorbeeld, worden de inhoud van het bestand Microsoft.PowerShell.Commands.Management.dll Help.xml bevat voor verschillende van de Windows PowerShell-cmdlets.

### <a name="to-add-a-description"></a>Een beschrijving toevoegen

- Door een uitleg van de belangrijkste functies van de cmdlet in meer detail te beginnen. In veel gevallen kunt u de termen die worden gebruikt in de cmdletnaam van de wordt uitgelegd en illustratie van de onbekende concepten met een voorbeeld. Bijvoorbeeld, als de cmdlet worden de gegevens naar een bestand toegevoegd, wordt uitgelegd dat voegt gegevens toe aan het einde van een bestaand bestand.

- Als u zoekt alle functies van de cmdlet, bekijk de lijst met parameters. De primaire functie van de cmdlet wordt beschreven, en vervolgens andere functies en onderdelen. Als de main-functie van de cmdlet is een eigenschap te wijzigen, maar de cmdlet alle eigenschappen kunt wijzigen, stel dit in de gedetailleerde beschrijving. Als de cmdlet-parameters, de gebruikers informatie op verschillende manieren werven kunnen, uitgelegd.

- Bevatten informatie over de manieren waarop dat gebruikers kunnen worden gebruikt voor het gebruik van de cmdlet, naast de hand liggende gebruikt. Bijvoorbeeld, kunt u het object dat de `Get-Host` cmdlet haalt de kleur van tekst in de Windows PowerShell-opdrachtvenster wilt wijzigen.

  Voorbeeld:  "De `Get-Acl` -cmdlet krijgt u objecten die staan voor de security descriptor van een bestand of de resource. De security descriptor bevat de toegangsbeheerlijsten (ACL's) van de resource. De ACL Hiermee geeft u de machtigingen die gebruikers en gebruikersgroepen hebben toegang tot de bron."

- De gedetailleerde beschrijving moet worden beschreven de cmdlet, maar deze moet niet worden beschreven concepten die gebruikmaakt van de cmdlet. Definities van concept in aanvullende opmerkingen plaatsen.

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)
