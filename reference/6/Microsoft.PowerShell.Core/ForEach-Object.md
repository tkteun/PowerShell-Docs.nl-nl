---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: 5a1a53c2b312ef36c80ecfb2a771d2fee2ebea7f
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/10/2020
ms.locfileid: "93251905"
---
# ForEach-Object

## SAMENVATTING
Hiermee wordt een bewerking uitgevoerd voor elk item in een verzameling invoer objecten.

## SYNTAXIS

### ScriptBlockSet (standaard)

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PropertyAndMethodSet

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`ForEach-Object`Met de cmdlet wordt een bewerking uitgevoerd op elk item in een verzameling invoer objecten. De invoer objecten kunnen worden gesluizen naar de cmdlet of worden opgegeven met behulp van de para meter **input object** .

Vanaf Windows Power Shell 3,0 zijn er twee verschillende manieren om een opdracht te maken `ForEach-Object` .

- **Script blok**. U kunt een script blok gebruiken om de bewerking op te geven. In het-script blok gebruikt `$_` u de variabele om het huidige object weer te geven. Het script blok is de waarde van de para meter **process** . Het script blok kan elk Power shell-script bevatten.

  Met de volgende opdracht wordt bijvoorbeeld de waarde van de eigenschap **proces** naam van elk proces op de computer opgehaald.

  `Get-Process | ForEach-Object {$_.ProcessName}`

  `ForEach-Object` ondersteunt de `begin` , `process` , en `end` blokken zoals beschreven in [about_functions](about/about_functions.md#piping-objects-to-functions).

  > [!NOTE]
  > De script blokken worden uitgevoerd in het bereik van de aanroeper. De blokken hebben daarom toegang tot variabelen in dat bereik en kunnen nieuwe variabelen maken die in dat bereik behouden blijven nadat de cmdlet is voltooid.

- **Bewerkings instructie**. U kunt ook een bewerkings instructie schrijven die veel meer lijkt op natuurlijke taal. U kunt de bewerkings instructie gebruiken om een eigenschaps waarde op te geven of een methode aan te roepen. Er zijn bewerkings instructies geïntroduceerd in Windows Power Shell 3,0.

  Met de volgende opdracht wordt ook de waarde van de eigenschap **proces** naam van elk proces op de computer opgehaald.

  `Get-Process | ForEach-Object ProcessName`

## VOORBEELDEN

### Voor beeld 1: gehele getallen in een matrix delen

In dit voor beeld wordt een matrix van drie gehele getallen gebruikt en worden elke reeks gedeeld door 1024.

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### Voor beeld 2: de lengte van alle bestanden in een map ophalen

In dit voor beeld worden de bestanden en mappen in de installatie directory van Power shell verwerkt `$PSHOME` .

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

Als het object geen map is, wordt de naam van het bestand door het script blok opgehaald, wordt de waarde van de eigenschap **Length** gedeeld door 1024 en wordt een spatie ("") toegevoegd om het te scheiden van de volgende vermelding. De cmdlet gebruikt de eigenschap **PSISContainer** om te bepalen of een object een directory is.

### Voor beeld 3: uitvoeren op de meest recente systeem gebeurtenissen

In dit voor beeld worden de 1000 meest recente gebeurtenissen van het systeem gebeurtenis logboek naar een tekst bestand geschreven. De huidige tijd wordt weer gegeven vóór en na de verwerking van de gebeurtenissen.

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

`Get-EventLog` Hiermee worden de 1000 meest recente gebeurtenissen van het systeem gebeurtenis logboek opgehaald en opgeslagen in de `$Events` variabele. `$Events` wordt vervolgens door gegeven aan de `ForEach-Object` cmdlet. Met de para meter **begin** worden de huidige datum en tijd weer gegeven. Vervolgens gebruikt de para meter **process** de `Out-File` cmdlet om een tekst bestand te maken met de naam events.txt en wordt de bericht eigenschap van elk van de gebeurtenissen in dat bestand opgeslagen. De laatste para meter **End** wordt gebruikt om de datum en tijd weer te geven nadat alle verwerking is voltooid.

### Voor beeld 4: de waarde van een register sleutel wijzigen

In dit voor beeld wordt de waarde van de register vermelding **remotepath** in alle subsleutels onder de sleutel gewijzigd in `HKCU:\Network` hoofd letters.

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

U kunt deze indeling gebruiken om het formulier of de inhoud van een register vermelding te wijzigen.

Elke subsleutel in de **netwerk** sleutel vertegenwoordigt een toegewezen netwerk station waarmee opnieuw verbinding wordt gemaakt bij het aanmelden.
De vermelding **remotepath** bevat het UNC-pad van het verbonden station. Als u bijvoorbeeld het station E: toewijst aan `\\Server\Share` , wordt er een **e** -subsleutel van `HKCU:\Network` en de waarde van de register vermelding **remotepath** in de **E** -subsleutel `\\Server\Share` .

De opdracht gebruikt de `Get-ItemProperty` cmdlet om alle subsleutels van de **netwerk** sleutel en de `Set-ItemProperty` cmdlet te verkrijgen om de waarde van de register **vermelding remotepath** in elke sleutel te wijzigen.
In de `Set-ItemProperty` opdracht is het pad de waarde van de eigenschap **PSPath** van de register sleutel. Dit is een eigenschap van het Microsoft .NET Framework-object dat de register sleutel vertegenwoordigt, niet een register vermelding. De opdracht maakt gebruik van de methode **ToUpper ()** van de **remotepath** -waarde. Dit is een teken reeks (REG_SZ).

Omdat `Set-ItemProperty` de eigenschap van elke sleutel wordt gewijzigd, `ForEach-Object` is de cmdlet vereist voor toegang tot de eigenschap.

### Voor beeld 5: de $Null automatische variabele gebruiken

In dit voor beeld ziet u het effect van de `$Null` Automatische variabele voor de `ForEach-Object` cmdlet.

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

Omdat in Power shell NULL wordt behandeld als een expliciete tijdelijke aanduiding, `ForEach-Object` genereert de cmdlet een waarde voor `$Null` , net zoals voor andere objecten die u naar de pipet.

### Voor beeld 6: eigenschaps waarden ophalen

In dit voor beeld wordt de waarde van de eigenschap **Path** van alle geïnstalleerde Power shell-modules opgehaald met behulp van de para meter **membernaam** van de `ForEach-Object` cmdlet.

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

De tweede opdracht is gelijk aan de eerste. Het gebruikt de `Foreach` alias van de `ForEach-Object` cmdlet en laat de naam van de para meter **lidnaam** , die optioneel is.

De `ForEach-Object` cmdlet is erg handig voor het ophalen van eigenschaps waarden, omdat deze de waarde ophaalt zonder het type te wijzigen, in tegens telling tot de **notatie** -cmdlets of de `Select-Object` cmdlet, waarmee het type eigenschaps waarde wordt gewijzigd.

### Voor beeld 7: module namen splitsen in onderdeel namen

In deze voor beelden ziet u drie manieren om twee punt-gescheiden module namen te splitsen in hun onderdeel namen.

```powershell
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object {$_.Split(".")}
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object -MemberName Split -ArgumentList "."
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | Foreach Split "."
```

```Output
Microsoft
PowerShell
Core
Microsoft
PowerShell
Host
```

Met de opdrachten wordt de **Splits** methode van teken reeksen aangeroepen. De drie opdrachten gebruiken een andere syntaxis, maar ze zijn gelijkwaardig en kunnen worden gewijzigd.

De eerste opdracht maakt gebruik van de traditionele syntaxis, die een script blok en de huidige object operator bevat `$_` . De punt notatie wordt gebruikt om de methode en haakjes op te geven voor het argument scheidings teken.

De tweede opdracht gebruikt de para meter **lidnaam** om de **Split** -methode en de para meter **argumentnaam** op te geven om de punt (".") als scheidings teken te identificeren.

De derde opdracht maakt gebruik van de **foreach** -alias van de `ForEach-Object` cmdlet en laat de namen van de para meters **lidnaam** en **argument List** , die optioneel zijn.

### Voor beeld 8: ForEach-Object gebruiken met twee script blokken

In dit voor beeld geven we twee script blokken op positie. Alle script blokken binden aan de **proces** parameter. Ze worden echter behandeld alsof ze zijn door gegeven aan de **begin** -en **proces** parameters.

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### Voor beeld 9: ForEach-Object gebruiken met meer dan twee script blokken

In dit voor beeld geven we twee script blokken op positie. Alle script blokken binden aan de **proces** parameter. Ze worden echter behandeld alsof ze zijn door gegeven aan de **begin** -, **proces** -en **End** -para meters.

```powershell
1..2 | ForEach-Object { 'begin' } { 'process A' }  { 'process B' }  { 'end' }
```

```Output
begin
process A
process B
process A
process B
end
```

> [!NOTE]
> Het eerste script blok wordt altijd toegewezen aan het `begin` blok, het laatste blok wordt toegewezen aan het `end` blok en de blokken tussen zijn allemaal toegewezen aan het blok `process` .

### Voor beeld 10: meerdere script blokken uitvoeren voor elk pijplijn item

Zoals weer gegeven in het vorige voor beeld, worden er meerdere script blokken door gegeven met behulp van de **proces** parameter Get toegewezen aan de **begin** -en **End** -para meters. Om deze toewijzing te vermijden, moet u expliciete waarden opgeven voor de **begin** -en **eind** parameters.

```powershell
1..2 | ForEach-Object -Begin $null -Process { 'one' }, { 'two' }, { 'three' } -End $null
```

```Output
one
two
three
one
two
three
```

## PARAMETERS

### -Argument List

Hiermee geeft u een matrix op met argumenten voor een methode aanroep. Zie [about_Splatting](about/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Object[]
Parameter Sets: PropertyAndMethodSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Begin

Hiermee geeft u een script blok op dat wordt uitgevoerd voordat deze cmdlet invoer objecten verwerkt. Dit script blok wordt slechts één keer uitgevoerd voor de volledige pijp lijn. Zie about_Functions voor meer informatie over het `begin` blok [about_Functions](about/about_functions.md#piping-objects-to-functions).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -End

Hiermee geeft u een script blok op dat wordt uitgevoerd nadat deze cmdlet alle invoer objecten heeft verwerkt. Dit script blok wordt slechts één keer uitgevoerd voor de volledige pijp lijn. Zie about_Functions voor meer informatie over het `end` blok [about_Functions](about/about_functions.md#piping-objects-to-functions).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee worden de invoer objecten opgegeven. `ForEach-Object` Hiermee wordt het script blok of de bewerkings instructie voor elk invoer object uitgevoerd. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

Wanneer u de para meter **input object** gebruikt in `ForEach-Object` plaats van de resultaten van de pijpleiding opdracht, `ForEach-Object` wordt de waarde van **input object** behandeld als een enkel object. Dit geldt ook als de waarde een verzameling is die het resultaat is van een opdracht, zoals `-InputObject (Get-Process)` .
Omdat **input object** geen individuele eigenschappen van een matrix of verzameling van objecten kan retour neren, raden we u aan dat als u gebruikt `ForEach-Object` om bewerkingen uit te voeren op een verzameling objecten voor objecten met specifieke waarden in gedefinieerde eigenschappen, u `ForEach-Object` in de pijp lijn gebruikt, zoals wordt weer gegeven in de voor beelden in dit onderwerp.

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

### -Lidnaam

Hiermee geeft u de eigenschap op die moet worden opgehaald of de methode die moet worden aangeroepen.

Joker tekens zijn toegestaan, maar werken alleen als de resulterende teken reeks wordt omgezet in een unieke waarde.
Als u bijvoorbeeld uitvoert `Get-Process | ForEach -MemberName *Name` , en er meer dan één lid bestaat met een naam die de naam van de teken reeks bevat, zoals de **ProcessName** eigenschappen van de **naam** van de computer en name, mislukt de opdracht.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: PropertyAndMethodSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Proces

Hiermee geeft u de bewerking op die op elk invoer object wordt uitgevoerd. Dit script blok wordt uitgevoerd voor elk object in de pijp lijn. Zie about_Functions voor meer informatie over het `process` blok [about_Functions](about/about_functions.md#piping-objects-to-functions).

Wanneer u meerdere script blokken voor de para meter **process** opgeeft, wordt het eerste script blok altijd toegewezen aan het `begin` blok. Als er slechts twee script blokken zijn, wordt het tweede blok toegewezen aan het `process` blok. Als er drie of meer script blokken zijn, wordt het eerste script blok altijd toegewezen aan het `begin` blok, wordt het laatste blok toegewezen aan het `end` blok en worden de blokken tussen beide toegewezen aan het `process` blok.

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemainingScripts

Hiermee geeft u alle script blokken op die niet worden gebruikt door de **proces** parameter.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
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

## INVOER

### System. Management. Automation. PSObject

U kunt elk object door sluizen naar deze cmdlet.

## UITVOER

### System. Management. Automation. PSObject

Deze cmdlet retourneert objecten die worden bepaald door de invoer.

## OPMERKINGEN

- De `ForEach-Object` cmdlet werkt op dezelfde manier als de **foreach** -instructie, behalve dat u invoer niet kunt door sluizen naar een **foreach** -instructie. Zie [about_Foreach](./About/about_Foreach.md)voor meer informatie over de instructie **foreach** .

- Vanaf Power Shell 4,0 `Where` en `ForEach` methoden zijn toegevoegd voor gebruik met verzamelingen. U kunt hier meer lezen over deze nieuwe methoden [about_arrays](./About/about_Arrays.md)

## GERELATEERDE KOPPELINGEN

[Compare-object](../Microsoft.PowerShell.Utility/Compare-Object.md)

[Where-object](Where-Object.md)

[Groep-object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Meting object](../Microsoft.PowerShell.Utility/Measure-Object.md)

[New-Object](../Microsoft.PowerShell.Utility/New-Object.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Sorteer object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[T-object](../Microsoft.PowerShell.Utility/Tee-Object.md)
