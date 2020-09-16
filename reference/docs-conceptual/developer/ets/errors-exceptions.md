---
title: Fouten en uitzonde ringen in het uitgebreide-type systeem
ms.date: 07/09/2020
ms.openlocfilehash: f60c53e33c031168eda53726e0d296bf91139fda
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786285"
---
# <a name="errors-and-exceptions-in-the-extended-type-system"></a>Fouten en uitzonde ringen in het uitgebreide-type systeem

Er kunnen fouten optreden in ETS tijdens de initialisatie van type gegevens en bij het openen van een lid van een **PSObject** -object of het gebruik van een van de hulpprogramma klassen zoals **LanguagePrimitives**.

## <a name="runtime-errors"></a>Runtime-fouten

Met één uitzonde ring, wanneer cast, worden alle uitzonde ringen die tijdens runtime worden gegenereerd, een **ExtendedTypeSystemException** -uitzonde ring of een uitzonde ring die is afgeleid van de **ExtendedTypeSystemException** -klasse. Hierdoor kunnen script ontwikkelaars deze uitzonde ringen overvullen met behulp van de- `Trap` instructie in hun script.

## <a name="errors-getting-member-values"></a>Fouten bij het ophalen van leden waarden

Bij alle fouten die optreden wanneer de waarde van een ETS-lid (eigenschap, methode of geparametriseerde eigenschap) wordt opgehaald, wordt een **GetValueException** -of **GetValueInvocationException** -uitzonde ring gegenereerd.
Wanneer ETS detecteert dat er een fout is opgetreden, wordt een **GetValueException** -uitzonde ring gegenereerd. Wanneer de onderliggende getter van een lid waarnaar wordt verwezen, detecteert dat er een fout is opgetreden, wordt een **GetValueInvocationException** -uitzonde ring gegenereerd die de interne uitzonde ring kan bevatten die de aanroep fout heeft veroorzaakt.

## <a name="errors-setting-member-values"></a>Fouten bij het instellen van leden waarden

Alle fouten die optreden bij het instellen van de waarde van een ETS-eigenschap veroorzaken een **SetValueException** -of **SetValueInvocationException** -uitzonde ring. Wanneer ETS detecteert dat er een fout is opgetreden, wordt een **SetValueException** -uitzonde ring gegenereerd. Wanneer de onderliggende setter van een eigenschap waarnaar wordt verwezen, detecteert dat er een fout is opgetreden, wordt er een **SetValueInvocationException** -uitzonde ring gegenereerd die de interne uitzonde ring kan bevatten die de ingestelde aanroep fout heeft veroorzaakt.

## <a name="errors-invoking-a-method"></a>Fouten bij het aanroepen van een methode

Alle fouten die optreden bij het aanroepen van een ETS-methode veroorzaken een **MethodException** -of **MethodInvocationException** -uitzonde ring. Wanneer ETS detecteert dat er een fout is opgetreden, wordt een **MethodException** -uitzonde ring gegenereerd. Wanneer de methode waarnaar wordt verwezen, detecteert dat er een fout is opgetreden, wordt er een **MethodInvocationException** -uitzonde ring gegenereerd die de binnenste uitzonde ring kan bevatten die de aanroep fout heeft veroorzaakt.

## <a name="casting-errors"></a>Fouten casten

Wanneer een ongeldige cast wordt geprobeerd, wordt een **PSInvalidCastException** gegenereerd. Omdat deze uitzonde ring is afgeleid van **System. InvalidCastException**, kan deze niet rechtstreeks worden onderschept vanuit het script. Houd er rekening mee dat de entiteit die de cast probeert, **PSInvalidCastException** in een **PSRuntimeException** moet teruglopen zodat deze kan worden onderschept door scripts. Als er een poging wordt gedaan om de waarde van een **PSPropertySet**, **PSMemberSet**, **PSMethodInfo**of een lid van de **ReadOnlyPSMemberInfoCollection ' 1 '** in te stellen, wordt een **NotSupportedException** gegenereerd.

## <a name="common-runtime-errors"></a>Veelvoorkomende runtime-fouten

Alle andere veelvoorkomende runtime-fouten die optreden, zijn van het type **ExtendedTypeSystemException** Exception zonder extra specifieke uitzonderings typen.

## <a name="initialization-errors"></a>Initialisatie fouten

Er kunnen fouten optreden bij het initialiseren `types.ps1xml` . Deze fouten worden meestal weer gegeven wanneer de Power shell-runtime wordt gestart. Ze kunnen echter ook worden weer gegeven wanneer een module wordt geladen.
