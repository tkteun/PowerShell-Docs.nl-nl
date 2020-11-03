---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: 3a3d431276074d7c2b66b442307071076fdfebd5
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "93251942"
---
# Out-File

## SAMENVATTING
Hiermee wordt de uitvoer naar een bestand verzonden.

## SYNTAXIS

### ByPath (standaard)

```
Out-File [-FilePath] <string> [[-Encoding] <Encoding>] [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Out-File [[-Encoding] <Encoding>] -LiteralPath <string> [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Out-File` cmdlet verzendt uitvoer naar een bestand. Het gebruik van het Power shell-opmaak systeem wordt impliciet gebruikt om naar het bestand te schrijven. Het bestand ontvangt dezelfde weergave representatie als de Terminal. Dit betekent dat de uitvoer mogelijk niet ideaal is voor programma verwerking, tenzij alle invoer objecten teken reeksen zijn.
Wanneer u para meters voor de uitvoer wilt opgeven, gebruikt u `Out-File` in plaats van de omleidings operator ( `>` ). Zie [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)voor meer informatie over omleiding.

## VOORBEELDEN

### Voor beeld 1: uitvoer verzenden en een bestand maken

In dit voor beeld ziet u hoe u een lijst met de processen van de lokale computer naar een bestand verzendt. Als het bestand niet bestaat, `Out-File` maakt het bestand in het opgegeven pad.

```powershell
Get-Process | Out-File -FilePath .\Process.txt
Get-Content -Path .\Process.txt
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     29    22.39      35.40      10.98   42764   9 Application
     53    99.04     113.96       0.00   32664   0 CcmExec
     27    96.62     112.43     113.00   17720   9 Code
```

De `Get-Process` cmdlet haalt een lijst op met processen die worden uitgevoerd op de lokale computer. De **proces** objecten worden in de pijp lijn naar de `Out-File` cmdlet verzonden. `Out-File` maakt gebruik van de **filepath** para meter en maakt een bestand in de huidige map met de naam **Process.txt**. De `Get-Content` opdracht haalt inhoud op uit het bestand en geeft deze weer in de Power shell-console.

### Voor beeld 2: voor komen dat een bestaand bestand wordt overschreven

In dit voor beeld wordt voor komen dat een bestaand bestand wordt overschreven. Standaard worden `Out-File` bestaande bestanden overschreven.

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

De `Get-Process` cmdlet haalt een lijst op met processen die worden uitgevoerd op de lokale computer. De **proces** objecten worden in de pijp lijn naar de `Out-File` cmdlet verzonden. `Out-File` maakt gebruik van de **filepath** para meter en probeert te schrijven naar een bestand in de huidige map met de naam **Process.txt**. Met de para meter **NoClobber** wordt voor komen dat het bestand wordt overschreven en wordt een bericht weer gegeven dat het bestand al bestaat.

### Voor beeld 3: uitvoer naar een bestand in ASCII-indeling verzenden

In dit voor beeld ziet u hoe uitvoer wordt gecodeerd met een specifiek coderings type.

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

De `Get-Process` cmdlet haalt een lijst op met processen die worden uitgevoerd op de lokale computer. De **proces** objecten worden opgeslagen in de variabele `$Procs` . `Out-File` maakt gebruik van de **filepath** para meter en maakt een bestand in de huidige map met de naam **Process.txt**. De **input object** para meter geeft de proces objecten door in `$Procs` de bestands **Process.txt**. De para meter **Encoding** converteert de uitvoer naar **ASCII** -indeling. De para meter **breedte** beperkt elke regel in het bestand tot 50 tekens, waardoor sommige gegevens kunnen worden afgekapt.

### Voor beeld 4: een provider gebruiken en uitvoer naar een bestand verzenden

In dit voor beeld ziet u hoe u de `Out-File` cmdlet gebruikt wanneer u zich niet in een **File System** -provider station bevindt. Gebruik de `Get-PSProvider` cmdlet om de providers op uw lokale computer weer te geven. Zie [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md)voor meer informatie.

```
PS> Set-Location -Path Alias:

PS> Get-Location

Path
----
Alias:\

PS> Get-ChildItem | Out-File -FilePath C:\TestDir\AliasNames.txt

PS> Get-Content -Path C:\TestDir\AliasNames.txt

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           cat -> Get-Content
```

