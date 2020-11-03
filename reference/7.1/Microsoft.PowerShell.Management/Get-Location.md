---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-location?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Location
ms.openlocfilehash: 79d6337574c2e354e49926fa894415fca2469ba7
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/14/2020
ms.locfileid: "93251824"
---
# Get-Location

## SAMENVATTING
Hiermee haalt u informatie op over de huidige werk locatie of een locatie stack.

## SYNTAXIS

### Locatie (standaard)

```
Get-Location [-PSProvider <String[]>] [-PSDrive <String[]>] [<CommonParameters>]
```

### Stack

```
Get-Location [-Stack] [-StackName <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Location` cmdlet haalt een object op dat de huidige map vertegenwoordigt, net als de opdracht Print Directory (PWD).

Wanneer u overstapt tussen Power Shell-stations, behoudt Power shell uw locatie in elk station. U kunt deze cmdlet gebruiken om uw locatie in elk station te vinden.

U kunt deze cmdlet gebruiken om de huidige map tijdens runtime op te halen en deze te gebruiken in functies en scripts, zoals in een functie die de huidige map in de Power shell-prompt weergeeft.

U kunt deze cmdlet ook gebruiken om de locaties in een locatie stack weer te geven. Zie voor meer informatie de opmerkingen en beschrijvingen van de para meters **stack** en **stack** .

## VOORBEELDEN

### Voor beeld 1: de huidige locatie van uw station weer geven

Met deze opdracht wordt uw locatie in het huidige Power Shell-station weer gegeven.

```powershell
PS C:\Windows> Get-Location
```

```Output
Path
----
C:\Windows
```

Bijvoorbeeld, als u zich in de `Windows` map van het station bevindt `C:` , wordt het pad naar die map weer gegeven.

### Voor beeld 2: uw huidige locatie weer geven voor verschillende stations

In dit voor beeld ziet u hoe `Get-Location` u uw huidige locatie in verschillende Power Shell-stations kunt weer geven. `Set-Location` wordt gebruikt om de locatie te wijzigen in verschillende paden op verschillende PSDrives.

```powershell
PS C:\> Set-Location C:\Windows
PS C:\Windows> Set-Location HKLM:\Software\Microsoft
PS HKLM:\Software\Microsoft> Set-Location "HKCU:\Control Panel\Input Method"
PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive C

Path
----
C:\Windows

PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive HKLM

Path
----
HKLM:\Software\Microsoft

PS HKCU:\Control Panel\Input Method> Set-Location C:
PS C:\Windows> Get-Location -PSProvider Registry

Path
----
HKCU:\Control Panel\Input Method
```

### Voor beeld 3: locaties ophalen met stacks

Dit voor beeld laat zien hoe u de **stack** -en **stack** -para meters van `Get-Location` kunt gebruiken om de locaties in de huidige locatie stack en alternatieve locatie stacks weer te geven.

De `Push-Location` cmdlet wordt gebruikt om te wijzigen in drie verschillende locaties. De derde push maakt gebruik van een andere stack naam. Met de **stack** parameter van `Get-Location` wordt de inhoud van de standaard stack weer gegeven. Met de para meter ' **stack** naam `Get-Location` ' wordt de inhoud van de stack weer gegeven `Stack2` .

```powershell
PS C:\> Push-Location C:\Windows
PS C:\Windows>Push-Location System32
PS C:\Windows\System32>Push-Location WindowsPowerShell -StackName Stack2
C:\Windows\System32\WindowsPowerShell>Get-Location -Stack

Path
----
C:\Windows
C:\

C:\Windows\System32\WindowsPowerShell>Get-Location -StackName Stack2

Path
----
C:\Windows\System32
```

### Voor beeld 4: de Power shell-prompt aanpassen

In dit voor beeld ziet u hoe u de Power shell-prompt aanpast.

```powershell
PS C:\>
function prompt { 'PowerShell: ' + (Get-Location) + '> '}
PowerShell: C:\>
```

De functie die de prompt definieert, bevat een `Get-Location` opdracht, die wordt uitgevoerd wanneer de prompt wordt weer gegeven in de-console.

De indeling van de standaard Power shell-prompt wordt gedefinieerd door een speciale functie met de naam `prompt` . U kunt de prompt in uw console wijzigen door een nieuwe functie te maken met de naam `prompt` .

Typ de volgende opdracht om de huidige prompt functie te bekijken: `Get-Content Function:\prompt`

## PARAMETERS

### -PSDrive

Hiermee wordt de huidige locatie in het opgegeven Power Shell-station opgehaald.

Als u bijvoorbeeld zich in het station bevindt `Cert:` , kunt u deze para meter gebruiken om uw huidige locatie in het station te vinden `C:` .

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

Hiermee wordt de huidige locatie opgehaald in het station dat wordt ondersteund door de opgegeven Power shell-provider.
Als de opgegeven provider meer dan één station ondersteunt, retourneert deze cmdlet de locatie op het meest recent geopende station.

