---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Objecten sorteren
ms.openlocfilehash: ed78e7e333f3468781c9cd96df2194fbdfebe753
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030780"
---
# <a name="sorting-objects"></a>Objecten sorteren

We kunnen weer gegeven gegevens ordenen om het scannen gemakkelijker te maken met behulp van de cmdlet `Sort-Object`. `Sort-Object` neemt de naam van een of meer eigenschappen op waarop moet worden gesorteerd, en retourneert gegevens gesorteerd op basis van de waarden van die eigenschappen.

## <a name="basic-sorting"></a>Basis sortering

Bekijk het probleem van het vermelden van submappen en bestanden in de huidige map.
Als we willen sorteren op **LastWriteTime** en vervolgens op **naam**, kunnen we dit doen door het volgende te typen:

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

U kunt de objecten ook in omgekeerde volg orde sorteren door de para meter **aflopende** switch op te geven.

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a>Hash-tabellen gebruiken

U kunt verschillende eigenschappen in verschillende orders sorteren door hash-tabellen in een matrix te gebruiken.
Elke hash-tabel gebruikt een **expressie** sleutel om de naam van de eigenschap op te geven als teken reeks en een **oplopende** of **aflopende** toets om de sorteer volgorde op te geven `$true` of `$false`.
De **expressie** sleutel is verplicht.
De **oplopende** of **aflopende** toets is optioneel.

In het volgende voor beeld worden objecten in aflopende volg orde **LastWriteTime** en oplopende **volg orde gesorteerd** .

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

U kunt ook een script Block instellen op de **expressie** sleutel.
Bij het uitvoeren van de `Sort-Object` cmdlet wordt de script Block uitgevoerd en wordt het resultaat gebruikt voor het sorteren.

In het volgende voor beeld worden objecten in aflopende volg orde gesorteerd op basis van de tijds Panne tussen **CreationTime** en **LastWriteTime**.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a>Tips

U kunt de naam van de **eigenschap** para meter als volgt weglaten:

```powershell
Sort-Object LastWriteTime, Name
```

U kunt niet alleen verwijzen naar `Sort-Object` door de ingebouwde alias `sort`:

```powershell
sort LastWriteTime, Name
```

De sleutels in de hash-tabellen voor het sorteren kunnen als volgt worden afgekort:

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

In dit voor beeld is **het e** staat voor **expressie**, **de d** staat voor **Aflopend**en de **een** staat voor **Oplopend**.

Om de Lees baarheid te verbeteren, kunt u de hash-tabellen in een afzonderlijke variabele plaatsen:

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
