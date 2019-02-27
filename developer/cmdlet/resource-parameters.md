---
title: Resourceparameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: f58e8ecb67238939e90d4c5650bddd03da3c9409
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851749"
---
# <a name="resource-parameters"></a>Resourceparameters

De volgende tabel bevat de aanbevolen namen en de functionaliteit voor resourceparameters. Voor deze parameters kunnen de resources worden de assembly waarin de cmdlet-klasse of de hosttoepassing die de cmdlet wordt uitgevoerd.

Toepassingsgegevens, typt u: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan een toepassing opgeven.

Assembly-gegevenstype: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan een assembly opgeven.

Het gegevenstype van het kenmerk: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan een kenmerk opgeven.

Klasse-gegevenstype: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan een Microsoft .NET Framework-klasse opgeven.

Cluster-gegevenstype: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan een cluster opgeven.

Het gegevenstype van de cultuur: Tekenreeks

Deze parameter implementeren zodat de gebruiker kan de cultuur waarin u de cmdlet uitvoeren opgeven.

Gegevens in een domein, typt u: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan de domeinnaam opgeven.

Gegevens van het type station: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan de naam van een station opgeven.

Gebeurtenis-gegevenstype: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan de naam van een gebeurtenis opgeven.

Interface-gegevenstype: Tekenreeks

Deze parameter implementeren zodat de gebruiker kan een network interface-naam opgeven.

IP-adres-gegevenstype: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan een IP-adres opgeven.

Gegevens van het type taak: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan een taak opgeven.

LiteralPath gegevenstype: Tekenreeks

Implementeer deze parameter zodat de gebruiker het pad naar een resource opgeven kan als jokertekens worden niet ondersteund. (Gebruik de `Path` parameter wanneer jokertekens worden ondersteund.)

Mac-gegevenstype: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan een adres media access controller (MAC) opgeven.

ParentId-gegevenstype: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan de bovenliggende id opgeven.

Pad naar het gegevenstype: String, String[]

Implementeer deze parameter zodat de gebruiker de paden naar een resource aangeven kan wanneer jokertekens worden ondersteund. (Gebruik de `LiteralPath` parameter wanneer jokertekens worden niet ondersteund.)

U wordt aangeraden deze parameter te ontwikkelen, zodat deze ondersteuning biedt voor de syntaxis van de volledige '-provider: pad"die worden gebruikt door providers. We raden u ook aan dat u ontwikkeling ervan zodat het werkt met zo veel providers mogelijk.

Het gegevenstype van de poort: Integer, String

Implementeer deze parameter zodat de gebruiker kan een geheel getal voor het netwerk of een string-waarde, zoals 'biztalk' voor andere typen van poort opgeven.

Printer-gegevenstype: Integer, String

Deze parameter implementeren zodat de gebruiker de printer voor de cmdlet te gebruiken kunt opgeven.

Het formaat van het gegevenstype: Int32

Implementeer deze parameter zodat de gebruiker kan een grootte opgeven.

TID gegevenstype: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan een transactie-id (TID) voor de cmdlet opgeven.

Type-gegevenstype: Tekenreeks

Deze parameter implementeren zodat de gebruiker van het type resource waarop opgeven kan moet worden uitgevoerd.

URL-gegevenstype: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan een URL (Uniform Resource Locator) opgeven.

Gebruikersgegevens typt u: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan de naam of de naam van een andere gebruiker opgeven.

## <a name="see-also"></a>Zie ook

[Cmdlet-Parameters](./cmdlet-parameters.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
