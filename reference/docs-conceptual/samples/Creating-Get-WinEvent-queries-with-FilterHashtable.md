---
ms.date: 09/13/2019
title: Get-WinEvent-query's maken met FilterHashtable
ms.openlocfilehash: 35d18dc894d90e698b38395b79ff4cf395515909
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "73444385"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a>Get-WinEvent-query's maken met FilterHashtable

Zie [FilterHashTable gebruiken om gebeurtenis logboeken te filteren met Power shell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/)voor meer informatie over de oorspronkelijke blog post van 3 juni 2014 **Scripting Guy** .

Dit artikel is een fragment van het oorspronkelijke blog bericht en legt uit hoe u de `Get-WinEvent` **FilterHashtable** -para meter van de cmdlet kunt gebruiken om gebeurtenis logboeken te filteren. De cmdlet `Get-WinEvent` van Power shell is een krachtige methode voor het filteren van Windows-gebeurtenis-en Diagnostische logboeken. Prestaties verbeteren wanneer een `Get-WinEvent` query gebruikmaakt van de para meter **FilterHashtable** .

Wanneer u werkt met grote gebeurtenis logboeken, is het niet efficiënt om objecten naar een `Where-Object` opdracht van de pijp lijn te verzenden. Vóór Power shell 6 was de `Get-EventLog` cmdlet een andere optie om logboek gegevens op te halen. De volgende opdrachten zijn bijvoorbeeld inefficiënt om de logboeken van **micro soft-Windows-defragmentatie** te filteren:

```powershell
Get-EventLog -LogName Application | Where-Object Source -Match defrag

Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }
```

De volgende opdracht maakt gebruik van een hash-tabel waarmee de prestaties worden verbeterd:

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a>Blog berichten over inventarisatie

