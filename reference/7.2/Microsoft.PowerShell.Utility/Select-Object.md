---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Object
ms.openlocfilehash: 80882d27c9c8fa2d7f9e1c8ca00a02cf73ae94e6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704751"
---
# Select-Object

## SAMENVATTING
Objecten of object eigenschappen selecteren.

## SYNTAXIS

### DefaultParameter (standaard)

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-Last <Int32>] [-First <Int32>] [-Skip <Int32>] [-Wait]
 [<CommonParameters>]
```

### SkipLastParameter

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-SkipLast <Int32>] [<CommonParameters>]
```

### IndexParameter

```
Select-Object [-InputObject <PSObject>] [-Unique] [-Wait] [-Index <Int32[]>] [<CommonParameters>]
```

### SkipIndexParameter

```
Select-Object [-InputObject <PSObject>] [-Unique] [-SkipIndex <Int32[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `Select-Object` cmdlet selecteert opgegeven eigenschappen van een object of set met objecten. Het kan ook unieke objecten, een opgegeven aantal objecten of objecten in een opgegeven positie in een matrix selecteren.

Als u objecten uit een verzameling wilt selecteren, gebruikt u de para meters **eerste**, **laatste**, **uniek**, **overs Laan** en **index** . Als u object eigenschappen wilt selecteren, gebruikt u de para meter **Property** . Wanneer u eigenschappen selecteert, `Select-Object` retourneert nieuwe objecten die alleen de opgegeven eigenschappen hebben.

Vanaf Windows Power Shell 3,0 `Select-Object` bevat een optimalisatie functie waarmee wordt voor komen dat opdrachten objecten maken en verwerken die niet worden gebruikt.

Wanneer u een opdracht opneemt `Select-Object` met de **eerste** of **index** parameters in een opdracht pijplijn, stopt Power shell de opdracht waarmee de objecten worden gegenereerd zodra het geselecteerde aantal objecten wordt gegenereerd, zelfs wanneer de opdracht die de objecten genereert, wordt weer gegeven voor de `Select-Object` opdracht in de pijp lijn. Als u dit optimalisatie gedrag wilt uitschakelen, gebruikt u de para meter **wait** .

## VOORBEELDEN

### Voor beeld 1: objecten op eigenschap selecteren

In dit voor beeld worden objecten gemaakt met de eigenschappen **name**, **id** en Working set (**WS**) van Process-objecten.

```powershell
Get-Process | Select-Object -Property ProcessName, Id, WS
```

### Voor beeld 2: objecten selecteren op eigenschap en de resultaten opmaken

In dit voor beeld wordt informatie opgehaald over de modules die worden gebruikt door de processen op de computer. De functie `Get-Process` cmdlet wordt gebruikt om het proces op de computer op te halen.

De cmdlet wordt gebruikt `Select-Object` om een matrix van exemplaren uit te voeren `[System.Diagnostics.ProcessModule]` , zoals opgenomen in de eigenschap **modules** van elk exemplaar dat `System.Diagnostics.Process` door wordt uitgevoerd `Get-Process` .

De **eigenschap** para meter van de `Select-Object` cmdlet selecteert de proces namen. Hiermee wordt een `ProcessName` **NoteProperty** toegevoegd aan elk `[System.Diagnostics.ProcessModule]` exemplaar en gevuld met de waarde van de eigenschap **proces** naam van het huidige proces.

Ten slotte `Format-List` wordt de cmdlet gebruikt om de naam en modules van elk proces in een lijst weer te geven.

```powershell
Get-Process Explorer | Select-Object -Property ProcessName -ExpandProperty Modules | Format-List
```

```Output
ProcessName       : explorer
ModuleName        : explorer.exe
FileName          : C:\WINDOWS\explorer.exe
BaseAddress       : 140697278152704
ModuleMemorySize  : 3919872
EntryPointAddress : 140697278841168
FileVersionInfo   : File:             C:\WINDOWS\explorer.exe
                    InternalName:     explorer
                    OriginalFilename: EXPLORER.EXE.MUI
                    FileVersion:      10.0.17134.1 (WinBuild.160101.0800)
                    FileDescription:  Windows Explorer
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.17134.1
...
```

### Voor beeld 3: processen selecteren met het meeste geheugen

In dit voor beeld worden de vijf processen opgehaald die het meeste geheugen gebruiken. De `Get-Process` cmdlet haalt de processen op de computer op. Met de `Sort-Object` cmdlet worden de processen gesorteerd op basis van het gebruik van geheugen (werkset) en de `Select-Object` cmdlet selecteert alleen de laatste vijf leden van de resulterende matrix met objecten.

De **wait** -para meter is niet vereist in opdrachten die de `Sort-Object` cmdlet bevatten `Sort-Object` , omdat alle objecten worden verwerkt en vervolgens een verzameling wordt geretourneerd. De `Select-Object` optimalisatie is alleen beschikbaar voor opdrachten die objecten afzonderlijk retour neren wanneer ze worden verwerkt.

```powershell
Get-Process | Sort-Object -Property WS | Select-Object -Last 5
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VS(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
2866     320       33432      45764   203   222.41   1292 svchost
577      17        23676      50516   265    50.58   4388 WINWORD
826      11        75448      76712   188    19.77   3780 Ps
1367     14        73152      88736   216    61.69    676 Ps
1612     44        66080      92780   380   900.59   6132 INFOPATH
```

### Voor beeld 4: unieke tekens uit een matrix selecteren

In dit voor beeld wordt de **unieke** para meter van gebruikt `Select-Object` om unieke tekens uit een matrix met tekens op te halen.

```powershell
"a","b","c","a","a","a" | Select-Object -Unique
```

```Output
a
b
c
```

### Voor beeld 5: de nieuwste en oudste gebeurtenissen in het gebeurtenis logboek selecteren

In dit voor beeld worden de eerste (nieuwste) en laatste (oudste) gebeurtenissen in het Windows Power shell-gebeurtenis logboek opgehaald.

`Get-EventLog` Hiermee worden alle gebeurtenissen in het Windows Power shell-logboek opgehaald en opgeslagen in de `$a` variabele.
Vervolgens wordt door gegeven `$a` aan de `Select-Object` cmdlet. De `Select-Object` opdracht gebruikt de para meter **index** om gebeurtenissen te selecteren uit de matrix met gebeurtenissen in de `$a` variabele. De index van de eerste gebeurtenis is 0. De index van de laatste gebeurtenis is het aantal items in `$a` min 1.

```powershell
$a = Get-EventLog -LogName "Windows PowerShell"
$a | Select-Object -Index 0, ($A.count - 1)
```

### Voor beeld 6: Alles selecteren, behalve het eerste object

In dit voor beeld wordt een nieuwe PSSession gemaakt op elke computer die wordt vermeld in de Servers.txt-bestanden, met uitzonde ring van de eerste.

`Select-Object` selecteert alle computers behalve de eerste computer in een lijst met computer namen. De resulterende lijst met computers wordt ingesteld als de waarde van de para meter **ComputerName** van de `New-PSSession` cmdlet.

```powershell
New-PSSession -ComputerName (Get-Content Servers.txt | Select-Object -Skip 1)
```

### Voor beeld 7: bestanden een andere naam geven en meerdere selecteren om weer te geven

In dit voor beeld wordt een "-ro"-achtervoegsel toegevoegd aan de basis namen van tekst bestanden met het kenmerk alleen-lezen en worden de eerste vijf bestanden weer gegeven, zodat de gebruiker een voor beeld van het effect kan zien.

`Get-ChildItem` maakt gebruik **van de alleen** -lezen dynamische para meter voor het ophalen van bestanden met het kenmerk alleen-laden De resulterende bestanden worden door gegeven aan de `Rename-Item` cmdlet, waarmee de naam van het bestand wordt gewijzigd. Hiermee wordt de para meter **PassThru** van verzonden voor het `Rename-Item` verzenden van de hernoemde bestanden naar de `Select-Object` cmdlet, waarmee de eerste 5 wordt geselecteerd voor weer gave.

De **wait** -para meter van `Select-Object` voor komt dat Power shell de `Get-ChildItem` cmdlet stopt nadat de eerste vijf tekst bestanden met het kenmerk alleen-lezen worden opgehaald. Zonder deze para meter worden alleen de eerste vijf alleen-lezen bestanden hernoemd.

```powershell
Get-ChildItem *.txt -ReadOnly |
    Rename-Item -NewName {$_.BaseName + "-ro.txt"} -PassThru |
    Select-Object -First 5 -Wait
```

### Voor beeld 8: Demonstreer de complexiteit van de para meter-ExpandProperty

In dit voor beeld wordt de complexiteit van de para meter **ExpandProperty** gedemonstreerd.

Houd er rekening mee dat de gegenereerde uitvoer een matrix van `[System.Int32]` exemplaren is. De exemplaren voldoen aan de standaard regels voor opmaak van de **uitvoer weergave**. Dit geldt voor alle *uitgevouwen* eigenschappen. Als de outputtende objecten een specifieke standaard indeling hebben, is de uitgebreide eigenschap mogelijk niet zichtbaar.

```powershell
# Create a custom object to use for the Select-Object example.
$object = [pscustomobject]@{Name="CustomObject";Expand=@(1,2,3,4,5)}
# Use the ExpandProperty parameter to Expand the property.
$object | Select-Object -ExpandProperty Expand -Property Name
```

```Output
1
2
3
4
5
```

```powershell
# The output did not contain the Name property, but it was added successfully.
# Use Get-Member to confirm the Name property was added and populated.
$object | Select-Object -ExpandProperty Expand -Property Name | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType   Definition
----        ----------   ----------
CompareTo   Method       int CompareTo(System.Object value), int CompareTo(int value), int IComparable.CompareTo(System.Object obj)...
Equals      Method       bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int].Equals(int other)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
GetTypeCode Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar      Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime  Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal   Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble    Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16     Method       int16 IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32     Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64     Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte     Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle    Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString    Method       string ToString(), string ToString(string format), string ToString(System.IFormatProvider provider)...
ToType      Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16    Method       uint16 IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32    Method       uint32 IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64    Method       uint64 IConvertible.ToUInt64(System.IFormatProvider provider)
Name        NoteProperty string Name=CustomObject
```

### Voor beeld 9: aangepaste eigenschappen maken voor objecten

In het volgende voor beeld ziet u hoe u `Select-Object` een aangepaste eigenschap aan een object kunt toevoegen.
Wanneer u een eigenschaps naam opgeeft die niet bestaat, `Select-Object` maakt deze eigenschap als een **NoteProperty** voor elk object dat wordt door gegeven.

```powershell
$customObject = 1 | Select-Object -Property MyCustomProperty
$customObject.MyCustomProperty = "New Custom Property"
$customObject
```

```Output
MyCustomProperty
----------------
New Custom Property
```

### Voor beeld 10: berekende eigenschappen maken voor elke input object

Dit voor beeld laat zien hoe u met behulp van `Select-Object` berekende eigenschappen aan uw invoer kunt toevoegen. Door een **script Block** door te geven aan de **eigenschaps parameter,** wordt `Select-Object` de expressie geëvalueerd op elk object dat is door gegeven en worden de resultaten aan de uitvoer toegevoegd. Binnen de **script Block** kunt u de variabele gebruiken `$_` om te verwijzen naar het huidige object in de pijp lijn.

`Select-Object`De **script Block** -teken reeks wordt standaard gebruikt als de naam van de eigenschap. Met behulp van een **hashtabel** kunt u de uitvoer van uw **script Block** labelen als een aangepaste eigenschap die aan elk object is toegevoegd. U kunt meerdere berekende eigenschappen toevoegen aan elk object dat wordt door gegeven aan `Select-Object` .

```powershell
# Create a calculated property called $_.StartTime.DayOfWeek
Get-Process | Select-Object -Property ProcessName,{$_.StartTime.DayOfWeek}
```

```Output
ProcessName  $_.StartTime.DayOfWeek
----         ----------------------
alg                       Wednesday
ati2evxx                  Wednesday
ati2evxx                   Thursday
...
```

```powershell
# Add a custom property to calculate the size in KiloBytes of each FileInfo object you pass in.
# Use the pipeline variable to divide each file's length by 1 KiloBytes
$size = @{label="Size(KB)";expression={$_.length/1KB}}
# Create an additional calculated property with the number of Days since the file was last accessed.
# You can also shorten the key names to be 'l', and 'e', or use Name instead of Label.
$days = @{l="Days";e={((Get-Date) - $_.LastAccessTime).Days}}
# You can also shorten the name of your label key to 'l' and your expression key to 'e'.
Get-ChildItem $PSHOME -File | Select-Object Name, $size, $days
```

```Output
Name                        Size(KB)        Days
----                        --------        ----
Certificate.format.ps1xml   12.5244140625   223
Diagnostics.Format.ps1xml   4.955078125     223
DotNetTypes.format.ps1xml   134.9833984375  223
```

## PARAMETERS

### -ExcludeProperty

Hiermee geeft u de eigenschappen op die met deze cmdlet worden uitgesloten van de bewerking. Joker tekens zijn toegestaan.

Vanaf Power shell 6 is het niet meer nodig om de para meter **Property** voor **ExcludeProperty** te gebruiken.

```yaml
Type: System.String[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ExpandProperty

Geeft een eigenschap aan die moet worden geselecteerd en geeft aan dat er een poging moet worden gedaan om die eigenschap uit te breiden.

- Als de opgegeven eigenschap een matrix is, wordt elke waarde van de matrix opgenomen in de uitvoer.
- Als de opgegeven eigenschap een object is, worden de eigenschappen van de objecten uitgebreid voor elke **input object**

In beide gevallen komt het **type** objecten uitvoer overeen met het **type** van de uitgevouwen eigenschap.

Als de **eigenschaps** parameter is opgegeven, `Select-Object` probeert elke geselecteerde eigenschap als een **NoteProperty** toe te voegen aan elk object dat wordt gegenereerd.

> [!WARNING]
> Als u de fout melding: Select: de eigenschap kan niet worden verwerkt omdat er al een eigenschap `<PropertyName>` bestaat, kunt u het volgende overwegen.
> Houd er rekening mee dat bij `-ExpandProperty` `Select-Object` het gebruik geen bestaande eigenschap kan worden vervangen.
> Dit betekent:
>
> - Als het uitgevouwen object een eigenschap met dezelfde naam heeft, treedt er een fout op.
> - Als het *geselecteerde* object een eigenschap heeft die dezelfde naam heeft als een *uitgebreide* objecten eigenschap, treedt er een fout op.

```yaml
Type: System.String
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Eerste

Hiermee wordt het aantal objecten aangegeven dat moet worden geselecteerd vanaf het begin van een matrix met invoer objecten.

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Index

Objecten uit een matrix selecteren op basis van de index waarden. Voer de indexen in een lijst met door komma's gescheiden waarden in. Indexen in een matrix beginnen met 0, waarbij 0 staat voor de eerste waarde en (n-1) de laatste waarde.

```yaml
Type: System.Int32[]
Parameter Sets: IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Geeft objecten aan die via de pijp lijn naar de cmdlet worden verzonden. Met deze para meter kunt u objecten pipet naar `Select-Object` .

Wanneer u objecten doorgeeft aan de para meter **input object** in plaats van de pijp lijn te gebruiken, `Select-Object` behandelt de **input object** als één object, zelfs als de waarde een verzameling is. Het is raadzaam om de pijp lijn te gebruiken bij het door geven van verzamelingen naar `Select-Object` .

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

### -Laatste

Hiermee wordt het aantal objecten aangegeven dat moet worden geselecteerd vanaf het einde van een matrix met invoer objecten.

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Eigenschap

Hiermee geeft u de eigenschappen te selecteren. Deze eigenschappen worden toegevoegd als **NoteProperty** -leden aan de uitvoer objecten. Joker tekens zijn toegestaan.

De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn. Gebruik een hash-tabel als u een berekende eigenschap wilt maken.

Geldige sleutels zijn:

- Naam (of label)- `<string>`
- Expressie- `<string>` of `<script block>`

Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.

```yaml
Type: System.Object[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Overs Laan

Hiermee wordt het opgegeven aantal items overgeslagen (niet geselecteerd). Standaard telt de para meter **overs Laan** van het begin van de matrix of lijst met objecten, maar als de opdracht de **laatste** para meter gebruikt, telt deze vanaf het einde van de lijst of matrix.

In tegens telling tot de **index** parameter, die begint met tellen bij 0, begint de para meter **overs Laan** om 1.

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipLast

Hiermee wordt het opgegeven aantal items vanaf het einde van de lijst of matrix overgeslagen (niet geselecteerd). Werkt op dezelfde manier als het gebruik van **overs Laan** samen met de **laatste** para meter.

In tegens telling tot de **index** parameter, die begint met tellen bij 0, begint de para meter **SkipLast** bij 1.

```yaml
Type: System.Int32
Parameter Sets: SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Uniek

Hiermee wordt aangegeven dat als een subset van de invoer objecten identieke eigenschappen en waarden heeft, er slechts één lid van de subset wordt geselecteerd.

Deze para meter is hoofdletter gevoelig. Als gevolg hiervan worden teken reeksen die alleen in Character-hoofdletter verschillen, als uniek beschouwd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wachten

Geeft aan dat de cmdlet optimalisatie uitschakelt. Power Shell voert opdrachten uit in de volg orde waarin ze worden weer gegeven in de opdracht pijp lijn en maken het mogelijk om alle objecten te genereren. Als u een opdracht opneemt `Select-Object` met de **eerste** of **index** parameters in een opdracht pijplijn, stopt Power shell de opdracht die de objecten genereert zodra het geselecteerde aantal objecten wordt gegenereerd.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultParameter, IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipIndex

```yaml
Type: System.Int32[]
Parameter Sets: SkipIndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt elk object door sluizen naar `Select-Object` .

## UITVOER

### System. Management. Automation. PSObject

## OPMERKINGEN

- U kunt ook naar de `Select-Object` cmdlet verwijzen met de ingebouwde alias `select` . Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.

- De optimalisatie functie van `Select-Object` is alleen beschikbaar voor opdrachten waarmee objecten naar de pijp lijn worden geschreven wanneer ze worden verwerkt. Dit heeft geen invloed op opdrachten die door buffer worden verwerkt en schrijf ze als een verzameling. Objecten direct schrijven is een best practice voor de cmdlet. Zie voor meer informatie _enkelvoudige records naar de pijp lijn schrijven_ in [sterk gestimuleerde ontwikkel richtlijnen](/powershell/scripting/developer/windows-powershell).

## GERELATEERDE KOPPELINGEN

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Groep-object](Group-Object.md)

[Sorteer object](Sort-Object.md)

[Where-object](../Microsoft.PowerShell.Core/Where-Object.md)
