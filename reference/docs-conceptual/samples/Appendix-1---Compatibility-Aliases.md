---
ms.date: 08/03/2020
keywords: powershell,cmdlet
title: Bijlage 1 - Compatibiliteitsaliassen
ms.openlocfilehash: e5bd170fea6b6109d2ef4fd58863d6cc8a0e3ae1
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/04/2020
ms.locfileid: "87758496"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="f1e91-103">Bijlage 1-compatibiliteits aliassen</span><span class="sxs-lookup"><span data-stu-id="f1e91-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="f1e91-104">Power Shell heeft verschillende aliassen waarmee **UNIX** -en **cmd.exe** -gebruikers bekende opdrachten kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f1e91-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="f1e91-105">De opdrachten en hun bijbehorende Power shell-cmdlet-en Power shell-alias worden weer gegeven in de volgende tabel:</span><span class="sxs-lookup"><span data-stu-id="f1e91-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|            <span data-ttu-id="f1e91-106">cmd.exe opdracht</span><span class="sxs-lookup"><span data-stu-id="f1e91-106">cmd.exe command</span></span>            | <span data-ttu-id="f1e91-107">UNIX-opdracht</span><span class="sxs-lookup"><span data-stu-id="f1e91-107">UNIX command</span></span> | <span data-ttu-id="f1e91-108">Power shell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="f1e91-108">PowerShell cmdlet</span></span> | <span data-ttu-id="f1e91-109">Power shell-alias</span><span class="sxs-lookup"><span data-stu-id="f1e91-109">PowerShell alias</span></span> |
| ------------------------------------- | ------------ | ----------------- | ---------------- |
| <span data-ttu-id="f1e91-110">**cd**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="f1e91-110">**cd**, **chdir**</span></span>                     | <span data-ttu-id="f1e91-111">**-**</span><span class="sxs-lookup"><span data-stu-id="f1e91-111">**cd**</span></span>       | `Set-Location`    | `sl`             |
| <span data-ttu-id="f1e91-112">**compatibiliteit**</span><span class="sxs-lookup"><span data-stu-id="f1e91-112">**cls**</span></span>                               | <span data-ttu-id="f1e91-113">**Maak**</span><span class="sxs-lookup"><span data-stu-id="f1e91-113">**clear**</span></span>    | `Clear-Host`      | `cls`            |
| <span data-ttu-id="f1e91-114">**Kopieer**</span><span class="sxs-lookup"><span data-stu-id="f1e91-114">**copy**</span></span>                              | <span data-ttu-id="f1e91-115">**p**</span><span class="sxs-lookup"><span data-stu-id="f1e91-115">**cp**</span></span>       | `Copy-Item`       | `cpi`            |
| <span data-ttu-id="f1e91-116">**del**, **wissen**, **RD**, **rmdir**</span><span class="sxs-lookup"><span data-stu-id="f1e91-116">**del**, **erase**, **rd**, **rmdir**</span></span> | <span data-ttu-id="f1e91-117">**RM**</span><span class="sxs-lookup"><span data-stu-id="f1e91-117">**rm**</span></span>       | `Remove-Item`     | `ri`             |
| <span data-ttu-id="f1e91-118">**dir**</span><span class="sxs-lookup"><span data-stu-id="f1e91-118">**dir**</span></span>                               | <span data-ttu-id="f1e91-119">**1**</span><span class="sxs-lookup"><span data-stu-id="f1e91-119">**ls**</span></span>       | `Get-ChildItem`   | `gci`            |
| <span data-ttu-id="f1e91-120">**echo**</span><span class="sxs-lookup"><span data-stu-id="f1e91-120">**echo**</span></span>                              | <span data-ttu-id="f1e91-121">**echo**</span><span class="sxs-lookup"><span data-stu-id="f1e91-121">**echo**</span></span>     | `Write-Output`    | `write`          |
| <span data-ttu-id="f1e91-122">**MD**</span><span class="sxs-lookup"><span data-stu-id="f1e91-122">**md**</span></span>                                | <span data-ttu-id="f1e91-123">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="f1e91-123">**mkdir**</span></span>    | `New-Item`        | `ni`             |
| <span data-ttu-id="f1e91-124">**Ga**</span><span class="sxs-lookup"><span data-stu-id="f1e91-124">**move**</span></span>                              | <span data-ttu-id="f1e91-125">**MV**</span><span class="sxs-lookup"><span data-stu-id="f1e91-125">**mv**</span></span>       | `Move-Item`       | `mi`             |
| <span data-ttu-id="f1e91-126">**popd**</span><span class="sxs-lookup"><span data-stu-id="f1e91-126">**popd**</span></span>                              | <span data-ttu-id="f1e91-127">**popd**</span><span class="sxs-lookup"><span data-stu-id="f1e91-127">**popd**</span></span>     | `Pop-Location`    | `popd`           |
| <span data-ttu-id="f1e91-128">**pushd**</span><span class="sxs-lookup"><span data-stu-id="f1e91-128">**pushd**</span></span>                             | <span data-ttu-id="f1e91-129">**pushd**</span><span class="sxs-lookup"><span data-stu-id="f1e91-129">**pushd**</span></span>    | `Push-Location`   | `pushd`          |
| <span data-ttu-id="f1e91-130">**Outlook**</span><span class="sxs-lookup"><span data-stu-id="f1e91-130">**ren**</span></span>                               | <span data-ttu-id="f1e91-131">**MV**</span><span class="sxs-lookup"><span data-stu-id="f1e91-131">**mv**</span></span>       | `Rename-Item`     | `rni`            |
| <span data-ttu-id="f1e91-132">**type**</span><span class="sxs-lookup"><span data-stu-id="f1e91-132">**type**</span></span>                              | <span data-ttu-id="f1e91-133">**Cat5**</span><span class="sxs-lookup"><span data-stu-id="f1e91-133">**cat**</span></span>      | `Get-Content`     | `gc`             |

<span data-ttu-id="f1e91-134">Als u de Power shell-aliassen wilt vinden, gebruikt u de cmdlet [Get-alias](xref:Microsoft.PowerShell.Utility.Get-Alias) .</span><span class="sxs-lookup"><span data-stu-id="f1e91-134">To find the PowerShell aliases, use the [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias) cmdlet.</span></span> <span data-ttu-id="f1e91-135">Als u de aliassen van een cmdlet wilt weer geven, gebruikt u de para meter **definitie** en geeft u de naam van de cmdlet op.</span><span class="sxs-lookup"><span data-stu-id="f1e91-135">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="f1e91-136">Als u de naam van de cmdlet van een alias wilt zoeken, gebruikt u de para meter **name** en geeft u de alias op.</span><span class="sxs-lookup"><span data-stu-id="f1e91-136">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
