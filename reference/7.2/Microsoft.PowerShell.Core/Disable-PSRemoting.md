---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 4410c8f41fffcaae9c9f447af246f335033d53a1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705767"
---
# Disable-PSRemoting

## SAMENVATTING
Hiermee voor komt u dat Power shell-eind punten externe verbindingen ontvangen.

## SYNTAXIS

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Disable-PSRemoting` cmdlet blokkeert externe toegang tot alle configuraties van de sessie-eindpunt versie 6 en groter op de lokale computer. Dit heeft geen invloed op Windows Power shell-eindpunt configuraties. Als u configuraties van Windows Power shell-sessie-eind punten wilt uitschakelen, voert u `Disable-PSRemoting` de opdracht uit vanuit een Windows Power shell-sessie.

Gebruik de cmdlet om externe toegang opnieuw in te scha kelen voor alle configuraties van Power shell versie 6 en de grotere sessie-eind punten `Enable-PSRemoting` . Als u externe toegang tot alle Windows Power shell-sessie-eindpunt configuraties opnieuw wilt inschakelen, voert u `Enable-PSRemoting` uit vanuit een Windows Power shell-sessie.

> [!NOTE]
> Als u alle Power shell-externe toegang wilt uitschakelen voor een lokale Windows-computer, moet u deze opdracht uitvoeren vanaf een van de Power shell-versie 6 of hoger en vanuit een Windows Power shell-sessie. Windows Power shell is standaard geïnstalleerd op alle Windows-computers.

Gebruik de cmdlets en om externe toegang tot specifieke configuraties voor sessie-eind punten uit te scha kelen en opnieuw in te scha kelen `Enable-PSSessionConfiguration` `Disable-PSSessionConfiguration` . Als u specifieke toegangs configuraties van afzonderlijke eind punten wilt instellen, gebruikt u de `Set-PSSessionConfiguration` cmdlet in combi natie met de para meter **AccessMode** . Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

> [!NOTE]
> Zelfs nadat `Disable-PSRemoting` u hebt uitgevoerd, kunt u nog steeds loop back-verbindingen maken op de lokale computer. Een loop back-verbinding is een externe Power shell-sessie die afkomstig is van en die verbinding maakt met dezelfde lokale computer. Externe sessies van externe bronnen blijven geblokkeerd. Voor loop back-verbindingen moet u impliciete referenties gebruiken in combi natie met de para meter **EnableNetworkAccess** . Zie [New-PSSession](New-PSSession.md)voor meer informatie over loop back-verbindingen.

Deze cmdlet is alleen beschikbaar op het Windows-platform. Het is niet beschikbaar in Linux-of macOS-versies van Power shell. Als u deze cmdlet wilt uitvoeren, start u Power shell met de optie **als administrator uitvoeren** .

## VOORBEELDEN

### Voor beeld 1: externe toegang tot alle Power shell-sessie configuraties voor komen

In dit voor beeld wordt voor komen dat externe toegang tot alle configuraties van het Power shell-sessie eindpunt op de computer.

```powershell
Disable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### Voor beeld 2: externe toegang tot alle Power shell-sessie configuraties zonder bevestigings prompt voor komen

In dit voor beeld wordt voor komen dat alle configuratie van het eind punt van een Power shell-sessie op de computer zonder dat dit wordt gevraagd

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
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
New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
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
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
```

`Enable-PSRemoting`Met de cmdlet wordt externe toegang tot alle configuratie van het eind punt van de Power shell-sessie op de computer opnieuw ingeschakeld. De **Force** -para meter onderdrukt alle gebruikers prompts en start de WinRM-service opnieuw op zonder toestemming te vragen. In de nieuwe uitvoer ziet u dat de security descriptors voor **AccessDenied** zijn verwijderd uit alle sessie configuraties.

### Voor beeld 5: loop back-verbindingen met uitgeschakelde sessie-eindpunt configuraties

In dit voor beeld ziet u hoe eindpunt configuraties worden uitgeschakeld en hoe u een geslaagde loop back-verbinding kunt maken met een uitgeschakeld eind punt. `Disable-PSRemoting` Hiermee worden alle configuratie van het eind punt van een Power shell-sessie uitgeschakeld.

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -Credential (Get-Credential)
```

