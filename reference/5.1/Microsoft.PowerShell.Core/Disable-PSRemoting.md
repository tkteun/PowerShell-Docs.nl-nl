---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 3a281786f99b2a46d0aeb9785480f02b35b2b433
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249977"
---
# Disable-PSRemoting

## SAMENVATTING
Hiermee voor komt u dat Power shell-eind punten externe verbindingen ontvangen.

## SYNTAXIS

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Disable-PSRemoting` cmdlet blokkeert externe toegang tot alle configuraties van Windows Power shell-sessie-eind punten op de lokale computer. Dit omvat alle eind punten die zijn gemaakt met Power shell 6 of hoger.

Als u externe toegang tot alle sessie configuraties opnieuw wilt inschakelen, gebruikt u de `Enable-PSRemoting` cmdlet. Dit omvat alle eind punten die zijn gemaakt met Power shell 6 of hoger. Als u externe toegang tot geselecteerde sessie configuraties wilt inschakelen, gebruikt u de para meter **AccessMode** van de `Set-PSSessionConfiguration` cmdlet.
U kunt ook de `Enable-PSSessionConfiguration` `Disable-PSSessionConfiguration` cmdlets en gebruiken om de sessie configuraties voor alle gebruikers in te scha kelen en uit te scha kelen. Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

> [!NOTE]
> Zelfs nadat `Disable-PSRemoting` u hebt uitgevoerd, kunt u nog steeds loop back-verbindingen maken op de lokale computer. Een loop back-verbinding is een externe Power shell-sessie die afkomstig is van en die verbinding maakt met dezelfde lokale computer. Externe sessies van externe bronnen blijven geblokkeerd. Voor loop back-verbindingen moet u impliciete referenties gebruiken in combi natie met de para meter **EnableNetworkAccess** . Zie [New-PSSession](New-PSSession.md)voor meer informatie over loop back-verbindingen.

Als u deze cmdlet wilt uitvoeren, start u Windows Power shell met de optie **als administrator uitvoeren** .

## VOORBEELDEN

### Voor beeld 1: externe toegang tot alle sessie configuraties voor komen

In dit voor beeld wordt voor komen dat externe toegang tot alle configuraties van het Power shell-sessie eindpunt op de computer.

```powershell
Disable-PSRemoting
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### Voor beeld 2: externe toegang tot alle sessie configuraties verhinderen zonder bevestiging te vragen

In dit voor beeld wordt voor komen dat alle configuratie van het eind punt van een Power shell-sessie op de computer zonder dat dit wordt gevraagd

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### Voor beeld 3: gevolgen van het uitvoeren van deze cmdlet

In dit voor beeld ziet u het effect van het gebruik van de `Disable-PSRemoting` cmdlet. Als u deze opdracht reeks wilt uitvoeren, start u Power shell met de optie **als administrator uitvoeren** .

Nadat de sessie configuraties zijn uitgeschakeld, `New-PSSession` probeert de cmdlet een externe sessie te maken naar de lokale computer (ook wel ' loop back ' genoemd). Omdat externe toegang is uitgeschakeld op de lokale computer, mislukt de opdracht.

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error
 message : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

### Voor beeld 4: gevolgen van het uitvoeren van deze cmdlet en Enable-PSRemoting

In dit voor beeld ziet u het effect van de sessie configuraties van met de- `Disable-PSRemoting` en- `Enable-PSRemoting` cmdlets.

`Disable-PSRemoting` wordt gebruikt om externe toegang uit te scha kelen voor alle configuraties van de Power shell-sessie-eind punten. De **Force** -para meter onderdrukt alle gebruikers prompts. `Get-PSSessionConfiguration`Met de `Format-Table` cmdlets en worden de sessie configuraties op de computer weer gegeven.

In de uitvoer ziet u dat alle externe gebruikers met een netwerk token de toegang tot de eindpunt configuraties hebben geweigerd. De groep Administrators op de lokale computer is toegang tot de eindpunt configuraties, zolang ze lokaal verbinding maken (ook wel loop back) en impliciete referenties gebruiken.

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow BUILTIN\Administrators AccessAllowed
microsoft.powershell32        BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   BUILTIN\Administrators AccessAllowed
```

`Enable-PSRemoting`Met de cmdlet wordt externe toegang tot alle configuratie van het eind punt van de Power shell-sessie op de computer opnieuw ingeschakeld. De **Force** -para meter onderdrukt alle gebruikers prompts en start de WinRM-service opnieuw op zonder toestemming te vragen. In de nieuwe uitvoer ziet u dat de security descriptors voor **AccessDenied** zijn verwijderd uit alle sessie configuraties.

### Voor beeld 5: loop back-verbindingen met uitgeschakelde sessie-eindpunt configuraties

In dit voor beeld ziet u hoe eindpunt configuraties worden uitgeschakeld en hoe u een geslaagde loop back-verbinding kunt maken met een uitgeschakeld eind punt. `Disable-PSRemoting` Hiermee worden alle configuratie van het eind punt van een Power shell-sessie uitgeschakeld.

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message : Access is
denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [New-PSSession], PSRemotin
   gTransportException
    + FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed

```

