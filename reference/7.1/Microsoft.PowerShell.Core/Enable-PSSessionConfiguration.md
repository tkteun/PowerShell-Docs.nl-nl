---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSSessionConfiguration
ms.openlocfilehash: 212a745276a51fce2ec3b00ef59629d4480d8661
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251368"
---
# Enable-PSSessionConfiguration

## SAMENVATTING
Hiermee schakelt u de sessie configuraties in op de lokale computer.

## SYNTAXIS

```
Enable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-SecurityDescriptorSddl <String>]
 [-SkipNetworkProfileCheck] [-NoServiceRestart] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Enable-PSSessionConfiguration` cmdlet worden geregistreerde sessie configuraties ingeschakeld die zijn uitgeschakeld, zoals met behulp van de `Disable-PSSessionConfiguration` `Disable-PSRemoting` cmdlets of de **AccessMode** -para meter van `Register-PSSessionConfiguration` . Dit is een geavanceerde cmdlet die is ontworpen om te worden gebruikt door systeem beheerders voor het beheren van aangepaste sessie configuraties voor hun gebruikers.

Zonder para meters wordt `Enable-PSSessionConfiguration` de configuratie van **micro soft. Power shell** ingeschakeld. Dit is de standaard configuratie die wordt gebruikt voor sessies.

`Enable-PSSessionConfiguration` Hiermee wordt de instelling **Deny_All** verwijderd uit de security descriptor van de betrokken sessie configuraties, wordt de listener ingeschakeld die aanvragen op een IP-adres accepteert en wordt de WinRM-service opnieuw gestart. Vanaf Power Shell 3,0 `Enable-PSSessionConfiguration` wordt ook de waarde van de eigenschap **enabled** van de sessie configuratie ( `WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled` ) ingesteld op True. `Enable-PSSessionConfiguration`De instelling **Network_Deny_All** (Security descriptor) wordt echter niet verwijderd of gewijzigd, `AccessMode=Local` waardoor alleen gebruikers van de lokale computer kunnen gebruiken voor de sessie configuratie.

## VOORBEELDEN

### Voor beeld 1: de standaard sessie opnieuw inschakelen

In dit voor beeld wordt de standaard sessie configuratie van **micro soft. Power shell** op de computer opnieuw ingeschakeld.

```powershell
Enable-PSSessionConfiguration
```

### Voor beeld 2: opgegeven sessies opnieuw inschakelen

In dit voor beeld worden de **MaintenanceShell** -en **AdminShell** -sessie configuraties op de computer opnieuw ingeschakeld.

```powershell
Enable-PSSessionConfiguration -Name MaintenanceShell, AdminShell
```

### Voor beeld 3: alle sessies opnieuw inschakelen

In dit voor beeld worden alle sessie configuraties op de computer opnieuw ingeschakeld. Deze opdrachten zijn gelijk.
Daarom kunt u beide gebruiken.

```powershell
Enable-PSSessionConfiguration -Name *
Get-PSSessionConfiguration | Enable-PSSessionConfiguration
```

`Enable-PSSessionConfiguration` Er wordt geen fout gegenereerd als u een sessie configuratie inschakelt die al is ingeschakeld.

### Voor beeld 4: een sessie opnieuw inschakelen en een nieuwe security descriptor opgeven

In dit voor beeld wordt de configuratie van de **MaintenanceShell** -sessie opnieuw ingeschakeld en wordt een nieuwe security descriptor voor de configuratie opgegeven.

```powershell
$sddl = "O:NSG:BAD:P(A;;GXGWGR;;;BA)(A;;GAGR;;;S-1-5-21-123456789-188441444-3100496)S:P"
Enable-PSSessionConfiguration -Name MaintenanceShell -SecurityDescriptorSDDL $sddl
```

## PARAMETERS

### -Force

Geeft aan dat de cmdlet niet vraagt om bevestiging en de WinRM-service opnieuw opstart zonder te vragen. Als de service opnieuw wordt gestart, wordt de configuratie wijziging effectief.

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

Hiermee geeft u de namen van de sessie configuraties op die moeten worden ingeschakeld. Voer een of meer configuratie namen in.
Joker tekens zijn toegestaan.

U kunt ook een teken reeks met een configuratie naam of een sessie configuratie object door sluizen naar `Enable-PSSessionConfiguration` .

Als u deze para meter weglaat, wordt `Enable-PSSessionConfiguration` de **micro soft. Power shell** -sessie configuratie ingeschakeld.

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

### -NoServiceRestart

Geeft aan dat de cmdlet de service niet opnieuw opstart.

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

### -SecurityDescriptorSddl

Hiermee geeft u een security descriptor op waarmee deze cmdlet de security descriptor in de sessie configuratie vervangt.

Als u deze para meter weglaat, wordt `Enable-PSSessionConfiguration` alleen het item alle items weigeren uit de security descriptor verwijderd.

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

### -SkipNetworkProfileCheck

Geeft aan dat met deze cmdlet de sessie configuratie wordt ingeschakeld wanneer de computer zich op een openbaar netwerk bevindt. Met deze para meter wordt een firewall regel ingeschakeld voor open bare netwerken die alleen externe toegang toestaan vanaf computers in hetzelfde lokale subnet. Standaard `Enable-PSSessionConfiguration` mislukt op een openbaar netwerk.

Deze para meter is ontworpen voor client versies van het Windows-besturings systeem. Server versies van het Windows-besturings systeem hebben een lokale subnet-firewall regel voor open bare netwerken. Als de regel voor de lokale subnet-firewall echter is uitgeschakeld op een server versie van het Windows-besturings systeem, wordt deze door deze para meter opnieuw ingeschakeld.

Als u de beperkingen voor lokale subnetten wilt verwijderen en externe toegang vanaf alle locaties op open bare netwerken wilt inschakelen, gebruikt u de `Set-NetFirewallRule` cmdlet in de module netsecurity. Voor meer informatie raadpleegt u `Enable-PSRemoting`.

Deze para meter is geïntroduceerd in Power Shell 3,0.

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

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

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

### Micro soft. Power shell. commands. PSSessionConfigurationCommands # PSSessionConfiguration, System. String

U kunt een sessie configuratie object of een teken reeks die de naam van een sessie configuratie bevat, door sluizen naar deze cmdlet.

## UITVOER

### Geen

Met deze cmdlet worden geen objecten geretourneerd.

## OPMERKINGEN

Als u deze cmdlet wilt gebruiken, moet u Power shell starten met de optie **als administrator uitvoeren** .

## GERELATEERDE KOPPELINGEN

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

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

