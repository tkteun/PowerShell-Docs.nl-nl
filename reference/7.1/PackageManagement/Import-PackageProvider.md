---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: 428cb3afa574345ef5cb4b79b76b31cf9bfb2e7b
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890076"
---
# Import-PackageProvider

## SAMENVATTING
Voegt pakket beheer pakket providers toe aan de huidige sessie.

## SYNTAXIS

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## BESCHRIJVING

De `Import-PackageProvider` cmdlet voegt een of meer pakket providers toe aan de huidige sessie.
De provider die u importeert, moet op de lokale computer zijn geïnstalleerd.

Voer uit om een lijst met beschik bare providers te verkrijgen `Get-PackageProvider -ListAvailable` .
Houd er rekening mee dat de naam van een pakket provider kan afwijken van de module naam.

Om veiligheids redenen vereist **Package Management** dat C#-providers een bevatten `provider.manifest` . `provider.manifest`Zie de `.csproj` Project bestanden op voor meer informatie over het bouwen van een provider met injected [https://github.com/oneget/oneget](https://github.com/oneget/oneget) .

## VOORBEELDEN

### Voor beeld 1: een pakket provider importeren van de lokale computer

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

Met deze opdracht wordt de Nuget-provider geïmporteerd nadat deze is geïnstalleerd op de lokale computer.

### Voor beeld 2: een specifieke versie van een pakket provider importeren

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

Met deze opdracht wordt een specifieke versie van de Nuget-pakket provider gevonden, geïnstalleerd en geïmporteerd.

## PARAMETERS

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.
Hiermee wordt een pakket provider opnieuw geïmporteerd.

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

### -MaximumVersion

Hiermee geeft u de Maxi maal toegestane versie van de pakket provider die u wilt importeren. Als u deze para meter niet toevoegt, wordt `Import-PackageProvider` de hoogste beschik bare versie van de provider geïmporteerd.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumVersion

Hiermee geeft u de mini maal toegestane versie van de pakket provider die u wilt importeren. Als u deze para meter niet toevoegt, wordt `Import-PackageProvider` de hoogste beschik bare versie van het pakket geïmporteerd die ook voldoet aan de maximum versie die is opgegeven met behulp van de para meter *MaximumVersion* .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een of meer pakket provider namen op. Joker tekens zijn niet toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

Hiermee geeft u de exacte versie van de pakket provider die u wilt importeren. Als u deze para meter niet toevoegt, wordt `Import-PackageProvider` de hoogste beschik bare versie van de provider geïmporteerd die ook voldoet aan de maximum versie die is opgegeven met behulp van de para meter **MaximumVersion** .

```yaml
Type: System.String
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

### Micro soft. package management. Implementation. package provider

U kunt een **package provider** -object dat wordt geretourneerd door `Get-PackageProvider` in `Import-PackageProvider` .

## UITVOER

## OPMERKINGEN

> [!IMPORTANT]
> Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1. Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery. Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.

## GERELATEERDE KOPPELINGEN

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Registratie ongedaan maken-PackageSource](Unregister-PackageSource.md)

[Get-PackageSource](Get-PackageSource.md)

[REGI ster-PackageSource](Register-PackageSource.md)

[Get-PackageProvider](Get-PackageProvider.md)
