---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/new-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-IseSnippet
ms.openlocfilehash: 0ed1c2913fc7531574bfbdd435a002d60931d24a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250046"
---
# New-IseSnippet

## SAMENVATTING
Hiermee maakt u een code fragment Windows PowerShell ISE.

## SYNTAXIS

```
New-IseSnippet [-Title] <String> [-Description] <String> [-Text] <String> [-Author <String>]
 [-CaretOffset <Int32>] [-Force] [<CommonParameters>]
```

## BESCHRIJVING

De `New-ISESnippet` cmdlet maakt een Herbruikbare tekst fragment voor Windows PowerShell ISE. U kunt fragmenten gebruiken om tekst toe te voegen aan het Script venster of het opdracht venster in Windows PowerShell ISE. Deze cmdlet is alleen beschikbaar in Windows PowerShell ISE.

Vanaf Windows Power Shell 3,0 bevat Windows PowerShell ISE een verzameling ingebouwde fragmenten. Met de `New-ISESnippet` cmdlet kunt u uw eigen fragmenten maken om toe te voegen aan de ingebouwde verzameling. U kunt fragment bestanden weer geven, wijzigen, toevoegen, verwijderen en delen in Windows Power shell-modules. Als u fragmenten in Windows PowerShell ISE wilt zien, selecteert u in het menu **bewerken** de optie **fragmenten starten** of drukt u op <kbd>CTRL</kbd> + <kbd>J</kbd>.

`New-ISESnippet`Met de cmdlet maakt `<Title>.Snippets.ps1xml` u een bestand in de `$home\Documents\WindowsPowerShell\Snippets` map met de titel die u opgeeft. Als u een fragment bestand wilt toevoegen in een module die u ontwerpt, voegt u het fragment bestand toe aan een subdirectory met fragmenten van uw module directory.

U kunt door de gebruiker gemaakte fragmenten niet gebruiken in een sessie waarin het uitvoerings beleid is **beperkt** of **Alles ondertekend**.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een Help-fragment maken voor een Comment-Based

```
New-IseSnippet -Title Comment-BasedHelp -Description "A template for comment-based help." -Text "<#
    .SYNOPSIS

    .DESCRIPTION
    .PARAMETER  <Parameter-Name>
    .INPUTS
    .OUTPUTS
    .EXAMPLE
    .LINK
#>"
```

Met deze opdracht maakt u een Comment-BasedHelp fragment voor Windows PowerShell ISE. Er wordt een bestand gemaakt `Comment-BasedHelp.snippets.ps1xml` met de naam in de map met fragmenten van de gebruiker `$home\Documents\WindowsPowerShell\Snippets` .

### Voor beeld 2: een verplicht fragment maken

```
$M = @'
Param
(
  [parameter(Mandatory=$true)]
  [String[]]
  $<ParameterName>
)
'@

New-ISESnippet -Text $M -Title Mandatory -Description "Adds a mandatory function parameter." -Author "Patti Fuller, Fabrikam Corp." -Force
```

In dit voor beeld wordt een code fragment gemaakt met de naam **verplicht** voor Windows PowerShell ISE. Met de eerste opdracht wordt de tekst van het fragment opgeslagen in de `$M` variabele. De tweede opdracht gebruikt de `New-ISESnippet` cmdlet om het fragment te maken. De opdracht gebruikt de para meter **Force** voor het overschrijven van een vorig fragment met dezelfde naam.

### Voor beeld 3: een verplicht fragment uit een map naar een doelmap kopiëren

```
Copy-Item "$Home\Documents\WindowsPowerShell\Snippets\Mandatory.Snippets.ps1xml" -Destination "\\Server\Share"
```

Met deze opdracht wordt de `Copy-Item` cmdlet gebruikt om het **verplichte** fragment te kopiëren uit de map waar het `New-ISESnippet` wordt geplaatst naar de Server\Share-bestands share.

## PARAMETERS

### -Author

Hiermee geeft u de auteur van het fragment. Het veld Auteur wordt weer gegeven in het fragment bestand, maar wordt niet weer gegeven wanneer u op de naam van het fragment in Windows PowerShell ISE klikt.

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

### -CaretOffset

Hiermee wordt het teken van de tekst van het fragment opgegeven waarin deze cmdlet de cursor plaatst. Voer een geheel getal in dat de positie van de cursor vertegenwoordigt en ' 1 ' staat voor het eerste teken van de tekst. De standaard waarde, 0 (nul), plaatst de cursor direct voor het eerste teken van de tekst. Met deze para meter wordt de tekst van het fragment niet Inge sprongen.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -Beschrijving

Hiermee geeft u een beschrijving van het fragment op. De waarde van de beschrijving wordt weer gegeven wanneer u op de naam van het fragment in Windows PowerShell ISE klikt. Deze parameter is vereist.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Geeft aan dat met deze cmdlet fragment bestanden met dezelfde naam op dezelfde locatie worden overschreven. Standaard worden `New-ISESnippet` bestanden niet overschreven.

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

### -Tekst

Hiermee geeft u de tekst waarde op die wordt toegevoegd wanneer u het fragment selecteert. De tekst van het fragment wordt weer gegeven wanneer u op de naam van het fragment in Windows PowerShell ISE klikt. Deze parameter is vereist.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Titel

Hiermee geeft u een titel of naam voor het fragment op. De titel heeft ook de naam van het fragment bestand. Deze parameter is vereist.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

Deze cmdlet neemt geen invoer van de pijp lijn.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

`New-IseSnippet` slaat nieuwe door de gebruiker gemaakte fragmenten op in niet-ondertekende. ps1xml-bestanden. Windows Power shell kan deze niet toevoegen aan een sessie waarin het uitvoerings beleid **Alles ondertekend** of **beperkt** is. In een **beperkte** of **Alles ondertekende** sessie kunt u niet-ondertekende door de gebruiker gemaakte fragmenten maken, ophalen en importeren, maar u kunt ze niet gebruiken in de sessie.

Als u de `New-IseSnippet` cmdlet in een **beperkte** of **Alles ondertekend** -sessie gebruikt, wordt het fragment gemaakt, maar er wordt een fout bericht weer gegeven wanneer Windows Power shell het zojuist gemaakte fragment aan de sessie probeert toe te voegen. Als u het nieuwe fragment (en andere niet-ondertekende door de gebruiker gemaakte fragmenten) wilt gebruiken, wijzigt u het uitvoerings beleid en start u Windows PowerShell ISE opnieuw.

Zie about_Execution_Policies voor meer informatie over het uitvoerings beleid van Windows Power shell.

- Bewerk het fragment bestand als u een fragment wilt wijzigen. U kunt fragment bestanden bewerken in het Script venster van Windows PowerShell ISE.
- Als u een toegevoegd fragment wilt verwijderen, verwijdert u het fragment bestand.
- Het is niet mogelijk om een ingebouwd fragment te verwijderen, maar u kunt alle ingebouwde fragmenten verbergen met behulp van de $psise. Opties. ShowDefaultSnippets = $false "opdracht.
- U kunt een fragment maken dat dezelfde naam heeft als een ingebouwd fragment. Beide fragmenten worden weer gegeven in het menu fragment in Windows PowerShell ISE.

## GERELATEERDE KOPPELINGEN

[Get-IseSnippet](Get-IseSnippet.md)

[Import-IseSnippet](Import-IseSnippet.md)
