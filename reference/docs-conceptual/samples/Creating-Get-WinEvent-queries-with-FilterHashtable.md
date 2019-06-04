---
ms.date: 03/18/2019
title: Get-WinEvent-query's maken met FilterHashtable
ms.openlocfilehash: 2f598fceb570f189bee776b6ed572b11a6938f64
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/03/2019
ms.locfileid: "66471011"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a>Get-WinEvent-query's maken met FilterHashtable

Lezen van de oorspronkelijke juni 3 2014 **Scripting Guy** blog post, Zie [gebruik FilterHashTable naar Filter gebeurtenislogboek met PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).

In dit artikel is een fragment van de oorspronkelijke blogpost en wordt uitgelegd hoe u de `Get-WinEvent` van de cmdlet **FilterHashtable** parameter voor het filteren van gebeurtenislogboeken. De PowerShell `Get-WinEvent` cmdlet is een krachtige methode voor het filteren van Windows-gebeurtenissen en logboeken met diagnostische gegevens. Verbetert de prestaties wanneer een `Get-WinEvent` query gebruikt de **FilterHashtable** parameter.

Wanneer u met grote gebeurtenislogboeken werkt, is het niet efficiënt voor het verzenden van objecten in de pijplijn in een `Where-Object` opdracht. Voorafgaand aan PowerShell 6, de `Get-EventLog` cmdlet is een andere optie om op te halen van logboekgegevens. De volgende opdrachten zijn bijvoorbeeld inefficiënt filter de **Microsoft-Windows-defragmentatie** Logboeken:

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

De volgende opdracht maakt gebruik van een hash-tabel waarmee de prestaties worden verbeterd:

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a>Blogberichten over de opsomming

