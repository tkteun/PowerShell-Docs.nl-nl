---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Host
ms.openlocfilehash: de7dc6027653db063311bd34e1282e3cb5294e92
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705780"
---
# Clear-Host

## SAMENVATTING

Hiermee wordt de weer gave in het hostprogramma gewist.

## SYNTAXIS

```
Clear-Host [<CommonParameters>]
```

## BESCHRIJVING

De `Clear-Host` functie verwijdert alle tekst uit de huidige weer gave, inclusief opdrachten en uitvoer die mogelijk zijn verzameld. Wanneer dit is voltooid, wordt de opdracht prompt weer gegeven. U kunt de functie naam of de alias ervan gebruiken `cls` .

`Clear-Host` alleen van invloed op de huidige weer gave. Er worden geen opgeslagen resultaten verwijderd of alle items uit de sessie verwijderd. Sessie-specifieke items, zoals variabelen en functies, worden niet beïnvloed door deze functie.

Omdat het gedrag van de `Clear-Host` functie wordt bepaald door het hostprogramma, `Clear-Host` werkt mogelijk anders in verschillende host-Program ma's.

## VOORBEELDEN

### Voorbeeld 1

```
# Before

PS C:\> Get-Process

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    843      33    14428      22556    99    17.41   1688 CcmExec
     44       6     2196       4964    52     0.23    692 conhost
    646      12     2332       4896    49     1.12    388 csrss
    189      11     2860       7084   114     0.66   2896 csrss
     78      11     1876       4008    42     0.22   4000 csrss
     76       7     1848       5064    54     0.08   1028 dwm
    610      41    23952      44048   208     4.40   2080 explorer
      0       0        0         24     0               0 Idle
    182      32     7692      15980    91     0.23   3056 LogonUI
    186      25     7832      16068    91     0.27   3996 LogonUI
   1272      32    11512      20432    58    25.07    548 lsass
    267      10     3536       6736    34     0.80    556 lsm
    137      17     3520       7472    61     0.05   1220 msdtc
    447      31    70316      84476   201 1,429.67    836 MsMpEng
    265      18     7136      15628   134     2.20   3544 msseces
    248      16     6476       4076    76     0.22   1592 NisSrv
    368      25    61312      65508   614     1.78    848 powershell
    101       8     2304       6624    70     0.64   3648 rdpclip
    258      15     6804      12156    50     2.65    536 services
...

PS C:\> cls
#After

PS C:>
```

Met deze opdracht wordt de `cls` alias van gebruikt `Clear-Host` om de huidige weer gave te wissen.

## PARAMETERS

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen pipe invoer naar `Clear-Host` .

## UITVOER

### Geen

`Clear-Host` Er wordt geen uitvoer gegenereerd

## OPMERKINGEN

`Clear-Host` is een eenvoudige functie, niet een geavanceerde functie. U kunt de algemene para meters, zoals **debug**, niet gebruiken in een `Clear-Host` opdracht.

## GERELATEERDE KOPPELINGEN

[Get-host](../Microsoft.PowerShell.Utility/Get-Host.md)

[Out-host](Out-Host.md)

[Read-host](../Microsoft.PowerShell.Utility/Read-Host.md)

[Write-host](../Microsoft.PowerShell.Utility/Write-Host.md)

