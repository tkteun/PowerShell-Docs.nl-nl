---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: ed69b50019b3393eeeda42a250d65d4dfb809a51
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250887"
---
# Install-PackageProvider

## SAMENVATTING
Hiermee worden een of meer pakket beheer pakket providers geïnstalleerd.

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

Met de cmdlet **install-package provider** worden overeenkomende pakket beheer providers geïnstalleerd die beschikbaar zijn in pakket bronnen die zijn geregistreerd bij **PowerShellGet**.
Dit omvat standaard modules die beschikbaar zijn in de PowerShell Gallery met het label **Package Management** .
De **PowerShellGet** -pakket beheer provider wordt gebruikt voor het zoeken naar providers in deze opslag plaatsen.

Met deze cmdlet worden ook overeenkomende pakket beheer providers geïnstalleerd die beschikbaar zijn via de toepassing voor het Boots trappen van het pakket beheer.

Met deze cmdlet worden ook overeenkomende pakket beheer providers geïnstalleerd die beschikbaar zijn in de Azure Blob Store van het pakket beheer.
Gebruik de Boots Trapper-provider om ze te zoeken en te installeren.

Voor de eerste keer moet Package Management een Internet verbinding hebben om de Nuget-pakket provider te downloaden.
Als uw computer echter geen Internet verbinding heeft en u de provider Nuget of PowerShellGet moet gebruiken, kunt u deze downloaden op een andere computer en deze naar uw doel computer kopiëren.
Gebruik de volgende stappen om dit te doen:

1.
Voer `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` uit om de provider te installeren vanaf een computer met een Internet verbinding.

2.
Na de installatie kunt u de provider vinden die is geïnstalleerd in `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` of `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` .

3.
Plaats de \<ProviderName\> map, in dit geval de map Nuget, in de bijbehorende locatie op de doel computer.
Als uw doel computer een nano server is, moet u **install-package provider** uitvoeren vanaf nano server om de juiste binaire bestanden voor Nuget te downloaden.

4.
Start Power shell opnieuw om de pakket provider automatisch te laden.
U kunt ook uitvoeren `Get-PackageProvider -ListAvailable` om alle pakket providers weer te geven die beschikbaar zijn op de computer.
Vervolgens gebruiken `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` om de provider te importeren in de huidige Power shell-sessie.

## VOORBEELDEN

### Voor beeld 1: een pakket provider installeren vanuit de PowerShell Gallery

```
PS C:\> Install-PackageProvider -Name "Gistprovider" -Verbose
```

Met deze opdracht wordt de Gistprovider van de PowerShell Gallery geïnstalleerd.

### Voor beeld 2: een opgegeven versie van een pakket provider installeren

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
PS C:\> Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.216" -Force
```

In dit voor beeld wordt een opgegeven versie van de Nuget-pakket provider geïnstalleerd.

Met de eerste opdracht vindt u alle versies van de pakket provider met de naam Nuget.
Met de tweede opdracht wordt een opgegeven versie van de Nuget-pakket provider geïnstalleerd.

### Voor beeld 3: een provider zoeken en installeren

```
PS C:\> Find-PackageProvider -Name "Gistprovider" | Install-PackageProvider -Verbose
```

Met deze opdracht worden Zoek **-package provider** en de pijp lijn gebruikt om te zoeken naar de DOS-provider en te installeren.

### Voor beeld 4: een provider installeren op de module map van de huidige gebruiker

```
PS C:\> Install-PackageProvider -Name Gistprovider -Verbose -Scope CurrentUser
```

Met deze opdracht wordt een pakket provider geïnstalleerd op $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies, zodat alleen de huidige gebruiker deze kan gebruiken.

## PARAMETERS

### -AllVersions

Geeft aan dat met deze cmdlet alle beschik bare versies van de pakket provider worden geïnstalleerd.
Standaard retourneert **install-package provider** alleen de hoogste beschik bare versie.

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

Hiermee geeft u een gebruikers account op dat is gemachtigd om pakket providers te installeren.

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

Geeft aan dat deze cmdlet alle acties met deze cmdlet afdwingt die kunnen worden geforceerd.
Dit betekent dat de para meter *Forces* hetzelfde is als de para meter *ForceBootstrap* .

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

Geeft aan dat met deze cmdlet automatisch de pakket provider wordt geïnstalleerd.

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

Hiermee geeft u een **SoftwareIdentity** -object op.
Gebruik de cmdlet **find-package provider** om een **SoftwareIdentity** -object naar een pipe te verkrijgen in **install-package provider**.

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

Hiermee geeft u de Maxi maal toegestane versie van de pakket provider op die u wilt installeren.
Als u deze para meter niet toevoegt, installeert **install-package provider** de hoogste beschik bare versie van de provider.

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

Hiermee geeft u de mini maal toegestane versie van de pakket provider die u wilt installeren.
Als u deze para meter niet toevoegt, installeert **install-package provider** de hoogste beschik bare versie van het pakket dat ook voldoet aan een vereiste die is opgegeven door de para meter *MaximumVersion* .

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

Hiermee geeft u een of meer module namen van een pakket provider op.
Scheid meerdere pakket namen met komma's.
Joker tekens worden niet ondersteund.

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

Hiermee geeft u de exacte toegestane versie van de pakket provider op die u wilt installeren.
Als u deze para meter niet toevoegt, installeert **install-package provider** de hoogste beschik bare versie van de provider die ook voldoet aan de maximum versie die is opgegeven door de para meter *MaximumVersion* .

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

Hiermee geeft u het installatie bereik van de provider op.
De acceptabele waarden voor deze para meter zijn: **ALLUSERS** en **CurrentUser**.

Met het **ALLUSERS** -bereik worden providers geïnstalleerd op een locatie die toegankelijk is voor alle gebruikers van de computer.
Dit is standaard **$env:P rogramfiles\packagemanagement\providerassemblies.**

Met het bereik **CurrentUser** worden providers geïnstalleerd op een locatie waar ze alleen toegankelijk zijn voor de huidige gebruiker.
Dit is standaard **$env: LOCALAPPDATA\PackageManagement\ProviderAssemblies.**

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

Hiermee geeft u een of meer pakket bronnen op.
Gebruik de cmdlet Get-PackageSource om een lijst met beschik bare pakket bronnen op te halen.

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

### Micro soft. package management. verpakking. SoftwareIdentity

U kunt een **SoftwareIdentity** -object door sluizen naar deze cmdlet.
Gebruik Find-PackageProvider om een **SoftwareIdentity** -object op te halen dat kan worden gepiped in **install-package provider**.

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Zoeken-package provider](Find-PackageProvider.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Import-package provider](Import-PackageProvider.md)

