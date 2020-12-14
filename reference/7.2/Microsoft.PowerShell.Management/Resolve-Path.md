---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resolve-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resolve-Path
ms.openlocfilehash: 0481526aead285e3d5fb494218d1573e03216f2e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705874"
---
# Resolve-Path

## SAMENVATTING
Hiermee worden de joker tekens in een pad omgezet en wordt de inhoud van het pad weer gegeven.

## SYNTAXIS

### Pad (standaard)

```
Resolve-Path [-Path] <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

### LiteralPath

```
Resolve-Path -LiteralPath <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Resolve-Path` cmdlet worden de items en containers weer gegeven die overeenkomen met het Joker teken patroon op de opgegeven locatie. De overeenkomst kan bestanden, mappen, register sleutels of andere objecten bevatten die toegankelijk zijn vanuit een PSDrive-provider.

## VOORBEELDEN

### Voor beeld 1: het pad naar de basismap oplossen

De tilde (~) is een steno notatie voor de basismap van de huidige gebruiker. In dit voor beeld wordt `Resolve-Path` de volledig gekwalificeerde pad waarde geretourneerd.

```powershell
PS C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

### Voor beeld 2: het pad naar de Windows-map oplossen

```powershell
PS C:\> Resolve-Path -Path "windows"
```

```Output
Path
----
C:\Windows
```

Wanneer u uitvoert vanuit de hoofdmap van station C:, retourneert deze opdracht het pad van de Windows-map in station C:.

### Voor beeld 3: alle paden ophalen in de Windows-map

```powershell
PS C:\> "C:\windows\*" | Resolve-Path
```

Met deze opdracht worden alle mappen in de map C:\Windows. geretourneerd. De opdracht maakt gebruik van een pijplijn operator (|) om een pad naar een padtekenreeks te verzenden `Resolve-Path` .

### Voor beeld 4: een UNC-pad omzetten

```powershell
PS C:\> Resolve-Path -Path "\\Server01\public"
```

Met deze opdracht wordt een UNC-pad (Universal Naming Convention) omgezet en worden de shares in het pad geretourneerd.

### Voor beeld 5: relatieve paden ophalen

```powershell
PS C:\> Resolve-Path -Path "c:\prog*" -Relative
```

```Output
.\Program Files
.\Program Files (x86)
.\programs.txt
```

Met deze opdracht worden relatieve paden geretourneerd voor de mappen in de hoofdmap van station C:.

### Voor beeld 6: een pad met haakjes oplossen

In dit voor beeld wordt de para meter **LiteralPath** gebruikt om het pad van de \[ XML-test-submap op te lossen \] .
Als u **LiteralPath** gebruikt, worden de haakjes beschouwd als normale tekens in plaats van een reguliere expressie.

```powershell
PS C:\> Resolve-Path -LiteralPath 'test[xml]'
```

## PARAMETERS

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.
Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of geef een **PSCredential** -object door. U kunt een **PSCredential** -object maken met behulp van de- `Get-Credential` cmdlet. Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.

Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u het pad op dat moet worden omgezet.
De waarde van de para meter **LiteralPath** wordt exact als getypt gebruikt.
Er worden geen tekens geïnterpreteerd als joker tekens.
Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.
Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het Power shell-pad op dat moet worden omgezet.
Deze parameter is vereist.
U kunt ook een padtekenreeks door sluizen naar `Resolve-Path` .
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Relatief

Geeft aan dat deze cmdlet een relatief pad retourneert.

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks met een pad naar deze cmdlet door sluizen

## UITVOER

### System. Management. Automation. PathInfo, System. String

Retourneert een **PathInfo** -object. Retourneert een teken reeks waarde voor het omgezette pad als u de **relatieve** para meter opgeeft.

## OPMERKINGEN

De `*-Path` cmdlets werken met het bestands systeem, het REGI ster en de certificaat providers.

`Resolve-Path` is ontworpen om te werken met elke provider. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` . Zie [about_providers](../microsoft.powershell.core/about/about_providers.md)voor meer informatie.

`Resolve-Path` Hiermee worden alleen bestaande paden opgelost. Het kan niet worden gebruikt om een locatie op te lossen die nog niet bestaat.

## GERELATEERDE KOPPELINGEN

[Convert-pad](Convert-Path.md)

[Pad voor samen voegen](Join-Path.md)

[Split-pad](Split-Path.md)

[Test-pad](Test-Path.md)