Als u zich bijvoorbeeld in het station bevindt `C:` , kunt u deze para meter gebruiken om uw huidige locatie te vinden in de stations van de Power shell- **register** provider.

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Stack

Geeft aan dat met deze cmdlet de locaties worden weer gegeven die worden toegevoegd aan de huidige locatie stack. U kunt locaties toevoegen aan stacks met behulp van de- `Push-Location` cmdlet.

Als u de locaties wilt weer geven in een andere locatie stack, gebruikt u de para meter ' **stacknaam** '. Zie de [opmerkingen](#notes)voor informatie over locatie stacks.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Stacknaam

Hiermee geeft u als een teken reeks matrix de benoemde locatie stapels op. Voer een of meer locatie-stack namen in.

Als u de locaties in de huidige locatie stack wilt weer geven, gebruikt u de **stack** -para meter. Als u een locatie wilt stapelen de huidige locatie stack, gebruikt u de `Set-Location` cmdlet.

Met deze cmdlet kunnen de locaties in de niet-genaamde standaard stack niet worden weer gegeven, tenzij dit de huidige stack is.

```yaml
Type: System.String[]
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

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. Management. Automation. PathInfo of System. Management. Automation. PathInfoStack

Als u de **stack** -of para meters voor de **stack** naam gebruikt, retourneert deze cmdlet een **PathInfoStack** -object. Anders wordt een **PathInfo** -object geretourneerd.

## OPMERKINGEN

Power shell ondersteunt meerdere runspaces per proces. Elke runs Pace heeft zijn eigen _huidige map_.
Dit is niet hetzelfde als `[System.Environment]::CurrentDirectory` . Dit gedrag kan een probleem zijn bij het aanroepen van .NET-Api's of het uitvoeren van systeem eigen toepassingen zonder expliciete mappaden te bieden.
`Get-Location`Met de cmdlet wordt de huidige map van de huidige Power shell-runs Pace geretourneerd.

Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Typ om de providers in uw sessie weer te geven `Get-PSProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

De manieren waarop de **PSProvider** -, **PSDrive** -, **stack** -en **stack** -para meters communiceren, zijn afhankelijk van de provider. Sommige combi Naties leiden tot fouten, zoals het opgeven van een station en een provider die dat station niet beschikbaar maakt. Als er geen para meters zijn opgegeven, retourneert deze cmdlet het **PathInfo** -object voor de provider die de huidige werk locatie bevat.

Een stack is een vervolg keuzelijst die het laatst is toegevoegd en die alleen toegankelijk is voor het laatst toegevoegde item. U voegt items toe aan een stack in de volg orde waarin u ze gebruikt en haalt deze vervolgens op voor gebruik in de omgekeerde volg orde. Met Power shell kunt u locatie locaties opslaan in site-stacks. In Power shell wordt een niet-benoemde standaard locatie stack gemaakt en u kunt meerdere naam locatie stacks maken. Als u geen stack naam opgeeft, gebruikt Power shell de huidige locatie stack. Standaard is de niet-naam standaard locatie de huidige locatie stack, maar u kunt de `Set-Location` cmdlet gebruiken om de huidige locatie stack te wijzigen.

Als u locatie stacks wilt beheren, gebruikt u de Power shell `*-Location` -cmdlets, als volgt.

- Gebruik de cmdlet om een locatie aan een locatie stack toe te voegen `Push-Location` .

- Als u een locatie wilt ophalen uit een locatie stack, gebruikt u de `Pop-Location` cmdlet.

- Als u de locaties wilt weer geven in de huidige locatie stack, gebruikt u de para meter **stack** van de `Get-Location` cmdlet. Als u de locaties wilt weer geven in een benoemde locatie stack, gebruikt u de para meter ' **stack** naam ' van de `Get-Location` cmdlet.

- Als u een nieuwe locatie stack wilt maken, gebruikt u de para meter ' **stacknaam** ' van de `Push-Location` cmdlet.
  Als u een stack opgeeft die niet bestaat, `Push-Location` maakt de stack.

- Als u wilt dat een locatie stack de huidige locatie stack is, gebruikt u de para meter ' **stacknaam** ' van de `Set-Location` cmdlet.

De niet-genaamde standaard locatie stack is alleen volledig toegankelijk wanneer het de huidige locatie-stack is.
Als u een benoemde locatie stapelt de huidige locatie stack, kunt u de-cmdlets niet meer gebruiken `Push-Location` `Pop-Location` om items toe te voegen aan of te ontvangen van de standaard stack of gebruikt u deze cmdlet om de locaties in de niet-benoemde stack weer te geven. Gebruik de para meter van de **stack** naam van de `Set-Location` cmdlet met een waarde van `$null` of een lege teken reeks () om de ongewijzigde stack de huidige stack te maken `""` .

## GERELATEERDE KOPPELINGEN

[Pop-locatie](Pop-Location.md)

[Push-locatie](Push-Location.md)

[Set-Location](Set-Location.md)

