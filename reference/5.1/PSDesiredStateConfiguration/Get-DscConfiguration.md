---
external help file: Get-DSCConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfiguration
ms.openlocfilehash: 42b24e72de4c4bcc9326d52861c08a05853b18e0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250780"
---
# Get-DscConfiguration

## SAMENVATTING
Hiermee wordt de huidige configuratie van de knoop punten opgehaald.

## SYNTAXIS

```
Get-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Get-DscConfiguration** wordt de huidige configuratie van de knoop punten opgehaald als de configuratie bestaat.
Geef computers op met behulp van Common Information Model (CIM)-sessies.
Als u geen doel computer opgeeft, wordt de configuratie door de cmdlet opgehaald van de lokale computer.

## VOORBEELDEN

### Voor beeld 1: de configuratie voor de lokale computer ophalen

```
PS C:\> Get-DscConfiguration
```

Met deze opdracht wordt de huidige status voor de lokale computer opgehaald.

### Voor beeld 2: de configuratie voor een opgegeven computer ophalen

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Get-DscConfiguration -CimSession $Session
```

In dit voor beeld wordt de huidige status opgehaald van een computer die is opgegeven door een CIM-sessie.
In het voor beeld wordt een CIM-sessie voor een computer met de naam Server01 gemaakt voor gebruik met de cmdlet.
U kunt ook een matrix met CIM-sessies maken om de cmdlet op meerdere opgegeven computers toe te passen.

Met de eerste opdracht maakt u een CIM-sessie met behulp van de cmdlet **New-CimSession** en slaat u het **CimSession** -object op in de variabele **$Session** .
De opdracht vraagt u om een wacht woord.
Typ `Get-Help New-CimSession` voor meer informatie.

Met de tweede opdracht wordt de huidige configuratie opgehaald voor de computers die worden geïdentificeerd door de **CimSession** -objecten die zijn opgeslagen in de variabele **$Session** , in dit geval de computer met de naam Server01.

## PARAMETERS

### -AsJob
Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak.

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

### -CimSession
Voert de cmdlet uit in een externe sessie of op een externe computer.
Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) of [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) .
De standaard waarde is de huidige sessie op de lokale computer.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.
Als deze para meter wordt wegge laten of een waarde van `0` wordt ingevoerd, wordt in Windows Power shell een optimale bandbreedte limiet voor de cmdlet berekend op basis van het aantal CIM-cmdlets dat op de computer wordt uitgevoerd.
De beperkings limiet geldt alleen voor de huidige cmdlet, niet voor de sessie of voor de computer.

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

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Overzicht van desired state Configuration voor Windows Power shell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
