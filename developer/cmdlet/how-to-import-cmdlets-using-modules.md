---
title: Het importeren van Modules met Cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849012"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="caa15-102">Cmdlets importeren met modules</span><span class="sxs-lookup"><span data-stu-id="caa15-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="caa15-103">In dit onderwerp wordt beschreven hoe u cmdlets in een Windows PowerShell-sessie met behulp van een binaire module importeren.</span><span class="sxs-lookup"><span data-stu-id="caa15-103">This topic describes how to import cmdlets to a Windows PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="caa15-104">De leden van de modules kunnen opnemen cmdlets, providers, functies, variabelen, aliassen en nog veel meer.</span><span class="sxs-lookup"><span data-stu-id="caa15-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="caa15-105">Alleen-cmdlets en providers bevatten-modules.</span><span class="sxs-lookup"><span data-stu-id="caa15-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="caa15-106">Het laden van cmdlets met behulp van een module</span><span class="sxs-lookup"><span data-stu-id="caa15-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="caa15-107">Maak een modulemap met dezelfde naam als de assemblybestand waarin de cmdlets worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="caa15-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="caa15-108">In deze procedure wordt de modulemap gemaakt de `system32` map.</span><span class="sxs-lookup"><span data-stu-id="caa15-108">In this procedure, the module folder is created in the `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. <span data-ttu-id="caa15-109">Zorg ervoor dat de `PSModulePath` omgevingsvariabele bevat het pad naar de nieuwe modulemap.</span><span class="sxs-lookup"><span data-stu-id="caa15-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="caa15-110">De map is standaard al toegevoegd aan de `PSModulePath` omgevingsvariabele.</span><span class="sxs-lookup"><span data-stu-id="caa15-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span>

3. <span data-ttu-id="caa15-111">Kopieer de cmdlet-assembly in de modulemap.</span><span class="sxs-lookup"><span data-stu-id="caa15-111">Copy the cmdlet assembly into the module folder.</span></span>

4. <span data-ttu-id="caa15-112">Voer de volgende opdracht uit om toe te voegen van de cmdlets met de sessie:</span><span class="sxs-lookup"><span data-stu-id="caa15-112">Run the following command to add the cmdlets to the session:</span></span>

   `import-module [Module_Name]`

   <span data-ttu-id="caa15-113">Deze procedure kan worden gebruikt voor het testen van uw cmdlets.</span><span class="sxs-lookup"><span data-stu-id="caa15-113">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="caa15-114">Alle cmdlets wordt toegevoegd in de assembly met de sessie.</span><span class="sxs-lookup"><span data-stu-id="caa15-114">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="caa15-115">Zie voor meer informatie over de verschillende soorten modules, de verschillende manieren om te laden modules en het beperken van de elementen van een module die zijn geëxporteerd, [schrijven van een Windows PowerShell-Module](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="caa15-115">For more information about modules, the different types of modules, the different ways to load modules, and how to restrict the elements of a module that are exported, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="caa15-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="caa15-116">See Also</span></span>

[<span data-ttu-id="caa15-117">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="caa15-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="caa15-118">Modules installeren</span><span class="sxs-lookup"><span data-stu-id="caa15-118">Installing Modules</span></span>](../module/installing-a-powershell-module.md)