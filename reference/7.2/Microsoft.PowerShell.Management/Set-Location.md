---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: ec6f69d1d4a0b382ceec26b9409d01501edb814f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706031"
---
# Set-Location

## SAMENVATTING
Hiermee stelt u de huidige werk locatie in op een opgegeven locatie.

## SYNTAXIS

### Pad (standaard)

```
Set-Location [[-Path] <String>] [-PassThru] [<CommonParameters>]
```

### LiteralPath

```
Set-Location -LiteralPath <String> [-PassThru] [<CommonParameters>]
```

### Stack

```
Set-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## BESCHRIJVING

`Set-Location`Met de cmdlet wordt de werk locatie ingesteld op een opgegeven locatie. Deze locatie kan een map, een submap, een register locatie of een pad naar de provider zijn.

Power shell 6,2 heeft ondersteuning toegevoegd voor `-` en `+` als waarde voor de para meter **Path** . Power shell houdt een geschiedenis bij van de laatste 20 locaties die kunnen worden gebruikt met `-` en `+` . Deze lijst is onafhankelijk van de locatie stack die wordt geopend met behulp van de para meter ' **stacknaam** '.

## VOORBEELDEN

### Voor beeld 1: de huidige locatie instellen

```
PS C:\> Set-Location -Path "HKLM:\"
PS HKLM:\>
```

Met deze opdracht wordt de huidige locatie ingesteld op de hoofdmap van het `HKLM:` station.

### Voor beeld 2: de huidige locatie instellen en de locatie weer geven

```
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```Output
Path
----
Env:\

PS Env:\>
```

Met deze opdracht wordt de huidige locatie ingesteld op de hoofdmap van het `Env:` station. De para meter **PassThru** wordt gebruikt om Power shell te sturen naar een **PathInfo** -object dat de `Env:\` locatie vertegenwoordigt.

### Voor beeld 3: locatie instellen op de huidige locatie in station C:

```powershell
PS C:\Windows\> Set-Location HKLM:\
PS HKLM:\> Set-Location C:
PS C:\Windows\>
```

Met de eerste opdracht wordt de locatie ingesteld op de hoofdmap van het `HKLM:` station in de register provider.
Met de tweede opdracht wordt de locatie ingesteld op de huidige locatie van het `C:` station in de File System Provider.
Als de naam van het station is opgegeven in de vorm `<DriveName>:` (zonder back slash), stelt de cmdlet de locatie in op de huidige locatie in de PSDrive.
Als u de huidige locatie wilt ophalen in de PSDrive use- `Get-Location -PSDrive <DriveName>` opdracht.

### Voor beeld 4: de huidige locatie instellen op een benoemde stack

```
PS C:\> Push-Location -Path 'C:\Program Files\PowerShell\' -StackName "Paths"
PS C:\Program Files\PowerShell\> Set-Location -StackName "Paths"
PS C:\Program Files\PowerShell\> Get-Location -Stack
```

```Output
Path
----
C:\
```

Met de eerste opdracht wordt de huidige locatie toegevoegd aan de paden-stack.
Met de tweede opdracht wordt de locatie van de paden stack de huidige locatie stack.
Met de derde opdracht worden de locaties in de huidige locatie stack weer gegeven.

De `*-Location` cmdlets gebruiken de huidige locatie stack, tenzij er een andere locatie stack is opgegeven in de opdracht. Zie de [opmerkingen](#notes)voor informatie over locatie stacks.

### Voor beeld 5: Navigeer naar locatie geschiedenis met `+` of `-`

```
PS C:\> Set-Location -Path $env:SystemRoot
PS C:\Windows> Set-Location -Path Cert:\
PS Cert:\> Set-Location -Path HKLM:\
PS HKLM:\>

# Navigate back through the history using "-"
PS HKLM:\> Set-Location -Path -
PS Cert:\> Set-Location -Path -
PS C:\Windows>

