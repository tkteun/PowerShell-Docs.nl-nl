---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-member?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Member
ms.openlocfilehash: f6cc98f31d42f3468fd864782fb7252b064302b8
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389467"
---
# Add-Member

## SAMENVATTING
Hiermee voegt u aangepaste eigenschappen en methoden toe aan een exemplaar van een Power shell-object.

## SYNTAXIS

### TypeNameset (standaard)

```
Add-Member -InputObject <PSObject> -TypeName <String> [-PassThru] [<CommonParameters>]
```

### NotePropertyMultiMemberSet

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru]
 [-NotePropertyMembers] <IDictionary> [<CommonParameters>]
```

### NotePropertySingleMemberSet

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru] [-NotePropertyName] <String>
 [-NotePropertyValue] <Object> [<CommonParameters>]
```

### Ledenset

```
Add-Member -InputObject <PSObject> [-MemberType] <PSMemberTypes> [-Name] <String> [[-Value] <Object>]
 [[-SecondValue] <Object>] [-TypeName <String>] [-Force] [-PassThru] [<CommonParameters>]
```

## BESCHRIJVING

`Add-Member`Met de cmdlet kunt u leden (eigenschappen en methoden) toevoegen aan een exemplaar van een Power shell-object. U kunt bijvoorbeeld een NoteProperty-lid toevoegen dat een beschrijving bevat van het object of een **ScriptMethod** -lid dat een script uitvoert om het object te wijzigen.

Als u het object wilt gebruiken `Add-Member` , pipet `Add-Member` of gebruikt u de para meter **input object** om het object op te geven.

De **member type** para meter geeft het type lid aan dat u wilt toevoegen. De para meter **name** wijst een naam toe aan het nieuwe lid en de para meter **Value** stelt de waarde van het lid in.

De eigenschappen en methoden die u toevoegt, worden alleen toegevoegd aan het specifieke exemplaar van het object dat u opgeeft. `Add-Member` wijzigt het object type niet. Als u een nieuw object type wilt maken, gebruikt u de `Add-Type` cmdlet.

U kunt ook de `Export-Clixml` -cmdlet gebruiken om het exemplaar van het object, met inbegrip van de extra leden, op te slaan in een bestand. Vervolgens kunt u de `Import-Clixml` cmdlet gebruiken om het exemplaar van het object opnieuw te maken op basis van de informatie die is opgeslagen in het geëxporteerde bestand.

Vanaf Windows Power Shell 3,0 `Add-Member` heeft nieuwe functies die het eenvoudiger maken om notitie-eigenschappen toe te voegen aan objecten.
U kunt de para meters **NotePropertyName** en **NotePropertyValue** gebruiken om een eigenschap Note te definiëren of de **NotePropertyMembers** -para meter, die een hash-tabel met notitie-eigenschaps namen en-waarden maakt.

Met ingang van Windows Power Shell 3,0, de para meter **PassThru** , waarmee een uitvoer object wordt gegenereerd, is ook minder vaak nodig. `Add-Member` voegt nu de nieuwe leden rechtstreeks toe aan het invoer object van meer typen. Zie de beschrijving van de **PassThru** -para meter voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: een notitie-eigenschap toevoegen aan een PSObject

In het volgende voor beeld wordt een **status** notitie-eigenschap met de waarde ' done ' toegevoegd aan het **file info** -object dat het `Test.txt` bestand vertegenwoordigt.

Met de eerste opdracht wordt de `Get-ChildItem` cmdlet gebruikt voor het ophalen van een **file info** -object dat het `Test.txt` bestand vertegenwoordigt. Het wordt opgeslagen in de `$a` variabele.

Met de tweede opdracht wordt de eigenschap Note aan het object toegevoegd in `$a` .

De derde opdracht maakt gebruik van punt notatie om de waarde van de eigenschap **status** van het object in op te halen `$a` . Zoals in de uitvoer wordt weer gegeven, is de waarde gereed.

```powershell
$A = Get-ChildItem c:\ps-test\test.txt
$A | Add-Member -NotePropertyName Status -NotePropertyValue Done
$A.Status
```

```Output
Done
```

### Voor beeld 2: een alias eigenschap toevoegen aan een PSObject

In het volgende voor beeld wordt een eigenschap voor **grootte** alias toegevoegd aan het object dat het `Test.txt` bestand vertegenwoordigt. De eigenschap New is een alias voor de eigenschap **Length** .

De eerste opdracht gebruikt de `Get-ChildItem` cmdlet om het file info-object op te halen `Test.txt` **FileInfo** .