Dit artikel bevat informatie over het gebruik van opgesomde waarden in een hash-tabel. Lees deze **Scripting Guy** blog-berichten voor meer informatie over inventarisatie. Als u een functie wilt maken die de opgesomde waarden retourneert, raadpleegt u [opsommingen en waarden](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).
Zie de [Scripting Guy-serie blog berichten over inventarisatie](https://devblogs.microsoft.com/scripting/?s=about+enumeration)voor meer informatie.

## <a name="hash-table-key-value-pairs"></a>Hash-tabel sleutel-waardeparen

Voor het bouwen van efficiënte query's gebruikt `Get-WinEvent` u de cmdlet met de para meter **FilterHashtable** .
**FilterHashtable** accepteert een hash-tabel als een filter voor het ophalen van specifieke informatie uit Windows-gebeurtenis Logboeken. Een hash-tabel gebruikt **sleutel-** waardeparen. Zie [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)voor meer informatie over hash-tabellen.

Als de **sleutel-** waardeparen zich op dezelfde regel bevinden, moeten ze worden gescheiden door een punt komma. Als elk **sleutel/waarde-** paar zich op een afzonderlijke regel bevindt, hoeft u geen punt komma te koppelen. Dit artikel plaatst bijvoorbeeld **sleutel-** waardeparen op afzonderlijke regels en maakt geen gebruik van punt komma's.

In dit voor beeld wordt gebruikgemaakt van een aantal **sleutel-** waardeparen van de **FilterHashtable** -para meter. De voltooide query bevat **LogName**, **ProviderName**, **tref woorden**, **id**en **niveau**.

De geaccepteerde **sleutel-** waardeparen worden weer gegeven in de volgende tabel en zijn opgenomen in de documentatie voor de para meter [Get-Wine vent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** .

De volgende tabel geeft de sleutel namen, gegevens typen en of joker tekens worden geaccepteerd voor een gegevens waarde.

|    Sleutelnaam    | Waarde gegevens type | Joker tekens accepteren? |
| -------------- | --------------- | ---------------------------- |
| LogName        | `<String[]>`    | Ja                          |
| ProviderName   | `<String[]>`    | Ja                          |
| Pad           | `<String[]>`    | Nee                           |
| Trefwoorden       | `<Long[]>`      | Nee                           |
| Id             | `<Int32[]>`     | Nee                           |
| Niveau          | `<Int32[]>`     | Nee                           |
| StartTime      | `<DateTime>`    | Nee                           |
| EndTime        | `<DateTime>`    | Nee                           |
| UserID         | `<SID>`         | Nee                           |
| Gegevens           | `<String[]>`    | Nee                           |
| `<named-data>` | `<String[]>`    | Nee                           |

De `<named-data>` sleutel vertegenwoordigt een benoemd gebeurtenis gegevens veld. De perflib-gebeurtenis 1008 kan bijvoorbeeld de volgende gebeurtenis gegevens bevatten:

```xml
<EventData>
  <Data Name="Service">BITS</Data>
  <Data Name="Library">C:\Windows\System32\bitsperf.dll</Data>
  <Data Name="Win32Error">2</Data>
</EventData>
```

Met de volgende opdracht kunt u een query uitvoeren voor deze gebeurtenissen:

```powershell
Get-WinEvent -FilterHashtable @{LogName='Application'; 'Service'='Bits'}
```

> [!NOTE]
> De mogelijkheid om een query `<named-data>` voor uit te zoeken, is toegevoegd aan Power shell 6.

## <a name="building-a-query-with-a-hash-table"></a>Een query bouwen met een hash-tabel

Om de resultaten te controleren en problemen op te lossen, kunt u de hash-tabel één **sleutel/waarde-** paar tegelijk maken. De query haalt gegevens op uit het **toepassings** logboek. De hash-tabel is gelijk `Get-WinEvent –LogName Application`aan.

Maak de `Get-WinEvent` query om te beginnen. Gebruik het **sleutel-** waardepaar van de para meter **FilterHashtable** met de sleutel, **LogName**en de waarde **toepassings**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

Ga door met het samen stellen van de hash-tabel met de sleutel van de **provider** . De **ProviderName** is de naam die wordt weer gegeven in het **bron** veld in het **Windows logboeken**. Bijvoorbeeld **.NET runtime** in de volgende scherm afbeelding:

![Afbeelding van Windows-Logboeken bronnen.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

Werk de hash-tabel bij en neem het **sleutel-** waardepaar op met de sleutel, * * ProviderName en de waarde **.NET runtime**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

Als uw query gegevens moet ophalen uit gearchiveerde gebeurtenis logboeken, gebruikt u de **pad** -sleutel. De waarde van het **pad** geeft het volledige pad naar het logboek bestand aan. Zie het blog bericht van **Scripting Guy** voor meer informatie. [gebruik Power shell om opgeslagen gebeurtenis logboeken te parseren op fouten](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).

## <a name="using-enumerated-values-in-a-hash-table"></a>Opsommings waarden gebruiken in een hash-tabel

**Tref woorden** is de volgende sleutel in de hash-tabel. Het gegevens type **Keywords** is een matrix van `[long]` het waardetype dat een groot getal bevat. Gebruik de volgende opdracht om de maximum waarde te vinden `[long]`van:

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

Voor de sleutel **tref woorden** gebruikt Power shell een getal, geen teken reeks zoals **beveiliging**. De **sleutel woorden** worden door **Windows logboeken** als teken reeksen weer gegeven, maar de waarden worden opgesomd. Als u in de tabel hash de sleutel **tref woorden** gebruikt met een teken reeks waarde, wordt een fout bericht weer gegeven.

Open de **Windows-logboeken** en klik in het deel venster **acties** op **Huidig logboek filteren**.
De vervolg keuzelijst **tref woorden** bevat de beschik bare tref woorden, zoals wordt weer gegeven in de volgende scherm afbeelding:

![Afbeelding van Windows-Logboeken tref woorden.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

Gebruik de volgende opdracht om de namen `StandardEventKeywords` van de eigenschappen weer te geven.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

De opgesomde waarden worden gedocumenteerd in de **.NET Framework**. Zie [StandardEventKeywords Enumeration (Engelstalig)](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2)voor meer informatie.

De namen van de **tref woorden** en opgesomde waarden zijn als volgt:

| Naam             |  Waarde            |
| ---------------- | ------------------|
| AuditFailure     | 4503599627370496  |
| AuditSuccess     | 9007199254740992  |
| CorrelationHint2 | 18014398509481984 |
| EventLogClassic  | 36028797018963968 |
| Sqm              | 2251799813685248  |
| WdiDiagnostic    | 1125899906842624  |
| WdiContext       | 562949953421312   |
| Respons tijd     | 281474976710656   |
| Geen             | 0                 |

Werk de hash-tabel bij en neem het **sleutel-** waardepaar op met de sleutel, **tref woorden**en de **EventLogClassic** -opsommings waarde **36028797018963968**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a>Waarde van de eigenschap static van tref woorden (optioneel)

De sleutel **tref woorden** wordt opgesomd, maar u kunt een statische eigenschaps naam gebruiken in de hash-tabel query.
In plaats van de geretourneerde teken reeks te gebruiken, moet de naam van de eigenschap worden geconverteerd naar een waarde met de eigenschap **Value__** .

Het volgende script maakt bijvoorbeeld gebruik van de eigenschap **Value__** .

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a>Filteren op gebeurtenis-id

Om meer specifieke gegevens te verkrijgen, worden de resultaten van de query gefilterd op **gebeurtenis-id**. Er wordt in de hash-tabel naar de **gebeurtenis-id** verwezen als sleutel **-id** en de waarde is een specifieke **gebeurtenis-id**. De **gebeurtenis-id**wordt weer gegeven in de **Windows-logboeken** . In dit voor beeld wordt **gebeurtenis-Id 1023**gebruikt.

Werk de hash-tabel bij en neem het **sleutel-** waardepaar op met de sleutel, **id** en de waarde **1023**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a>Filteren op niveau

Gebruik de **niveau** sleutel om de resultaten verder te verfijnen en alleen gebeurtenissen toe te voegen die fouten bevatten.
**Windows logboeken** geeft het **niveau** weer als teken reeks waarden, maar ze zijn opsommings waarden. Als u in de tabel hash de **niveau** sleutel met een teken reeks waarde gebruikt, wordt er een fout bericht weer gegeven.

**Niveau** heeft waarden zoals **fout**, **waarschuwing**of **informatief**. Gebruik de volgende opdracht om de namen `StandardEventLevel` van de eigenschappen weer te geven.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

De opgesomde waarden worden gedocumenteerd in de **.NET Framework**. Zie [StandardEventLevel Enumeration (Engelstalig)](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2)voor meer informatie.

De namen van de **niveau** sleutel en opgesomde waarden zijn als volgt:

| Naam           | Waarde |
| -------------- | ----- |
| Verbose        |   5   |
| Informatief  |   4   |
| Waarschuwing        |   3   |
| Fout          |   2   |
| Kritiek       |   1   |
| LogAlways      |   0   |

De hash-tabel voor de voltooide query bevat de sleutel, het **niveau**en de waarde **2**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a>Niveau static-eigenschap in opsomming (optioneel)

De **niveau** sleutel wordt opgesomd, maar u kunt een statische eigenschaps naam in de hash-tabel query gebruiken.
In plaats van de geretourneerde teken reeks te gebruiken, moet de naam van de eigenschap worden geconverteerd naar een waarde met de eigenschap **Value__** .

Het volgende script maakt bijvoorbeeld gebruik van de eigenschap **Value__** .

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```