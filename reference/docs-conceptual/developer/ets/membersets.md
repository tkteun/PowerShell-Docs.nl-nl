---
ms.date: 07/09/2020
ms.topic: reference
title: Leden sets van uitgebreid type systeem
description: Leden sets van uitgebreid type systeem
ms.openlocfilehash: b04d2618dc4bcf302d2e683d50c351ad3aa076ac
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650083"
---
# <a name="ets-member-sets"></a>ETS-ledensets

Met leden sets kunt u de leden van het **PSObject** -object in twee subsets partitioneren, zodat er door de naam van de subset naar de leden van de subsets kan worden verwezen. De twee typen subsets bevatten eigenschappen sets en leden sets. Als u bijvoorbeeld wilt zien hoe Power shell leden sets gebruikt, is er een specifieke eigenschappenset met de naam **DefaultDisplayPropertySet** die wordt gebruikt om tijdens runtime de eigenschappen te bepalen die moeten worden weer gegeven voor een bepaald **PSObject** -object.

## <a name="property-sets"></a>Eigenschappen sets

Eigenschappen sets kunnen een wille keurig aantal eigenschappen van een **PSObject** -type bevatten. In het algemeen kan een eigenschappen reeks worden gebruikt wanneer een verzameling eigenschappen (van hetzelfde type) nodig is. De eigenschappenset wordt gemaakt door de `PSPropertySet(System.String,System.Collections.Generic.IEnumerable{System.String})` constructor aan te roepen met de naam van de eigenschappenset en de namen van de eigenschappen waarnaar wordt verwezen. Het gemaakte **PSPropertySet** -object kan vervolgens worden gebruikt als een alias dat verwijst naar de eigenschappen in de set. De klasse [PSPropertySet](/dotnet/api/system.management.automation.pspropertyset) heeft de volgende eigenschappen en methoden.

- Eigenschap **IsInstance** : haalt een **Boolean** -waarde op die de bron van de eigenschap aangeeft.
- Eigenschap **member type** : Hiermee wordt het type eigenschappen in de eigenschappenset opgehaald.
- **Naam** eigenschap: Hiermee wordt de naam van de ingestelde eigenschap opgehaald.
- Eigenschap **ReferencedPropertyNames** : Hiermee worden de namen opgehaald van de eigenschappen in de set eigenschappen.
- Eigenschap **TypeNameOfValue** : Hiermee wordt **een** opsommings constante opgehaald die deze set definieert als een eigenschaps set.
- Eigenschap **waarde** : Hiermee wordt het **PSPropertySet** -object opgehaald of ingesteld.
- `PSPropertySet.Copy` methode: maakt een exacte kopie van het **PSPropertySet** -object.
- `PSMemberSet.ToString` methode: converteert het **PSPropertySet** -object naar een teken reeks.

## <a name="member-sets"></a>Leden sets

Leden sets kunnen elk wille keurig aantal uitgebreide leden van elk type bevatten. De ledenset wordt gemaakt door het aanroepen van de `PSMemberSet(System.String,System.Collections.Generic.IEnumerable{System.Management.Automation.PSMemberInfo})`
constructor met de naam van de ledenset en de namen van de gerefereerde onderdelen. Het gemaakte **PSPropertySet** -object kan vervolgens worden gebruikt als een alias die verwijst naar de leden in de set. De klasse [PSMemberSet](/dotnet/api/system.management.automation.psmemberset) heeft de volgende eigenschappen en methoden.

- Eigenschap **IsInstance** : haalt een **Boolean** -waarde op die de bron van het lid aangeeft.
- Eigenschap **Members** : Hiermee worden alle leden van de ledenset opgehaald.
- Eigenschap **member type** : haalt een **memberset** -opsommings constante op die deze set definieert als een ledenset.
- **Methoden** Property: Hiermee worden de methoden opgehaald die zijn opgenomen in de ledenset.
- **Eigenschappen** eigenschap: Hiermee worden de eigenschappen opgehaald die zijn opgenomen in de leden reeks.
- Eigenschap **TypeNameOfValue** : haalt een **memberset** -opsommings constante op die deze set definieert als een ledenset.
- Eigenschap **waarde** : Hiermee wordt het **PSMemberSet** -object opgehaald.
- `PSMemberSet.Copy` methode: maakt een exacte kopie van het **PSMemberSet** -object.
- `PSMemberSet.ToString` methode: converteert het **PSMemberSet** -object naar een teken reeks.
