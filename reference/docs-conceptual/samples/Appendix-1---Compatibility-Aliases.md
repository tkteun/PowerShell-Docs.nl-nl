---
ms.date: 09/09/2019
keywords: Power shell, cmdlet
title: Bijlage 1 - Compatibiliteitsaliassen
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848161"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="8b3d1-103">Bijlage 1-compatibiliteits aliassen</span><span class="sxs-lookup"><span data-stu-id="8b3d1-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="8b3d1-104">Power Shell heeft verschillende aliassen waarmee **UNIX** -en **cmd. exe** -gebruikers bekende opdrachten kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8b3d1-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="8b3d1-105">De opdrachten en hun bijbehorende Power shell-cmdlet-en Power shell-alias worden weer gegeven in de volgende tabel:</span><span class="sxs-lookup"><span data-stu-id="8b3d1-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|<span data-ttu-id="8b3d1-106">opdracht cmd. exe</span><span class="sxs-lookup"><span data-stu-id="8b3d1-106">cmd.exe command</span></span>|<span data-ttu-id="8b3d1-107">UNIX-opdracht</span><span class="sxs-lookup"><span data-stu-id="8b3d1-107">UNIX command</span></span>|<span data-ttu-id="8b3d1-108">Power shell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="8b3d1-108">PowerShell cmdlet</span></span>|<span data-ttu-id="8b3d1-109">Power shell-alias</span><span class="sxs-lookup"><span data-stu-id="8b3d1-109">PowerShell alias</span></span>|
|---------------|----------------|--------------|------------|
|<span data-ttu-id="8b3d1-110">**compatibiliteit**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-110">**cls**</span></span>|<span data-ttu-id="8b3d1-111">**Maak**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-111">**clear**</span></span>|<span data-ttu-id="8b3d1-112">`Clear-Host`functieassembly</span><span class="sxs-lookup"><span data-stu-id="8b3d1-112">`Clear-Host` (function)</span></span>|`cls`|
|<span data-ttu-id="8b3d1-113">**Kopieer**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-113">**copy**</span></span>|<span data-ttu-id="8b3d1-114">**p**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-114">**cp**</span></span>|`Copy-Item`|`cpi`|
|<span data-ttu-id="8b3d1-115">**dir**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-115">**dir**</span></span>|<span data-ttu-id="8b3d1-116">**1**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-116">**ls**</span></span>|`Get-ChildItem`|`gci`|
|<span data-ttu-id="8b3d1-117">**type**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-117">**type**</span></span>|<span data-ttu-id="8b3d1-118">**cat**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-118">**cat**</span></span>|`Get-Content`|`gc`|
|<span data-ttu-id="8b3d1-119">**Ga**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-119">**move**</span></span>|<span data-ttu-id="8b3d1-120">**MV**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-120">**mv**</span></span>|`Move-Item`|`mi`|
|<span data-ttu-id="8b3d1-121">**MD**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-121">**md**</span></span>|<span data-ttu-id="8b3d1-122">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-122">**mkdir**</span></span>|`New-Item`|`ni`|
|<span data-ttu-id="8b3d1-123">**pushd**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-123">**pushd**</span></span>|<span data-ttu-id="8b3d1-124">**pushd**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-124">**pushd**</span></span>|`Push-Location`|`pushd`|
|<span data-ttu-id="8b3d1-125">**popd**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-125">**popd**</span></span>|<span data-ttu-id="8b3d1-126">**popd**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-126">**popd**</span></span>|`Pop-Location`|`popd`|
|<span data-ttu-id="8b3d1-127">**del**, **wissen**, **RD**, **rmdir**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-127">**del**, **erase**, **rd**, **rmdir**</span></span>|<span data-ttu-id="8b3d1-128">**RM**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-128">**rm**</span></span>|`Remove-Item`|`ri`|
|<span data-ttu-id="8b3d1-129">**Outlook**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-129">**ren**</span></span>|<span data-ttu-id="8b3d1-130">**MV**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-130">**mv**</span></span>|`Rename-Item`|`rni`|
|<span data-ttu-id="8b3d1-131">**cd**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-131">**cd**, **chdir**</span></span>|<span data-ttu-id="8b3d1-132">**-**</span><span class="sxs-lookup"><span data-stu-id="8b3d1-132">**cd**</span></span>|`Set-Location`|`sl`|

<span data-ttu-id="8b3d1-133">Als u de Power shell-aliassen wilt vinden, gebruikt u de cmdlet [Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) .</span><span class="sxs-lookup"><span data-stu-id="8b3d1-133">To find the PowerShell aliases, use the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet.</span></span> <span data-ttu-id="8b3d1-134">Als u de aliassen van een cmdlet wilt weer geven, gebruikt u de para meter **definitie** en geeft u de naam van de cmdlet op.</span><span class="sxs-lookup"><span data-stu-id="8b3d1-134">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="8b3d1-135">Als u de naam van de cmdlet van een alias wilt zoeken, gebruikt u de para meter **name** en geeft u de alias op.</span><span class="sxs-lookup"><span data-stu-id="8b3d1-135">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

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
