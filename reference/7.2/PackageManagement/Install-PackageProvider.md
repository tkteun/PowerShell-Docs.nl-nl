---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 04/26/2021
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: d5f12ec88c94a6ed21cd7a419b5963ce54bfae64
ms.sourcegitcommit: 1e1535cb22d16de06f80beafe77a37a7c77de6d3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/27/2021
ms.locfileid: "108025720"
---
# Install-PackageProvider

## SAMENVATTING
Installeert een of meer pakketproviders voor pakketbeheer.

## SYNTAXIS

### PackageBySearch (standaard)

```
Install-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Credential <PSCredential>] [-Scope <String>] [-Source <String[]>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### PackageByInputObject

```
Install-PackageProvider [-Scope <String>] [-InputObject] <SoftwareIdentity[]> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Install-PackageProvider` cmdlet installeert overeenkomende Package Management-providers die beschikbaar zijn in pakketbronnen die zijn geregistreerd bij **PowerShellGet.** Dit omvat standaard modules die beschikbaar zijn in de Windows PowerShell Gallery met de **tag PackageManagement.** De **PowerShellGet Package** Management-provider wordt gebruikt voor het zoeken naar providers in deze opslagplaatsen.

Met deze cmdlet worden ook overeenkomende Package Management-providers geïnstalleerd die beschikbaar zijn met behulp van de toepassing Voor pakketbeheer opstarten.

Met deze cmdlet worden ook overeenkomende Package Management-providers geïnstalleerd die beschikbaar zijn in de Package Management Azure Blob Store. Gebruik de bootstrapper-provider om ze te zoeken en te installeren.

Om de eerste keer uit te voeren, vereist PackageManagement een internetverbinding om de NuGet-pakketprovider te downloaden. Als uw computer echter geen internetverbinding heeft en u de NuGet- of PowerShellGet-provider moet gebruiken, kunt u deze downloaden op een andere computer en naar uw doelcomputer kopiëren. Gebruik de volgende stappen om dit te doen:

1. Voer `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` uit om de provider te installeren vanaf een computer met een internetverbinding.
1. Na de installatie kunt u de provider vinden die is geïnstalleerd in `$env:ProgramFiles\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>` of `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>` .
1. Plaats de `<ProviderName>` map, in dit geval de nuGet-map, op de bijbehorende locatie op de doelcomputer. Als uw doelcomputer een Nano-server is, moet u uitvoeren vanaf Nano Server om de `Install-PackageProvider` juiste binaire NuGet-bestanden te downloaden.
1. Start PowerShell opnieuw om de pakketprovider automatisch te laden. U kunt ook uitvoeren om `Get-PackageProvider -ListAvailable` alle pakketproviders weer te geven die beschikbaar zijn op de computer.
   Gebruik vervolgens `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` om de provider te importeren in de huidige Windows PowerShell sessie.

## VOORBEELDEN

### Voorbeeld 1: een pakketprovider installeren vanuit de PowerShell Gallery

Met deze opdracht installeert u de Pakketprovider Van de PowerShell Gallery.

```powershell
Install-PackageProvider -Name "GistProvider" -Verbose
```

### Voorbeeld 2: een opgegeven versie van een pakketprovider installeren

In dit voorbeeld wordt een opgegeven versie van de NuGet-pakketprovider geïnstalleerd.

Met de eerste opdracht worden alle versies van de pakketprovider met de naam NuGet gevonden.
Met de tweede opdracht wordt een opgegeven versie van de NuGet-pakketprovider geïnstalleerd.

```powershell
Find-PackageProvider -Name "NuGet" -AllVersions
Install-PackageProvider -Name "NuGet" -RequiredVersion "2.8.5.216" -Force
```

### Voorbeeld 3: Een provider zoeken en installeren

In dit voorbeeld wordt `Find-PackageProvider` en de pijplijn gebruikt om te zoeken naar de Provider En deze te installeren.

```powershell
Find-PackageProvider -Name "GistProvider" | Install-PackageProvider -Verbose
```

### Voorbeeld 4: Een provider installeren in de modulemap van de huidige gebruiker

Met deze opdracht wordt een pakketprovider geïnstalleerd `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies` op zodat alleen de huidige gebruiker deze kan gebruiken.

```powershell
Install-PackageProvider -Name GistProvider -Verbose -Scope CurrentUser
```

## PARAMETERS

### -AllVersions

Geeft aan dat deze cmdlet alle beschikbare versies van de pakketprovider installeert. Standaard `Install-PackageProvider` retourneert alleen de hoogste beschikbare versie.

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

### -Credential

Hiermee geeft u een gebruikersaccount met machtigingen voor het installeren van pakketproviders.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Geeft aan dat deze cmdlet alle acties forceerd met deze cmdlet die kunnen worden geforceerd. Op dit moment betekent dit dat de parameter **Force** hetzelfde werkt als de **parameter ForceBootstrap.**

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

Geeft aan dat deze cmdlet automatisch de pakketprovider installeert.

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

### -InputObject

Hiermee geeft u een **SoftwareIdentity-object.** Gebruik de `Find-PackageProvider` cmdlet om een **SoftwareIdentity-object** te verkrijgen om door te se pijpen naar `Install-PackageProvider` .

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MaximumVersion

Hiermee geeft u de maximaal toegestane versie van de pakketprovider die u wilt installeren. Als u deze parameter niet toevoegt, `Install-PackageProvider` installeert de hoogst beschikbare versie van de provider.

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumVersion

Hiermee geeft u de minimaal toegestane versie van de pakketprovider op die u wilt installeren. Als u deze parameter niet toevoegt, installeert de hoogste beschikbare versie van het pakket dat ook voldoet aan een vereiste die is opgegeven door de `Install-PackageProvider` *parameter MaximumVersion.*

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een of meer modulenamen van pakketproviders op. Scheid meerdere pakketnamen met komma's.
Jokertekens worden niet ondersteund.

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Proxy

Hiermee geeft u een proxyserver voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de internetresource.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

Hiermee geeft u een gebruikersaccount dat is gemachtigd voor het gebruik van de proxyserver die is opgegeven door de **Proxy parameter.**

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

### -RequiredVersion

Hiermee geeft u de exacte toegestane versie van de pakketprovider die u wilt installeren. Als u deze parameter niet toevoegt, installeert de hoogst beschikbare versie van de provider die ook voldoet aan een maximumversie die is opgegeven door `Install-PackageProvider` de **parameter MaximumVersion.**

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Bereik

Hiermee geeft u het installatiebereik van de provider. De aanvaardbare waarden voor deze parameter zijn:

- **AllUsers:** installeert providers op een locatie die toegankelijk is voor alle gebruikers van de computer.
  Standaard is dit **$env:ProgramFiles\PackageManagement\ProviderAssemblies.**

- **CurrentUser:** installeert providers op een locatie waar ze alleen toegankelijk zijn voor de huidige gebruiker. Standaard is dit **$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies.**

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Hiermee geeft u een of meer pakketbronnen. Gebruik de `Get-PackageSource` cmdlet om een lijst met beschikbare pakketbronnen op te halen.

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INVOER

### Microsoft.PackageManagement.Packaging.SoftwareIdentity

U kunt een **SoftwareIdentity-object doorseen** naar deze cmdlet. Gebruik `Find-PackageProvider` om een **SoftwareIdentity-object** op te halen dat kan worden doorspijpt naar `Install-PackageProvider` .

## UITVOER

## OPMERKINGEN

> [!IMPORTANT]
> Vanaf april 2020 biedt de PowerShell Gallery geen ondersteuning meer voor Transport Layer Security versies 1.0 en 1.1 (TLS). Als u TLS 1.2 of hoger niet gebruikt, wordt er een foutbericht weergegeven wanneer u toegang probeert te krijgen tot PowerShell Gallery. Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1.2 gebruikt:
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Zie de aankondiging in [de](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) PowerShell-blog voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Find-PackageProvider](Find-PackageProvider.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Import-PackageProvider](Import-PackageProvider.md)
