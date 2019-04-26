---
title: Cmdlet aliassen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068711"
---
# <a name="cmdlet-aliases"></a>Cmdlet-aliassen

U kunt cmdlet-aliassen gebruiken voor het verbeteren van de gebruikerservaring van de cmdlet. U kunt aliassen voor veelgebruikte-cmdlets te verminderen te typen en eenvoudiger taken uitvoeren snel toevoegen. U kunt ingebouwde aliassen opnemen in uw cmdlets, of gebruikers kunnen hun eigen aangepaste aliassen definiëren.

Bijvoorbeeld, de [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet heeft een ingebouwde `gcm` alias. U kunt ook aliassen gebruiken om toe te voegen opdrachtnamen van andere talen zodat gebruikers geen nieuwe opdrachten te leren.

## <a name="alias-guidelines"></a>Alias-richtlijnen

Volg deze richtlijnen wanneer u ingebouwde aliassen voor uw cmdlets maakt:

- Voordat u alias toewijst, start u Windows PowerShell en voer vervolgens de [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet om te controleren van de aliassen die al worden gebruikt.

- Een alias-voorvoegsel dat verwijst naar de bewerking van de cmdlet-naam en een alias-achtervoegsel die verwijst naar het zelfstandig naamwoord van de cmdlet-naam bevatten. Bijvoorbeeld: de alias voor de `Import-Module` cmdlet is 'ipmo'. Zie voor een lijst van alle bewerkingen en hun aliassen, [werkwoorden](./approved-verbs-for-windows-powershell-commands.md).

- Cmdlets die de dezelfde opdracht hebben, zijn hetzelfde voorvoegsel alias. Bijvoorbeeld de aliassen voor alle Windows PowerShell-cmdlets die de term 'Get' in hun naam hebben het voorvoegsel "g" gebruiken.

- De cmdlets die de dezelfde zelfstandig naamwoord, het achtervoegsel van dezelfde alias opgenomen. Bijvoorbeeld, gebruik de aliassen voor alle Windows PowerShell-cmdlets die de "Sessie" zelfstandig naamwoord in hun naam hebben het achtervoegsel 'sn'.

- De cmdlets die gelijk aan de opdrachten in andere talen zijn, de naam van de opdracht te gebruiken.

- In het algemeen moet u aliassen zo kort mogelijk. Zorg ervoor dat de alias is ten minste één afzonderlijke voor het werkwoord en een afzonderlijke teken voor het zelfstandig naamwoord. Voeg meer tekens zo nodig de alias uniek te maken.

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
