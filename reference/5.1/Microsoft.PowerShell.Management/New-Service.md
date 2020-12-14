---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: 758b0a8ef9a5f65f0e7cfa7f3633086cf9f0445d
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891765"
---
# New-Service

## SAMENVATTING
Hiermee maakt u een nieuwe Windows-service.

## SYNTAXIS

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Credential <PSCredential>] [-DependsOn <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
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

### Voor beeld 4: een service verwijderen

```powershell
sc.exe delete TestService
# - or -
(Get-CimInstance -Class Win32_Service -Filter "name='TestService'").delete()
```

In dit voor beeld ziet u twee manieren om de TestService-service te verwijderen. De eerste opdracht maakt gebruik van de optie verwijderen van `Sc.exe` . Met de tweede opdracht wordt de methode **Delete** gebruikt van de **Win32_Service** -objecten die worden `Get-CimInstance` geretourneerd.

## PARAMETERS

### -BinaryPathName

Hiermee geeft u het pad van het uitvoer bare bestand voor de service. Deze parameter is vereist.

Het volledig gekwalificeerde pad naar het binaire bestand van de service. Als het pad een spatie bevat, moet het een aanhalings teken bevatten zodat het op de juiste wijze wordt geïnterpreteerd. Bijvoorbeeld `d:\my share\myservice.exe` moet worden opgegeven als `'"d:\my share\myservice.exe"'` .

Het pad kan ook argumenten bevatten voor een service die automatisch wordt gestart. Bijvoorbeeld `'"d:\myshare\myservice.exe arg1 arg2"'`. Deze argumenten worden door gegeven aan het service toegangs punt.

Zie de para meter **lpBinaryPathName** van [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) API voor meer informatie.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

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
- **Uitgeschakeld** : de service is uitgeschakeld en kan niet worden gestart door een gebruiker of toepassing.
- **Hand matig** : de service wordt alleen hand matig gestart door een gebruiker, met behulp van service besturings beheer of door een toepassing.
- **Boot** : geeft aan dat de service een apparaatstuurprogramma is dat door de System loader wordt gestart. Deze waarde is alleen geldig voor apparaatstuurprogramma's.
- **Systeem** : geeft aan dat de service een apparaatstuurprogramma is dat is gestart door de functie IOInitSystem (). Deze waarde is alleen geldig voor apparaatstuurprogramma's.

 De standaard waarde is **automatisch**.

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases:
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
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

Als u deze cmdlet wilt uitvoeren, start u Power shell met de optie **als administrator uitvoeren** .

Als u een service wilt verwijderen, gebruikt u Sc.exe of gebruikt `Get-CimInstance` u de cmdlet om het **Win32_Service** -object op te halen dat de service vertegenwoordigt en gebruikt u vervolgens de **Delete** -methode om de service te verwijderen. Het `Get-Service` geretourneerde object heeft geen verwijderings methode.

## GERELATEERDE KOPPELINGEN

[Get-Service](Get-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
