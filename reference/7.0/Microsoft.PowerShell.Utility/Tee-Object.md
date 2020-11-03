---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/tee-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Tee-Object
ms.openlocfilehash: 47c1eb6b31f762e3950c07f9edec81a081ce616e
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249811"
---
# Tee-Object

## SAMENVATTING
Slaat de uitvoer van de opdracht op in een bestand of variabele, en verzendt deze ook naar de pijp lijn.

## SYNTAXIS

### Bestand (standaard)

```
Tee-Object [-InputObject <PSObject>] [-FilePath] <String> [-Append] [<CommonParameters>]
```

### LiteralFile

```
Tee-Object [-InputObject <PSObject>] -LiteralPath <String> [<CommonParameters>]
```

### Variabele

```
Tee-Object [-InputObject <PSObject>] -Variable <String> [<CommonParameters>]
```

## BESCHRIJVING

De `Tee-Object` cmdlet stuurt uitvoer om, dat wil zeggen, de uitvoer van een opdracht in twee richtingen (zoals de letter T). De uitvoer wordt opgeslagen in een bestand of variabele, en wordt ook verzonden naar de pijp lijn. Als de `Tee-Object` laatste opdracht in de pijp lijn is, wordt de opdracht uitvoer weer gegeven bij de prompt.

## VOORBEELDEN

### Voor beeld 1: uitvoer processen naar een bestand en naar de-console

In dit voor beeld wordt een lijst opgehaald met de processen die op de computer worden uitgevoerd en wordt het resultaat naar een bestand verzonden.
Omdat er geen tweede pad is opgegeven, worden de processen ook weer gegeven in de-console.

```powershell
Get-Process | Tee-Object -FilePath "C:\Test1\testfile2.txt"
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
83       4     2300       4520    39     0.30    4032 00THotkey
272      6     1400       3944    34     0.06    3088 alg
81       3      804       3284    21     2.45     148 ApntEx
81       4     2008       5808    38     0.75    3684 Apoint
...
```

### Voor beeld 2: uitvoer processen naar een variabele en `Select-Object`

In dit voor beeld wordt een lijst opgehaald met de processen die op de computer worden uitgevoerd, worden deze opgeslagen in de `$proc` variabele en worden ze door sluizen naar `Select-Object` .

```powershell
Get-Process notepad | Tee-Object -Variable proc | Select-Object processname,handles
```

```Output
ProcessName                              Handles
-----------                              -------
notepad                                  43
notepad                                  37
notepad                                  38
notepad                                  38
```

`Select-Object`Met de cmdlet worden de eigenschappen **proces** -en **handle** geselecteerd. Houd er rekening mee dat de `$proc` variabele de standaard gegevens bevat die worden geretourneerd door `Get-Process` .

### Voor beeld 3: systeem bestanden uitvoeren naar twee logboek bestanden

In dit voor beeld wordt een lijst met systeem bestanden opgeslagen in twee logboek bestanden, een cumulatief bestand en een actueel bestand.

```powershell
Get-ChildItem -Path D: -File -System -Recurse |
  Tee-Object -FilePath "c:\test\AllSystemFiles.txt" -Append |
    Out-File c:\test\NewSystemFiles.txt
```

De opdracht gebruikt de `Get-ChildItem` cmdlet voor het uitvoeren van een recursieve zoek opdracht voor systeem bestanden op station D:. Een pijplijn operator (|) verzendt de lijst naar `Tee-Object` , waarmee de lijst wordt toegevoegd aan het AllSystemFiles.txt-bestand en de lijst wordt door gegeven aan de `Out-File` -cmdlet, waarmee de lijst wordt opgeslagen in het NewSystemFiles.txt bestand.

## PARAMETERS

### -Toevoegen

Geeft aan dat de cmdlet de uitvoer aan het opgegeven bestand toevoegt. Zonder deze para meter vervangt de nieuwe inhoud alle bestaande inhoud in het bestand zonder dat er een waarschuwing wordt gegeven.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Hiermee geeft u een bestand op dat met deze cmdlet het object opslaat in joker tekens, maar moet worden omgezet in één bestand.

```yaml
Type: System.String
Parameter Sets: File
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Input object

Hiermee geeft u het object op dat moet worden opgeslagen en weer gegeven. Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald. U kunt ook een object pipet naar `Tee-Object` .

Wanneer u de para meter **input object** gebruikt in `Tee-Object` plaats van de resultaten van de pijpleiding opdracht, `Tee-Object` wordt de waarde van **input object** behandeld als één enkel object, zelfs als de waarde een verzameling is.

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

### -LiteralPath

Hiermee geeft u een bestand op waarvan deze cmdlet het object opslaat. In tegens telling tot het **bestandspad** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String
Parameter Sets: LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variabele

Hiermee geeft u een variabele op waaraan de cmdlet het object opslaat. Geef een naam op voor de variabele zonder het voor gaande dollar teken ( `$` ).

```yaml
Type: System.String
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt objecten door sluizen naar `Tee-Object` .

## UITVOER

### System. Management. Automation. PSObject

`Tee-Object` retourneert het object dat wordt omgeleid.

## OPMERKINGEN

U kunt ook de `Out-File` cmdlet of de omleidings operator gebruiken, beide waarmee de uitvoer in een bestand wordt opgeslagen, maar deze niet wordt verzonden naar de pijp lijn.

Vanaf Power shell 6 `Tee-Object` gebruikt de stuk lijst-minder UTF-8-code ring wanneer deze naar bestanden wordt geschreven. Als u een andere code ring nodig hebt, gebruikt u de `Out-File` cmdlet met de para meter **Encoding** .

## GERELATEERDE KOPPELINGEN

[Compare-object](Compare-Object.md)

[ForEach-object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Groep-object](Group-Object.md)

[Meting object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sorteer object](Sort-Object.md)

[Where-object](../Microsoft.PowerShell.Core/Where-Object.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)
