---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSSessionConfiguration
ms.openlocfilehash: ce8b77d9d3de16e16302fc7846ca8a45852511bf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251374"
---
# Disable-PSSessionConfiguration

## SAMENVATTING
Hiermee schakelt u de sessie configuraties op de lokale computer uit.

## SYNTAXIS

```
Disable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet worden de `Disable-PSSessionConfiguration` sessie configuraties op de lokale computer uitgeschakeld, waardoor wordt voor komen dat alle gebruikers de sessie configuraties gebruiken om een door de gebruiker beheerde sessies ( **PSSessions** ) te maken op de lokale computer. Dit is een geavanceerde cmdlet die is ontworpen om te worden gebruikt door systeem beheerders voor het beheren van aangepaste sessie configuraties voor hun gebruikers.

Vanaf Power Shell 3,0 stelt de `Disable-PSSessionConfiguration` cmdlet de **ingeschakelde** instelling van de sessie configuratie ( `WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled` ) in op ONWAAR.

In Power Shell 2,0 `Disable-PSSessionConfiguration` voegt de cmdlet een **Deny_All** vermelding toe aan de security descriptor van een of meer geregistreerde sessie configuraties.

Zonder para meters wordt `Disable-PSSessionConfiguration` de configuratie van **micro soft. Power shell** uitgeschakeld, de standaard configuratie die wordt gebruikt voor sessies. Tenzij de gebruiker een andere configuratie opgeeft, kunnen lokale en externe gebruikers effectief geen sessies maken die verbinding maken met de computer.

Als u alle sessie configuraties op de computer wilt uitschakelen, gebruikt u `Disable-PSRemoting` .

## VOORBEELDEN

### Voor beeld 1: de standaard configuratie uitschakelen

In dit voor beeld wordt de micro soft. Power shell-sessie configuratie uitgeschakeld.

```powershell
Disable-PSSessionConfiguration
```

### Voor beeld 2: alle geregistreerde sessie configuraties uitschakelen

In dit voor beeld worden alle geregistreerde sessie configuraties op de computer uitgeschakeld.

```powershell
Disable-PSSessionConfiguration -Name *
```

### Voor beeld 3: sessie configuraties op naam uitschakelen

In dit voor beeld worden alle sessie configuraties uitgeschakeld die namen hebben die beginnen met micro soft. De **Force** -para meter onderdrukt alle gebruikers prompts van de cmdlet.

```powershell
Disable-PSSessionConfiguration -Name Microsoft* -Force
```

### Voor beeld 4: sessie configuraties uitschakelen met behulp van de pijp lijn

In dit voor beeld worden de **MaintenanceShell** -en **AdminShell** -sessie configuraties uitgeschakeld. Met de pijplijn operator (|) worden de resultaten van een `Get-PSSessionConfiguration` naar verzonden `Disable-PSSessionConfiguration` .

```powershell
Get-PSSessionConfiguration -Name MaintenanceShell, AdminShell | Disable-PSSessionConfiguration
```

### Voor beeld 5: gevolgen van het uitschakelen van een sessie configuratie

In dit voor beeld ziet u de machtigingen vóór en na `Disable-PSSessionConfiguration` het uitvoeren en het effect van het uitschakelen van een sessie configuratie.

```
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> Disable-PSSessionConfiguration -Name MaintenanceShell -Force
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       Everyone AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> New-PSSession -ComputerName localhost -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message : Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

> [!NOTE]
> Door de configuratie uit te scha kelen, kunt u de configuratie niet wijzigen met de `Set-PSSessionConfiguration` cmdlet. Hiermee wordt alleen het gebruik van de configuratie voor komen.

## PARAMETERS

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

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

Hiermee geeft u een matrix met namen van sessie configuraties op die moeten worden uitgeschakeld. Voer een of meer configuratie namen in. Joker tekens zijn toegestaan. U kunt ook een teken reeks met een configuratie naam of een sessie configuratie object door sluizen naar `Disable-PSSessionConfiguration` .

Als u deze para meter weglaat, wordt `Disable-PSSessionConfiguration` de micro soft. Power shell-sessie configuratie uitgeschakeld.

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

Wordt gebruikt om te voor komen dat de WSMan-service opnieuw wordt gestart. Het is niet nodig om de service opnieuw te starten om de configuratie uit te scha kelen.

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

Als u deze cmdlet wilt uitvoeren, moet u Power shell starten met de optie **als administrator uitvoeren** .

## GERELATEERDE KOPPELINGEN

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Registratie ongedaan maken-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)

