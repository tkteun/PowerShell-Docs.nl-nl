---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/group-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Group-Object
ms.openlocfilehash: aa97115217be5363e2f81e87c4d6ce7e03c453a4
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251752"
---
# Group-Object

## SAMENVATTING
Groeps objecten die dezelfde waarde voor opgegeven eigenschappen bevatten.

## SYNTAXIS

### Hashtabel

```
Group-Object [-NoElement] [-AsHashTable] [-AsString] [-InputObject <PSObject>]
 [[-Property] <Object[]>] [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## BESCHRIJVING

De `Group-Object` cmdlet geeft objecten weer in groepen op basis van de waarde van een opgegeven eigenschap.
`Group-Object` retourneert een tabel met één rij voor elke eigenschaps waarde en een kolom waarin het aantal items met die waarde wordt weer gegeven.

Als u meer dan één eigenschap opgeeft, worden `Group-Object` deze eerst gegroepeerd op de waarden van de eerste eigenschap en vervolgens in elke eigenschappen groep, die wordt gegroepeerd op de waarde van de volgende eigenschap.

Vanaf Power shell 7 `Group-Object` kunnen de para meters **CaseSensitive** en **AsHashtable** combi neren om een hoofdletter gevoelige hash-tabel te maken. De hash-tabel sleutels gebruiken hoofdletter gevoelige vergelijkingen en voeren een **System. Collections. Hashtable** -object uit.

## VOORBEELDEN

### Voor beeld 1: bestanden groeperen op extensie

In dit voor beeld worden de bestanden op basis `$PSHOME` van de bestandsnaam extensie recursief opgehaald en gegroepeerd. De uitvoer wordt verzonden naar de `Sort-Object` cmdlet, die deze sorteert op het aantal bestanden dat is gevonden voor de opgegeven extensie. De lege **naam** vertegenwoordigt directory's.

In dit voor beeld wordt de para meter **element** niet gebruikt om de leden van de groep weg te laten.

```powershell
$files = Get-ChildItem -Path $PSHOME -Recurse
$files | Group-Object -Property extension -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  365 .xml
  231 .cdxml
  197
  169 .ps1xml
  142 .txt
  114 .psd1
   63 .psm1
   49 .xsd
   36 .dll
   15 .mfl
   15 .mof
...
```

### Voor beeld 2: gehele getallen groeperen op conflicteert en zelfs

In dit voor beeld ziet u hoe u script blokken gebruikt als de waarde van de **eigenschaps** parameter. Met deze opdracht worden de gehele getallen van 1 tot en met 20, gegroepeerd op conflicteert en zelfs weer gegeven.

```powershell
1..20 | Group-Object -Property {$_ % 2}
```

```Output
Count Name                      Group
----- ----                      -----
   10 0                         {2, 4, 6, 8...}
   10 1                         {1, 3, 5, 7...}
