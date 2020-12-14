---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageProvider
ms.openlocfilehash: fd8325f1a68755ee1b5c05719a04e71b22a7e9fd
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889487"
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

**$env:P rogramFiles\PackageManagement\ProviderAssemblies * * * * $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies**

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

> [!IMPORTANT]
> Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1. Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery. Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.

## GERELATEERDE KOPPELINGEN

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Get-PackageSource](Get-PackageSource.md)

[REGI ster-PackageSource](Register-PackageSource.md)

[Registratie ongedaan maken-PackageSource](Unregister-PackageSource.md)
