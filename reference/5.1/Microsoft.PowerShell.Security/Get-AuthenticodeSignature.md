---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-authenticodesignature?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-AuthenticodeSignature
ms.openlocfilehash: 910897ae1e41b2e4bd082977ac2904388f924769
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250512"
---
# Get-AuthenticodeSignature

## SAMENVATTING
Hiermee haalt u informatie op over de Authenticode-hand tekening voor een bestand.

## SYNTAXIS

### ByPath (standaard)

```
Get-AuthenticodeSignature [-FilePath] <String[]> [<CommonParameters>]
```

### ByLiteralPath

```
Get-AuthenticodeSignature -LiteralPath <String[]> [<CommonParameters>]
```

### ByContent

```
Get-AuthenticodeSignature -SourcePathOrExtension <String[]> -Content <Byte[]> [<CommonParameters>]
```

## BESCHRIJVING

De `Get-AuthenticodeSignature` cmdlet haalt informatie op over de Authenticode-hand tekening voor een bestand of bestands inhoud als een byte matrix. Als het bestand niet is ondertekend, wordt de informatie opgehaald, maar zijn de velden leeg.

## VOORBEELDEN

### Voor beeld 1: de Authenticode-hand tekening voor een bestand ophalen

```powershell
Get-AuthenticodeSignature -FilePath "C:\Test\NewScript.ps1"
```

Met deze opdracht wordt informatie opgehaald over de Authenticode-hand tekening in het NewScript.ps1-bestand. De para meter **filepath** wordt gebruikt om het bestand op te geven.

### Voor beeld 2: de Authenticode-hand tekening voor meerdere bestanden ophalen

```powershell
Get-AuthenticodeSignature test.ps1, test1.ps1, sign-file.ps1, makexml.ps1
```

Met deze opdracht wordt informatie opgehaald over de Authenticode-hand tekening voor de vier bestanden die worden vermeld op de opdracht regel. In dit voor beeld wordt de naam van de **filepath** -para meter, die optioneel is, wegge laten.

### Voor beeld 3: alleen geldige Authenticode-hand tekeningen ophalen voor meerdere bestanden

```powershell
Get-ChildItem $PSHOME\*.* | ForEach-object {Get-AuthenticodeSignature $_} | Where-Object {$_.status -eq "Valid"}
```

Met deze opdracht worden alle bestanden in de map weer gegeven `$PSHOME` die een geldige Authenticode-hand tekening hebben. De `$PSHOME` Automatische variabele bevat het pad naar de installatie directory van Power shell.

De opdracht gebruikt de `Get-ChildItem` cmdlet om de bestanden in de map op te halen `$PSHOME` . Er wordt een patroon van gebruikt *.* om directory's uit te sluiten (hoewel er ook bestanden worden uitgesloten zonder punt in de bestands naam).

De opdracht maakt gebruik van een pijplijn operator ( `|` ) voor het verzenden van de bestanden in `$PSHOME` naar de `ForEach-Object` cmdlet, waarbij `Get-AuthenticodeSignature` wordt aangeroepen voor elk bestand.

De resultaten van de `Get-AuthenticodeSignature` opdracht worden verzonden naar een `Where-Object` opdracht die alleen de handtekening objecten met de status geldig selecteert.

### Voor beeld 4: de Authenticode-hand tekening ophalen voor een bestands inhoud die is opgegeven als byte matrix

```powershell
Get-AuthenticodeSignature -Content (Get-Content foo.ps1 -AsByteStream) -SourcePathorExtension ps1
```

Met deze opdracht wordt informatie over de Authenticode-hand tekening voor de inhoud van een bestand opgehaald. In dit voor beeld wordt de bestands extensie opgegeven samen met de inhoud van het bestand.

## PARAMETERS

### -Inhoud

Inhoud van een bestand als een byte matrix waarvoor de Authenticode-hand tekening wordt opgehaald. Deze para meter moet worden gebruikt met de para meter **SourcePathOrExtension** . De inhoud van het bestand moet de Unicode-indeling (UTF-16LE) hebben.

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -FilePath

Hiermee geeft u het pad op naar het bestand dat u wilt onderzoeken. Joker tekens zijn toegestaan, maar moeten tot één bestand leiden. Het is niet nodig om het **bestandspad** te typen op de opdracht regel wanneer u een waarde voor deze para meter opgeeft.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -LiteralPath

Hiermee geeft u het pad op naar het bestand dat wordt onderzocht. In tegens telling tot het **bestandspad** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad een escape-teken bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape-tekens.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourcePathOrExtension

Het pad naar het bestand of het bestands type van de inhoud waarvoor de Authenticode-hand tekening is opgehaald. Deze para meter wordt gebruikt met **inhoud** waar bestands inhoud als een byte matrix wordt door gegeven.

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks die een bestandspad bevat, door sluizen naar `Get-AuthenticodeSignature` .

## UITVOER

### System. Management. Automation. Signature

`Get-AuthenticodeSignature` retourneert een Signature-object voor elke hand tekening die wordt opgehaald.

## OPMERKINGEN

Zie [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)voor meer informatie over Authenticode-hand tekeningen in Power shell.

## GERELATEERDE KOPPELINGEN

[Get-ExecutionPolicy](Get-ExecutionPolicy.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)