```

### Voor beeld 3: gebeurtenissen in gebeurtenis logboeken groeperen op entry type is

In dit voor beeld worden de 1.000 meest recente vermeldingen in het systeem gebeurtenis logboek weer gegeven, gegroepeerd op **entry type is**.

In de uitvoer staat de kolom **aantal** voor het aantal items in elke groep. De kolom **naam** vertegenwoordigt de waarden van het type **Event** waarmee een groep wordt gedefinieerd. De kolom **groep** vertegenwoordigt de objecten in elke groep.

```powershell
Get-WinEvent -LogName System -MaxEvents 1000 | Group-Object -Property LevelDisplayName
```

```Output
Count Name          Group
----- ----          -----
  153 Error         {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  722 Information   {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  125 Warning       {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
```

### Voor beeld 4: groeps processen op prioriteits klasse

In dit voor beeld ziet u het effect van de para meter **element** . Met deze opdrachten worden de processen op de computer gegroepeerd op prioriteits klasse.

Met de eerste opdracht wordt de- `Get-Process` cmdlet gebruikt om de processen op de computer op te halen en de objecten naar de pijp lijn te verzenden. `Group-Object`groepeert de objecten op de waarde van de eigenschap **PriorityClass** van het proces.

In het tweede voor beeld wordt de para meter **element** niet gebruikt om de leden van de groep uit de uitvoer te verwijderen. Het resultaat is een tabel met alleen de waarde van de eigenschap **Count** en **name** .

De resultaten worden weer gegeven in de volgende voorbeeld uitvoer.

```powershell
Get-Process | Group-Object -Property PriorityClass
```

```Output
Count Name         Group
----- ----         -----
   55 Normal       {System.Diagnostics.Process (AdtAgent), System.Diagnosti...
    1              {System.Diagnostics.Process (Idle)}
    3 High         {System.Diagnostics.Process (Newproc), System.Diagnostic...
    2 BelowNormal  {System.Diagnostics.Process (winperf),
```

```powershell
Get-Process | Group-Object -Property PriorityClass -NoElement
```

```Output
Count Name
----- ----
   55 Normal
    1
    3 High
    2 BelowNormal
```

### Voor beeld 5: processen groeperen op naam

In het volgende voor beeld wordt gebruikgemaakt `Group-Object` van het groeperen van meerdere exemplaren van processen die op de lokale computer worden uitgevoerd. `Where-Object` Hiermee worden processen met meer dan één exemplaar weer gegeven.

```powershell
Get-Process | Group-Object -Property Name -NoElement | Where-Object {$_.Count -gt 1}
```

```Output
Count Name
----- ----
2     csrss
5     svchost
2     winlogon
2     wmiprvse
```

### Voor beeld 6: objecten groeperen in een hash-tabel

In dit voor beeld worden de para meters **AsHashTable** en **AsString** gebruikt voor het retour neren van de groepen in een hash-tabel, als een verzameling sleutel-waardeparen.

In de resulterende hash-tabel is elke eigenschaps waarde een sleutel en de groeps elementen zijn de waarden.
Omdat elke sleutel een eigenschap van het object van een hash-tabel is, kunt u de teken punt notatie gebruiken om de waarden weer te geven.

Met de eerste opdracht `Get` worden de `Set` -en-cmdlets in de sessie opgehaald, gegroepeerd op werk woord, worden de groepen geretourneerd als een hash-tabel en wordt de hash-tabel in de `$A` variabele opgeslagen.

Met de tweede opdracht wordt de hash-tabel in weer gegeven `$A` . Er zijn twee sleutel-waardeparen, een voor de `Get` cmdlets en één voor de `Set` cmdlets.

De derde opdracht maakt gebruik van punt notatie `$A.Get` om de waarden van de **Get** -toets in weer te geven `$A` . De waarden zijn **CmdletInfo** -object. Met de para meter **AsString** worden de objecten in de groepen niet geconverteerd naar teken reeksen.

```powershell
$A = Get-Command Get-*, Set-* -CommandType cmdlet | Group-Object -Property Verb -AsHashTable -AsString
$A
```

```Output
Name     Value
----     -----
Get      {Get-Acl, Get-Alias, Get-AppLockerFileInformation, Get-AppLockerPolicy...}
Set      {Set-Acl, Set-Alias, Set-AppBackgroundTaskResourcePolicy, Set-AppLockerPolicy...}
```

```powershell
$A.Get
```

```Output
CommandType     Name                                Version    Source
-----------     ----                                -------    ------
Cmdlet          Get-Acl                             7.0.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-Alias                           7.0.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-AppLockerFileInformation        2.0.0.0    AppLocker
Cmdlet          Get-AppLockerPolicy                 2.0.0.0    AppLocker
...
```

### Voor beeld 7: een hoofdletter gevoelige hash-tabel maken

In dit voor beeld worden de para meters **CaseSensitive** en **AsHashTable** gecombineerd om een hoofdletter gevoelige hash-tabel te maken. De bestanden in het voor beeld hebben uitbrei dingen van `.txt` en `.TXT` .

```powershell
$hash = Get-ChildItem -Path C:\Files | Group-Object -Property Extension -CaseSensitive -AsHashTable
$hash
```

```Output
Name           Value
----           -----
.TXT           {C:\Files\File7.TXT, C:\Files\File8.TXT, C:\Files\File9.TXT}
.txt           {C:\Files\file1.txt, C:\Files\file2.txt, C:\Files\file3.txt}
```

De `$hash` variabele slaat het object **System. Collections. hashtabel** op. `Get-ChildItem` Hiermee worden de bestands namen opgehaald uit de `C:\Files` Directory en worden de **System. io. file info** -objecten omlaag in de pijp lijn verzonden. `Group-Object`de objecten worden gegroepeerd met de **extensie** van de **eigenschaps** waarde. De para meters **CaseSensitive** en **AsHashTable** maken de tabel hash en de sleutels worden gegroepeerd met behulp van hoofdletter gevoelige sleutels `.txt` en `.TXT` .

## PARAMETERS

### -AsHashTable

Geeft aan dat deze cmdlet de groep als een hash-tabel retourneert. De sleutels van de hash-tabel zijn de eigenschapwaarden waarmee de objecten worden gegroepeerd. De waarden van de hash-tabel zijn de objecten met die eigenschaps waarde.

De **AsHashTable** -para meter retourneert elke hash-tabel waarin elke sleutel een exemplaar van het gegroepeerde object is. In combi natie met de para meter **AsString** zijn de sleutels in de hash-tabel teken reeksen.

Vanaf Power shell 7, voor het maken van hoofdletter gevoelige hash-tabellen, neemt u **CaseSensitive** en **AsHashtable** op in de opdracht.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: AHT

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsString

Geeft aan dat met deze cmdlet de hash-tabel sleutels naar teken reeksen worden geconverteerd. De hash-tabel sleutels zijn standaard instanties van het gegroepeerde object. Deze para meter is alleen geldig in combi natie met de para meter **AsHashTable** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -CaseSensitive

Geeft aan dat met deze cmdlet de groepering hoofdletter gevoelig wordt gemaakt. Zonder deze para meter kunnen de eigenschaps waarden van objecten in een groep verschillende cases hebben.

Vanaf Power shell 7, voor het maken van hoofdletter gevoelige hash-tabellen, neemt u **CaseSensitive** en **AsHashtable** op in de opdracht.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Cultuur

Hiermee geeft u de cultuur op die moet worden gebruikt bij het vergelijken van teken reeksen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Geeft aan welke objecten moeten worden gegroepeerd. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

Wanneer u de para meter **input object** gebruikt voor het verzenden van een verzameling objecten naar `Group-Object` , ontvangt u `Group-Object` één object dat de verzameling vertegenwoordigt. Als gevolg hiervan wordt een afzonderlijke groep met dat object gemaakt als lid.

Als u de objecten in een verzameling wilt groeperen, pipet u de objecten naar `Group-Object` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Element

Geeft aan dat met deze cmdlet de leden van een groep uit de resultaten worden wegge laten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Eigenschap

Hiermee geeft u de eigenschappen voor groeperen op. De objecten worden ingedeeld in groepen op basis van de waarde van de opgegeven eigenschap.

De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn. De berekende eigenschap kan een script blok of een hash-tabel zijn. Geldige sleutel-waardeparen zijn:

- Expressie- `<string>` of `<script block>`

Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt elk object door sluizen naar `Group-Object` .

## UITVOER

### Micro soft. Power shell. commands. GroupInfo of System. Collections. hashtabel

Wanneer u de para meter **AsHashTable** gebruikt, `Group-Object` wordt een **Hashtable** -object geretourneerd.
Anders wordt een **GroupInfo** -object geretourneerd.

## OPMERKINGEN

U kunt de para meter **GroupBy** van de Format-cmdlets, zoals `Format-Table` en `Format-List` , gebruiken voor het groeperen van objecten. In tegens telling tot `Group-Object` , waarmee een enkele tabel wordt gemaakt met een rij voor elke eigenschaps waarde, maken de para meter **GroupBy** een tabel voor elke eigenschaps waarde met een rij voor elk item met de waarde van de eigenschap.

`Group-Object` vereist niet dat de objecten die worden gegroepeerd hetzelfde Microsoft .NET-kern type hebben. Bij het groeperen van objecten van verschillende .NET-kern typen, `Group-Object` worden de volgende regels gebruikt:

- Dezelfde eigenschapnamen en typen.

  Als de objecten een eigenschap hebben met de opgegeven naam en de eigenschaps waarden hetzelfde .NET core-type hebben, worden de eigenschaps waarden gegroepeerd met dezelfde regels die zouden worden gebruikt voor objecten van hetzelfde type.

- Dezelfde eigenschapnamen, verschillende typen.

  Als de objecten een eigenschap hebben met de opgegeven naam, maar de eigenschaps waarden een ander .NET-kern type hebben in verschillende objecten, `Group-Object` gebruikt het .net-kern type van het eerste exemplaar van de eigenschap als .net-kern type voor die eigenschaps groep. Wanneer een object een eigenschap heeft met een ander type, wordt de waarde van de eigenschap geconverteerd naar het type voor die groep. Als het type conversie mislukt, is het object niet opgenomen in de groep.

- Eigenschappen ontbreken.

  Objecten waarvoor geen eigenschap is opgegeven, kunnen niet worden gegroepeerd. Objecten die niet zijn gegroepeerd, worden weer gegeven in de uiteindelijke uitvoer van de **GroupInfo** -objecten in een groep met de naam `AutomationNull.Value` .

## GERELATEERDE KOPPELINGEN

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[Compare-object](Compare-Object.md)

[ForEach-object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Meting object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sorteer object](Sort-Object.md)

[T-object](Tee-Object.md)

[Where-object](../Microsoft.PowerShell.Core/Where-Object.md)