Met de tweede opdracht wordt de eigenschap alias **grootte** toegevoegd.
De derde opdracht maakt gebruik van punt notatie om de waarde van de eigenschap nieuwe **grootte** op te halen.

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$A | Add-Member -MemberType AliasProperty -Name Size -Value Length
$A.Size
```

```Output
2394
```

### Voor beeld 3: een StringUse Note-eigenschap toevoegen aan een teken reeks

In dit voor beeld wordt de eigenschap **StringUse** Note toegevoegd aan een teken reeks.
Omdat `Add-Member` typen niet kunnen worden toegevoegd aan invoer objecten voor **teken reeksen** , kunt u de para meter **PassThru** opgeven om een uitvoer object te genereren. Met de laatste opdracht in het voor beeld wordt de nieuwe eigenschap weer gegeven.

In dit voor beeld wordt de para meter **NotePropertyMembers** gebruikt. De waarde van de para meter **NotePropertyMembers** is een hash-tabel. De sleutel is de eigenschaps naam van de notitie, **StringUse** en de waarde is de eigenschap waarde van de notitie, **weer geven**.

```powershell
$A = "A string"
$A = $A | Add-Member -NotePropertyMembers @{StringUse="Display"} -PassThru
$A.StringUse
```

```Output
Display
```

### Voor beeld 4: een script methode toevoegen aan een file info-object

In dit voor beeld wordt de methode **sizeinmb kleiner** toegevoegd aan een **file info** -object dat de bestands grootte in de dichtstbijzijnde Mega byte berekent. Met de tweede opdracht maakt u een **script Block** die gebruikmaakt van de **ronde** statische methode van het `[math]` type om de bestands grootte af te ronden op de tweede decimaal positie.

De **waarde** para meter gebruikt ook de `$This` Automatische variabele, die het huidige object vertegenwoordigt. De `$This` variabele is alleen geldig in script blokken waarmee nieuwe eigenschappen en methoden worden gedefinieerd.

De laatste opdracht maakt gebruik van punt notatie voor het aanroepen van de nieuwe **sizeinmb kleiner** -script methode voor het object in de `$A` variabele.

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$S = {[math]::Round(($this.Length / 1MB), 2)}
$A | Add-Member -MemberType ScriptMethod -Name "SizeInMB" -Value $S
$A.SizeInMB()
```

```Output
0.43
```

### Voor beeld 5: alle eigenschappen van een object naar een ander kopiëren

Deze functie kopieert alle eigenschappen van een object naar een ander object.

De `foreach` lus gebruikt de `Get-Member` cmdlet om alle eigenschappen van het **from** -object op te halen. De opdrachten binnen de `foreach` lus worden uitgevoerd in reeksen op elk van de eigenschappen.

De `Add-Member` opdracht wordt de eigenschap van het object **from** aan het object **aan** toegevoegd als **een NoteProperty**. De waarde wordt gekopieerd met behulp van de **waarde** -para meter. De para meter **Force** wordt gebruikt om leden met dezelfde lidnaam toe te voegen.

```powershell
function Copy-Property ($From, $To)
{
    $properties = Get-Member -InputObject $From -MemberType Property
    foreach ($p in $properties)
    {
        $To | Add-Member -MemberType NoteProperty -Name $p.Name -Value $From.$($p.Name) -Force
    }
}
```

### Voor beeld 6: een aangepast object maken

In dit voor beeld wordt een aangepast **activa** object gemaakt.

Met de `New-Object` cmdlet maakt u een **PSObject**. In het voor beeld wordt de **PSObject** in de `$Asset` variabele opgeslagen.

Met de tweede opdracht wordt de `[ordered]` type Accelerator gebruikt voor het maken van een geordende woorden lijst met namen en waarden. De opdracht slaat het resultaat op in de `$D` variabele.

De derde opdracht maakt gebruik van de para meter **NotePropertyMembers** van de `Add-Member` cmdlet om de woorden lijst in de variabele toe te voegen `$D` aan de **PSObject**.
De eigenschap **TypeName** wijst een nieuwe naam, **activa** , toe aan de **PSObject**.

De laatste opdracht sluizen het nieuwe **Asset** -object naar de `Get-Member` cmdlet. In de uitvoer ziet u dat het object de type naam **Asset** heeft en de notitie-eigenschappen die we in de geordende woorden lijst hebben gedefinieerd.

```powershell
$Asset = New-Object -TypeName PSObject
$d = [ordered]@{Name="Server30";System="Server Core";PSVersion="4.0"}
$Asset | Add-Member -NotePropertyMembers $d -TypeName Asset
$Asset | Get-Member
```

```Output
   TypeName: Asset

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty System.String Name=Server30
PSVersion   NoteProperty System.String PSVersion=4.0
System      NoteProperty System.String System=Server Core
```

## PARAMETERS

### -Force

Geeft aan dat deze cmdlet een nieuw lid toevoegt, zelfs het object heeft een aangepast lid met dezelfde naam.
U kunt de para meter **Force** niet gebruiken om een standaard lid van een type te vervangen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MemberSet, NotePropertySingleMemberSet, NotePropertyMultiMemberSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u het object waaraan het nieuwe lid wordt toegevoegd.
Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Member type

Hiermee geeft u het type lid dat moet worden toegevoegd.
Deze parameter is vereist.
De aanvaardbare waarden voor deze parameter zijn:

- NoteProperty
- AliasProperty
- ScriptProperty
- CodeProperty
- ScriptMethod
- CodeMethod

Zie [PSMemberTypes-inventarisatie](/dotnet/api/system.management.automation.psmembertypes) in de Power shell-SDK voor meer informatie over deze waarden.

