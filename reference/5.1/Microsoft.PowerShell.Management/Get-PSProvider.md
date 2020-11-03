---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: 997d86460837946a2cf18fc78f058f21472dd909
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250791"
---
# Get-PSProvider

## SAMENVATTING
Hiermee haalt u informatie op over de opgegeven Windows Power shell-provider.

## SYNTAXIS

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Get-PSProvider** worden de Windows Power shell-providers in de huidige sessie opgehaald.
U kunt een bepaald station of alle stations in de sessie ophalen.

Windows Power shell-providers stellen u in staat om toegang te krijgen tot diverse gegevens archieven, alsof ze bestandssysteem stations zijn.
Zie about_Providers voor meer informatie over Windows Power shell-providers.

## VOORBEELDEN

### Voor beeld 1: een lijst met alle beschik bare providers weer geven

```
PS C:\> Get-PSProvider
```

Met deze opdracht wordt een lijst weer gegeven met alle beschik bare Windows Power shell-providers.

### Voor beeld 2: een lijst weer geven met alle Windows Power shell-providers die beginnen met opgegeven letters

```
PS C:\> Get-PSProvider f*, r* | Format-List
```

Met deze opdracht wordt een lijst weer gegeven met alle Windows Power shell-providers met namen die beginnen met de letter f of r.

### Voor beeld 3: modules of modules zoeken die providers aan uw sessie hebben toegevoegd

```
PS C:\> Get-PSProvider | Format-Table name, module, pssnapin -auto

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

PS C:\> Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}

Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

Met deze opdrachten vindt u de Windows Power shell-modules die providers hebben toegevoegd aan uw sessie.
Alle Windows Power shell-elementen, inclusief providers, zijn afkomstig uit een module of een module.

Deze opdrachten gebruiken de eigenschappen PSSnapin en module van het **ProviderInfo** -object die **Get-PSProvider** retourneert.
De waarden van deze eigenschappen bevatten de naam van de module of module die de provider toevoegt.

Met de eerste opdracht worden alle providers in de sessie opgehaald en opgemaakt in een tabel met de waarden van hun naam, module en PSSnapin eigenschappen.

De tweede opdracht gebruikt de cmdlet Where-Object om de providers op te halen die afkomstig zijn uit de module **micro soft. Power shell. Security** .

### Voor beeld 4: het pad naar de start-eigenschap van de bestandssysteem provider oplossen

```
PS C:\> Resolve-Path ~

Path
----
C:\Users\User01

PS C:\> (get-psprovider FileSystem).home
C:\Users\User01
```

In dit voor beeld ziet u dat het tilde-symbool (~) de waarde vertegenwoordigt van de eigenschap Home van de File System-Provider.
De waarde van de eigenschap Home is optioneel, maar voor de bestandssysteem provider is deze gedefinieerd als $env: HOMEDRIVE \$ env: homepath of $Home.

## PARAMETERS

### -PSProvider
Hiermee geeft u de naam of namen van de Windows Power shell-providers waarover deze cmdlet informatie ophaalt.

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
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Teken reeks []

U kunt een of meer provider naam reeksen door geven aan deze cmdlet.

## UITVOER

### System. Management. Automation. ProviderInfo
Deze cmdlet retourneert objecten die de Windows Power shell-providers in de sessie vertegenwoordigen.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

## GERELATEERDE KOPPELINGEN
