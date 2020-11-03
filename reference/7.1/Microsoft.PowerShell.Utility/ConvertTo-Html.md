---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: 27a1d2994dee46b9e5bfd54132ff4a665330c2b4
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251787"
---
# ConvertTo-Html

## SAMENVATTING
Hiermee converteert u .NET-objecten naar HTML die kunnen worden weer gegeven in een webbrowser.

## SYNTAXIS

### Pagina (standaard)

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [-Meta <Hashtable>] [-Charset <String>] [-Transitional]
 [<CommonParameters>]
```

### Fragment

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

`ConvertTo-Html`Met de cmdlet worden .net-objecten geconverteerd naar HTML die kan worden weer gegeven in een webbrowser. U kunt deze cmdlet gebruiken om de uitvoer van een opdracht in een webpagina weer te geven.

U kunt de para meters van gebruiken `ConvertTo-Html` om object eigenschappen te selecteren, om een tabel-of lijst indeling op te geven, om de titel van de HTML-pagina op te geven, tekst voor en toe te voegen voor en na het object, en om alleen het tabel-of lijst fragment op te halen in plaats van een strikte DTD-pagina.

Wanneer u meerdere objecten indient naar `ConvertTo-Html` , maakt Power shell de tabel (of lijst) op basis van de eigenschappen van het eerste object dat u verzendt. Als de resterende objecten niet beschikken over een van de opgegeven eigenschappen, is de waarde van de eigenschap van dat object een lege cel. Als de resterende objecten extra eigenschappen hebben, worden deze eigenschaps waarden niet opgenomen in het bestand.

## VOORBEELDEN

### Voor beeld 1: een webpagina maken om de datum weer te geven

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

Met deze opdracht maakt u een HTML-pagina waarop de eigenschappen van de huidige datum worden weer gegeven. De para meter **input object** wordt gebruikt om de resultaten van een `Get-Date` opdracht bij de cmdlet in te dienen `ConvertTo-Html` .

### Voor beeld 2: een webpagina maken voor het weer geven van Power shell-aliassen

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

Met deze opdracht maakt u een HTML-pagina waarop de Power shell-aliassen in de huidige console worden weer gegeven.

De opdracht gebruikt de `Get-Alias` cmdlet om de aliassen op te halen. Er wordt gebruikgemaakt van de pijplijn operator ( `|` ) om de aliassen te verzenden naar de `ConvertTo-Html` cmdlet, waarmee de HTML-pagina wordt gemaakt. De opdracht gebruikt ook de `Out-File` cmdlet om de HTML-code naar het `aliases.htm` bestand te verzenden.

### Voor beeld 3: een webpagina maken om Power shell-gebeurtenissen weer te geven

```powershell
`Get-EventLog` -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

Met deze opdracht maakt u een HTML-pagina `pslog.htm` met de naam waarmee de gebeurtenissen in het Windows Power shell-gebeurtenis logboek op de lokale computer worden weer gegeven.

De cmdlet wordt gebruikt `Get-EventLog` om de gebeurtenissen in het Windows Power shell-logboek op te halen. vervolgens wordt de pijplijn operator ( `|` ) gebruikt om de gebeurtenissen te verzenden naar de `ConvertTo-Html` cmdlet. De opdracht gebruikt ook de `Out-File` cmdlet om de HTML-code naar het `pslog.htm` bestand te verzenden.

De opdracht gebruikt ook de `Out-File` cmdlet om de HTML-code naar het `pslog.htm` bestand te verzenden.

### Voor beeld 4: een webpagina maken om processen weer te geven

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

Met deze opdrachten maakt en opent u een HTML-pagina met een lijst met de naam, het pad en het bedrijf van de processen op de lokale computer.

De eerste opdracht gebruikt de `Get-Process` cmdlet om objecten op te halen die de processen vertegenwoordigen die worden uitgevoerd op de computer. De opdracht maakt gebruik van de pijplijn operator ( `|` ) om de proces objecten naar de `ConvertTo-Html` cmdlet te verzenden.

