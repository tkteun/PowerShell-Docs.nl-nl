---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-String
ms.openlocfilehash: 665a0ca8332c4052b59362c7947e408ba811c5f2
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/01/2020
ms.locfileid: "93251882"
---
# ConvertFrom-String

## SAMENVATTING
Hiermee worden gestructureerde eigenschappen geëxtraheerd en geparseerd uit de teken reeks inhoud.

## SYNTAXIS

### ByDelimiter (standaard)

```
ConvertFrom-String [-Delimiter <String>] [-PropertyNames <String[]>] [-InputObject] <String>
 [<CommonParameters>]
```

### TemplateParsing

```
ConvertFrom-String [-TemplateFile <String[]>] [-TemplateContent <String[]>] [-IncludeExtent] [-UpdateTemplate]
 [-InputObject] <String> [<CommonParameters>]
```

## BESCHRIJVING

Met de **ConvertFrom-** cmdlet worden gestructureerde eigenschappen geëxtraheerd uit de teken reeks inhoud en geparseerd.
Met deze cmdlet wordt een object gegenereerd door tekst van een traditionele tekst stroom te parseren.
Voor elke teken reeks in de pijp lijn splitst de cmdlet de invoer met een scheidings teken of een parseringsstructuur en wijst vervolgens eigenschapnamen toe aan elk van de resulterende Splits elementen.
U kunt deze eigenschapnamen opgeven. Als u dit niet doet, worden ze automatisch voor u gegenereerd.

De standaard parameterset van de cmdlet **ByDelimiter** , wordt exact op het reguliere expressie scheidings teken gesplitst.
Er worden geen aanhalings tekens of scheidings tekens voor het afstemmen van de `Import-Csv` cmdlet uitgevoerd.

De alternatieve parameterset van de cmdlet, **TemplateParsing** , genereert elementen van de groepen die worden vastgelegd met een reguliere expressie. Zie [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)voor meer informatie over reguliere expressies.

Deze cmdlet biedt ondersteuning voor twee modi: basis-gescheiden parsering en automatisch gegenereerde, voor beeld-geparseerd parseren.

Met een scheidings teken voor het parseren wordt standaard de invoer gesplitst in witruimte en worden eigenschapnamen toegewezen aan de resulterende groepen.

U kunt het scheidings teken aanpassen door de resultaten te pijpleidingen `ConvertFrom-String` in een van de `Format-*` cmdlets, of u kunt de para meter **scheidings teken** gebruiken.

De cmdlet biedt ook ondersteuning voor automatisch gegenereerde, voor beelden geparseerd parseren op basis van de [FlashExtract, onderzoek werkzaamheden door micro soft Research](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples/).

## VOORBEELDEN

### Voor beeld 1: een object met standaard eigenschapnamen genereren

```powershell
"Hello World" | ConvertFrom-String
```

```Output
P1    P2
--    --
Hello World
```

Met deze opdracht wordt een object gegenereerd met standaard namen van eigenschappen, **P1** en **P2**.

### Voor beeld 1A: meer weten over het gegenereerde object

Met deze opdracht wordt één object gegenereerd met de eigenschappen **P1** , **P2** ; beide eigenschappen zijn standaard van het type **teken reeks** .

```powershell
"Hello World" | ConvertFrom-String | Get-Member
```

```Output

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
P1          NoteProperty string P1=Hello
P2          NoteProperty string P2=World
```

### Voor beeld 2: een object met standaard eigenschapnamen genereren met behulp van een scheidings teken

