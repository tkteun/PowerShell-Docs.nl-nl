---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Objecten sorteren
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 06aa15d89888f1ecbe60b8e1dfb4efebb1d73673
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403898"
---
# <a name="sorting-objects"></a><span data-ttu-id="3ae55-103">Objecten sorteren</span><span class="sxs-lookup"><span data-stu-id="3ae55-103">Sorting Objects</span></span>

<span data-ttu-id="3ae55-104">We kunt indelen weergegeven gegevens zodat u gemakkelijk te scannen met behulp van de `Sort-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3ae55-104">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="3ae55-105">`Sort-Object` de naam van een of meer eigenschappen om te sorteren op neemt, en gegevens gesorteerd op basis van de waarden van deze eigenschappen worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3ae55-105">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="3ae55-106">Basic sorteren</span><span class="sxs-lookup"><span data-stu-id="3ae55-106">Basic sorting</span></span>

<span data-ttu-id="3ae55-107">Houd rekening met het probleem van de aanbieding submappen en bestanden in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="3ae55-107">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="3ae55-108">Als we sorteren willen op **LastWriteTime** en vervolgens op **naam**, kunnen we doen door te typen:</span><span class="sxs-lookup"><span data-stu-id="3ae55-108">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

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

<span data-ttu-id="3ae55-109">U kunt de objecten ook in omgekeerde volgorde sorteren door op te geven de **aflopend** parameter overschakelen.</span><span class="sxs-lookup"><span data-stu-id="3ae55-109">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

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

## <a name="using-hash-tables"></a><span data-ttu-id="3ae55-110">Met behulp van hash-tabellen</span><span class="sxs-lookup"><span data-stu-id="3ae55-110">Using hash tables</span></span>

<span data-ttu-id="3ae55-111">U kunt verschillende eigenschappen op verschillende plekken sorteren met behulp van hash-tabellen in een matrix.</span><span class="sxs-lookup"><span data-stu-id="3ae55-111">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="3ae55-112">Elke hash-tabel maakt gebruik van een **expressie** sleutel om op te geven van de naam van de eigenschap als tekenreeks en een **oplopend** of **aflopend** sleutel om op te geven van de sorteervolgorde door `$true` of `$false`.</span><span class="sxs-lookup"><span data-stu-id="3ae55-112">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="3ae55-113">De **expressie** sleutel is verplicht.</span><span class="sxs-lookup"><span data-stu-id="3ae55-113">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="3ae55-114">De **oplopend** of **aflopend** sleutel is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3ae55-114">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="3ae55-115">Het volgende voorbeeld worden objecten in aflopende volgorde gesorteerd **LastWriteTime** volgorde en oplopend **naam** volgorde.</span><span class="sxs-lookup"><span data-stu-id="3ae55-115">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

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

<span data-ttu-id="3ae55-116">U kunt ook een scriptblock instellen op de **expressie** sleutel.</span><span class="sxs-lookup"><span data-stu-id="3ae55-116">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="3ae55-117">Bij het uitvoeren van de `Sort-Object` cmdlet, de scriptblock wordt uitgevoerd en het resultaat wordt gebruikt voor het sorteren.</span><span class="sxs-lookup"><span data-stu-id="3ae55-117">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="3ae55-118">Het volgende voorbeeld worden gesorteerd van objecten in aflopende volgorde van de tijdsduur tussen **CreationTime** en **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="3ae55-118">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

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

## <a name="tips"></a><span data-ttu-id="3ae55-119">Tips</span><span class="sxs-lookup"><span data-stu-id="3ae55-119">Tips</span></span>

<span data-ttu-id="3ae55-120">U kunt weglaten de **eigenschap** parameternaam als volgt:</span><span class="sxs-lookup"><span data-stu-id="3ae55-120">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="3ae55-121">Daarnaast kunt u verwijzen naar `Sort-Object` door de ingebouwde alias `sort`:</span><span class="sxs-lookup"><span data-stu-id="3ae55-121">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="3ae55-122">De sleutels in de hashtabellen voor het sorteren van kunnen worden afgekort als volgt:</span><span class="sxs-lookup"><span data-stu-id="3ae55-122">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="3ae55-123">In dit voorbeeld wordt de **e** staat voor **expressie**, wordt de **d** staat voor **aflopend**, en de **een** staat voor **oplopend**.</span><span class="sxs-lookup"><span data-stu-id="3ae55-123">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="3ae55-124">Voor een betere leesbaarheid, plaatst u de hashtabellen in een afzonderlijke variabele:</span><span class="sxs-lookup"><span data-stu-id="3ae55-124">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```