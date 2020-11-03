---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-typedata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-TypeData
ms.openlocfilehash: 5f6a9014ad86ba0c80694d7cf49104b56ce27d9d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250626"
---
# Update-TypeData

## Samen vatting
Hiermee werkt u de uitgebreide type gegevens in de sessie bij.

## Syntax

### Bestandsset (standaard)

```
Update-TypeData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DynamicTypeSet

```
Update-TypeData [-MemberType <PSMemberTypes>] [-MemberName <String>] [-Value <Object>]
 [-SecondValue <Object>] [-TypeConverter <Type>] [-TypeAdapter <Type>]
 [-SerializationMethod <String>] [-TargetTypeForDeserialization <Type>]
 [-SerializationDepth <Int32>] [-DefaultDisplayProperty <String>]
 [-InheritPropertySerializationSet <Nullable`1>] [-StringSerializationSource <String>]
 [-DefaultDisplayPropertySet <String[]>] [-DefaultKeyPropertySet <String[]>]
 [-PropertySerializationSet <String[]>] -TypeName <String> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### TypeDataSet

```
Update-TypeData [-Force] [-TypeData] <TypeData[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Beschrijving

`Update-TypeData`Met de cmdlet worden de uitgebreide type gegevens in de sessie bijgewerkt door de `Types.ps1xml` bestanden opnieuw in het geheugen te laden en nieuwe uitgebreide-type gegevens toe te voegen.

Power shell laadt standaard uitgebreide type gegevens als dat nodig is. Zonder para meters worden `Update-TypeData` alle `Types.ps1xml` bestanden die in de sessie zijn geladen, opnieuw geladen, inclusief alle typen bestanden die u hebt toegevoegd. U kunt de para meters van gebruiken `Update-TypeData` om nieuwe type bestanden toe te voegen en uitgebreide type gegevens toe te voegen en te vervangen.

De `Update-TypeData` cmdlet kan worden gebruikt om alle type gegevens vooraf te laden. Deze functie is vooral nuttig wanneer u typen ontwikkelt en deze nieuwe typen wilt laden voor test doeleinden.

Vanaf Windows Power Shell 3,0 kunt u gebruiken `Update-TypeData` om uitgebreide type gegevens in de sessie toe te voegen en te vervangen zonder een bestand te gebruiken `Types.ps1xml` . Type gegevens die dynamisch worden toegevoegd, dat wil zeggen, zonder een bestand, wordt alleen toegevoegd aan de huidige sessie. Als u de type gegevens wilt toevoegen aan alle sessies, voegt u een `Update-TypeData` opdracht toe aan uw Power shell-profiel. Zie [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)voor meer informatie.

Met ingang van Windows Power Shell 3,0 kunt u ook de- `Get-TypeData` cmdlet gebruiken om de uitgebreide typen in de huidige sessie en de `Remove-TypeData` cmdlet te verkrijgen voor het verwijderen van uitgebreide typen uit de huidige sessie.

Uitzonde ringen die optreden in eigenschappen of van het toevoegen van eigenschappen aan een `Update-TypeData` opdracht, rapporteren geen fouten. Dit is om uitzonde ringen te onderdrukken die tijdens het format teren en uitvoeren in veel voorkomende typen zouden optreden. Als u .NET-eigenschappen krijgt, kunt u de onderdrukking van uitzonde ringen omzeilen door in plaats daarvan de syntaxis van de methode te gebruiken, zoals wordt weer gegeven in het volgende voor beeld:

`"hello".get_Length()`

Houd er rekening mee dat syntaxis van een methode alleen kan worden gebruikt met .NET-eigenschappen. Eigenschappen die worden toegevoegd door de cmdlet uit te voeren `Update-TypeData` , kunnen de syntaxis van de methode niet gebruiken.

Zieabout_Types.ps1XML voor meer informatie over de `Types.ps1xml` bestanden in [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)Power shell.

## Voorbeelden

### Voor beeld 1: uitgebreide typen bijwerken

```powershell
Update-TypeData
```

Met deze opdracht wordt de uitgebreide type configuratie bijgewerkt op basis van de `Types.ps1xml` bestanden die al in de sessie zijn gebruikt.

### Voor beeld 2: typen meerdere keren bijwerken

In dit voor beeld ziet u hoe u de typen in een type bestand meerdere keren in dezelfde sessie bijwerkt.

Met de eerste opdracht wordt de uitgebreide type configuratie van de bestanden bijgewerkt en `Types.ps1xml` worden de `TypesA.types.ps1xml` en `TypesB.types.ps1xml` bestanden eerst verwerkt.

De tweede opdracht laat zien hoe u de update `TypesA.types.ps1xml` opnieuw uitvoert, zoals u kunt doen als u een type in het bestand hebt toegevoegd of gewijzigd. U kunt de vorige opdracht voor het bestand herhalen `TypesA.types.ps1xml` of een `Update-TypeData` opdracht zonder para meters uitvoeren, omdat `TypesA.types.ps1xml` deze al in de lijst met type bestanden voor de huidige sessie staat.

```powershell
Update-TypeData -PrependPath TypesA.types.ps1xml, TypesB.types.ps1xml
Update-TypeData -PrependPath TypesA.types.ps1xml
```

### Voor beeld 3: een script eigenschap toevoegen aan DateTime-objecten

In dit voor beeld wordt gebruikt `Update-TypeData` om de eigenschap **kwar taal** toe te voegen aan **System. datetime** -objecten in de huidige sessie, zoals die worden geretourneerd door de `Get-Date` cmdlet.

```powershell
Update-TypeData -TypeName "System.DateTime" -MemberType ScriptProperty -MemberName "Quarter" -Value {
  if ($this.Month -in @(1,2,3)) {"Q1"}
  elseif ($this.Month -in @(4,5,6)) {"Q2"}
  elseif ($this.Month -in @(7,8,9)) {"Q3"}
  else {"Q4"}
}
(Get-Date).Quarter
```

```Output
Q1
```

De `Update-TypeData` opdracht gebruikt de **TypeName** para meter om **het type System. datetime** op te geven, de para meter **lidnaam** om een naam op te geven voor de nieuwe eigenschap, de eigenschap **member type** om het type **ScriptProperty** op te geven, en de **waarde** para meter om het script op te geven dat het jaarlijkse kwar taal bepaalt.

De waarde van de eigenschap **Value** is een script waarmee het huidige jaar kwar taal wordt berekend. Het script blok gebruikt de `$this` Automatische variabele voor het huidige exemplaar van het object en de in-operator om te bepalen of de waarde van de maand wordt weer gegeven in elke matrix met gehele getallen. Zie about_Comparison_Operators voor meer informatie over de `-in` - [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md)operator.

Met de tweede opdracht wordt de nieuwe eigenschap Quarter van de huidige datum opgehaald.

### Voor beeld 4: een type bijwerken dat standaard in lijsten wordt weer gegeven

In dit voor beeld ziet u hoe u de eigenschappen van een type kunt instellen dat standaard wordt weer gegeven in lijsten, dat wil zeggen, wanneer er geen eigenschappen zijn opgegeven. Omdat de type gegevens niet in een bestand zijn opgegeven `Types.ps1xml` , is deze alleen geldig in de huidige sessie.

```powershell
Update-TypeData -TypeName "System.DateTime" -DefaultDisplayPropertySet "DateTime, DayOfYear, Quarter"
Get-Date | Format-List
```

```Output
Thursday, March 15, 2012 12:00:00 AM
DayOfYear : 75
Quarter   : Q1
```

Met de eerste opdracht wordt de `Update-TypeData` cmdlet gebruikt om de standaard lijst eigenschappen voor het type **System. datetime** in te stellen. De opdracht gebruikt de **TypeName** para meter om het type en de para meter **DefaultDisplayPropertySet** op te geven om de standaard eigenschappen voor een lijst op te geven. De geselecteerde eigenschappen zijn onder andere de nieuwe **kwartaal** eigenschap die in een vorig voor beeld is toegevoegd.

De tweede opdracht gebruikt de `Get-Date` cmdlet om een **System. datetime** -object op te halen dat de huidige datum voor stelt. De opdracht maakt gebruik van een pijplijn operator ( `|` ) om het **DateTime** -object naar de cmdlet te verzenden `Format-List` . Omdat met de `Format-List` opdracht niet de eigenschappen worden opgegeven die in de lijst worden weer gegeven, gebruikt Power shell de standaard waarden die door de opdracht zijn ingesteld `Update-TypeData` .

### Voor beeld 5: type gegevens bijwerken voor een object met pijp lijn

```powershell
Get-Module | Update-TypeData -MemberType ScriptProperty -MemberName "SupportsUpdatableHelp" -Value {
  if ($this.HelpInfoUri) {$True} else {$False}
}
Get-Module -ListAvailable | Format-Table Name, SupportsUpdatableHelp
```

```Output
Name                             SupportsUpdatableHelp
----                             ---------------------
Microsoft.PowerShell.Diagnostics                  True
Microsoft.PowerShell.Host                         True
Microsoft.PowerShell.Management                   True
Microsoft.PowerShell.Security                     True
Microsoft.PowerShell.Utility                      True
Microsoft.WSMan.Management                        True
PSDiagnostics                                    False
PSScheduledJob                                    True
PSWorkflow                                        True
ServerManager                                     True
TroubleshootingPack                              False
```

In dit voor beeld wordt gedemonstreerd dat wanneer u een object pipet op `Update-TypeData` , `Update-TypeData` uitgebreide type gegevens toevoegt voor het object type.

Deze techniek is sneller dan het gebruik van de `Get-Member` cmdlet of de `Get-Type` methode om het object type op te halen. Als u echter een verzameling objecten naar een pipet `Update-TypeData` stuurt, worden de type gegevens van het eerste object type bijgewerkt en wordt er een fout geretourneerd voor alle andere objecten in de verzameling, omdat het lid al is gedefinieerd voor het type.

De eerste opdracht gebruikt de `Get-Module` cmdlet om de PSScheduledJob-module op te halen. De opdracht sluizen het module object naar de `Update-TypeData` cmdlet, waarmee de type gegevens voor het type **System. Management. Automation. PSModuleInfo** en de typen die hiervan zijn afgeleid, worden bijgewerkt, zoals het ModuleInfoGrouping-type dat `Get-Module` wordt geretourneerd wanneer u de **ListAvailable** -para meter in de opdracht gebruikt.

`Update-TypeData`Met de opdrachten wordt de script eigenschap **SupportsUpdatableHelp** toegevoegd aan alle geïmporteerde modules. De waarde van de **waarde** -para meter is een script dat retourneert `$True` als de eigenschap **HelpInfoUri** van de module is gevuld en `$False` anders.

Met de tweede opdracht worden de module objecten sluizen van `Get-Module` naar de `Format-Table` cmdlet, die de **naam** en **SupportsUpdatableHelp** -eigenschappen van alle modules in een lijst weergeeft.

## Parameters

### -AppendPath

Hiermee geeft u het pad naar optionele `.ps1xml` bestanden. De opgegeven bestanden worden geladen in de volg orde waarin ze worden weer gegeven nadat de ingebouwde bestanden zijn geladen. U kunt ook een **AppendPath** -waarde naar `Update-TypeData` .

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -DefaultDisplayProperty

Hiermee geeft u de eigenschap op van het type dat door de cmdlet wordt weer gegeven `Format-Wide` wanneer er geen andere eigenschappen zijn opgegeven.

Typ de naam van een standaard-of uitgebreide eigenschap van het type. De waarde van deze para meter kan de naam van een type zijn dat in dezelfde opdracht wordt toegevoegd.

Deze waarde is alleen effectief wanneer er geen brede weer gaven zijn gedefinieerd voor het type in een `Format.ps1xml` bestand.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultDisplayPropertySet

Hiermee geeft u een of meer eigenschappen van het type op. Deze eigenschappen worden weer gegeven door de `Format-List` cmdlet wanneer er geen andere eigenschappen zijn opgegeven.

Typ de namen van de standaard-of uitgebreide eigenschappen van het type. De waarde van deze para meter kan de namen zijn van typen die in dezelfde opdracht worden toegevoegd.

Deze waarde is alleen effectief als er geen lijst Weergaven zijn gedefinieerd voor het type in een `Format.ps1xml` bestand.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultKeyPropertySet

Hiermee geeft u een of meer eigenschappen van het type op. Deze eigenschappen worden gebruikt door de `Group-Object` `Sort-Object` cmdlets en wanneer er geen andere eigenschappen zijn opgegeven.

Typ de namen van de standaard-of uitgebreide eigenschappen van het type. De waarde van deze para meter kan de namen zijn van typen die in dezelfde opdracht worden toegevoegd.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Geeft aan dat de cmdlet de opgegeven type gegevens gebruikt, zelfs als er al een type gegevens voor dat type zijn opgegeven.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DynamicTypeSet, TypeDataSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InheritPropertySerializationSet

Hiermee wordt aangegeven of de set eigenschappen die worden geserialiseerd is overgenomen. De standaardwaarde is `$Null`. De aanvaardbare waarden voor deze parameter zijn:

- `$True`. De eigenschappenset is overgenomen.
- `$False`. De eigenschappenset is niet overgenomen.
- `$Null`. Overname is niet gedefinieerd.

Deze para meter is alleen geldig wanneer de waarde van de para meter **methode serializationmethod** is `SpecificProperties` . Wanneer de waarde van deze para meter is `$False` , is de para meter **PropertySerializationSet** vereist.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Nullable`1[System.Boolean]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Lidnaam

Hiermee geeft u de naam van een eigenschap of methode op.

Gebruik deze para meter met de para meters **TypeName** , **member type** , **Value** en **SecondValue** om een eigenschap of methode van een type toe te voegen of te wijzigen.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Member type

Hiermee geeft u het type lid dat moet worden toegevoegd of gewijzigd.

Gebruik deze para meter met de para meters **TypeName** , **member type** , **Value** en **SecondValue** om een eigenschap of methode van een type toe te voegen of te wijzigen. De aanvaardbare waarden voor deze parameter zijn:

- AliasProperty
- CodeMethod
- CodeProperty
- Noteproperty
- ScriptMethod
- ScriptProperty

Zie [PSMemberTypes Enumeration (Engelstalig)](/dotnet/api/system.management.automation.psmembertypes)voor meer informatie over deze waarden.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: DynamicTypeSet
Aliases:
Accepted values: NoteProperty, AliasProperty, ScriptProperty, CodeProperty, ScriptMethod, CodeMethod

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PrependPath

Hiermee geeft u het pad naar de optionele `.ps1xml` bestanden. De opgegeven bestanden worden geladen in de volg orde waarin ze worden weer gegeven voordat de ingebouwde bestanden worden geladen.

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PropertySerializationSet

Hiermee geeft u de namen van eigenschappen die worden geserialiseerd. Gebruik deze para meter wanneer de waarde van de para meter **methode serializationmethod** is **SpecificProperties**.

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecondValue

Hiermee geeft u aanvullende waarden op voor **AliasProperty** -, **ScriptProperty** -, **CodeProperty** -of **CodeMethod** -leden.

Gebruik deze para meter met de para meters **TypeName** , **member type** , **Value** en **SecondValue** om een eigenschap of methode van een type toe te voegen of te wijzigen.

Wanneer de waarde van de para meter **member type** is `AliasProperty` , moet de waarde van de para meter **SecondValue** een gegevens type zijn. In Power shell wordt de waarde van de alias eigenschap geconverteerd naar het opgegeven type. Als u bijvoorbeeld een alias eigenschap toevoegt die een alternatieve naam voor een teken reeks eigenschap levert, kunt u ook een **SecondValue** van **System. Int32** opgeven om de teken reeks waarde met alias te converteren naar een geheel getal.

Wanneer de waarde van de para meter **member type** is `ScriptProperty` , kunt u de para meter **SecondValue** gebruiken om een extra script blok op te geven. Het script blok in de waarde van de para meter **Value** retourneert de waarde van een variabele. Het script blok in de waarde van de para meter **SecondValue** stelt de waarde van de variabele in.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SerializationDepth

Hiermee geeft u op hoeveel niveaus van het type-objecten als teken reeksen worden geserialiseerd. Met de standaard waarde worden `1` het object en de bijbehorende eigenschappen geserialiseerd. Een waarde voor `0` het serialiseren van het object, maar niet de eigenschappen ervan. Een waarde voor `2` het serialiseren van het object, de eigenschappen ervan en alle objecten in eigenschaps waarden.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Int32
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### -Methode serializationmethod

Hiermee geeft u een serialisatie methode voor het type op. Een serialisatie methode bepaalt welke eigenschappen van het type zijn geserialiseerd en de techniek die wordt gebruikt om ze te serialiseren. De aanvaardbare waarden voor deze parameter zijn:

- `AllPublicProperties`. Alle open bare eigenschappen van het type serialiseren. U kunt de para meter **SerializationDepth** gebruiken om te bepalen of onderliggende eigenschappen geserialiseerd zijn.
- `String`. Serialiseren van het type als een teken reeks. U kunt de **StringSerializationSource** gebruiken om een eigenschap van het type op te geven dat moet worden gebruikt als het serialisatie resultaat. Anders wordt het type geserialiseerd met de methode **toString** van het object.
- `SpecificProperties`. Alleen de opgegeven eigenschappen van dit type serialiseren. Gebruik de para meter **PropertySerializationSet** om de eigenschappen op te geven van het type dat is geserialiseerd.
  U kunt ook de para meter **InheritPropertySerializationSet** gebruiken om te bepalen of de eigenschappenset is overgenomen en de para meter **SerializationDepth** om te bepalen of onderliggende eigenschappen geserialiseerd zijn.

In Power shell worden serialisatie methoden opgeslagen in **PSStandardMembers** interne objecten.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StringSerializationSource

Hiermee geeft u de naam van een eigenschap van het type op. De waarde van de opgegeven eigenschap wordt gebruikt als het serialisatie resultaat. Deze para meter is alleen geldig wanneer de waarde van de para meter **methode serializationmethod** een teken reeks is.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TargetTypeForDeserialization

Hiermee geeft u het type op van welk object van dit type wordt geconverteerd wanneer deze worden gedeserialiseerd.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeAdapter

Hiermee geeft u het type van een type adapter, zoals **micro soft. Power shell. CIM. CimInstanceAdapter**. Met een type adapter kan Power shell de leden van een type ophalen.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeConverter

Hiermee geeft u een type Converter op om waarden te converteren tussen verschillende typen. Als er een type Converter is gedefinieerd voor een type, wordt een exemplaar van het type Converter gebruikt voor de conversie.

Voer een **System. type** -waarde in die is afgeleid van de klassen **System. ComponentModel. TypeConverter** of **System. Management. Automation. PSTypeConverter** .

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeData

Hiermee geeft u een matrix van het type gegevens dat met deze cmdlet wordt toegevoegd aan de sessie. Voer een variabele in die een **TypeData** -object bevat of een opdracht waarmee een **TypeData** -object wordt opgehaald, zoals een `Get-TypeData` opdracht. U kunt ook een **TypeData** -object pipeen naar `Update-TypeData` .

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.Runspaces.TypeData[]
Parameter Sets: TypeDataSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -TypeName

Hiermee geeft u de naam van het type dat moet worden uitgebreid.

Voor typen in de naam ruimte van het **systeem** voert u de korte naam in. Anders is de volledige type naam vereist. Jokertekens worden niet ondersteund.

U kunt typen van het type sluizen naar `Update-TypeData` . Wanneer u een object pipet op `Update-TypeData` , `Update-TypeData` wordt hiermee de type naam van het object opgehaald en worden gegevens naar het object type getypt.

Gebruik deze para meter met de para meters **lidnaam** , **member type** , **Value** en **SecondValue** om een eigenschap of methode van een type toe te voegen of te wijzigen.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Waarde

Hiermee geeft u de waarde van de eigenschap of methode op.

Als u een `AliasProperty` ,, `CodeProperty` `ScriptProperty` of lid toevoegt `CodeMethod` , kunt u de para meter **SecondValue** gebruiken om aanvullende informatie toe te voegen.

Gebruik deze para meter met de para meters **lidnaam** , **member type** , **Value** en **SecondValue** om een eigenschap of methode van een type toe te voegen of te wijzigen.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## Invoerwaarden

### System. String

U kunt een teken reeks die de waarden van de para meters **AppendPath** , **TypeName** of **TypeData** bevat, door sluizen naar `Update-TypeData` .

## Uitvoer

### Geen

Met deze cmdlet wordt geen uitvoer geretourneerd.

## Opmerkingen

## Verwante koppelingen

[about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Get-TypeData](Get-TypeData.md)

[Remove-TypeData](Remove-TypeData.md)

