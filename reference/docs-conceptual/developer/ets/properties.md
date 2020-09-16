---
title: Uitgebreide-type systeem eigenschappen
ms.date: 07/09/2020
ms.openlocfilehash: c0a994e5b946117dcc1a2d647d07ae62af883861
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786200"
---
# <a name="ets-properties"></a>ETS-eigenschappen

Eigenschappen zijn leden die kunnen worden behandeld als een eigenschap. In feite kunnen ze worden weer gegeven aan de linkerkant van een expressie. De beschik bare eigenschappen zijn onder andere alias-, code-, notitie-en script eigenschappen.

## <a name="alias-property"></a>Alias eigenschap

Een alias eigenschap is een eigenschap die verwijst naar een andere eigenschap die het **PSObject** -object bevat. Het wordt voornamelijk gebruikt voor het wijzigen van de naam van de eigenschap waarnaar wordt verwezen. Het kan echter ook worden gebruikt om de waarde van de eigenschap waarnaar wordt verwezen, te converteren naar een ander type. Met betrekking tot ETS is dit type eigenschap altijd een uitgebreid lid en gedefinieerd door de [PSAliasProperty](/dotnet/api/system.management.automation.psaliasproperty) -klasse. De klasse bevat de volgende eigenschappen.

- Eigenschap **ConversionType** : het CLR-type dat wordt gebruikt voor het converteren van de waarde van het onderdeel waarnaar wordt verwezen.
- Eigenschap **IsGettable** : geeft aan of de waarde van de eigenschap waarnaar wordt verwezen, kan worden opgehaald.
  Deze eigenschap wordt dynamisch bepaald door het controleren van de eigenschap **IsGettable** van de eigenschap waarnaar wordt verwezen.
- Eigenschap **IsSettable** : geeft aan of de waarde van de eigenschap waarnaar wordt verwezen, kan worden ingesteld. Deze eigenschap wordt dynamisch bepaald door het controleren van de eigenschap **IsSettable** van de eigenschap waarnaar wordt verwezen.
- Eigenschap **member type** : een **AliasProperty** -opsommings constante die deze eigenschap definieert als een alias eigenschap.
- Eigenschap **ReferencedMemberName** : de naam van de eigenschap waarnaar wordt verwezen waarnaar deze alias verwijst.
- Eigenschap **TypeNameOfValue** : de volledige naam van het CLR-type van de waarde van de eigenschap waarnaar wordt verwezen.
- Eigenschap **waarde** : de waarde van de eigenschap waarnaar wordt verwezen.

## <a name="code-property"></a>Code-eigenschap

Een code-eigenschap is een eigenschap die een getter en Setter is die is gedefinieerd in een CLR-taal. Om een code-eigenschap beschikbaar te maken, moet een ontwikkelaar de eigenschap schrijven in een CLR-taal, compileren en de resulterende assembly verzenden. Deze assembly moet beschikbaar zijn in de runs Pace waar de code-eigenschap gewenst is. Met betrekking tot ETS is dit type eigenschap altijd een uitgebreid lid en gedefinieerd door de [PSCodeProperty](/dotnet/api/system.management.automation.pscodeproperty) -klasse. De klasse bevat de volgende eigenschappen.

- Eigenschap **GetterCodeReference** : de methode die wordt gebruikt om de waarde van de eigenschap code op te halen.
- Eigenschap **IsGettable** : geeft aan of de waarde van de code-eigenschap kan worden opgehaald. de eigenschap **SetterCodeReference** : de methode die wordt gebruikt om de waarde van de eigenschap code in te stellen.
- Eigenschap **IsSettable** : geeft aan of de waarde van de eigenschap code kan worden ingesteld, dat de eigenschap **SetterCodeReference** niet null is.
- Eigenschap **member type** : een **CodeProperty** -opsommings constante die deze eigenschap definieert als een code-eigenschap.
- Eigenschap **SetterCodeReference** : de methode die wordt gebruikt om de waarde van de eigenschap code op te halen.
- Eigenschap **TypeNameOfValue** : het CLR-type van de code-eigenschaps waarde die wordt geretourneerd door de eigenschappen Get-bewerking.
- Eigenschap **waarde** : de waarde van de code-eigenschap. Wanneer deze eigenschap wordt opgehaald, wordt de getter-code in de eigenschap GetterCodeReference aangeroepen, waarbij het huidige **PSObject** -object wordt door gegeven en de waarde die door de aanroep wordt geretourneerd, wordt geretourneerd. Wanneer deze eigenschap is ingesteld, wordt de Setter code in de eigenschap **SetterCodeReference** aangeroepen, waarbij het huidige **PSObject** -object wordt door gegeven als het eerste argument en het object dat wordt gebruikt om de waarde als tweede argument in te stellen.