De opdracht gebruikt de para meter **Property** om drie eigenschappen te selecteren van de proces objecten die in de tabel moeten worden opgenomen. De opdracht gebruikt de para meter **title** om een titel voor de HTML-pagina op te geven. De opdracht gebruikt ook de `Out-File` cmdlet om de resulterende HTML naar een bestand met de naam Proc.htm te verzenden.

Met de tweede opdracht wordt de `Invoke-Item` cmdlet gebruikt om de `Proc.htm` in de standaard browser te openen.

### Voor beeld 5: een webpagina maken voor het weer geven van service objecten

```powershell
Get-Service | ConvertTo-Html -CssUri "test.css"
```

```Output
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"  "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
<title>HTML TABLE</title>
<link rel="stylesheet" type="text/css" href="test.css" />
...
```

Met deze opdracht maakt u een HTML-pagina van de service objecten die door de `Get-Service` cmdlet worden geretourneerd. De opdracht gebruikt de para meter **CssUri** om een trapsgewijs opmaak model voor de HTML-pagina op te geven.

De para meter **CssUri** voegt een extra `<link rel="stylesheet" type="text/css" href="test.css">` tag toe aan de resulterende HTML. Het kenmerk HREF in het label bevat de naam van het opmaak model.

### Voor beeld 6: een webpagina maken voor het weer geven van service objecten

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

Met deze opdracht maakt u een HTML-pagina van de service objecten die door de `Get-Service` cmdlet worden geretourneerd. De opdracht gebruikt de **as** -para meter om een lijst indeling op te geven. De cmdlet `Out-File` verzendt de resulterende HTML naar het `Services.htm` bestand.

### Voor beeld 7: een webtabel maken voor de huidige datum

```powershell
Get-Date | ConvertTo-Html -Fragment
```

```Output
<table>
<colgroup>...</colgroup>
<tr><th>DisplayHint</th><th>DateTime</th><th>Date</th><th>Day</th><th>DayOfWeek</th><th>DayOfYear</th><th>Hour</th>
<th>Kind</th><th>Millisecond</th><th>Minute</th><th>Month</th><th>Second</th><th>Ticks</th><th>TimeOfDay</th><th>Year</th></tr>
<tr><td>DateTime</td><td>Monday, May 05, 2008 10:40:04 AM</td><td>5/5/2008 12:00:00 AM</td><td>5</td><td>Monday</td>
<td>126</td><td>10</td><td>Local</td><td>123</td><td>40</td><td>5</td><td>4</td><td>633455808041237213</td><td>10:40:04.12
37213</td><td>2008</td></tr>
</table>
```

Met deze opdracht wordt `ConvertTo-Html` een HTML-tabel van de huidige datum gegenereerd. De opdracht gebruikt de `Get-Date` cmdlet om de huidige datum op te halen. Er wordt gebruikgemaakt van een pijplijn operator (|) om de resultaten naar de cmdlet te verzenden `ConvertTo-Html` .

De `ConvertTo-Html` opdracht bevat de **fragment** parameter, waarmee de uitvoer wordt beperkt tot een HTML-tabel. Als gevolg hiervan worden de andere elementen van een HTML-pagina, zoals de `<HEAD>` `<BODY>` Tags en wegge laten.

### Voor beeld 8: een webpagina maken om Power shell-gebeurtenissen weer te geven

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

Met deze opdracht wordt de `Get-EventLog` cmdlet gebruikt om gebeurtenissen van het Windows Power shell-gebeurtenis logboek op te halen.

Er wordt een pijplijn operator ( `|` ) gebruikt om de gebeurtenissen te verzenden naar de `ConvertTo-Html` cmdlet, waarmee de gebeurtenissen worden geconverteerd naar een HTML-indeling.

