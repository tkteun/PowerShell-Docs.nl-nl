---
ms.date: 08/28/2019
ms.topic: reference
title: Cmdlets importeren met modules
description: Cmdlets importeren met modules
ms.openlocfilehash: 485a4be4d2accaf050a6536e7f92a0673f62a30b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657290"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="b9d51-103">Cmdlets importeren met modules</span><span class="sxs-lookup"><span data-stu-id="b9d51-103">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="b9d51-104">In dit artikel wordt beschreven hoe u cmdlets importeert in een Power shell-sessie met behulp van een binaire module.</span><span class="sxs-lookup"><span data-stu-id="b9d51-104">This article describes how to import cmdlets to a PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="b9d51-105">De leden van modules kunnen cmdlets, providers, functies, variabelen, aliassen en nog veel meer bevatten.</span><span class="sxs-lookup"><span data-stu-id="b9d51-105">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="b9d51-106">Modules kunnen alleen cmdlets en providers bevatten.</span><span class="sxs-lookup"><span data-stu-id="b9d51-106">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="b9d51-107">Cmdlets laden met behulp van een module</span><span class="sxs-lookup"><span data-stu-id="b9d51-107">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="b9d51-108">Maak een map met de naam van het assembly-bestand waarin de cmdlets worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="b9d51-108">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="b9d51-109">In deze procedure wordt de map module gemaakt in de map Windows `system32` .</span><span class="sxs-lookup"><span data-stu-id="b9d51-109">In this procedure, the module folder is created in the Windows `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. <span data-ttu-id="b9d51-110">Zorg ervoor dat de `PSModulePath` omgevings variabele het pad naar de nieuwe module map bevat.</span><span class="sxs-lookup"><span data-stu-id="b9d51-110">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="b9d51-111">Standaard wordt de systeemmap al toegevoegd aan de `PSModulePath` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="b9d51-111">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span> <span data-ttu-id="b9d51-112">Als u wilt weer geven `PSModulePath` , typt u: `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="b9d51-112">To view the `PSModulePath`, type: `$env:PSModulePath`.</span></span>

1. <span data-ttu-id="b9d51-113">Kopieer de cmdlet-assembly naar de module map.</span><span class="sxs-lookup"><span data-stu-id="b9d51-113">Copy the cmdlet assembly into the module folder.</span></span>

1. <span data-ttu-id="b9d51-114">Voeg een module manifest bestand ( `.psd1` ) toe aan de hoofdmap van de module.</span><span class="sxs-lookup"><span data-stu-id="b9d51-114">Add a module manifest file (`.psd1`) in the module's root folder.</span></span> <span data-ttu-id="b9d51-115">Power shell gebruikt het module manifest om uw module te importeren.</span><span class="sxs-lookup"><span data-stu-id="b9d51-115">PowerShell uses the module manifest to import your module.</span></span> <span data-ttu-id="b9d51-116">Zie [een Power shell-module manifest schrijven](../module/how-to-write-a-powershell-module-manifest.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b9d51-116">For more information, see [How to Write a PowerShell Module Manifest](../module/how-to-write-a-powershell-module-manifest.md).</span></span>

1. <span data-ttu-id="b9d51-117">Voer de volgende opdracht uit om de cmdlets toe te voegen aan de sessie:</span><span class="sxs-lookup"><span data-stu-id="b9d51-117">Run the following command to add the cmdlets to the session:</span></span>

   `Import-Module [Module_Name]`

   <span data-ttu-id="b9d51-118">Deze procedure kan worden gebruikt om uw cmdlets te testen.</span><span class="sxs-lookup"><span data-stu-id="b9d51-118">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="b9d51-119">Alle cmdlets in de assembly worden toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="b9d51-119">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="b9d51-120">Zie [een Windows Power shell-module schrijven](../module/writing-a-windows-powershell-module.md)voor meer informatie over modules.</span><span class="sxs-lookup"><span data-stu-id="b9d51-120">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b9d51-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b9d51-121">See also</span></span>

[<span data-ttu-id="b9d51-122">Een manifest voor een PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="b9d51-122">How to Write a PowerShell Module Manifest</span></span>](../module/how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="b9d51-123">Een PowerShell-module importeren</span><span class="sxs-lookup"><span data-stu-id="b9d51-123">Importing a PowerShell Module</span></span>](../module/importing-a-powershell-module.md)

[<span data-ttu-id="b9d51-124">Import-module</span><span class="sxs-lookup"><span data-stu-id="b9d51-124">Import-Module</span></span>](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[<span data-ttu-id="b9d51-125">Modules installeren</span><span class="sxs-lookup"><span data-stu-id="b9d51-125">Installing Modules</span></span>](../module/installing-a-powershell-module.md)

[<span data-ttu-id="b9d51-126">Het PSModulePath-installatiepad wijzigen</span><span class="sxs-lookup"><span data-stu-id="b9d51-126">Modifying the PSModulePath Installation Path</span></span>](../module/modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="b9d51-127">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="b9d51-127">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