## <a name="note-property"></a>Eigenschap Note

Een eigenschap Note is een eigenschap die een naam/waarde-koppeling heeft. Met betrekking tot ETS is dit type eigenschap altijd een uitgebreid lid en gedefinieerd door de [PSNoteProperty](/dotnet/api/system.management.automation.psnoteproperty) -klasse. De klasse bevat de volgende eigenschappen.

- Eigenschap **IsGettable** : geeft aan of de waarde van de eigenschap Note kan worden opgehaald.
- Eigenschap **IsSettable** : geeft aan of de waarde van de eigenschap Note kan worden ingesteld.
- Eigenschap **member type** : een **NoteProperty** -opsommings constante die deze eigenschap definieert als een notitie-eigenschap.
- Eigenschap **TypeNameOfValue** : de volledig gekwalificeerde type naam van het object dat door de Get-bewerking van de eigenschap Note wordt geretourneerd.
- **Waarde**: de waarde van de eigenschap Note.

## <a name="powershell-property"></a>Power shell-eigenschap

Een Power shell-eigenschap is een eigenschap die is gedefinieerd in het basis object of een eigenschap die beschikbaar wordt gemaakt via een adapter. Het kan zowel CLR-velden als CLR-eigenschappen hebben. Met betrekking tot ETS kan dit type eigenschap een base-lid of een adapter-lid zijn en wordt gedefinieerd door de [PSProperty](/dotnet/api/system.management.automation.psproperty) -klasse. De klasse bevat de volgende eigenschappen.

- Eigenschap **IsGettable** : geeft aan of de waarde van de eigenschap base of aangepast kan worden opgehaald.
- Eigenschap **IsSettable** : geeft aan of de waarde van de eigenschap base of aangepast kan worden ingesteld.
- Eigenschap **member type** : een opsommings constante voor eigenschappen die deze eigenschap definieert als een Power shell-eigenschap.
- Eigenschap **TypeNameOfValue** : de volledig gekwalificeerde naam van het type eigenschaps waarde. Bijvoorbeeld, voor een eigenschap waarvan de waarde een teken reeks is, is het type eigenschaps waarde **System. String**.
- Eigenschap **waarde** : de waarde van de eigenschap. Als de Get-of set-bewerking wordt aangeroepen voor een eigenschap die deze bewerking niet ondersteunt, wordt een **GetValueException** -of **SetValueException** -uitzonde ring gegenereerd

## <a name="powershell-script-property"></a>Power shell-script eigenschap

Een script eigenschap is een eigenschap met getter-en setter-scripts. Met betrekking tot ETS is dit type eigenschap altijd een uitgebreid lid en gedefinieerd door de [PSScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) -klasse. De klasse bevat de volgende eigenschappen.

- Eigenschap **GetterScript** : het script dat wordt gebruikt om de waarde van de script eigenschap op te halen.
- Eigenschap **IsGettable** : geeft aan of de eigenschap **GetterScript** een script blok beschrijft.
- Eigenschap **IsSettable** : geeft aan of de eigenschap **SetterScript** een script blok beschrijft.
- Eigenschap **member type** : een ScriptProperty-opsommings constante die deze eigenschap identificeert als een script eigenschap.
- Eigenschap **SetterScript** : het script dat wordt gebruikt om de waarde van de script eigenschap in te stellen.
- Eigenschap **TypeNameOfValue** : de volledig gekwalificeerde type naam van het object dat door het getter-script wordt geretourneerd. In dit geval **System. object** wordt altijd geretourneerd.
- Eigenschap **waarde** : de waarde van de eigenschap script. Een Get roept het getter script aan en retourneert de gegeven waarde. Een set roept het Setter script aan.