De `ConvertTo-Html` opdracht gebruikt de para meter **Property** om alleen de eigenschappen **id** , **niveau** en **Task** van de gebeurtenis te selecteren.

### Voor beeld 9: een webpagina maken om opgegeven services weer te geven

```powershell
$htmlParams = @{
  Title = "Windows Services: Server01"
  Body = Get-Date
  PreContent = "<P>Generated by Corporate IT</P>"
  PostContent = "For details, contact Corporate IT."
}
Get-Service A* |
  ConvertTo-Html @htmlParams |
    Out-File Services.htm
Invoke-Item Services.htm
```

Met deze opdracht wordt een webpagina gemaakt en geopend waarop de services op de computer worden weer gegeven die beginnen met een. Het maakt gebruik van de para meters **titel** , **hoofd tekst** **, voor-en** **PostContent** van `ConvertTo-Html` om de uitvoer aan te passen.

Het eerste deel van de opdracht gebruikt de `Get-Service` cmdlet om de services op de computer te verkrijgen die met een beginnen. De opdracht maakt gebruik van een pijplijn operator ( `|` ) om de resultaten naar de `ConvertTo-Html` cmdlet te verzenden. De opdracht gebruikt ook de `Out-File` cmdlet om de uitvoer naar het Services.htm-bestand te verzenden.

Een punt komma ( `;` ) eindigt de eerste opdracht en start een tweede opdracht, waarbij de `Invoke-Item` cmdlet wordt gebruikt om het bestand te openen `Services.htm` in de standaard browser.

### Voor beeld 10: de meta-eigenschappen en charset van de HTML instellen

```powershell
Get-Service | ConvertTo-HTML -Meta @{
  refresh=10
  author="Author's Name"
  keywords="PowerShell, HTML, ConvertTo-HTML"
} -Charset "UTF-8"
```

Met deze opdracht wordt de HTML-code voor een webpagina gemaakt met de meta tags voor vernieuwen, auteur en tref woorden.
De charset voor de pagina is ingesteld op UTF-8

### Voor beeld 11: de HTML instellen op XHTML-overgangs DTD

```powershell
Get-Service | ConvertTo-HTML -Transitional
```

Met deze opdracht wordt het DOCTYPE van de geretourneerde HTML ingesteld op XHTML-overgangs DTD

## PARAMETERS

### -As

Bepaalt of het object wordt opgemaakt als een tabel of een lijst. Geldige waarden zijn **tabel** en **lijst**. De standaard waarde is **Table**.

De **tabel** waarde genereert een HTML-tabel die overeenkomt met de indeling van de Power shell-tabel. In de rij met koppen worden de namen van eigenschappen weer gegeven. Elke tabelrij vertegenwoordigt een object en geeft de waarden van het object voor elke eigenschap.

De **lijst** waarde genereert een HTML-tabel met twee kolommen voor elk object dat lijkt op de Power shell-lijst indeling. In de eerste kolom wordt de naam van de eigenschap weer gegeven. De tweede kolom bevat de waarde van de eigenschap.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Table, List

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Hoofd tekst

Hiermee geeft u de tekst op die moet worden toegevoegd na de openings `<BODY>` code. Standaard is er geen tekst op die positie.

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Charset

Hiermee geeft u de tekst op die moet worden toegevoegd aan de openings `<charset>` code. Standaard is er geen tekst op die positie.

Deze para meter is geïntroduceerd in Power shell 6,0.

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CssUri

Hiermee geeft u de URI (Uniform Resource Identifier) van het trapsgewijze opmaak model (CSS) op dat wordt toegepast op het HTML-bestand. De URI wordt opgenomen in een koppeling naar een opmaak model in de uitvoer.

