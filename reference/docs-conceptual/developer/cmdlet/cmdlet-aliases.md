---
title: Cmdlet-aliassen | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fed4055f09e01c5f3fa87584d48551918606f4eb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784534"
---
# <a name="cmdlet-aliases"></a>Cmdlet-aliassen

U kunt cmdlet-aliassen gebruiken om de gebruikers ervaring van de cmdlet te verbeteren. U kunt aliassen toevoegen aan veelgebruikte cmdlets om het typen te verminderen en om het eenvoudiger te maken om taken snel uit te voeren. U kunt ingebouwde aliassen in uw cmdlets toevoegen, of gebruikers kunnen hun eigen aangepaste aliassen definiëren.

De [Get-opdracht](/powershell/module/microsoft.powershell.core/get-command) cmdlet heeft bijvoorbeeld een ingebouwde `gcm` alias. U kunt ook aliassen gebruiken om opdracht namen uit andere talen toe te voegen, zodat gebruikers geen nieuwe opdrachten hoeven te leren.

## <a name="alias-guidelines"></a>Richt lijnen voor alias

Volg deze richt lijnen wanneer u ingebouwde aliassen voor uw cmdlets maakt:

- Voordat u aliassen toewijst, start u Windows Power shell en voert u de cmdlet [Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) uit om de aliassen weer te geven die al zijn gebruikt.

- Neem een voor voegsel van een alias op dat verwijst naar het werk woord van de naam van de cmdlet en een alias achtervoegsel dat verwijst naar het zelfstandig naam woord van de cmdletnaam. De alias voor de `Import-Module` cmdlet is bijvoorbeeld ' ipmo '. Zie [cmdlet-termen](./approved-verbs-for-windows-powershell-commands.md)voor een lijst met alle termen en de bijbehorende aliassen.

- Voor cmdlets die dezelfde term hebben, neemt u hetzelfde alias voorvoegsel op. Bijvoorbeeld: de aliassen voor alle Windows Power shell-cmdlets die de opdracht ' Get ' hebben in hun naam, gebruiken het voor voegsel ' g '.

- Voor cmdlets die hetzelfde zelfstandig naam woord hebben, neemt u hetzelfde alias achtervoegsel op. De aliassen voor alle Windows Power shell-cmdlets die het zelfstandig naam woord ' session ' hebben, gebruiken bijvoorbeeld het achtervoegsel ' SN '.

- Voor cmdlets die gelijk zijn aan opdrachten in andere talen, gebruikt u de naam van de opdracht.

- In het algemeen maakt u aliassen zo kort mogelijk. Zorg ervoor dat de alias ten minste één afzonderlijk teken voor de opdracht en één afzonderlijk teken voor het zelfstandige naam heeft. Voeg indien nodig meer tekens toe om de alias uniek te maken.

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
