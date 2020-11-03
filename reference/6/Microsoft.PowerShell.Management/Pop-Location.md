---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/pop-location?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Pop-Location
ms.openlocfilehash: 42a5c9c75c11a40b5bb842d86894688a354bed15
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2020
ms.locfileid: "93251728"
---
# Pop-Location

## SAMENVATTING
Hiermee wordt de huidige locatie gewijzigd in de locatie die het laatst is gepusht naar de stack.

## SYNTAXIS

```
Pop-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## BESCHRIJVING

`Pop-Location`Met de cmdlet wordt de huidige locatie gewijzigd in de locatie die het laatst is gepusht naar de stack met behulp van de- `Push-Location` cmdlet. U kunt een locatie van de standaard stack of van een stack die u maakt met behulp van een `Push-Location` opdracht.

## VOORBEELDEN

### Voor beeld 1: overschakelen naar de meest recente locatie

```
PS C:\> Pop-Location
```

Met deze opdracht wordt uw locatie gewijzigd in de locatie die het laatst aan de huidige stack is toegevoegd.

### Voor beeld 2: wijzigen naar de meest recente locatie in een benoemde stack

```
PS C:\> Pop-Location -StackName "Stack2"
```

Met deze opdracht wordt uw locatie gewijzigd in de locatie die het laatst is toegevoegd aan de Stack2-locatie stack.

Zie de [opmerkingen](#notes)voor meer informatie over locatie stacks.

### Voor beeld 3: verplaatsen tussen locaties voor verschillende providers

```
PS C:\> pushd HKLM:\Software\Microsoft\PowerShell
PS HKLM:\Software\Microsoft\PowerShell> pushd Cert:\LocalMachine\TrustedPublisher
PS cert:\LocalMachine\TrustedPublisher> popd
PS HKLM:\Software\Microsoft\PowerShell> popd
PS C:\>
```

Met deze opdrachten worden de- `Push-Location` en- `Pop-Location` cmdlets gebruikt om te scha kelen tussen locaties die door verschillende Power shell-providers worden ondersteund. De opdrachten gebruiken de `pushd` alias voor `Push-Location` en de `popd` alias voor `Pop-Location` .

Met de eerste opdracht wordt de huidige locatie van het bestands systeem naar de stack gepusht en verplaatst naar het HKLM-station dat wordt ondersteund door de Power shell-register provider.

Met de tweede opdracht wordt de register locatie naar de stack gepusht en verplaatst naar een locatie die wordt ondersteund door de Power shell-certificaat provider.

De laatste twee opdrachten hebben een pop die de locaties van de stack. De eerste `popd` opdracht keert terug naar het register station en de tweede opdracht keert terug naar het bestandssysteem station.

## PARAMETERS

### -PassThru

Hiermee wordt een object door gegeven dat de locatie van de pijp lijn vertegenwoordigt. Deze cmdlet genereert standaard geen uitvoer.

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

### -Stacknaam

Hiermee geeft u de locatie stapel op van waaruit de locatie wordt opvolgd. Voer de naam van de locatie stack in.

Zonder deze para meter wordt `Pop-Location` een locatie uit de huidige locatie stack weer gegeven. Standaard is de huidige locatie stack de niet-genaamde standaard locatie stack die Power Shell maakt. Als u wilt dat een locatie stack de huidige locatie stack is, gebruikt u de para meter ' **stacknaam** ' van de `Set-Location` cmdlet. Zie de [opmerkingen](#notes)voor meer informatie over locatie stacks.

`Pop-Location` kan geen locatie van de niet-genaamde standaard stack hebben als dit de huidige locatie stack is.

```yaml
Type: System.String
Parameter Sets: (All)
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

### Geen, System. Management. Automation. PathInfo

Met deze cmdlet wordt een **System. Management. Automation. PathInfo** -object gegenereerd dat de locatie vertegenwoordigt, als u de para meter **PassThru** opgeeft. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

Power shell ondersteunt meerdere runspaces per proces. Elke runs Pace heeft zijn eigen _huidige map_.
Dit is niet hetzelfde als `[System.Environment]::CurrentDirectory` . Dit gedrag kan een probleem zijn bij het aanroepen van .NET-Api's of het uitvoeren van systeem eigen toepassingen zonder expliciete mappaden te bieden.

Zelfs als de locatie-cmdlets de huidige map voor het gehele proces hebben ingesteld, kunt u er niet op vertrouwen, omdat deze op elk gewenst moment door een andere runs Pace kan worden gewijzigd. U moet de locatie-cmdlets gebruiken om op paden gebaseerde bewerkingen uit te voeren op basis van de huidige werkmap die specifiek is voor de huidige-runs Pace.

Een stack is een laatste-in-lijst waarin alleen het laatst toegevoegde item kan worden geopend. U voegt items toe aan een stack in de volg orde waarin u ze gebruikt en haalt deze vervolgens op voor gebruik in de omgekeerde volg orde. Met Power shell kunt u locatie locaties opslaan in site-stacks.

In Power shell wordt een niet-benoemde standaard locatie stack gemaakt en u kunt meerdere naam locatie stacks maken. Als u geen stack naam opgeeft, gebruikt Power shell de huidige locatie stack. Standaard is de niet-naam standaard locatie de huidige locatie stack, maar u kunt de `Set-Location` cmdlet gebruiken om de huidige locatie stack te wijzigen.

Als u locatie stacks wilt beheren, gebruikt u de Power shell `*-Location` -cmdlets, als volgt:

- Gebruik de cmdlet om een locatie aan een locatie stack toe te voegen `Push-Location` .

- Als u een locatie wilt ophalen uit een locatie stack, gebruikt u de `Pop-Location` cmdlet.

- Als u de locaties wilt weer geven in de huidige locatie stack, gebruikt u de para meter **stack** van de `Get-Location` cmdlet.

- Als u de locaties wilt weer geven in een benoemde locatie stack, gebruikt u de para meter ' **stack** naam ' van de `Get-Location` cmdlet.

- Als u een nieuwe locatie stack wilt maken, gebruikt u de para meter ' **stacknaam** ' van de `Push-Location` cmdlet. Als u een stack opgeeft die niet bestaat, `Push-Location` maakt de stack.

- Als u wilt dat een locatie stack de huidige locatie stack is, gebruikt u de para meter ' **stacknaam** ' van de `Set-Location` cmdlet.

De niet-genaamde standaard locatie stack is alleen volledig toegankelijk wanneer het de huidige locatie-stack is.
Als u een benoemde locatie stapelt de huidige locatie stack, kunt u de-cmdlets niet meer gebruiken `Push-Location` `Pop-Location` om items toe te voegen aan of te ontvangen van de standaard stack of gebruikt u de `Get-Location` cmdlet om de locaties in de niet-benoemde stack weer te geven. Gebruik de para meter van de **stack** naam van de `Set-Location` cmdlet met een waarde van `$Null` of een lege teken reeks () om de ongewijzigde stack de huidige stack te maken `""` .

U kunt ook verwijzen naar `Pop-Location` de ingebouwde alias `popd` . Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.

`Pop-Location` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Get-locatie](Get-Location.md)

[Push-locatie](Push-Location.md)

[Set-Location](Set-Location.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