```powershell
New-PSSession -ComputerName localhost -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

Het eerste gebruik van `New-PSSession` pogingen om een externe sessie te maken op de lokale computer. Dit type verbinding loopt via de netwerk stack en is geen loop back. Daarom mislukt de verbindings poging met het uitgeschakelde eind punt met een fout bericht **geweigerd** .

Het tweede gebruik van `New-PSSession` ook pogingen om een externe sessie te maken op de lokale computer.
In dit geval slaagt dit omdat het een loop back-verbinding is die de netwerk stack omzeilt.

Er wordt een loop back-verbinding gemaakt wanneer aan de volgende voor waarden wordt voldaan:

- De computer naam waarmee verbinding moet worden gemaakt, is ' localhost '.
- Er zijn geen referenties door gegeven in. De huidige aangemelde gebruiker (impliciete referenties) wordt gebruikt voor de verbinding.
- De switch parameter **EnableNetworkAccess** wordt gebruikt.

Zie [New-PSSession](New-PSSession.md) document voor meer informatie over loop back-verbindingen.

### Voor beeld 6: externe toegang tot sessie configuraties met aangepaste Security descriptors voor komen

In dit voor beeld wordt gedemonstreerd dat `Disable-PSRemoting` externe toegang wordt uitgeschakeld voor alle sessie configuraties die sessie configuraties met aangepaste Security descriptors bevatten.

`Register-PSSessionConfiguration` Hiermee maakt u de configuratie van de **test** sessie. De **filepath** para meter geeft een sessie configuratie bestand op waarmee de sessie wordt aangepast. De para meter **ShowSecurityDescriptorUI** geeft een dialoog venster weer waarin machtigingen worden ingesteld voor de sessie configuratie. In het dialoog venster machtigingen maken we aangepaste machtigingen voor volledige toegang voor de aangegeven gebruiker.

`Get-PSSessionConfiguration`Met de `Format-Table` cmdlets en worden de sessie configuraties en de bijbehorende eigenschappen weer gegeven. In de uitvoer ziet u dat de configuratie van de **test** sessie interactieve toegang en speciale machtigingen voor de aangegeven gebruiker toestaat.

`Disable-PSRemoting` externe toegang tot alle sessie configuraties wordt uitgeschakeld.

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
DOMAIN01\User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\NETWORK AccessDenied, NTAUTHORITY\INTERACTIVE AccessAllowed,
BUILTIN\Administrators AccessAllowed, DOMAIN01\User01 AccessAllowed


[Server01] Connecting to remote server failed with the following error message : Access is denied. For more information, see the about_Rem
ote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

Met de `Get-PSSessionConfiguration` `Format-Table` cmdlets en wordt aangegeven dat een **AccessDenied** -security descriptor voor alle netwerk gebruikers wordt toegevoegd aan alle sessie configuraties, met inbegrip van de configuratie van de **test** sessie. Hoewel de andere security descriptors niet worden gewijzigd, heeft de security descriptor network_deny_all voor rang. Dit wordt geïllustreerd door de poging om `New-PSSession` verbinding te maken met de configuratie van de **test** sessie.

### Voor beeld 7: externe toegang tot geselecteerde sessie configuraties opnieuw inschakelen

In dit voor beeld ziet u hoe u externe toegang opnieuw inschakelt voor geselecteerde sessie configuraties. Nadat alle sessie configuraties zijn uitgeschakeld, wordt een specifieke sessie opnieuw ingeschakeld.

De `Set-PSSessionConfiguration` cmdlet wordt gebruikt om de **micro soft te wijzigen.** Sessie configuratie van Server Manager. De **AccessMode** para meter met de waarde **extern** opnieuw inschakelen externe toegang tot de configuratie.

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name Microsoft.ServerManager -AccessMode Remote -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
```

## PARAMETERS

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

### Geen

U kunt geen objecten door sluizen naar deze cmdlet.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

- Door de sessie configuraties uit te scha kelen, worden niet alle wijzigingen ongedaan gemaakt die zijn aangebracht door de- `Enable-PSRemoting` of- `Enable-PSSessionConfiguration` cmdlets. Mogelijk moet u de volgende wijzigingen hand matig ongedaan maken.

  1. Stop de WinRM-service en schakel deze uit.
  2. Verwijder de listener die aanvragen op een IP-adres accepteert.
  3. Schakel de firewall-uitzonde ringen voor de communicatie van WS-Management uit.
  4. Herstel de waarde van LocalAccountTokenFilterPolicy in 0, waardoor externe toegang wordt beperkt tot leden van de groep Administrators op de computer.

  Een sessie configuratie is een groep instellingen waarmee de omgeving voor een sessie wordt gedefinieerd. Elke sessie die verbinding maakt met de computer, moet een van de sessie configuraties gebruiken die zijn geregistreerd op de computer. Door externe toegang tot alle sessie configuraties te weigeren, voor komt u dat externe gebruikers sessies kunnen instellen die verbinding maken met de computer.

  In Windows Power Shell 2,0 `Disable-PSRemoting` voegt een Deny_All vermelding toe aan de security descriptors van alle sessie configuraties. Met deze instelling wordt voor komen dat alle gebruikers door gebruikers beheerde sessies op de lokale computer maken. In Windows Power Shell 3,0 `Disable-PSRemoting` voegt een Network_Deny_All vermelding toe aan de security descriptors van alle sessie configuraties. Met deze instelling wordt voor komen dat gebruikers op andere computers door gebruikers beheerde sessies op de lokale computer maken, maar kunnen gebruikers van de lokale computer een loop back-sessie maken die door gebruikers wordt beheerd.

  In Windows Power Shell 2,0 `Disable-PSRemoting` is het equivalent van `Disable-PSSessionConfiguration -Name *` . In Windows Power Shell 3,0 en latere versies `Disable-PSRemoting` is het equivalent van `Set-PSSessionConfiguration -Name \<Configuration name\> -AccessMode Local`

## GERELATEERDE KOPPELINGEN

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSRemoting](Enable-PSRemoting.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Registratie ongedaan maken-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
