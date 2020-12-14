---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 908a43506bfbff964cfbdd8eea270b1fa42c3e77
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705411"
---
# Unregister-PSRepository

## SAMENVATTING
Hiermee wordt de registratie van een opslag plaats ongedaan gemaakt.

## SYNTAXIS

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet wordt de `Unregister-PSRepository` registratie van een opslag plaats voor de huidige gebruiker ongedaan gemaakt.

## VOORBEELDEN

### Voor beeld 1: de registratie van een opslag plaats opheffen

In dit voor beeld wordt de registratie van de opslag plaats met de naam myNuGetSource ongedaan gemaakt.

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### Voor beeld 2: alle opslag plaatsen ongedaan maken

In dit voor beeld worden `Get-PSRepository` alle geregistreerde opslag plaatsen gebruikt en wordt de pijplijn operator gebruikt om de `Unregister-PSRepository` registratie ervan ongedaan te maken.

```powershell
Get-PSRepository | Unregister-PSRepository
```

## PARAMETERS

### -Name

Hiermee geeft u een matrix met namen op van de opslag plaatsen die u wilt verwijderen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System.String[]

## UITVOER

### System. object

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-PSRepository](Get-PSRepository.md)

[REGI ster-PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)
