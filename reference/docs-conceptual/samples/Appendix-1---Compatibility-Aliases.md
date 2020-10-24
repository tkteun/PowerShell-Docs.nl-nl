---
ms.date: 08/03/2020
keywords: powershell,cmdlet
title: Bijlage 1 - Compatibiliteitsaliassen
description: Power Shell heeft verschillende aliassen waarmee UNIX-en cmd.exe-gebruikers bekende opdrachten kunnen gebruiken.
ms.openlocfilehash: 8cbbd5a358de9018fcb5c840e711cd76f7a9a353
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500739"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="e896d-104">Bijlage 1-compatibiliteits aliassen</span><span class="sxs-lookup"><span data-stu-id="e896d-104">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="e896d-105">Power Shell heeft verschillende aliassen waarmee **UNIX** -en **cmd.exe** -gebruikers bekende opdrachten kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e896d-105">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="e896d-106">De opdrachten en hun bijbehorende Power shell-cmdlet-en Power shell-alias worden weer gegeven in de volgende tabel:</span><span class="sxs-lookup"><span data-stu-id="e896d-106">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|            <span data-ttu-id="e896d-107">cmd.exe opdracht</span><span class="sxs-lookup"><span data-stu-id="e896d-107">cmd.exe command</span></span>            | <span data-ttu-id="e896d-108">UNIX-opdracht</span><span class="sxs-lookup"><span data-stu-id="e896d-108">UNIX command</span></span> | <span data-ttu-id="e896d-109">Power shell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="e896d-109">PowerShell cmdlet</span></span> | <span data-ttu-id="e896d-110">Power shell-alias</span><span class="sxs-lookup"><span data-stu-id="e896d-110">PowerShell alias</span></span> |
| ------------------------------------- | ------------ | ----------------- | ---------------- |
| <span data-ttu-id="e896d-111">**cd**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="e896d-111">**cd**, **chdir**</span></span>                     | <span data-ttu-id="e896d-112">**-**</span><span class="sxs-lookup"><span data-stu-id="e896d-112">**cd**</span></span>       | `Set-Location`    | `sl`             |
| <span data-ttu-id="e896d-113">**compatibiliteit**</span><span class="sxs-lookup"><span data-stu-id="e896d-113">**cls**</span></span>                               | <span data-ttu-id="e896d-114">**Maak**</span><span class="sxs-lookup"><span data-stu-id="e896d-114">**clear**</span></span>    | `Clear-Host`      | `cls`            |
| <span data-ttu-id="e896d-115">**Kopieer**</span><span class="sxs-lookup"><span data-stu-id="e896d-115">**copy**</span></span>                              | <span data-ttu-id="e896d-116">**p**</span><span class="sxs-lookup"><span data-stu-id="e896d-116">**cp**</span></span>       | `Copy-Item`       | `cpi`            |
| <span data-ttu-id="e896d-117">**del**, **wissen**, **RD**, **rmdir**</span><span class="sxs-lookup"><span data-stu-id="e896d-117">**del**, **erase**, **rd**, **rmdir**</span></span> | <span data-ttu-id="e896d-118">**RM**</span><span class="sxs-lookup"><span data-stu-id="e896d-118">**rm**</span></span>       | `Remove-Item`     | `ri`             |
| <span data-ttu-id="e896d-119">**dir**</span><span class="sxs-lookup"><span data-stu-id="e896d-119">**dir**</span></span>                               | <span data-ttu-id="e896d-120">**1**</span><span class="sxs-lookup"><span data-stu-id="e896d-120">**ls**</span></span>       | `Get-ChildItem`   | `gci`            |
| <span data-ttu-id="e896d-121">**echo**</span><span class="sxs-lookup"><span data-stu-id="e896d-121">**echo**</span></span>                              | <span data-ttu-id="e896d-122">**echo**</span><span class="sxs-lookup"><span data-stu-id="e896d-122">**echo**</span></span>     | `Write-Output`    | `write`          |
| <span data-ttu-id="e896d-123">**MD**</span><span class="sxs-lookup"><span data-stu-id="e896d-123">**md**</span></span>                                | <span data-ttu-id="e896d-124">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="e896d-124">**mkdir**</span></span>    | `New-Item`        | `ni`             |
| <span data-ttu-id="e896d-125">**Ga**</span><span class="sxs-lookup"><span data-stu-id="e896d-125">**move**</span></span>                              | <span data-ttu-id="e896d-126">**MV**</span><span class="sxs-lookup"><span data-stu-id="e896d-126">**mv**</span></span>       | `Move-Item`       | `mi`             |
| <span data-ttu-id="e896d-127">**popd**</span><span class="sxs-lookup"><span data-stu-id="e896d-127">**popd**</span></span>                              | <span data-ttu-id="e896d-128">**popd**</span><span class="sxs-lookup"><span data-stu-id="e896d-128">**popd**</span></span>     | `Pop-Location`    | `popd`           |
| <span data-ttu-id="e896d-129">**pushd**</span><span class="sxs-lookup"><span data-stu-id="e896d-129">**pushd**</span></span>                             | <span data-ttu-id="e896d-130">**pushd**</span><span class="sxs-lookup"><span data-stu-id="e896d-130">**pushd**</span></span>    | `Push-Location`   | `pushd`          |
| <span data-ttu-id="e896d-131">**Outlook**</span><span class="sxs-lookup"><span data-stu-id="e896d-131">**ren**</span></span>                               | <span data-ttu-id="e896d-132">**MV**</span><span class="sxs-lookup"><span data-stu-id="e896d-132">**mv**</span></span>       | `Rename-Item`     | `rni`            |
| <span data-ttu-id="e896d-133">**type**</span><span class="sxs-lookup"><span data-stu-id="e896d-133">**type**</span></span>                              | <span data-ttu-id="e896d-134">**Cat5**</span><span class="sxs-lookup"><span data-stu-id="e896d-134">**cat**</span></span>      | `Get-Content`     | `gc`             |

<span data-ttu-id="e896d-135">Als u de Power shell-aliassen wilt vinden, gebruikt u de cmdlet [Get-alias](xref:Microsoft.PowerShell.Utility.Get-Alias) .</span><span class="sxs-lookup"><span data-stu-id="e896d-135">To find the PowerShell aliases, use the [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias) cmdlet.</span></span> <span data-ttu-id="e896d-136">Als u de aliassen van een cmdlet wilt weer geven, gebruikt u de para meter **definitie** en geeft u de naam van de cmdlet op.</span><span class="sxs-lookup"><span data-stu-id="e896d-136">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="e896d-137">Als u de naam van de cmdlet van een alias wilt zoeken, gebruikt u de para meter **name** en geeft u de alias op.</span><span class="sxs-lookup"><span data-stu-id="e896d-137">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

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
