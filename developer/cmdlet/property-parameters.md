---
title: De Eigenschapsparameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251418"
---
# <a name="property-parameters"></a>Eigenschapsparameters

De volgende tabel bevat de aanbevolen namen en de functionaliteit voor de Eigenschapsparameters.

|Parameter|Functionaliteit|
|---|---|
|**Aantal**<br>Gegevenstype: Int32|Deze parameter implementeren zodat de gebruiker het aantal objecten opgeven kan moeten worden verwerkt.|
|**Beschrijving**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan een beschrijving op voor een resource opgeven.|
|**From**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan het referentieobject voor het ophalen van gegevens uit opgeven.|
|**Id**<br>Gegevenstype: Afhankelijke resource|Implementeer deze parameter zodat de gebruiker kan de id van een resource opgeven.|
|**Invoer**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan de specificatie-bestand voor invoer opgeven.|
|**Locatie**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan de locatie van de resource opgeven.|
|**LogName**<br>Gegevenstype: Tekenreeks|Deze parameter implementeren zodat de gebruiker de naam van het logboekbestand opgeven kan te verwerken of gebruiken.|
|**Naam**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan de naam van de resource opgeven.|
|**Uitvoer**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan het uitvoerbestand opgeven.|
|**Eigenaar**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan de naam van de eigenaar van de resource opgeven.|
|**De eigenschap**<br>Gegevenstype: Tekenreeks|Deze parameter implementeren zodat de gebruiker opgeven kan de naam of de namen van de eigenschappen te gebruiken.|
|**Reden**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan aangeven waarom deze cmdlet wordt aangeroepen.|
|**Regex**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat de reguliere expressies worden gebruikt wanneer de parameter is opgegeven. Als deze parameter is opgegeven, worden de jokertekens zijn niet omgezet.|
|**snelheid**<br>Gegevenstype: Int32|Implementeer deze parameter zodat de gebruiker kan de baudrate opgeven. De gebruiker Hiermee stelt u deze parameter met de snelheid van de resource.|
|**status**<br>Gegevenstype: Sleutelwoord matrix|Implementeer deze parameter zodat de gebruiker kan de namen van Staten, zoals KEYDOWN opgeven.|
|**Waarde**<br>Gegevenstype: Object|Implementeer deze parameter zodat de gebruiker kan een waarde om te bieden aan de cmdlet opgeven.|
|**Versie**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan de versie van de eigenschap opgeven.|

## <a name="see-also"></a>Zie ook

[Cmdlet-Parameters](./cmdlet-parameters.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
