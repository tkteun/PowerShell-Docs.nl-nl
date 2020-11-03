---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscresource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscResource
ms.openlocfilehash: d710881f4444a35bd1dca7950292660889a3e38c
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/24/2020
ms.locfileid: "93251679"
---
# Get-DscResource

## SAMENVATTING
Hiermee worden de resources voor desired state Configuration (DSC) aanwezig op de computer.

## SYNTAXIS

```
Get-DscResource [[-Name] <String[]>] [[-Module] <Object>] [-Syntax] [<CommonParameters>]
```

## BESCHRIJVING

`Get-DscResource`Met de cmdlet worden de Power shell DSC-resources opgehaald die aanwezig zijn op de computer. Met deze cmdlet worden alleen de resources gedetecteerd die in de PSModulePath zijn geïnstalleerd. Hierin worden de details weer gegeven van ingebouwde en aangepaste providers die door de gebruiker zijn gemaakt. Met deze cmdlet wordt ook informatie over samengestelde resources weer gegeven. Dit zijn andere configuraties die zijn verpakt als module of tijdens runtime worden gemaakt in de sessie.

## VOORBEELDEN

### Voor beeld 1: alle resources op de lokale computer ophalen

```powershell
 Get-DscResource
```

Met deze opdracht worden alle resources op de lokale computer opgehaald.

### Voor beeld 2: een resource ophalen door de naam op te geven

```powershell
Get-DscResource -Name "WindowsFeature"
```

Met deze opdracht wordt de resource WindowsFeature opgehaald.

### Voor beeld 3: alle resources uit een module ophalen

```powershell
Get-DscResource -Module "xHyper-V"
```

Met deze opdracht worden alle resources opgehaald uit de xHyper-V-module.

### Voor beeld 4: een resource ophalen met behulp van joker tekens

```powershell
Get-DscResource -Name P*,r*
```

Met deze opdracht worden alle resources opgehaald die overeenkomen met het Joker teken patroon dat is opgegeven door de para meter **name** .

### Voor beeld 5: een resource syntaxis ophalen

```powershell
Get-DscResource -Name "WindowsFeature" -Syntax
```

Met deze opdracht wordt de resource WindowsFeature opgehaald en wordt de syntaxis voor de resource weer gegeven.

### Voor beeld 6: alle eigenschappen voor een resource ophalen

```powershell
Get-DscResource -Name "User" | Select-Object -ExpandProperty Properties
```

Met deze opdracht wordt de gebruikers bron opgehaald, waarna de pijplijn operator wordt gebruikt om alle eigenschappen voor de gebruikers bron te retour neren.

### Voor beeld 7: alle resources van een opgegeven module ophalen met een opgegeven versie

```powershell
Get-DscResource -Module @{ModuleName='xHyper-V';RequiredVersion='3.0.0.0'}
```

Met deze opdracht worden alle resources opgehaald uit de xHyper-V-module met versie 3.0.0.0.

## PARAMETERS

### -Module

Hiermee geeft u de naam of de volledig gekwalificeerde naam van de module waarvoor u de DSC-resource wilt weer geven.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een matrix met namen van de DSC-resource op die u wilt weer geven.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Syntaxis

Geeft aan dat de cmdlet de syntaxis weergave van de opgegeven DSC-resources retourneert. De geretourneerde syntaxis laat zien hoe u de resources in een Power shell-script gebruikt.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System.String[]

### System. object

## UITVOER

### Micro soft. Power shell. DesiredStateConfiguration. DscResourceInfo []

### teken reeks []

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Overzicht van desired state Configuration van Power shell](/powershell/scripting/dsc/overview/overview)

[Invoke-Dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
