---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Objecten sorteren
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 06aa15d89888f1ecbe60b8e1dfb4efebb1d73673
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086048"
---
# <a name="sorting-objects"></a>Objecten sorteren

We kunt indelen weergegeven gegevens zodat u gemakkelijk te scannen met behulp van de `Sort-Object` cmdlet. `Sort-Object` de naam van een of meer eigenschappen om te sorteren op neemt, en gegevens gesorteerd op basis van de waarden van deze eigenschappen worden geretourneerd.

## <a name="basic-sorting"></a>Basic sorteren

Houd rekening met het probleem van de aanbieding submappen en bestanden in de huidige map.
Als we sorteren willen op **LastWriteTime** en vervolgens op **naam**, kunnen we doen door te typen:

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

U kunt de objecten ook in omgekeerde volgorde sorteren door op te geven de **aflopend** parameter overschakelen.

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

## <a name="using-hash-tables"></a>Met behulp van hash-tabellen

U kunt verschillende eigenschappen op verschillende plekken sorteren met behulp van hash-tabellen in een matrix.
Elke hash-tabel maakt gebruik van een **expressie** sleutel om op te geven van de naam van de eigenschap als tekenreeks en een **oplopend** of **aflopend** sleutel om op te geven van de sorteervolgorde door `$true` of `$false`.
De **expressie** sleutel is verplicht.
De **oplopend** of **aflopend** sleutel is optioneel.

Het volgende voorbeeld worden objecten in aflopende volgorde gesorteerd **LastWriteTime** volgorde en oplopend **naam** volgorde.

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

U kunt ook een scriptblock instellen op de **expressie** sleutel.
Bij het uitvoeren van de `Sort-Object` cmdlet, de scriptblock wordt uitgevoerd en het resultaat wordt gebruikt voor het sorteren.

Het volgende voorbeeld worden gesorteerd van objecten in aflopende volgorde van de tijdsduur tussen **CreationTime** en **LastWriteTime**.

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

U kunt weglaten de **eigenschap** parameternaam als volgt:

```powershell
Sort-Object LastWriteTime, Name
```

Daarnaast kunt u verwijzen naar `Sort-Object` door de ingebouwde alias `sort`:

```powershell
sort LastWriteTime, Name
```

De sleutels in de hashtabellen voor het sorteren van kunnen worden afgekort als volgt:

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

In dit voorbeeld wordt de **e** staat voor **expressie**, wordt de **d** staat voor **aflopend**, en de **een** staat voor **oplopend**.

Voor een betere leesbaarheid, plaatst u de hashtabellen in een afzonderlijke variabele:

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```