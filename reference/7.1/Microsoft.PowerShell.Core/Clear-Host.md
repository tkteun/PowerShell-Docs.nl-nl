---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Host
ms.openlocfilehash: 7f1481c34c22d3fdface82828b6c3afbbbd6fce0
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103193886"
---
# <span data-ttu-id="cfa1e-103">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="cfa1e-103">Clear-Host</span></span>

## <span data-ttu-id="cfa1e-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cfa1e-104">SYNOPSIS</span></span>

<span data-ttu-id="cfa1e-105">Hiermee wordt de weer gave in het hostprogramma gewist.</span><span class="sxs-lookup"><span data-stu-id="cfa1e-105">Clears the display in the host program.</span></span>

## <span data-ttu-id="cfa1e-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cfa1e-106">SYNTAX</span></span>

```
Clear-Host [<CommonParameters>]
```

## <span data-ttu-id="cfa1e-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cfa1e-107">DESCRIPTION</span></span>

<span data-ttu-id="cfa1e-108">De `Clear-Host` functie verwijdert alle tekst uit de huidige weer gave, inclusief opdrachten en uitvoer die mogelijk zijn verzameld.</span><span class="sxs-lookup"><span data-stu-id="cfa1e-108">The `Clear-Host` function removes all text from the current display, including commands and output that might have accumulated.</span></span> <span data-ttu-id="cfa1e-109">Wanneer dit is voltooid, wordt de opdracht prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="cfa1e-109">When complete, it displays the command prompt.</span></span> <span data-ttu-id="cfa1e-110">U kunt de functie naam of de alias ervan gebruiken `cls` .</span><span class="sxs-lookup"><span data-stu-id="cfa1e-110">You can use the function name or its alias, `cls`.</span></span>

<span data-ttu-id="cfa1e-111">`Clear-Host` alleen van invloed op de huidige weer gave.</span><span class="sxs-lookup"><span data-stu-id="cfa1e-111">`Clear-Host` affects only the current display.</span></span> <span data-ttu-id="cfa1e-112">Er worden geen opgeslagen resultaten verwijderd of alle items uit de sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="cfa1e-112">It does not delete saved results or remove any items from the session.</span></span> <span data-ttu-id="cfa1e-113">Sessie-specifieke items, zoals variabelen en functies, worden niet beïnvloed door deze functie.</span><span class="sxs-lookup"><span data-stu-id="cfa1e-113">Session-specific items, such as variables and functions, are not affected by this function.</span></span>

<span data-ttu-id="cfa1e-114">Omdat het gedrag van de `Clear-Host` functie wordt bepaald door het hostprogramma, `Clear-Host` werkt mogelijk anders in verschillende host-Program ma's.</span><span class="sxs-lookup"><span data-stu-id="cfa1e-114">Because the behavior of the `Clear-Host` function is determined by the host program, `Clear-Host` might work differently in different host programs.</span></span>

## <span data-ttu-id="cfa1e-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cfa1e-115">EXAMPLES</span></span>

### <span data-ttu-id="cfa1e-116">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="cfa1e-116">Example 1</span></span>

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

<span data-ttu-id="cfa1e-117">Met deze opdracht wordt de `cls` alias van gebruikt `Clear-Host` om de huidige weer gave te wissen.</span><span class="sxs-lookup"><span data-stu-id="cfa1e-117">This command uses the `cls` alias of `Clear-Host` to clear the current display.</span></span>

## <span data-ttu-id="cfa1e-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cfa1e-118">PARAMETERS</span></span>

### <span data-ttu-id="cfa1e-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cfa1e-119">CommonParameters</span></span>
<span data-ttu-id="cfa1e-120">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cfa1e-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cfa1e-121">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cfa1e-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cfa1e-122">INVOER</span><span class="sxs-lookup"><span data-stu-id="cfa1e-122">INPUTS</span></span>

### <span data-ttu-id="cfa1e-123">Geen</span><span class="sxs-lookup"><span data-stu-id="cfa1e-123">None</span></span>

<span data-ttu-id="cfa1e-124">U kunt geen pipe invoer naar `Clear-Host` .</span><span class="sxs-lookup"><span data-stu-id="cfa1e-124">You cannot pipe input to `Clear-Host`.</span></span>

## <span data-ttu-id="cfa1e-125">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cfa1e-125">OUTPUTS</span></span>

### <span data-ttu-id="cfa1e-126">Geen</span><span class="sxs-lookup"><span data-stu-id="cfa1e-126">None</span></span>

<span data-ttu-id="cfa1e-127">`Clear-Host` Er wordt geen uitvoer gegenereerd</span><span class="sxs-lookup"><span data-stu-id="cfa1e-127">`Clear-Host` does not generate any output</span></span>

## <span data-ttu-id="cfa1e-128">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cfa1e-128">NOTES</span></span>

<span data-ttu-id="cfa1e-129">`Clear-Host` is een eenvoudige functie, niet een geavanceerde functie.</span><span class="sxs-lookup"><span data-stu-id="cfa1e-129">`Clear-Host` is a simple function, not an advanced function.</span></span> <span data-ttu-id="cfa1e-130">U kunt de algemene para meters, zoals **debug**, niet gebruiken in een `Clear-Host` opdracht.</span><span class="sxs-lookup"><span data-stu-id="cfa1e-130">As such, you cannot use common parameters, such as **Debug**, in a `Clear-Host` command.</span></span>

## <span data-ttu-id="cfa1e-131">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cfa1e-131">RELATED LINKS</span></span>

[<span data-ttu-id="cfa1e-132">Get-host</span><span class="sxs-lookup"><span data-stu-id="cfa1e-132">Get-Host</span></span>](../Microsoft.PowerShell.Utility/Get-Host.md)

[<span data-ttu-id="cfa1e-133">Out-host</span><span class="sxs-lookup"><span data-stu-id="cfa1e-133">Out-Host</span></span>](Out-Host.md)

[<span data-ttu-id="cfa1e-134">Read-host</span><span class="sxs-lookup"><span data-stu-id="cfa1e-134">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)

[<span data-ttu-id="cfa1e-135">Write-host</span><span class="sxs-lookup"><span data-stu-id="cfa1e-135">Write-Host</span></span>](../Microsoft.PowerShell.Utility/Write-Host.md)