In dit artikel bevat informatie over het gebruik van vaste waarden in een hash-tabel. Lees voor meer informatie over opsomming deze **Scripting Guy** blogberichten. Zie voor het maken van een functie waarmee de opsommingswaarden worden geretourneerd, [opsommingen en waarden](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).
Zie voor meer informatie de [Scripting Guy blog reeks blogberichten over opsomming](https://devblogs.microsoft.com/scripting/?s=about+enumeration).

## <a name="hash-table-keyvalue-pairs"></a>Hash-tabel sleutel/waarde-paren

Voor het bouwen van efficiënte query's, gebruikt u de `Get-WinEvent` cmdlet met de **FilterHashtable** parameter.
**FilterHashtable** accepteert van een hash-tabel als een filter voor specifieke informatie uit Windows-gebeurtenislogboeken. Maakt gebruik van een hash-tabel **sleutel/waarde** paren. Zie voor meer informatie over hashtabellen [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).

Als de **sleutel/waarde** paren zijn op dezelfde regel, ze moeten worden gescheiden door puntkomma's. Als elke **sleutel/waarde** paar is op een afzonderlijke regel, de puntkomma is niet nodig. Bijvoorbeeld: in dit artikel wordt geplaatst **sleutel/waarde** paren op afzonderlijke regels en geen gebruik maakt van puntkomma's.

In dit voorbeeld maakt gebruik van verschillende van de **FilterHashtable** van de parameter **sleutel/waarde** paren. De voltooide query bevat **logboeknaam**, **ProviderName**, **trefwoorden**, **ID**, en **niveau**.

De geaccepteerde **sleutel/waarde** paren in de volgende tabel worden weergegeven en worden opgenomen in de documentatie voor de [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** de parameter.

De volgende tabel bevat de namen van sleutels, gegevenstypen, en of de jokertekens voor een gegevenswaarde worden geaccepteerd.

| Sleutelnaam     | Gegevenstype    | Jokertekens accepteren? |
|------------- | ------------------ | ---------------------------- |
| LogName      | `<String[]>`       | Ja |
| ProviderName | `<String[]>`       | Ja |
| Pad         | `<String[]>`       | Nee  |
| Trefwoorden     | `<Long[]>`         | Nee  |
| ID           | `<Int32[]>`        | Nee  |
| Niveau        | `<Int32[]>`        | Nee  |
| StartTime    | `<DateTime>`       | Nee  |
| EndTime      | `<DateTime>`       | Nee  |
| Gebruikers-id       | `<SID>`            | Nee  |
| Gegevens         | `<String[]>`       | Nee  |
| *            | `<String[]>`       | Nee  |

## <a name="building-a-query-with-a-hash-table"></a>Het bouwen van een query met een hash-tabel

Resultaten controleren en problemen oplossen, is het handig om het bouwen van de hash-tabel een **sleutel/waarde** paar op een tijdstip. De query haalt gegevens uit de **toepassing** log. De hash-tabel is gelijk aan `Get-WinEvent –LogName Application`.

Als u wilt, maakt de `Get-WinEvent` query. Gebruik de **FilterHashtable** van de parameter **sleutel/waarde** koppelen aan de sleutel **logboeknaam**, en de waarde **toepassing**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

Doorgaan met het bouwen van de hash-tabel met de **ProviderName** sleutel. De **ProviderName** is de naam die wordt weergegeven in de **bron** veld in de **Windows logboeken**. Bijvoorbeeld, **.NET Runtime** in de volgende schermafbeelding:

![Afbeelding van Logboeken van Windows-bronnen.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

De hash-tabel bijwerken en bevatten de **sleutel/waarde** koppelen aan de sleutel ** ProviderName, en de waarde **.NET Runtime**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

Als de query gegevens ophalen uit de gearchiveerde gebeurtenislogboeken moet, gebruikt u de **pad** sleutel. De **pad** waarde geeft het volledige pad naar het logboekbestand. Zie voor meer informatie de **Scripting Guy** blogbericht, [Gebruik PowerShell om te parseren opgeslagen gebeurtenislogboeken voor fouten](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).

## <a name="using-enumerated-values-in-a-hash-table"></a>Met behulp van de opsommingswaarden zijn in een hash-tabel

**Trefwoorden** is de volgende sleutel in de hash-tabel. De **trefwoorden** gegevenstype is een matrix met de `[long]` waardetype die een groot aantal bevat. Gebruik de volgende opdracht te vinden van de maximale waarde van `[long]`:

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

Voor de **trefwoorden** sleutel, PowerShell maakt gebruik van een getal, niet een tekenreeks, zoals **Security**. **Windows-logboeken** geeft de **trefwoorden** als tekenreeksen, maar ze zijn opsommingswaarden zijn. In de hashtabel, als u de **trefwoorden** sleutel met een string-waarde, een foutbericht wordt weergegeven.

Open de **Windows logboeken** en van de **acties** deelvenster, klikt u op **Huidig logboek filteren**.
De **trefwoorden** vervolgkeuzelijst geeft de beschikbare trefwoorden, zoals wordt weergegeven in de volgende schermafbeelding:

![Afbeelding van Windows-Logboeken trefwoorden.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

Gebruik de volgende opdracht om weer te geven de `StandardEventKeywords` namen van eigenschappen.

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

De opsommingswaarden worden beschreven in de **.NET Framework**. Zie voor meer informatie, [StandardEventKeywords opsomming](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).

De **trefwoorden** namen en opsommingswaarden zijn als volgt:

| Naam             |  Waarde            |
| ---------------- | ------------------|
| AuditFailure     | 4503599627370496  |
| AuditSuccess     | 9007199254740992  |
| CorrelationHint2 | 18014398509481984 |
| EventLogClassic  | 36028797018963968 |
| Sqm              | 2251799813685248  |
| WdiDiagnostic    | 1125899906842624  |
| WdiContext       | 562949953421312   |
| ResponseTime     | 281474976710656   |
| Geen             | 0                 |

De hash-tabel bijwerken en bevatten de **sleutel/waarde** koppelen aan de sleutel **trefwoorden**, en de **EventLogClassic** -opsommingswaarde, **36028797018963968** .

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a>Trefwoorden statische eigenschapswaarde (optioneel)

De **trefwoorden** sleutel wordt opgesomd, maar kunt u de naam van een statische eigenschap in de query van hash-tabel.
In plaats van de tekenreeks wordt geretourneerd, de eigenschapsnaam moet worden geconverteerd naar een waarde met de **Value__** eigenschap.

Bijvoorbeeld, het volgende script maakt gebruik van de **Value__** eigenschap.

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a>Filteren op gebeurtenis-Id

Als u gedetailleerdere gegevens, van de query resultaten worden gefilterd op **gebeurtenis-Id**. De **gebeurtenis-Id** wordt verwezen in de hash-tabel als de sleutel **ID** en de waarde is een specifieke **gebeurtenis-Id**. De **Windows logboeken** geeft de **gebeurtenis-Id**. In dit voorbeeld wordt **gebeurtenis-Id 1023**.

De hash-tabel bijwerken en bevatten de **sleutel/waarde** koppelen aan de sleutel **ID** en de waarde **1023**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a>Filteren op niveau

Om verder te verfijnen van de resultaten en alleen de gebeurtenissen die fouten bevatten, gebruikt u de **niveau** sleutel.
**Windows-logboeken** geeft de **niveau** als tekenreekswaarden, maar ze zijn opsommingswaarden zijn. In de hashtabel, als u de **niveau** sleutel met een string-waarde, een foutbericht wordt weergegeven.

**Niveau** heeft waarden zoals **fout**, **waarschuwing**, of **ter informatie**. Gebruik de volgende opdracht om weer te geven de `StandardEventLevel` namen van eigenschappen.

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

De opsommingswaarden worden beschreven in de **.NET Framework**. Zie voor meer informatie, [StandardEventLevel opsomming](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).

De **niveau** de namen van de sleutel en de opsommingswaarden zijn als volgt:

| Naam           | Waarde |
| -------------- | ----- |
| Verbose        |   5   |
| Ter informatie  |   4   |
| Waarschuwing        |   3   |
| Fout          |   2   |
| Kritieke       |   1   |
| LogAlways      |   0   |

De hashtabel voor de voltooide query bevat de sleutel **niveau**, en de waarde **2**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a>Statische eigenschap in de opsomming is (optioneel)

De **niveau** sleutel wordt opgesomd, maar kunt u de naam van een statische eigenschap in de query van hash-tabel.
In plaats van de tekenreeks wordt geretourneerd, de eigenschapsnaam moet worden geconverteerd naar een waarde met de **Value__** eigenschap.

Bijvoorbeeld, het volgende script maakt gebruik van de **Value__** eigenschap.

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