---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/unregister-packagesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PackageSource
ms.openlocfilehash: 6ef89e9143fe8883bc98723d10775bf739fe72f9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705560"
---
# Unregister-PackageSource

## SAMENVATTING
Hiermee verwijdert u een geregistreerde pakket bron.

## SYNTAXIS

### SourceBySearch

```
Unregister-PackageSource [[-Source] <String>] [-Location <String>] [-Credential <PSCredential>]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### SourceByInputObject

```
Unregister-PackageSource -InputObject <PackageSource[]> [-Credential <PSCredential>] [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NuGet: SourceByInputObject

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### NuGet: SourceBySearch

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### PowerShellGet: SourceByInputObject

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### PowerShellGet: SourceBySearch

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Unregister-PackageSource` cmdlet wordt een geregistreerde pakket bron verwijderd. Pakket bronnen worden altijd beheerd door een pakket provider. Als u pakket bronnen wilt zoeken, gebruikt u de `Get-PackageSource` cmdlet.

## VOORBEELDEN

### Voor beeld 1: de registratie van een pakket bron voor de Nuget-provider opheffen

Met de cmdlet wordt de `Unregister-PackageSource` registratie van een pakket bron van de lokale computer ongedaan gemaakt. De para meters **locatie** en **provider** kunnen worden gebruikt om de bron die moet worden verwijderd, nader op te geven.

```
PS> Unregister-PackageSource -Source MyNuGet
```

De `Unregister-PackageSource` cmdlet gebruikt de para meter **Source** om op te geven welke bron moet worden verwijderd.

### Voor beeld 2: een PackageSource-object gebruiken om de registratie van een pakket op te heffen

In dit voor beeld wordt de `Get-PackageSource` en gebruikt `Unregister-PackageSource` om de registratie van een pakket bron ongedaan te maken. Het **PackageSource** -object wordt opgeslagen in een variabele.

```
PS> $pkgsource = Get-PackageSource -Name MyNuGet
PS> Unregister-PackageSource -InputObject $pkgsource
```

De `$pkgsource` variabele bevat de **PackageSource** die door de `Get-PackageSource` cmdlet is gemaakt.
`Unregister-PackageSource` gebruikt de `$pkgsource` als-invoer voor de para meter **input object** .

Als alternatief `Unregister-PackageSource` kan de cmdlet een waarde opgeven voor de para meter **input object** :

`Unregister-PackageSource -InputObject ( Get-PackageSource -Name MyNuGet )`

## PARAMETERS

### -ConfigFile

Hiermee geeft u een configuratie bestand op.

```yaml
Type: System.String
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om toegang te krijgen tot de computer en om opdrachten uit te voeren. Typ een gebruikers naam, zoals **gebruiker01**, **Domain01\User01**, of voer een **PSCredential** -object in dat door de `Get-Credential` cmdlet wordt gegenereerd. Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.

Als de para meter **Credential** niet is opgegeven, wordt het huidige gebruikers account gebruikt.

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

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd. Onderdrukkingen van beperkingen die voor komen dat `Unregister-PackageSource` de slagen worden voltooid, met uitzonde ring van beveiliging.

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

Geeft aan `Unregister-PackageSource` dat **Package Management** automatisch de pakket provider voor de opgegeven pakket bron verwijdert.

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

### -Input object

Hiermee wordt een pijplijn invoer geaccepteerd die het **PackageSource** -object van de cmdlet specificeert `Get-PackageSource` . **Input object** accepteert het **PackageSource** -object als een `Get-PackageSource` waarde of een variabele die het object bevat.

```yaml
Type: Microsoft.PackageManagement.Packaging.PackageSource[]
Parameter Sets: SourceByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Locatie

Hiermee geeft u de locatie op van de pakket bron punten. De waarde van deze para meter kan een URI, een bestandspad of een andere bestemmings indeling zijn die wordt ondersteund door de pakket provider.

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

Hiermee geeft u de **Package Management** -provider.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

Hiermee geeft u de naam van de provider.

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PublishLocation

Hiermee geeft u de publicatie locatie op.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptPublishLocation

Hiermee geeft u de publicatie locatie van het script op.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptSourceLocation

Hiermee geeft u de bron locatie van het script op.

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipValidate

Switch waarmee de validatie van de referenties van een pakket bron wordt overgeslagen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Hiermee geeft u de beschrijvende naam van de pakket bron op.

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vraagt u om bevestiging voordat deze `Unregister-PackageSource` wordt uitgevoerd.

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

Laat zien wat er zou gebeuren als de `Unregister-PackageSource` cmdlet wordt uitgevoerd. De cmdlet wordt niet uitgevoerd.

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

### `Unregister-PackageSource` Hiermee worden **PackageSource** -objecten van de pijp lijn geaccepteerd als invoer.

## UITVOER

### `Unregister-PackageSource` Er wordt geen uitvoer gegenereerd.

## OPMERKINGEN

Het opnemen van een pakket provider in een opdracht kan dynamische para meters beschikbaar maken voor een cmdlet. Dynamische para meters zijn specifiek voor een pakket provider. De `Get-Help` cmdlet geeft een lijst van de parameter sets van de cmdlet en bevat de parameterset van de provider.

## GERELATEERDE KOPPELINGEN

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Get-PackageSource](Get-PackageSource.md)

[REGI ster-PackageSource](Register-PackageSource.md)

[Set-PackageSource](Set-PackageSource.md)

