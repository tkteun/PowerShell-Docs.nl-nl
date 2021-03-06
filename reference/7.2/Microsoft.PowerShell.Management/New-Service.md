---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: d3c6d77db88683c134335cf05d0165b542644b7b
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891036"
---
# New-Service

## SAMENVATTING
Hiermee maakt u een nieuwe Windows-service.

## SYNTAXIS

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-SecurityDescriptorSddl <String>] [-StartupType <ServiceStartupType>] [-Credential <PSCredential>]
 [-DependsOn <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `New-Service` cmdlet maakt een nieuwe vermelding voor een Windows-service in het REGI ster en in de service database. Een nieuwe service vereist een uitvoerbaar bestand dat tijdens de service wordt uitgevoerd.

Met de para meters van deze cmdlet kunt u de weergave naam, de beschrijving, het opstart type en de afhankelijkheden van de service instellen.

## VOORBEELDEN

### Voor beeld 1: een service maken

```powershell
New-Service -Name "TestService" -BinaryPathName '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
```

Met deze opdracht maakt u een service met de naam TestService.

### Voor beeld 2: een service maken die de beschrijving, het opstart type en de weergave naam bevat

```powershell
$params = @{
  Name = "TestService"
  BinaryPathName = '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
  DependsOn = "NetLogon"
  DisplayName = "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
}
New-Service @params
```

Met deze opdracht maakt u een service met de naam TestService. Hierbij worden de para meters van gebruikt `New-Service` om een beschrijving, opstart type en weergave naam voor de nieuwe service op te geven.

### Voor beeld 3: de nieuwe service weer geven

```powershell
Get-CimInstance -ClassName Win32_Service -Filter "Name='testservice'"
```

```Output
ExitCode  : 0
Name      : testservice
ProcessId : 0
StartMode : Auto
State     : Stopped
Status    : OK
```

Met deze opdracht wordt `Get-CimInstance` het **Win32_Service** -object voor de nieuwe service opgehaald. Dit object bevat de start modus en de beschrijving van de service.

### Voor beeld 4: de security descriptor van een service instellen bij het maken.

In dit voor beeld wordt de **security descriptor** toegevoegd van de service die wordt gemaakt.

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
$params = @{
  BinaryPathName = '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
  DependsOn = "NetLogon"
  DisplayName "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
  SecurityDescriptorSddl = $SDDL
}
New-Service @params
```

De **security descriptor** wordt opgeslagen in de `$SDDLToSet` variabele. De para meter **SecurityDescriptorSddl** maakt gebruik `$SDDL` van om de **security descriptor** van de nieuwe service in te stellen.

## PARAMETERS

### -BinaryPathName

Hiermee geeft u het pad van het uitvoer bare bestand voor de service. Deze parameter is vereist.

Het volledig gekwalificeerde pad naar het binaire bestand van de service. Als het pad een spatie bevat, moet het een aanhalings teken bevatten zodat het op de juiste wijze wordt ge??nterpreteerd. Bijvoorbeeld `d:\my share\myservice.exe` moet worden opgegeven als `'"d:\my share\myservice.exe"'` .

Het pad kan ook argumenten bevatten voor een service die automatisch wordt gestart. Bijvoorbeeld `'"d:\myshare\myservice.exe arg1 arg2"'`. Deze argumenten worden door gegeven aan het service toegangs punt.

Zie de para meter **lpBinaryPathName** van [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) API voor meer informatie.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u het account op dat door de service wordt gebruikt als [account voor aanmelding](/windows/desktop/ad/about-service-logon-accounts)bij de service.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**, of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet. Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DependsOn

Hiermee geeft u de namen op van andere services waarvan de nieuwe service afhankelijk is. Als u meerdere service namen wilt opgeven, gebruikt u een komma om de namen van elkaar te scheiden.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Beschrijving

Hiermee geeft u een beschrijving van de service.

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

### -DisplayName

Hiermee geeft u een weergave naam voor de service op.

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

Hiermee geeft u de naam van de service. Deze parameter is vereist.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Opstart type

Hiermee stelt u het opstart type van de service in. De aanvaardbare waarden voor deze parameter zijn:

- **Automatisch** : de service wordt gestart of is door het besturings systeem gestart tijdens het opstarten van het systeem.
  Als een service die automatisch wordt gestart, afhankelijk is van een hand matig gestarte service, wordt de hand matig gestarte service ook automatisch gestart bij het opstarten van het systeem.
- **AutomaticDelayedStart** -binnenkort gestart nadat het systeem is opgestart.
- **Uitgeschakeld** : de service is uitgeschakeld en kan niet worden gestart door een gebruiker of toepassing.
- **InvalidValue** : deze waarde wordt niet ondersteund. Als u deze waarde gebruikt, resulteert dit in een fout.
- **Hand matig** : de service wordt alleen hand matig gestart door een gebruiker, met behulp van service besturings beheer of door een toepassing.

 De standaard waarde is **automatisch**.

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases:
Accepted values: Automatic, Manual, Disabled, AutomaticDelayedStart, InvalidValue

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecurityDescriptorSddl

Hiermee geeft u de **security descriptor** voor de service op in **SDDL** -indeling.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sd

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

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. ServiceProcess. ServiceController

Met deze cmdlet wordt een object geretourneerd dat de nieuwe service vertegenwoordigt.

## OPMERKINGEN

Deze cmdlet is alleen beschikbaar op Windows-platforms.

Als u deze cmdlet wilt uitvoeren, start u Power shell met de optie **als administrator uitvoeren** .

## GERELATEERDE KOPPELINGEN

[Get-Service](Get-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Verwijderen-service](Remove-Service.md)
