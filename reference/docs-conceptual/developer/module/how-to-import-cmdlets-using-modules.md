---
title: Cmdlets importeren met modules | Microsoft Docs
ms.date: 08/28/2019
ms.openlocfilehash: fa8d629c14b06e3f9e9d6151cf09aa6b4acce358
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779366"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="8402c-102">Cmdlets importeren met modules</span><span class="sxs-lookup"><span data-stu-id="8402c-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="8402c-103">In dit artikel wordt beschreven hoe u cmdlets importeert in een Power shell-sessie met behulp van een binaire module.</span><span class="sxs-lookup"><span data-stu-id="8402c-103">This article describes how to import cmdlets to a PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="8402c-104">De leden van modules kunnen cmdlets, providers, functies, variabelen, aliassen en nog veel meer bevatten.</span><span class="sxs-lookup"><span data-stu-id="8402c-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="8402c-105">Modules kunnen alleen cmdlets en providers bevatten.</span><span class="sxs-lookup"><span data-stu-id="8402c-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="8402c-106">Cmdlets laden met behulp van een module</span><span class="sxs-lookup"><span data-stu-id="8402c-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="8402c-107">Maak een map met de naam van het assembly-bestand waarin de cmdlets worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="8402c-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="8402c-108">In deze procedure wordt de map module gemaakt in de map Windows `system32` .</span><span class="sxs-lookup"><span data-stu-id="8402c-108">In this procedure, the module folder is created in the Windows `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. <span data-ttu-id="8402c-109">Zorg ervoor dat de `PSModulePath` omgevings variabele het pad naar de nieuwe module map bevat.</span><span class="sxs-lookup"><span data-stu-id="8402c-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="8402c-110">Standaard wordt de systeemmap al toegevoegd aan de `PSModulePath` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="8402c-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span> <span data-ttu-id="8402c-111">Als u wilt weer geven `PSModulePath` , typt u: `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="8402c-111">To view the `PSModulePath`, type: `$env:PSModulePath`.</span></span>

1. <span data-ttu-id="8402c-112">Kopieer de cmdlet-assembly naar de module map.</span><span class="sxs-lookup"><span data-stu-id="8402c-112">Copy the cmdlet assembly into the module folder.</span></span>

1. <span data-ttu-id="8402c-113">Voeg een module manifest bestand ( `.psd1` ) toe aan de hoofdmap van de module.</span><span class="sxs-lookup"><span data-stu-id="8402c-113">Add a module manifest file (`.psd1`) in the module's root folder.</span></span> <span data-ttu-id="8402c-114">Power shell gebruikt het module manifest om uw module te importeren.</span><span class="sxs-lookup"><span data-stu-id="8402c-114">PowerShell uses the module manifest to import your module.</span></span> <span data-ttu-id="8402c-115">Zie [een Power shell-module manifest schrijven](../module/how-to-write-a-powershell-module-manifest.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8402c-115">For more information, see [How to Write a PowerShell Module Manifest](../module/how-to-write-a-powershell-module-manifest.md).</span></span>

1. <span data-ttu-id="8402c-116">Voer de volgende opdracht uit om de cmdlets toe te voegen aan de sessie:</span><span class="sxs-lookup"><span data-stu-id="8402c-116">Run the following command to add the cmdlets to the session:</span></span>

   `Import-Module [Module_Name]`

   <span data-ttu-id="8402c-117">Deze procedure kan worden gebruikt om uw cmdlets te testen.</span><span class="sxs-lookup"><span data-stu-id="8402c-117">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="8402c-118">Alle cmdlets in de assembly worden toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="8402c-118">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="8402c-119">Zie [een Windows Power shell-module schrijven](../module/writing-a-windows-powershell-module.md)voor meer informatie over modules.</span><span class="sxs-lookup"><span data-stu-id="8402c-119">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8402c-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8402c-120">See also</span></span>

[<span data-ttu-id="8402c-121">Een manifest voor een PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="8402c-121">How to Write a PowerShell Module Manifest</span></span>](../module/how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="8402c-122">Een PowerShell-module importeren</span><span class="sxs-lookup"><span data-stu-id="8402c-122">Importing a PowerShell Module</span></span>](../module/importing-a-powershell-module.md)

[<span data-ttu-id="8402c-123">Import-module</span><span class="sxs-lookup"><span data-stu-id="8402c-123">Import-Module</span></span>](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[<span data-ttu-id="8402c-124">Modules installeren</span><span class="sxs-lookup"><span data-stu-id="8402c-124">Installing Modules</span></span>](../module/installing-a-powershell-module.md)

[<span data-ttu-id="8402c-125">Het PSModulePath-installatiepad wijzigen</span><span class="sxs-lookup"><span data-stu-id="8402c-125">Modifying the PSModulePath Installation Path</span></span>](../module/modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="8402c-126">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="8402c-126">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
