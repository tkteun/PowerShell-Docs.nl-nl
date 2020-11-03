---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packageprovider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageProvider
ms.openlocfilehash: 43f70d400cc2d9b81e2bf59a6d2b3bb986737c69
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249573"
---
# Get-PackageProvider

## SAMENVATTING
Retourneert een lijst met pakket providers die zijn verbonden met pakket beheer.

## SYNTAXIS

```
Get-PackageProvider [[-Name] <String[]>] [-ListAvailable] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet **Get-package provider** retourneert een lijst met pakket providers die zijn verbonden met pakket beheer.
Voor beelden van deze providers zijn PSModule, NuGet en Choco lade.
U kunt de resultaten filteren op basis van alle of een deel van een of meer provider namen.

## VOORBEELDEN

### Voor beeld 1: alle momenteel geladen pakket providers ophalen

```
PS C:\> Get-PackageProvider
```

Met deze opdracht wordt een lijst opgehaald van alle pakket providers die momenteel zijn geladen op de lokale computer.

### Voor beeld 2: alle beschik bare pakket providers ophalen

```
PS C:\> Get-PackageProvider -ListAvailable
```

Met deze opdracht wordt een lijst opgehaald van alle pakket providers die beschikbaar zijn op de lokale computer.

### Voor beeld 3: dynamisch een pakket provider ophalen

```
PS C:\> Get-PackageProvider -Name "Chocolatey" -ForceBootstrap
```

Met deze opdracht wordt de chocolade-provider automatisch geïnstalleerd als de chocolade-provider niet is geïnstalleerd op de computer.

## PARAMETERS

### -Force

Geeft aan dat deze cmdlet alle andere acties met deze cmdlet afdwingt die kunnen worden geforceerd.
In **Get-package provider** betekent dit dat de para meter *Forces* hetzelfde is als de para meter *ForceBootstrap* .

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

### -ForceBootstrap

Geeft aan dat deze cmdlet pakket beheer afdwingt om de pakket provider automatisch te installeren.

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

### -ListAvailable

Hiermee worden alle geïnstalleerde providers opgehaald.
**Get-package provider** haalt de provider op in paden die worden vermeld in de omgevings variabele **PSModulePath** en de assembly mappen van de pakket provider:

**$env:P rogramfiles\packagemanagement\providerassemblies** **$env: LOCALAPPDATA\PackageManagement\ProviderAssemblies**

Zonder deze para meter worden met **Get-package provider** alleen de providers opgehaald die in de huidige sessie zijn geladen.

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

### -Name

Hiermee geeft u een of meer provider namen of gedeeltelijke provider namen op.
Scheid meerdere provider namen met komma's.
Geldige waarden voor deze para meter zijn namen van providers die u hebt geïnstalleerd met pakketten. Package Management wordt geleverd met een set standaard providers, met inbegrip van de **PSModule** -en **MSI** -providers.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

### Package provider []

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Get-PackageSource](Get-PackageSource.md)

[REGI ster-PackageSource](Register-PackageSource.md)

[Registratie ongedaan maken-PackageSource](Unregister-PackageSource.md)
