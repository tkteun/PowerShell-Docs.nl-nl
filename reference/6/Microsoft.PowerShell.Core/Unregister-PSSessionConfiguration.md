---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/unregister-pssessionconfiguration?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSSessionConfiguration
ms.openlocfilehash: f9cc2f83ec0fca1c957c670e13ac7b455c322adb
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345338"
---
# Unregister-PSSessionConfiguration

## SAMENVATTING
Hiermee verwijdert u geregistreerde sessie configuraties van de computer.

## SYNTAXIS

```
Unregister-PSSessionConfiguration [-Name] <String> [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

`Unregister-PSSessionConfiguration`Met de cmdlet worden geregistreerde sessie configuraties van de computer verwijderd. Deze cmdlet is ontworpen voor systeem beheerders voor het beheren van aangepaste sessie configuraties voor gebruikers.

`Unregister-PSSessionConfiguration`Start de **WinRM** -service opnieuw om de wijziging van kracht te laten worden. Geef de para meter **NoServiceRestart** op om het opnieuw opstarten te voor komen.

Als u per ongeluk de standaard **micro soft. Power shell** -of **micro soft. PowerShell32** -sessie configuraties verwijdert, gebruikt u de `Enable-PSRemoting` cmdlet om ze te herstellen. Zie [about_Session_Configurations](About/about_Session_Configurations.md)voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: een sessie configuratie verwijderen

In dit voor beeld wordt de **MaintenanceShell** -sessie configuratie van de computer verwijderd.

```powershell
Unregister-PSSessionConfiguration -Name "MaintenanceShell"
```

### Voor beeld 2: een sessie configuratie verwijderen en de WinRM-service opnieuw starten

In dit voor beeld wordt de **MaintenanceShell** -configuratie verwijderd en wordt de WinRM-service opnieuw gestart. De **Force** -para meter onderdrukt alle gebruikers berichten om de **WinRM** -service opnieuw te starten zonder dat dit wordt gevraagd.

```powershell
Unregister-PSSessionConfiguration -Name MaintenanceShell -Force
```

### Voor beeld 3: alle sessie configuraties verwijderen

In deze voor beelden ziet u twee manieren om alle sessie configuraties op de computer te verwijderen. Beide opdrachten hebben hetzelfde effect en kunnen door elkaar worden gebruikt.

```
Unregister-PSSessionConfiguration -Name *
Get-PSSessionConfiguration -Name * | Unregister-PSSessionConfiguration
```

### Voor beeld 4: de registratie ongedaan maken zonder opnieuw op te starten

In dit voor beeld ziet u het effect van het gebruik van de para meter **NoServiceRestart** om te voor komen dat een service opnieuw wordt gestart, waardoor sessies op de computer worden verstoord.

```
PS> Unregister-PSSessionConfiguration -Name "MaintenanceShell" -NoServiceRestart
PS> Get-PSSessionConfiguration -Name "MaintenanceShell"

Get-PSSessionConfiguration -Name MaintenanceShell : No Session Configuration matches criteria "MaintenanceShell".
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

PS> New-PSSession -ConfigurationName "MaintenanceShell"

Id Name      ComputerName    State    Configuration         Availability
-- ----      ------------    -----    -------------         ------------
1 Session1  localhost       Opened   MaintenanceShell      Available

PS> Restart-Service winrm
PS> New-PSSession -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message :
 The WS-Management service cannot process the request.
 The resource URI (http://schemas.microsoft.com/powershell/MaintenanceShell) was not found in the WS-Management catalog.
 The catalog contains the metadata that describes resources, or logical endpoints.
 For more information, see the about_Remote_Troubleshooting Help topic.
 + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
 + FullyQualifiedErrorId : PSSessionOpenFailed
```

`Unregister-PSSessionConfiguration`Hiermee verwijdert u de **MaintenanceShell** -sessie configuratie.
Omdat de opdracht echter de para meter **NoServiceRestart** gebruikt, wordt de **WinRM** -service niet opnieuw gestart en is de wijziging nog niet volledig effectief.

Vervolgens wordt `Get-PSSessionConfiguration` geprobeerd de **MaintenanceShell** -sessie op te halen. Omdat de sessie is verwijderd uit de resource tabel van WS-Management, `Get-PSSessionConfiguration` kan deze niet worden geretourneerd.

`New-PSSession`Met de cmdlet wordt een sessie gemaakt met behulp van de **MaintenanceShell** -configuratie. De opdracht is geslaagd. Vervolgens wordt de **WinRM** -service opnieuw gestart.

Ten slotte `New-PSSession` probeert de cmdlet een sessie te maken die gebruikmaakt van de **MaintenanceShell** -configuratie. Deze keer mislukt de sessie omdat de **MaintenanceShell** -configuratie is verwijderd toen de WinRM-service opnieuw werd gestart.

## PARAMETERS

### -Force

Geeft aan dat de cmdlet niet vraagt om bevestiging en de **WinRM** -service opnieuw opstart zonder te vragen. Als de service opnieuw wordt gestart, wordt de configuratie wijziging effectief.

Als u het opnieuw opstarten wilt voor komen en de prompt voor opnieuw opstarten wilt onderdrukken, gebruikt u de para meter **NoServiceRestart** .

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

Hiermee geeft u de namen van de sessie configuraties die moeten worden verwijderd. Voer één sessie configuratie naam of een configuratie naam patroon in. Joker tekens zijn toegestaan. Deze parameter is vereist.

U kunt ook een sessie configuratie door sluizen naar `Unregister-PSSessionConfiguration` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -NoServiceRestart

Geeft aan dat met deze cmdlet de **WinRM** -service niet opnieuw wordt gestart en wordt de prompt voor het opnieuw starten van de service onderdrukt.

Wanneer u een `Unregister-PSSessionConfiguration` opdracht uitvoert, wordt u standaard gevraagd de **WinRM** -service opnieuw op te starten om de wijziging van kracht te laten worden. Zolang de **WinRM** -service opnieuw is gestart, kunnen gebruikers nog steeds de niet-geregistreerde sessie configuratie gebruiken, zelfs `Get-PSSessionConfiguration` niet.

Als u de **WinRM** -service opnieuw wilt starten zonder te vragen, geeft u de para meter **Force** op. Gebruik de cmdlet om de **WinRM** -service hand matig opnieuw te starten `Restart-Service` .

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

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Micro soft. Power shell. commands. PSSessionConfigurationCommands # PSSessionConfiguration

U kunt een sessie configuratie object door sluizen van `Get-PSSessionConfiguration` naar deze cmdlet.

## UITVOER

### Geen

Met deze cmdlet worden geen objecten geretourneerd.

## OPMERKINGEN

Deze cmdlet is alleen beschikbaar op Windows-platforms.

Als u deze cmdlet wilt uitvoeren, moet u Power shell starten met de optie **als administrator uitvoeren** .

## GERELATEERDE KOPPELINGEN

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Registratie ongedaan maken-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