```yaml
Type: System.Uri
Parameter Sets: Page
Aliases: cu, uri

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fragment

Genereert alleen een HTML-tabel. De tags HTML, HEAD, TITLE en BODY worden wegge laten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Fragment
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Head

Hiermee geeft u de inhoud van de `<HEAD>` tag. De standaardwaarde is `<title\>HTML TABLE</title>`. Als u de para meter **Head** gebruikt, wordt de para meter **title** genegeerd.

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u de objecten op die in HTML moeten worden weer gegeven. Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.

Als u deze para meter gebruikt voor het indienen van meerdere objecten, zoals alle services op een computer, `ConvertTo-Html` wordt een tabel gemaakt waarin de eigenschappen van een verzameling of een matrix met objecten worden weer gegeven. Als u een tabel van de afzonderlijke objecten wilt maken, gebruikt u de pijplijn operator om de objecten naar te sluizen `ConvertTo-Html` .

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

### -Meta

Hiermee geeft u de tekst op die moet worden toegevoegd aan de openings `<meta>` code. Standaard is er geen tekst op die positie.

Deze para meter is geïntroduceerd in Power shell 6,0.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PostContent

Geeft aan dat er tekst moet worden toegevoegd na de afsluitende `</TABLE>` tag. Standaard is er geen tekst op die positie.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Precontent

Hiermee geeft u de tekst die moet worden toegevoegd voor de openings `<TABLE>` code. Standaard is er geen tekst op die positie.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Eigenschap

Bevat de opgegeven eigenschappen van de objecten in de HTML. De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn. De berekende eigenschap kan een script blok of een hash-tabel zijn. Geldige sleutel-waardeparen zijn:

- Naam (of label): `<string>` (toegevoegd in Power shell 6. x)
- Expressie- `<string>` of `<script block>`
- Tring `<string>`
- Breedte: `<int32>` moet groter zijn dan `0`
- Uitlijning-waarde kan `Left` , `Center` of `Right`

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

### -Titel

Hiermee geeft u een titel voor het HTML-bestand, dat wil zeggen, de tekst die wordt weer gegeven tussen de `<TITLE>` Tags.

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Overgang

Wijzigt het **DOCTYPE** - **overgangs DTD** , het standaard **DOCTYPE** is **XHTML Strict DTD**.

Deze para meter is geïntroduceerd in Power shell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt elk .NET-object door sluizen naar `ConvertTo-Html` .

## UITVOER

### Systeem. teken reeks of System.Xml.Xmldocument

`ConvertTo-Html` retourneert reeksen van teken reeksen waaruit een geldige HTML bestaat.

## OPMERKINGEN

Als u deze cmdlet wilt gebruiken, pipet u een of meer objecten aan de cmdlet of gebruikt u de para meter **input object** om het object op te geven. Wanneer de invoer uit meerdere objecten bestaat, is de uitvoer van deze twee methoden heel anders.

- Wanneer u meerdere objecten naar een cmdlet Pipet, verzendt Power shell de objecten per keer naar de cmdlet. Als gevolg hiervan `ConvertTo-Html` wordt een tabel gemaakt waarin de afzonderlijke objecten worden weer gegeven. Als u bijvoorbeeld de processen op een computer wilt `ConvertTo-Html` door sluizen, worden in de resulterende tabel alle processen weer gegeven.

- Wanneer u de para meter **input object** gebruikt voor het verzenden van meerdere objecten, `ConvertTo-Html` ontvangt deze objecten als een verzameling of als een matrix. Als gevolg hiervan wordt een tabel gemaakt waarin de matrix en de bijbehorende eigenschappen worden weer gegeven, niet de items in de matrix. Als u bijvoorbeeld **input object** gebruikt om de processen op een computer in te dienen `ConvertTo-Html` , worden in de resulterende tabel een object matrix en de bijbehorende eigenschappen weer gegeven.

  Om te voldoen aan de XHTML Strict DTD, wordt de DOCTYPE-tag dienovereenkomstig gewijzigd:

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## GERELATEERDE KOPPELINGEN

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertTo-Xml](ConvertTo-Xml.md)

[Exporteren-Clixml](Export-Clixml.md)

[Import-Clixml](Import-Clixml.md)
