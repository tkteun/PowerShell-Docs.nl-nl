---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: e11a62163f70615f33825c46999d37077b1c3d93
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249921"
---
# Get-PSProvider

## SAMENVATTING
Hiermee haalt u informatie op over de opgegeven Power shell-provider.

## SYNTAXIS

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-PSProvider` cmdlet haalt de Power shell-providers in de huidige sessie op.
U kunt een bepaald station of alle stations in de sessie ophalen.

Power shell-providers stellen u in staat om toegang te krijgen tot diverse gegevens archieven, alsof ze bestandssysteem stations zijn.
Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie over Power shell-providers.

## VOORBEELDEN

### Voor beeld 1: een lijst met alle beschik bare providers weer geven

```powershell
Get-PSProvider
```

Met deze opdracht wordt een lijst weer gegeven met alle beschik bare Power shell-providers.

### Voor beeld 2: een lijst weer geven van alle Power shell-providers die met de opgegeven letters beginnen

```powershell
Get-PSProvider f*, r* | Format-List
```

Met deze opdracht wordt een lijst weer gegeven met alle Power shell-providers met namen die beginnen met de letter f of r.

### Voor beeld 3: modules of modules zoeken die providers aan uw sessie hebben toegevoegd

```powershell
Get-PSProvider | Format-Table name, module, pssnapin -auto
```

```Output
Name        Module       PSSnapIn
----        ------       --------
Test        TestModule
WSMan                    Microsoft.WSMan.Management
Alias                    Microsoft.PowerShell.Core
Environment              Microsoft.PowerShell.Core
FileSystem               Microsoft.PowerShell.Core
Function                 Microsoft.PowerShell.Core
Registry                 Microsoft.PowerShell.Core
Variable                 Microsoft.PowerShell.Core
Certificate              Microsoft.PowerShell.Security
```

```powershell
Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}
```

```Output
Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

Met deze opdrachten worden de Power shell-modules of-modules gevonden die providers aan uw sessie hebben toegevoegd.
Alle Power shell-elementen, inclusief providers, zijn afkomstig uit een module of een module.

Deze opdrachten gebruiken de eigenschappen PSSnapin en module van het **ProviderInfo** -object dat `Get-PSProvider` retourneert.
De waarden van deze eigenschappen bevatten de naam van de module of module die de provider toevoegt.

Met de eerste opdracht worden alle providers in de sessie opgehaald en opgemaakt in een tabel met de waarden van hun naam, module en PSSnapin eigenschappen.

De tweede opdracht gebruikt de `Where-Object` cmdlet om de providers op te halen die afkomstig zijn uit de module **micro soft. Power shell. Security** .

### Voor beeld 4: het pad naar de start-eigenschap van de bestandssysteem provider oplossen

```powershell
C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

```powershell
PS C:\> (get-psprovider FileSystem).home
```

```Output
C:\Users\User01
```

In dit voor beeld ziet u dat het tilde-symbool (~) de waarde vertegenwoordigt van de eigenschap **Home** van de File System-Provider.
De waarde van de eigenschap **Home** is optioneel, maar voor de **bestandssysteem** provider wordt deze gedefinieerd als `$env:homedrive\$env:homepath` of `$home` .

## PARAMETERS

### -PSProvider

Hiermee geeft u de naam of namen van de Power shell-providers waarover deze cmdlet informatie ophaalt.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### Teken reeks []

U kunt een of meer provider naam reeksen door geven aan deze cmdlet.

## UITVOER

### System. Management. Automation. ProviderInfo

Deze cmdlet retourneert objecten die de Power shell-providers in de sessie vertegenwoordigen.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

