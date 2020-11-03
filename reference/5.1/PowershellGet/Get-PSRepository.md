---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-psrepository?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSRepository
ms.openlocfilehash: e86f06b5e2ebbf51431e362af87b22ba4bd9c30d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250753"
---
# Get-PSRepository

## SAMENVATTING
Hiermee worden Power shell-opslag plaatsen opgehaald.

## SYNTAXIS

```
Get-PSRepository [[-Name] <String[]>] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Get-PSRepository** worden Power shell-module opslagplaatsen opgehaald die zijn geregistreerd voor de huidige gebruiker.

## VOORBEELDEN

### Voor beeld 1: alle module opslagplaatsen ophalen

```
PS C:\> Get-PSRepository
Name                                     SourceLocation                                     OneGetProvider       InstallationPolicy
----                                     --------------                                     --------------       ------------------
PSGallery                                http://go.micro...                                 NuGet                Untrusted
myNuGetSource                            https://myget.c...                                 NuGet                Trusted
```

Met deze opdracht worden alle module opslagplaatsen die zijn geregistreerd voor de huidige gebruiker.

### Voor beeld 2: module opslagplaatsen op naam ophalen

```
PS C:\> Get-PSRepository -Name "*NuGet*"
```

Met deze opdracht worden alle module opslagplaatsen opgehaald die NuGet in hun namen bevatten.

### Voor beeld 3: een module opslagplaats ophalen en de uitvoer opmaken

```
PS C:\> Get-PSRepository -Name "Local01" | Format-List * -Force
Name                      : local01
SourceLocation            : http://manikb-dev:8765/api/v2/
Trusted                   : True
Registered                : True
InstallationPolicy        : Trusted
PackageManagementProvider : NuGet
PublishLocation           : http://pattif-dev:8765/api/v2/package/
ScriptSourceLocation      : http://pattif-dev:8765/api/v2/artifacts/psscript
ScriptPublishLocation     : http://pattif-dev:8765/api/v2/package/
ProviderOptions           : {}
```

Met deze opdracht wordt de opslag plaats met de naam Local01 opgehaald en wordt de pijplijn operator gebruikt om dat object door te geven aan de Format-List-cmdlet.

## PARAMETERS

### -Name
Hiermee geeft u de namen op van de opslag plaatsen die moeten worden opgehaald.

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

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[REGI ster-PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

[Registratie ongedaan maken-PSRepository](Unregister-PSRepository.md)
