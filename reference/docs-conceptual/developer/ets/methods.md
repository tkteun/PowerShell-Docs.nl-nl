---
ms.date: 07/09/2020
ms.topic: reference
title: Methoden voor uitgebreid type systeem klasse
description: Methoden voor uitgebreid type systeem klasse
ms.openlocfilehash: b53604a36e0a0c3587f345262e8f274e3a2c4859
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660377"
---
# <a name="ets-class-methods"></a>ETS-klasse-methoden

ETS-methoden zijn leden waarmee argumenten kunnen worden geretourneerd, kunnen resultaten retour neren en kunnen niet aan de linkerkant van een expressie worden weer gegeven. De methoden die beschikbaar zijn binnen ETS zijn onder andere code, Windows Power shell en script methoden.

> [!NOTE]
> Vanuit scripts worden methoden gebruikt met dezelfde syntaxis als andere leden met de toevoeging van een haakje aan het einde van de naam van de methode.

## <a name="code-methods"></a>Code methoden

Een code methode is een uitgebreid lid dat is gedefinieerd in een CLR-taal. Het biedt soort gelijke functionaliteit voor een methode die is gedefinieerd voor een basis object. een code methode kan echter dynamisch worden toegevoegd aan een **PSObject** -object. Om een code methode beschikbaar te maken, moet een ontwikkelaar de eigenschap schrijven in een CLR-taal, compileren en de resulterende assembly verzenden. Deze assembly moet beschikbaar zijn in de runs Pace waarvoor de code methode gewenst is. Houd er rekening mee dat de implementatie van code methode thread-safe moet zijn. Toegang tot deze methoden wordt uitgevoerd via [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) -objecten die de volgende open bare methoden en eigenschappen bieden.

- `PSCodeMethod.Copy` methode: maakt een exacte kopie van het **PSCodeMethod** -object.
- `PSCodeMethod.Invoke(System.Object[])` methode: roept de onderliggende code methode aan.
- `PSCodeMethod.ToString` methode: converteert het **PSCodeMethod** -object naar een teken reeks.
- `PSCodeMethod.CodeReference` eigenschap: Hiermee wordt de onderliggende methode opgehaald waarop de code methode is gebaseerd.
- Eigenschap **PSMemberInfo. IsInstance** : haalt een **Boolean** -waarde op die de bron van het lid aangeeft.
- Eigenschap **PSCodeMethod. member type** : Hiermee wordt een enumeratie constante van **PSMemberTypes. CodeMethod** opgehaald waarmee deze methode als code methode wordt geïdentificeerd.
- Eigenschap **PSMemberInfo.name** : Hiermee wordt de naam van de onderliggende code methode opgehaald.
- Eigenschap **PSCodeMethod. OverloadDefinitions** : Hiermee wordt een definitie opgehaald van alle Overloads van de onderliggende code methode.
- Eigenschap **PSCodeMethod. TypeNameOfValue** : haalt de volledige naam van de code methode op.
- Eigenschap **PSMemberInfo. Value** : Hiermee wordt het **PSCodeMethod** -object opgehaald.

## <a name="windows-powershell-methods"></a>Windows Power shell-methoden

Een Power shell-methode is een CLR-methode die is gedefinieerd in het basis object of toegankelijk is via een adapter. Toegang tot deze methoden wordt uitgevoerd via **PSMethod** -objecten die de volgende open bare methoden en eigenschappen bieden.

- `PSMethod.Copy` methode: maakt een exacte kopie van het **PSMethod** -object.
- `PSMethod.Invoke(System.Object[])` methode: roept de onderliggende methode aan.
- `PSMethod.ToString` methode: converteert het **PSMethod** -object naar een teken reeks.
- Eigenschap **PSMemberInfo. IsInstance** : haalt een **Boolean** -waarde op die de bron van het lid aangeeft.
- Eigenschap **PSMethod. member type** : Hiermee wordt een enumeratie constante van **PSMemberTypes. Method** opgehaald waarmee deze methode als Power shell-methode wordt geïdentificeerd.
- Eigenschap **PSMemberInfo.name** : Hiermee wordt de naam van de onderliggende methode opgehaald.
- Eigenschap **PSMethod. OverloadDefinitions** : Hiermee worden de definities van alle Overloads van de onderliggende methode opgehaald.
- Eigenschap **PSMethod. TypeNameOfValue** : Hiermee wordt het type ETS van deze methode opgehaald.
- Eigenschap **PSMemberInfo. Value** : Hiermee wordt het **PSMethod** -object opgehaald.

## <a name="script-methods"></a>Script methoden

Een script methode is een uitgebreid lid dat is gedefinieerd in de Power shell-taal. Het biedt soort gelijke functionaliteit voor een methode die is gedefinieerd voor een basis object. een script methode kan echter dynamisch worden toegevoegd aan een **PSObject** -object. Toegang tot deze methoden wordt uitgevoerd via [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) -objecten die de volgende open bare methoden en eigenschappen bieden.

- `PSScriptMethod.Copy` methode: maakt een exacte kopie van het **PSScriptMethod** -object.
- `PSScriptMethod.Invoke(System.Object[])` methode: roept de onderliggende script methode aan.
- `PSScriptMethod.ToString` methode: converteert het **PSScriptMethod** -object naar een teken reeks.
- Eigenschap **PSMemberInfo. IsInstance** : haalt een **Boolean** -waarde op die de bron van het lid aangeeft.
- Eigenschap **PSScriptMethod. member type** : Hiermee wordt een inventarisatie constante van **PSMemberTypes. ScriptMethod** opgehaald waarmee deze methode als een script methode wordt geïdentificeerd.
- Eigenschap **PSMemberInfo.name** : Hiermee wordt de naam van de onderliggende code methode opgehaald.
- Eigenschap **PSScriptMethod. OverloadDefinitions** : Hiermee worden de definities van alle Overloads van de onderliggende script methode opgehaald.
- Eigenschap **PSScriptMethod. TypeNameOfValue** : Hiermee wordt het type ETS van deze methode opgehaald.
- **PSScriptMethod. script** -eigenschap: Hiermee wordt het script opgehaald dat wordt gebruikt om de methode aan te roepen.
- Eigenschap **PSMemberInfo. Value** : Hiermee wordt het **PSScriptMethod** -object opgehaald.