De `Set-Location` opdracht gebruikt de para meter **Path** om de huidige locatie van de register provider in te stellen `Alias:` . Met de `Get-Location` cmdlet wordt het volledige pad voor weer gegeven `Alias:` .
`Get-ChildItem` Hiermee worden objecten van de pijp lijn naar de `Out-File` cmdlet verzonden. `Out-File` gebruikt de **filepath** para meter om het volledige pad en de bestands naam voor de uitvoer op te geven **C:\TestDir\AliasNames.txt**. Met de `Get-Content` cmdlet wordt de para meter **Path** gebruikt en wordt de inhoud van het bestand weer gegeven in de Power shell-console.

## PARAMETERS

### -Toevoegen

Hiermee wordt de uitvoer toegevoegd aan het einde van een bestaand bestand.

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

### -Encoding

Hiermee geeft u het type code ring voor het doel bestand op. De standaardwaarde is `utf8NoBOM`.

De acceptabele waarden voor deze para meter zijn als volgt:

- `ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).
- `bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.
- `bigendianutf32`: Codeert in UTF-32-indeling met behulp van de byte volgorde big endian.
- `oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.
- `unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.
- `utf7`: Wordt gecodeerd in de indeling UTF-7.
- `utf8`: Wordt gecodeerd in UTF-8-indeling.
- `utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)
- `utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)
- `utf32`: Gecodeerd in UTF-32-indeling.

Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` . Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.

> [!NOTE]
> **UTF-7** * wordt niet meer aanbevolen voor gebruik. In Power shell 7,1 wordt een waarschuwing geschreven als u `utf7` voor de para meter **Encoding** opgeeft.

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: 1
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Hiermee geeft u het pad naar het uitvoer bestand.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Onderdrukt het kenmerk alleen-lezen en overschrijft een bestaand alleen-lezen bestand. De para meter **Force** overschrijft geen beveiligings beperkingen.

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

### -Input object

Hiermee geeft u de objecten die naar het bestand moeten worden geschreven. Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.

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

Hiermee geeft u het pad naar het uitvoer bestand. De para meter **LiteralPath** wordt exact gebruikt als deze wordt getypt.
Jokertekens worden niet geaccepteerd. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen. Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoClobber

Met **NoClobber** wordt voor komen dat een bestaand bestand wordt overschreven en wordt een bericht weer gegeven dat het bestand al bestaat. Als een bestand bestaat in het opgegeven pad, wordt standaard `Out-File` het bestand overschreven zonder dat er een waarschuwing wordt gegeven.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Nieuwe regel

Hiermee geeft u op dat de inhoud die naar het bestand wordt geschreven, niet eindigt met een teken voor een nieuwe regel. De teken reeks representaties van de invoer objecten worden samengevoegd om de uitvoer te vormen. Er worden geen spaties of nieuwe regels tussen de uitvoer teken reeksen ingevoegd. Er wordt geen nieuwe regel toegevoegd na de laatste uitvoer teken reeks.

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

### -Breedte

Hiermee geeft u het aantal tekens in elke regel van uitvoer op. Eventuele extra tekens worden afgekapt, niet verpakt. Als deze para meter niet wordt gebruikt, wordt de breedte bepaald door de kenmerken van de host. De standaard instelling voor de Power shell-console is 80 tekens.

```yaml
Type: System.Int32
Parameter Sets: (All)
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

U kunt elk object door sluizen naar `Out-File` .

## UITVOER

### Geen

`Out-File` Er wordt geen uitvoer gegenereerd.

## OPMERKINGEN

Invoer objecten worden automatisch opgemaakt zoals ze zich in de terminal bevinden, maar u kunt een `Format-*` cmdlet gebruiken om de opmaak van de uitvoer naar het bestand expliciet te bepalen. bijvoorbeeld `Get-Date | Format-List | Out-File out.txt`

Als u de uitvoer van een Power shell-opdracht naar de cmdlet wilt verzenden `Out-File` , gebruikt u de pijp lijn. U kunt ook gegevens opslaan in een variabele en de para meter **input object** gebruiken om gegevens door te geven aan de `Out-File` cmdlet.

`Out-File` gegevens worden opgeslagen in een bestand, maar er worden geen uitvoer objecten naar de pijp lijn geproduceerd.

## GERELATEERDE KOPPELINGEN

[about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[Out-standaard](../Microsoft.PowerShell.Core/Out-Default.md)

[Out-host](../Microsoft.PowerShell.Core/Out-Host.md)

[Out-Null](../Microsoft.PowerShell.Core/Out-Null.md)

[Out-teken reeks](Out-String.md)

[T-object](Tee-Object.md)

