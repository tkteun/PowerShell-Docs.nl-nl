---
title: Eigenschaps parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359373"
---
# <a name="property-parameters"></a>Eigenschapsparameters

De volgende tabel bevat de aanbevolen namen en functionaliteit voor eigenschaps parameters.

|Parameter|Functionaliteit|
|---|---|
|**Aantal**<br>Gegevens type: Int32|Implementeer deze para meter zodat de gebruiker het aantal objecten kan opgeven dat moet worden verwerkt.|
|**Beschrijving**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een beschrijving voor een resource kan opgeven.|
|**Van**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker het referentie object kan opgeven om informatie uit op te halen.|
|**Id**<br>Gegevens type: bron afhankelijk|Implementeer deze para meter zodat de gebruiker de id van een resource kan opgeven.|
|**Ingevoerd**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de specificatie van het invoer bestand kan opgeven.|
|**Locatie**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de locatie van de resource kan opgeven.|
|**LogName**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de naam kan opgeven van het logboek bestand dat moet worden verwerkt of gebruikt.|
|**Naam**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de naam van de resource kan opgeven.|
|**Uitvoer**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker het uitvoer bestand kan opgeven.|
|**Bent**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de naam van de eigenaar van de resource kan opgeven.|
|**Eigenschap**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de naam of de namen van de te gebruiken eigenschappen kan opgeven.|
|**Gemotiveerd**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker kan opgeven waarom deze cmdlet wordt aangeroepen.|
|**Reguliere**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat reguliere expressies worden gebruikt wanneer de para meter is opgegeven. Als deze para meter is opgegeven, worden joker tekens niet omgezet.|
|**Waarmee**<br>Gegevens type: Int32|Implementeer deze para meter zodat de gebruiker de baud-rate kan opgeven. De gebruiker stelt deze para meter in op de snelheid van de resource.|
|**Overheids**<br>Gegevens type: trefwoord matrix|Implementeer deze para meter zodat de gebruiker de namen van statussen kan opgeven, zoals TOETSOMLAAG.|
|**Value**<br>Gegevens type: object|Implementeer deze para meter zodat de gebruiker een waarde kan opgeven die aan de cmdlet moet worden verstrekt.|
|**Versie**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de versie van de eigenschap kan opgeven.|

## <a name="see-also"></a>Zie ook

[Cmdlet-para meters](./cmdlet-parameters.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)

[Windows Power shell SDK](../windows-powershell-reference.md)