Met deze opdracht wordt een object gegenereerd met een domein en gebruikers naam met behulp van de back slash ( `\` ) als scheidings teken. Het back slash-teken moet worden voorafgegaan door een andere back slash wanneer reguliere expressies worden gebruikt.

```powershell
"Contoso\Administrator" | ConvertFrom-String -Delimiter "\\"
```

```Output
P1      P2
--      --
Contoso Administrator
```

### Voor beeld 3: een object genereren dat twee benoemde eigenschappen bevat

In het volgende voor beeld worden objecten gemaakt op basis van Windows hosts-bestands vermeldingen.

```powershell
$content = Get-Content C:\Windows\System32\drivers\etc\hosts
$content = $content -match "^[^#]"
$content | ConvertFrom-String -PropertyNames IP, Server
```

```Output
IP             Server
--             ------
192.168.7.10   W2012R2
192.168.7.20   W2016
192.168.7.101  WIN8
192.168.7.102  WIN10
```

De- `Get-Content` cmdlet slaat de inhoud van een Windows hosts-bestand op in `$content` . Met de tweede opdracht verwijdert u eventuele opmerkingen aan het begin van het hosts-bestand met behulp van een reguliere expressie die overeenkomt met een regel die niet begint met ( `#` ). Met de laatste opdracht wordt de resterende tekst geconverteerd naar objecten met de eigenschappen **Server** en **IP** .

### Voor beeld 4: een expressie gebruiken als de waarde van de TemplateContent-para meter, sla de resultaten op in een variabele.

Met deze opdracht wordt een expressie gebruikt als de waarde van de para meter **TemplateContent** .
De expressie wordt opgeslagen in een variabele voor eenvoud.
Windows Power shell begrijpt nu dat de teken reeks die wordt gebruikt voor de pijp lijn `ConvertFrom-String` drie eigenschappen heeft:

- **Naam**
- **telefoon**
- **leeftijd**

```powershell
$template = @'
{Name*:Phoebe Cat}, {phone:425-123-6789}, {age:6}
{Name*:Lucky Shot}, {phone:(206) 987-4321}, {age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789    6
Lucky Shot    (206) 987-4321  12
Elephant Wise 425-888-7766    87
Wild Shrimp   (111)  222-3333 1
```

Elke regel in de invoer wordt geëvalueerd op basis van de voor beelden van overeenkomsten. Als de lijn overeenkomt met de voor beelden die zijn opgegeven in het patroon, worden waarden geëxtraheerd en door gegeven aan de uitvoer variabele.

De voorbeeld gegevens, `$template` , biedt twee verschillende telefoon indelingen:

- `425-123-6789`
- `(206) 987-4321`

De voorbeeld gegevens bieden ook twee verschillende leeftijds notaties:

- `6`
- `12`

Dit betekent dat telefoons zoals `(206) 987 4321` niet worden herkend, omdat er geen voorbeeld gegevens zijn die overeenkomen met het patroon omdat er geen afbreek streepjes zijn.

### Voor beeld 5: gegevens typen opgeven voor de gegenereerde eigenschappen

Dit is hetzelfde voor beeld als voor beeld 4 hierboven.
Het verschil is dat de patroon teken reeks een gegevens type voor elke gewenste eigenschap bevat.

```powershell
$template = @'
{[string]Name*:Phoebe Cat}, {[string]phone:425-123-6789}, {[int]age:6}
{[string]Name*:Lucky Shot}, {[string]phone:(206) 987-4321}, {[int]age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789      6
Lucky Shot    (206) 987-4321   12
Elephant Wise 425-888-7766     87
Wild Shrimp   (111)  222-3333   1
```

```powershell
$PersonalData | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
age         NoteProperty int age=6
Name        NoteProperty string Name=Phoebe Cat
phone       NoteProperty string phone=425-123-6789
```

De `Get-Member` cmdlet wordt gebruikt om aan te geven dat de eigenschap **Age** een geheel getal is.

## PARAMETERS

### -Scheidings teken

Hiermee geeft u een reguliere expressie op waarmee de grens tussen elementen wordt aangegeven.
Elementen die door de splitsing worden gemaakt, worden eigenschappen in het resulterende object.
Het scheidings teken wordt uiteindelijk gebruikt in een aanroep van de methode **Split** van het type `[System.Text.RegularExpressions.RegularExpression]` .

```yaml
Type: System.String
Parameter Sets: ByDelimiter
Aliases: DEL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeExtent

Geeft aan dat deze cmdlet een eigenschap voor de grootte van een tekst bevat die standaard wordt verwijderd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: IE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Specificeert teken reeksen die zijn ontvangen van de pijp lijn of een variabele die een teken reeks object bevat.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -PropertyNames

Hiermee geeft u een matrix met eigenschapnamen op waaraan u gesplitste waarden in het resulterende object wilt toewijzen.
Elke regel tekst die u splitst of parseert, genereert elementen die eigenschaps waarden vertegenwoordigen.
Als het element het resultaat is van een vastleg groep en die vastleg groep heet (bijvoorbeeld `(?<name>)` of `(?'name')` ), wordt de naam van die vastleg groep toegewezen aan de eigenschap.

Als u elementen in de **PropertyName** -matrix opgeeft, worden deze namen toegewezen aan eigenschappen die nog niet zijn benoemd.

Als u meer eigenschapnamen opgeeft dan er velden zijn, negeert Power shell de extra eigenschaps namen. Als u niet voldoende eigenschapnamen opgeeft om alle velden een naam te geven, wijst Power shell automatisch numerieke eigenschapnamen toe aan eigenschappen die geen naam hebben: **P1** , **P2** , enzovoort.

```yaml
Type: System.String[]
Parameter Sets: ByDelimiter
Aliases: PN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TemplateContent

Hiermee geeft u een expressie op, of een expressie die is opgeslagen als een variabele, waarin de eigenschappen worden beschreven waaraan deze cmdlet teken reeksen toewijst. De syntaxis van een sjabloon veld specificatie is het volgende: `{[optional-typecast]<name>:<example-value>}` .

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TemplateFile

Hiermee geeft u een bestand, als een matrix, op dat een sjabloon bevat voor de gewenste parsering van de teken reeks.
In het sjabloon bestand staan eigenschappen en hun waarden tussen vier Kante haken, zoals hieronder wordt weer gegeven.
Als een eigenschap, zoals de eigenschap **name** en de bijbehorende andere eigenschappen, meerdere keren wordt weer gegeven, kunt u een asterisk ( `*` ) toevoegen om aan te geven dat dit resulteert in meerdere records. Dit voor komt dat meerdere eigenschappen worden geëxtraheerd tot één record.

```
{Name*:David Chew}
{City:Redmond}, {State:WA}
{Name*:Evan Narvaez}    {Name*:Antonio Moreno}
{City:Issaquah}, {State:WA}
```

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UpdateTemplate

Geeft aan dat met deze cmdlet de resultaten van een leer algoritme worden opgeslagen in een opmerking in het sjabloon bestand.
Hierdoor wordt het algoritme learning proces sneller uitgevoerd.
Als u deze para meter wilt gebruiken, moet u ook een sjabloon bestand met de para meter **TemplateFile** opgeven.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: UT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` . Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[ConvertFrom-string: voor beelden van het parseren van tekst](https://devblogs.microsoft.com/powershell/convertfrom-string-example-based-text-parsing/)

[ConvertFrom-StringData](ConvertFrom-StringData.md)

[ConvertFrom-CSV](ConvertFrom-Csv.md)

[ConvertTo-Xml](ConvertTo-Xml.md)
