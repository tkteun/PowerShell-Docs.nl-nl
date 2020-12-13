---
ms.date: 07/09/2020
ms.topic: reference
title: Uitgebreide type systeem klasse leden
description: Uitgebreide type systeem klasse leden
ms.openlocfilehash: 06488ce423f363a285ab53b21ab45989654346dc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666838"
---
# <a name="extended-type-system-class-members"></a>Uitgebreide type systeem klasse leden

ETS verwijst naar een aantal verschillende soorten leden waarvan de typen worden gedefinieerd door de **PSMemberTypes** -inventarisatie. Deze leden typen zijn onder andere eigenschappen, methoden, leden en leden sets die zijn gedefinieerd door hun eigen CLR-type. Een **NoteProperty** wordt bijvoorbeeld gedefinieerd door het eigen **PSNoteProperty** -type. Deze afzonderlijke CLR-typen hebben zowel hun eigen unieke eigenschappen als algemene eigenschappen die worden overgenomen van de [klasse PSMemberInfo](/dotnet/api/system.management.automation.psmemberinfo).

## <a name="the-psmemberinfo-class"></a>De PSMemberInfo-klasse

De klasse **PSMemberInfo** fungeert als basis klasse voor alle ETS-leden typen. Deze klasse biedt de volgende basis eigenschappen aan alle member CLR-typen.

- **Naam** eigenschap: de naam van het lid. Deze naam kan worden gedefinieerd door het basis object of door Power shell gedefinieerd wanneer aangepaste leden of uitgebreide leden worden weer gegeven.
- Eigenschap **waarde** : de waarde die is geretourneerd door het specifieke lid. Elk lidtype bepaalt hoe de waarde van het lid wordt verwerkt.
- Eigenschap **TypeNameOfValue** : dit is de naam van het CLR-type van de waarde die wordt geretourneerd door de eigenschap Value.

## <a name="accessing-members"></a>Toegang tot leden

U kunt toegang krijgen tot verzamelingen van leden via de eigenschappen van de **leden**, **methoden** en **Eigenschappen** van het object **PSObject** .

## <a name="ets-properties"></a>ETS-eigenschappen

ETS-eigenschappen zijn leden die als eigenschap kunnen worden behandeld. In feite kunnen ze worden weer gegeven aan de linkerkant van een expressie. Deze bevatten alias eigenschappen, code-eigenschappen, eigenschappen van de Power shell, notitie-eigenschappen en script eigenschappen. Zie [ETS-eigenschappen](properties.md)voor meer informatie over deze typen eigenschappen.

## <a name="ets-methods"></a>ETS-methoden

ETS-methoden zijn leden waarmee argumenten kunnen worden geretourneerd, kunnen resultaten retour neren en kunnen niet aan de linkerkant van een expressie worden weer gegeven. Ze omvatten code methoden, Power shell-methoden en script methoden.
Zie voor meer informatie over deze typen methoden ETS- [methoden](methods.md).