```Output
PowerShell credential request
Enter your credentials.
User: UserName
Password for user UserName: ************

New-PSSession: [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

Het eerste gebruik van `New-PSSession` pogingen om een externe sessie te maken op de lokale computer. De para meter **configuratiepad** wordt gebruikt om een uitgeschakeld Power shell-eind punt op te geven. Referenties worden expliciet door gegeven aan de opdracht via de para meter **Credential** . Dit type verbinding loopt via de netwerk stack en is geen loop back. Daarom mislukt de verbindings poging met het uitgeschakelde eind punt met een fout bericht **geweigerd** .

Het tweede gebruik van `New-PSSession` ook pogingen om een externe sessie te maken op de lokale computer.
In dit geval slaagt dit omdat het een loop back-verbinding is die de netwerk stack omzeilt.

Er wordt een loop back-verbinding gemaakt wanneer aan de volgende voor waarden wordt voldaan:

- De computer naam waarmee verbinding moet worden gemaakt, is ' localhost '.
- Er zijn geen referenties door gegeven in. De huidige aangemelde gebruiker (impliciete referenties) wordt gebruikt voor de verbinding.
- De switch parameter **EnableNetworkAccess** wordt gebruikt.

Zie [New-PSSession](New-PSSession.md) document voor meer informatie over loop back-verbindingen.

### Voor beeld 6: alle Power shell-configuraties voor externe eind punten uitschakelen

Dit voor beeld laat zien hoe het uitvoeren van de `Disable-PSRemoting` opdracht niet van invloed is op Windows Power shell-eindpunt configuraties. `Get-PSSessionConfiguration` uitvoeren in Windows Power shell toont alle eindpunt configuraties. We zien dat de configuratie van Windows Power shell-eind punten niet is uitgeschakeld.

```powershell
Disable-PSRemoting -Force
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

```powershell
powershell.exe -command 'Disable-PSRemoting -Force'
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting or
Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the
Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management
                Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

Als u deze eindpunt configuraties wilt uitschakelen, moet u de `Disable-PSRemoting` opdracht uitvoeren vanuit een Windows Power shell-sessie. Vanaf nu `Get-PSSessionConfiguration` voert u uit vanuit Windows Power shell om aan te geven dat alle eindpunt configuraties zijn uitgeschakeld.

### Voor beeld 7: externe toegang tot sessie configuraties met aangepaste Security descriptors voor komen

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
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, User01 AccessAllowed

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName Test
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

Met de `Get-PSSessionConfiguration` `Format-Table` cmdlets en wordt aangegeven dat een **AccessDenied** -security descriptor voor alle netwerk gebruikers wordt toegevoegd aan alle sessie configuraties, met inbegrip van de configuratie van de **test** sessie. Hoewel de andere security descriptors niet worden gewijzigd, heeft de security descriptor network_deny_all voor rang. Dit wordt geïllustreerd door de poging om `New-PSSession` verbinding te maken met de configuratie van de **test** sessie.

### Voor beeld 8: externe toegang tot geselecteerde sessie configuraties opnieuw inschakelen

In dit voor beeld ziet u hoe u externe toegang opnieuw inschakelt voor geselecteerde sessie configuraties. Nadat alle sessie configuraties zijn uitgeschakeld, wordt een specifieke sessie opnieuw ingeschakeld.

De `Set-PSSessionConfiguration` cmdlet wordt gebruikt om de configuratie van de **Power shell. 6** -sessie te wijzigen. De **AccessMode** para meter met de waarde **extern** opnieuw inschakelen externe toegang tot de configuratie.

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name PowerShell.6 -AccessMode Remote -Force
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

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\ ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
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

Deze cmdlet is alleen beschikbaar op Windows-platforms.

- Door de sessie configuraties uit te scha kelen, worden niet alle wijzigingen ongedaan gemaakt die zijn aangebracht door de- `Enable-PSRemoting` of- `Enable-PSSessionConfiguration` cmdlets. Mogelijk moet u de volgende wijzigingen hand matig ongedaan maken.

  1. Stop de WinRM-service en schakel deze uit.
  2. Verwijder de listener die aanvragen op een IP-adres accepteert.
  3. Schakel de firewall-uitzonde ringen voor de communicatie van WS-Management uit.
  4. Herstel de waarde van LocalAccountTokenFilterPolicy in 0, waardoor externe toegang wordt beperkt tot leden van de groep Administrators op de computer.

- Een configuratie van het eind punt van een sessie is een groep instellingen waarmee de omgeving voor een sessie wordt gedefinieerd.
  Elke sessie die verbinding maakt met de computer, moet een van de sessie-eindpunt configuraties gebruiken die zijn geregistreerd op de computer. Door externe toegang tot alle sessie-eindpunt configuraties te weigeren, voor komt u dat externe gebruikers sessies kunnen instellen die verbinding maken met de computer.

## GERELATEERDE KOPPELINGEN

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSRemoting](Enable-PSRemoting.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Registratie ongedaan maken-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
