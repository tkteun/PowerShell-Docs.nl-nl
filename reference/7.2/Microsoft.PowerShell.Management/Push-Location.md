---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/push-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Push-Location
ms.openlocfilehash: eaa7622e29680de4228579f8b77a6c829a586bf8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705963"
---
# Push-Location

## SAMENVATTING
De huidige locatie wordt toegevoegd aan de bovenkant van een locatie stack.

## SYNTAXIS

### Pad (standaard)

```
Push-Location [[-Path] <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

### LiteralPath

```
Push-Location [-LiteralPath <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## BESCHRIJVING

De `Push-Location` cmdlet voegt de huidige locatie (' pushes ') toe aan een locatie stack. Als u een pad opgeeft, wordt `Push-Location` de huidige locatie naar een locatie stack gepusht en wordt de huidige locatie gewijzigd in de locatie die is opgegeven door het pad. U kunt de `Pop-Location` cmdlet gebruiken om locaties op te halen uit de locatie stack.

Standaard `Push-Location` duwt de cmdlet de huidige locatie naar de huidige locatie stack, maar u kunt de para meter van de **stacknaam** gebruiken om een alternatieve locatie-stack op te geven. Als de stack niet bestaat, `Push-Location` wordt deze gemaakt.

Zie de [opmerkingen](#notes)voor meer informatie over locatie stacks.

## VOORBEELDEN

### Voorbeeld 1

In dit voor beeld wordt de huidige locatie naar de standaard locatie stack gepusht. vervolgens wordt de locatie gewijzigd in `C:\Windows` .

```
PS C:\> Push-Location C:\Windows
```

### Voorbeeld 2

In dit voor beeld wordt de huidige locatie naar de RegFunction-stack gepusht en wordt de huidige locatie gewijzigd in de `HKLM:\Software\Policies` locatie.

```
PS C:\> Push-Location HKLM:\Software\Policies -StackName RegFunction
```

U kunt de locatie-cmdlets gebruiken in een Power Shell-station (PSDrive).

### Voorbeeld 3

Met deze opdracht wordt de huidige locatie naar de standaard stack gepusht. De locatie wordt niet gewijzigd.

```
PS C:\> Push-Location
```

### Voor beeld 4: een benoemde stack maken en gebruiken

Deze opdrachten laten zien hoe u een benoemde locatie stapel maakt en gebruikt.

```
PS C:\> Push-Location ~ -StackName Stack2
PS C:\Users\User01> Pop-Location -StackName Stack2
PS C:\>
```

De eerste opdracht duwt de huidige locatie naar een nieuwe stack met de naam Stack2 en wijzigt vervolgens de huidige locatie naar de basismap, die wordt weer gegeven in de opdracht door het tilde-symbool ( `~` ), die wordt gebruikt voor de stations van een bestands systeem provider en die gelijk is aan `$HOME` en `$env:USERPROFILE` .

Als Stack2 al in de sessie bestaat, `Push-Location` wordt deze gemaakt. Met de tweede opdracht wordt de `Pop-Location` cmdlet gebruikt om de oorspronkelijke locatie ( `C:\` ) van de Stack2-stack te pop. Zonder de para meter ' **stuurprogrammastack** ' `Pop-Location` zou de locatie van de niet-genaamde standaard stack zouden pop-en.

Zie de [opmerkingen](#notes)voor meer informatie over locatie stacks.

## PARAMETERS

### -LiteralPath

Hiermee geeft u het pad naar de nieuwe locatie. In tegens telling tot de para meter **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt terwijl deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Hiermee wordt een object door gegeven dat de locatie naar de pijp lijn vertegenwoordigt. Deze cmdlet genereert standaard geen uitvoer.

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

### -Path

Hiermee wordt uw locatie gewijzigd in de locatie die is opgegeven door dit pad nadat deze de huidige locatie boven aan de stack heeft toegevoegd (pushes). Geef een pad op naar een locatie waarvan de provider deze cmdlet ondersteunt. Joker tekens zijn toegestaan. De parameter naam is optioneel.

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Stacknaam

Hiermee geeft u de locatie stack op waaraan de huidige locatie wordt toegevoegd. Voer de naam van de locatie stack in.
Als de stack niet bestaat, `Push-Location` wordt deze gemaakt.

Zonder deze para meter `Push-Location` voegt de locatie toe aan de huidige locatie stack. Standaard is de huidige locatie stack de niet-genaamde standaard locatie stack die Power Shell maakt.
Als u wilt dat een locatie stack de huidige locatie stack is, gebruikt u de para meter ' **stacknaam** ' van de `Set-Location` cmdlet. Zie de [opmerkingen](#notes)voor meer informatie over locatie stacks.

> [!NOTE]
> `Push-Location` kan geen locatie toevoegen aan de niet-genaamde standaard stack, tenzij dit de huidige locatie stack is.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default stack
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks die een pad (maar geen letterlijk pad) bevat, door sluizen naar `Push-Location` .

## UITVOER

### Geen of System. Management. Automation. PathInfo

Wanneer u de para meter **PassThru** gebruikt, `Push-Location` genereert een **System. Management. Automation. PathInfo** -object dat de locatie vertegenwoordigt. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

Power shell ondersteunt meerdere runspaces per proces. Elke runs Pace heeft zijn eigen _huidige map_.
Dit is niet hetzelfde als `[System.Environment]::CurrentDirectory` . Dit gedrag kan een probleem zijn bij het aanroepen van .NET-Api's of het uitvoeren van systeem eigen toepassingen zonder expliciete mappaden te bieden.

Zelfs als de locatie-cmdlets de huidige map voor het gehele proces hebben ingesteld, kunt u er niet op vertrouwen, omdat deze op elk gewenst moment door een andere runs Pace kan worden gewijzigd. U moet de locatie-cmdlets gebruiken om op paden gebaseerde bewerkingen uit te voeren op basis van de huidige werkmap die specifiek is voor de huidige-runs Pace.

Een stack is een vervolg keuzelijst die het laatst is toegevoegd en die alleen toegankelijk is voor het laatst toegevoegde item.
U voegt items toe aan een stack in de volg orde waarin u ze gebruikt en haalt deze vervolgens op voor gebruik in de omgekeerde volg orde. Met Power shell kunt u locatie locaties opslaan in site-stacks.

In Power shell wordt een niet-benoemde standaard locatie stack gemaakt en u kunt meerdere naam locatie stacks maken. Als u geen stack naam opgeeft, gebruikt Power shell de huidige locatie stack. Standaard is de niet-naam standaard locatie de huidige locatie stack, maar u kunt de `Set-Location` cmdlet gebruiken om de huidige locatie stack te wijzigen.

Als u locatie stacks wilt beheren, gebruikt u de Power shell location-cmdlets, als volgt.

- Gebruik de cmdlet om een locatie aan een locatie stack toe te voegen `Push-Location` .

- Als u een locatie wilt ophalen uit een locatie stack, gebruikt u de `Pop-Location` cmdlet.

- Als u de locaties wilt weer geven in de huidige locatie stack, gebruikt u de para meter **stack** van de `Get-Location` cmdlet.

- Als u de locaties wilt weer geven in een benoemde locatie stack, gebruikt u de para meter ' **stack** naam ' van de `Get-Location` cmdlet.

- Als u een nieuwe locatie stack wilt maken, gebruikt u de para meter ' Stacknaam ' van de `Push-Location` cmdlet. Als u een stack opgeeft die niet bestaat, `Push-Location` maakt de stack.

- Als u wilt dat een locatie stack de huidige locatie stack is, gebruikt u de para meter ' Stacknaam ' van de `Set-Location` cmdlet.

De niet-genaamde standaard locatie stack is alleen volledig toegankelijk wanneer het de huidige locatie-stack is.
Als u een benoemde locatie stapelt de huidige locatie stack, kunt u de-cmdlets niet meer gebruiken `Push-Location` `Pop-Location` om items toe te voegen aan of te ontvangen van de standaard stack of gebruikt u de `Get-Location` cmdlet om de locaties in de niet-benoemde stack weer te geven. Gebruik de para meter van de **stack** naam van de `Set-Location` cmdlet met een waarde van `$null` of een lege teken reeks () om de ongewijzigde stack de huidige stack te maken `""` .

U kunt ook verwijzen naar `Push-Location` de ingebouwde alias `pushd` . Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.

De `Push-Location` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Get-locatie](Get-Location.md)

[Pop-locatie](Pop-Location.md)

[Set-Location](Set-Location.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