Niet alle objecten hebben elk type lid.
Als u een lidtype opgeeft dat het object niet heeft, retourneert Power shell een fout.

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: MemberSet
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de naam van het lid dat met deze cmdlet wordt toegevoegd.

```yaml
Type: System.String
Parameter Sets: MemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotePropertyMembers

Hiermee geeft u een hash-tabel of een geordende woorden lijst met namen en waarden van notitie-eigenschappen.
Typ een hash-tabel of-woorden lijst waarin de sleutels namen van notitie-eigenschappen zijn en de waarden zijn eigenschaps waarden van notities.

Zie [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)voor meer informatie over hash-tabellen en geordende woorden lijsten in Power shell.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: NotePropertyMultiMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotePropertyName

Hiermee geeft u de naam van de notitie-eigenschap.

Gebruik deze para meter met de para meter **NotePropertyValue** .
Deze parameter is optioneel.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotePropertyValue

Geeft de waarde van de eigenschap Note aan.

Gebruik deze para meter met de para meter **NotePropertyName** .
Deze parameter is optioneel.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Object
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourneert een object dat het item vertegenwoordigt waarmee u werkt.
Deze cmdlet genereert standaard geen uitvoer.

Voor de meeste objecten `Add-Member` voegt de nieuwe leden toe aan het invoer object.
Wanneer het invoer object echter een teken reeks is, `Add-Member` kan het lid niet toevoegen aan het invoer object.
Voor deze objecten gebruikt u de para meter **PassThru** om een uitvoer object te maken.

In Windows Power Shell 2,0 worden `Add-Member` leden alleen toegevoegd aan de **PSObject** -wrapper van objecten, niet aan het object.
Gebruik de para meter **PassThru** om een uitvoer object te maken voor een object met een **PSObject** -wrapper.

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

### -SecondValue

Hiermee geeft u optionele aanvullende informatie op over **AliasProperty** -, **ScriptProperty** -, **CodeProperty** -of **CodeMethod** -leden.

Als deze para meter wordt gebruikt bij het toevoegen van een **AliasProperty** , moet deze een gegevens type zijn.
Een conversie naar het opgegeven gegevens type wordt toegevoegd aan de waarde van de **AliasProperty**.

Als u bijvoorbeeld een **AliasProperty** toevoegt die een alternatieve naam voor een teken reeks eigenschap levert, kunt u ook een **SecondValue** -para meter van **System. Int32** opgeven om aan te geven dat de waarde van de teken reeks eigenschap moet worden geconverteerd naar een geheel getal wanneer deze wordt geopend met behulp van de bijbehorende **AliasProperty**.

U kunt de para meter **SecondValue** gebruiken om een extra **script Block** op te geven bij het toevoegen van een **ScriptProperty** -lid. De eerste **script Block** , die in de **waarde** para meter wordt opgegeven, wordt gebruikt om de waarde van een variabele op te halen. De tweede **script Block** , opgegeven in de para meter **SecondValue** , wordt gebruikt om de waarde van een variabele in te stellen.

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Waarde

Hiermee geeft u de begin waarde van het toegevoegde lid op.
Als u een **AliasProperty** -, **CodeProperty** -, **ScriptProperty** -of **CodeMethod** -lid toevoegt, kunt u optionele, aanvullende informatie opgeven met behulp van de **SecondValue** -para meter.

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

Hiermee geeft u een naam op voor het type.

Wanneer het type een klasse in de naam ruimte van het **systeem** is of een type dat een type Accelerator heeft, kunt u de korte naam van het type opgeven. Anders is de volledige type naam vereist.
Deze para meter is alleen effectief wanneer de **input object** een **PSObject** is.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: TypeNameSet, NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet
Aliases:

Required: True (TypeNameSet), False (NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt elk object type door sluizen naar deze cmdlet.

## UITVOER

### Geen-of System. object

Wanneer u de para meter **PassThru** gebruikt, retourneert deze cmdlet het nieuwe uitgebreide object.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

U kunt leden alleen toevoegen aan **PSObject** -objecten. Gebruik de operator om te bepalen of een object een **PSObject** -object is `-is` .

Als u bijvoorbeeld een object wilt testen dat is opgeslagen in de `$obj` variabele, typt u `$obj -is [PSObject]` .

De namen van de para meters **member type** , **name** , **Value** en **SecondValue** zijn optioneel.
Als u de parameter namen weglaat, moeten de niet-genaamde parameter waarden in deze volg orde worden weer gegeven: **member type** , **name** , **Value** en **SecondValue**.

Als u de parameter namen toevoegt, kunnen de para meters in een wille keurige volg orde worden weer gegeven.

U kunt de `$this` Automatische variabele gebruiken in script blokken waarmee de waarden van nieuwe eigenschappen en methoden worden gedefinieerd.
De `$this` variabele verwijst naar het exemplaar van het object waarnaar de eigenschappen en methoden worden toegevoegd. Zie about_Automatic_Variables voor meer informatie over de `$this` variabele [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

## GERELATEERDE KOPPELINGEN

[Exporteren-Clixml](Export-Clixml.md)

[Get-member](Get-Member.md)

[Import-Clixml](Import-Clixml.md)

[New-Object](New-Object.md)

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