# Navigate using the Set-Location alias "cd" and the implicit positional Path parameter
PS C:\Windows> cd -
PS C:\> cd +
PS C:\Windows> cd +
PS Cert:\>
```

Met behulp van de alias `cd -` of `cd +` is een eenvoudige manier om door uw locatie geschiedenis te navigeren in uw Terminal. `-` / `+` Zie de para meter **Path** voor meer informatie over navigeren met.

## PARAMETERS

### -LiteralPath

Hiermee geeft u een pad naar de locatie. De waarde van de para meter **LiteralPath** wordt precies zo gebruikt als deze wordt getypt. Er worden geen tekens geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Retourneert een **PathInfo** -object dat de locatie vertegenwoordigt. Deze cmdlet genereert standaard geen uitvoer.

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

Geef het pad op van een nieuwe werk locatie. Als u geen pad opgeeft, wordt `Set-Location` standaard de basismap van de huidige gebruiker gebruikt. Wanneer joker tekens worden gebruikt, kiest de cmdlet het eerste pad dat overeenkomt met het Joker teken patroon.

Power shell houdt een geschiedenis bij van de laatste 20 locaties die u hebt ingesteld. Als de waarde van de para meter **Path** het `-` teken is, wordt de nieuwe werk locatie de vorige werk locatie in de geschiedenis (als deze bestaat). Op dezelfde manier geldt dat als de waarde het `+` teken is, de nieuwe werk locatie de volgende werk locatie in de geschiedenis is (indien aanwezig). Dit is vergelijkbaar met `Pop-Location` en `Push-Location` behalve dat de geschiedenis een lijst is, niet een stack en wordt impliciet gevolgd en niet hand matig wordt gecontroleerd. Op dit moment is er geen manier om de geschiedenis lijst weer te geven.

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Stacknaam

Hiermee geeft u de naam van de bestaande locatie stapel op die met deze cmdlet de huidige locatie stack maakt. Voer de naam van de locatie stack in. Typ `$null` of een lege teken reeks () om de niet-naam standaard locatie stack aan te duiden `""` .

De `*-Location` cmdlets handelen op de huidige stack, tenzij u de para meter van de **stacknaam** gebruikt om een andere stack op te geven. Zie de [opmerkingen](#notes)voor meer informatie over locatie stacks.

```yaml
Type: System.String
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks die een pad bevat, maar geen letterlijk pad, naar deze cmdlet pipet.

## UITVOER

### Geen, System. Management. Automation. PathInfo, System. Management. Automation. PathInfoStack

Met deze cmdlet wordt geen uitvoer gegenereerd tenzij u de para meter **PassThru** opgeeft. Met behulp van **PassThru** met **Path** of **LiteralPath** wordt een **PathInfo** -object gegenereerd dat de nieuwe locatie vertegenwoordigt. Het gebruik van **PassThru** met de **stack** naam genereert een **PathInfoStack** -object dat de nieuwe stack context vertegenwoordigt.

## OPMERKINGEN

Power shell ondersteunt meerdere runspaces per proces. Elke runs Pace heeft zijn eigen _huidige map_.
Dit is niet hetzelfde als `[System.Environment]::CurrentDirectory` . Dit gedrag kan een probleem zijn bij het aanroepen van .NET-Api's of het uitvoeren van systeem eigen toepassingen zonder expliciete mappaden te bieden.

Zelfs als de locatie-cmdlets de huidige map voor het gehele proces hebben ingesteld, kunt u er niet op vertrouwen, omdat deze op elk gewenst moment door een andere runs Pace kan worden gewijzigd. U moet de locatie-cmdlets gebruiken om op paden gebaseerde bewerkingen uit te voeren op basis van de huidige werkmap die specifiek is voor de huidige-runs Pace.

De `Set-Location` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md)voor meer informatie.

Een stack is een laatste-in-lijst waarin alleen het laatst toegevoegde item kan worden geopend. U voegt items toe aan een stack in de volg orde waarin u ze gebruikt en haalt deze vervolgens op voor gebruik in de omgekeerde volg orde. Met Power shell kunt u locatie locaties opslaan in site-stacks. Power Shell maakt een niet-genaamde standaard locatie van de stack. U kunt meerdere benoemde locatie stapels maken. Als u geen stack naam opgeeft, gebruikt Power shell de huidige locatie stack. Standaard is de niet-naam standaard locatie de huidige locatie stack, maar u kunt de `Set-Location` cmdlet gebruiken om de huidige locatie stack te wijzigen.

Als u locatie stacks wilt beheren, gebruikt u de `*-Location` -cmdlets, als volgt:

- Gebruik de cmdlet om een locatie aan een locatie stack toe te voegen `Push-Location` .

- Als u een locatie wilt ophalen uit een locatie stack, gebruikt u de `Pop-Location` cmdlet.

- Als u de locaties wilt weer geven in de huidige locatie stack, gebruikt u de para meter **stack** van de `Get-Location` cmdlet. Als u de locaties wilt weer geven in een benoemde locatie stack, gebruikt u de para meter ' **stack** naam ' van `Get-Location` .

- Als u een nieuwe locatie stapel wilt maken, gebruikt u de para meter ' **stacknaam** ' van `Push-Location` . Als u een stack opgeeft die niet bestaat, `Push-Location` maakt de stack.

- Als u een locatie wilt stapelen de huidige locatie stack, gebruikt u de para meter ' **stacknaam** ' van `Set-Location` .

De niet-genaamde standaard locatie stack is alleen volledig toegankelijk wanneer het de huidige locatie-stack is.
Als u een benoemde locatie stapelt de huidige locatie stack, kunt u de-cmdlets niet meer gebruiken `Push-Location` `Pop-Location` om items toe te voegen aan of te ontvangen van de standaard stack of gebruikt u de `Get-Location` cmdlet om de locaties in de niet-benoemde stack weer te geven. Gebruik de para meter van de **stack** naam van de `Set-Location` cmdlet met een waarde van `$null` of een lege teken reeks () om de ongewijzigde stack de huidige stack te maken `""` .

## GERELATEERDE KOPPELINGEN

[Get-locatie](Get-Location.md)

[Pop-locatie](Pop-Location.md)

[Push-locatie](Push-Location.md)

