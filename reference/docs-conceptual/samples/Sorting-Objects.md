---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Objecten sorteren
description: Met de cmdlet Sort-Object kunt u een verzameling objecten op een of meer eigenschappen sorteren.
ms.openlocfilehash: 836207adfc566003e9714e45920d9b4e24a677e9
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501011"
---
# <a name="sorting-objects"></a><span data-ttu-id="1d574-104">Objecten sorteren</span><span class="sxs-lookup"><span data-stu-id="1d574-104">Sorting Objects</span></span>

<span data-ttu-id="1d574-105">We kunnen weer gegeven gegevens ordenen om het scannen gemakkelijker te maken met behulp van de `Sort-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1d574-105">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="1d574-106">`Sort-Object` neemt de naam op van een of meer eigenschappen waarop moet worden gesorteerd, en retourneert gegevens die zijn gesorteerd op de waarden van die eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="1d574-106">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="1d574-107">Basis sortering</span><span class="sxs-lookup"><span data-stu-id="1d574-107">Basic sorting</span></span>

<span data-ttu-id="1d574-108">Bekijk het probleem van het vermelden van submappen en bestanden in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="1d574-108">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="1d574-109">Als we willen sorteren op **LastWriteTime** en vervolgens op **naam**, kunnen we dit doen door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="1d574-109">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

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

<span data-ttu-id="1d574-110">U kunt de objecten ook in omgekeerde volg orde sorteren door de para meter **aflopende** switch op te geven.</span><span class="sxs-lookup"><span data-stu-id="1d574-110">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

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

## <a name="using-hash-tables"></a><span data-ttu-id="1d574-111">Hash-tabellen gebruiken</span><span class="sxs-lookup"><span data-stu-id="1d574-111">Using hash tables</span></span>

<span data-ttu-id="1d574-112">U kunt verschillende eigenschappen in verschillende orders sorteren door hash-tabellen in een matrix te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1d574-112">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="1d574-113">Elke hash-tabel gebruikt een **expressie** sleutel om de naam van de eigenschap op te geven als teken reeks en een **oplopende** of **aflopende** toets om de sorteer volgorde op te geven `$true` `$false` .</span><span class="sxs-lookup"><span data-stu-id="1d574-113">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="1d574-114">De **expressie** sleutel is verplicht.</span><span class="sxs-lookup"><span data-stu-id="1d574-114">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="1d574-115">De **oplopende** of **aflopende** toets is optioneel.</span><span class="sxs-lookup"><span data-stu-id="1d574-115">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="1d574-116">In het volgende voor beeld worden objecten in aflopende volg orde **LastWriteTime** en oplopende **volg orde gesorteerd** .</span><span class="sxs-lookup"><span data-stu-id="1d574-116">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

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

<span data-ttu-id="1d574-117">U kunt ook een script Block instellen op de **expressie** sleutel.</span><span class="sxs-lookup"><span data-stu-id="1d574-117">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="1d574-118">Wanneer de cmdlet wordt uitgevoerd `Sort-Object` , wordt de script Block uitgevoerd en wordt het resultaat gebruikt voor het sorteren.</span><span class="sxs-lookup"><span data-stu-id="1d574-118">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="1d574-119">In het volgende voor beeld worden objecten in aflopende volg orde gesorteerd op basis van de tijds Panne tussen **CreationTime** en **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="1d574-119">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

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

## <a name="tips"></a><span data-ttu-id="1d574-120">Tips</span><span class="sxs-lookup"><span data-stu-id="1d574-120">Tips</span></span>

<span data-ttu-id="1d574-121">U kunt de naam van de **eigenschap** para meter als volgt weglaten:</span><span class="sxs-lookup"><span data-stu-id="1d574-121">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="1d574-122">U kunt ook verwijzen naar `Sort-Object` de ingebouwde alias `sort` :</span><span class="sxs-lookup"><span data-stu-id="1d574-122">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="1d574-123">De sleutels in de hash-tabellen voor het sorteren kunnen als volgt worden afgekort:</span><span class="sxs-lookup"><span data-stu-id="1d574-123">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="1d574-124">In dit voor beeld is **het e** staat voor **expressie**, **de d** staat voor **Aflopend**en de **een** staat voor **Oplopend**.</span><span class="sxs-lookup"><span data-stu-id="1d574-124">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="1d574-125">Om de Lees baarheid te verbeteren, kunt u de hash-tabellen in een afzonderlijke variabele plaatsen:</span><span class="sxs-lookup"><span data-stu-id="1d574-125">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
