---
title: Cmdlets importeren met modules | Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 2f145795a57c988da0cb4ed294142aa141c53cae
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355543"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="5c612-102">Cmdlets importeren met modules</span><span class="sxs-lookup"><span data-stu-id="5c612-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="5c612-103">In dit artikel wordt beschreven hoe u cmdlets importeert in een Power shell-sessie met behulp van een binaire module.</span><span class="sxs-lookup"><span data-stu-id="5c612-103">This article describes how to import cmdlets to a PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="5c612-104">De leden van modules kunnen cmdlets, providers, functies, variabelen, aliassen en nog veel meer bevatten.</span><span class="sxs-lookup"><span data-stu-id="5c612-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="5c612-105">Modules kunnen alleen cmdlets en providers bevatten.</span><span class="sxs-lookup"><span data-stu-id="5c612-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="5c612-106">Cmdlets laden met behulp van een module</span><span class="sxs-lookup"><span data-stu-id="5c612-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="5c612-107">Maak een map met de naam van het assembly-bestand waarin de cmdlets worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="5c612-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="5c612-108">In deze procedure wordt de map module gemaakt in de map Windows `system32`.</span><span class="sxs-lookup"><span data-stu-id="5c612-108">In this procedure, the module folder is created in the Windows `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. <span data-ttu-id="5c612-109">Zorg ervoor dat de omgevings variabele @no__t 0 het pad naar de nieuwe module map bevat.</span><span class="sxs-lookup"><span data-stu-id="5c612-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="5c612-110">Standaard is de systeemmap al toegevoegd aan de omgevings variabele `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="5c612-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span> <span data-ttu-id="5c612-111">Als u de `PSModulePath` wilt weer geven, typt u: `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="5c612-111">To view the `PSModulePath`, type: `$env:PSModulePath`.</span></span>

1. <span data-ttu-id="5c612-112">Kopieer de cmdlet-assembly naar de module map.</span><span class="sxs-lookup"><span data-stu-id="5c612-112">Copy the cmdlet assembly into the module folder.</span></span>

1. <span data-ttu-id="5c612-113">Voeg een module manifest bestand (`.psd1`) toe in de hoofdmap van de module.</span><span class="sxs-lookup"><span data-stu-id="5c612-113">Add a module manifest file (`.psd1`) in the module's root folder.</span></span> <span data-ttu-id="5c612-114">Power shell gebruikt het module manifest om uw module te importeren.</span><span class="sxs-lookup"><span data-stu-id="5c612-114">PowerShell uses the module manifest to import your module.</span></span> <span data-ttu-id="5c612-115">Zie [een Power shell-module manifest schrijven](../module/how-to-write-a-powershell-module-manifest.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5c612-115">For more information, see [How to Write a PowerShell Module Manifest](../module/how-to-write-a-powershell-module-manifest.md).</span></span>

1. <span data-ttu-id="5c612-116">Voer de volgende opdracht uit om de cmdlets toe te voegen aan de sessie:</span><span class="sxs-lookup"><span data-stu-id="5c612-116">Run the following command to add the cmdlets to the session:</span></span>

   `Import-Module [Module_Name]`

   <span data-ttu-id="5c612-117">Deze procedure kan worden gebruikt om uw cmdlets te testen.</span><span class="sxs-lookup"><span data-stu-id="5c612-117">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="5c612-118">Alle cmdlets in de assembly worden toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="5c612-118">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="5c612-119">Zie [een Windows Power shell-module schrijven](../module/writing-a-windows-powershell-module.md)voor meer informatie over modules.</span><span class="sxs-lookup"><span data-stu-id="5c612-119">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5c612-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5c612-120">See also</span></span>

[<span data-ttu-id="5c612-121">Een Power shell-module manifest schrijven</span><span class="sxs-lookup"><span data-stu-id="5c612-121">How to Write a PowerShell Module Manifest</span></span>](../module/how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="5c612-122">Een Power shell-module importeren</span><span class="sxs-lookup"><span data-stu-id="5c612-122">Importing a PowerShell Module</span></span>](../module/importing-a-powershell-module.md)

[<span data-ttu-id="5c612-123">Import-module</span><span class="sxs-lookup"><span data-stu-id="5c612-123">Import-Module</span></span>](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[<span data-ttu-id="5c612-124">Modules installeren</span><span class="sxs-lookup"><span data-stu-id="5c612-124">Installing Modules</span></span>](../module/installing-a-powershell-module.md)

[<span data-ttu-id="5c612-125">Het installatiepad van PSModulePath wijzigen</span><span class="sxs-lookup"><span data-stu-id="5c612-125">Modifying the PSModulePath Installation Path</span></span>](../module/modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="5c612-126">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="5c612-126">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
