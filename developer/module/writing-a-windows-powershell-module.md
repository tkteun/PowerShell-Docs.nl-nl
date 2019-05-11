---
title: Schrijven van een Windows PowerShell-Module | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229343"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="0a7bc-102">Een Windows PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="0a7bc-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="0a7bc-103">Dit document is geschreven voor beheerders, script-ontwikkelaars en cmdlet-ontwikkelaars die willen Inpakken en distribueren van de Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="0a7bc-104">Met behulp van Windows PowerShell-modules, kunt u Inpakken en distribueren van uw Windows PowerShell-oplossingen zonder een gecompileerde taal gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="0a7bc-105">Windows PowerShell-modules kunnen u naar partitie, organiseren en uw Windows PowerShell-code in zelfstandige, herbruikbare eenheden abstract.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="0a7bc-106">Met deze herbruikbare eenheden, kunt u eenvoudig uw modules rechtstreeks met anderen delen.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="0a7bc-107">Als u een script-ontwikkelaar bent, kunt u modules van derden voor het maken van aangepaste toepassingen op basis van een script ook verpakken.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="0a7bc-108">Modules, die vergelijkbaar is met modules in andere scripttalen zoals Perl en Python, kunt scripts gereed is voor productie-oplossingen die gebruikmaken van herbruikbare, herdistribueerbare onderdelen, met het voordeel van zodat u kunt verpakken en meerdere onderdelen te abstraheren aangepaste oplossingen maken.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="0a7bc-109">Op de meest eenvoudige Windows PowerShell een geldige Windows PowerShell-script-code opgeslagen in een psm1-bestand als een module wordt behandeld.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="0a7bc-110">PowerShell wordt ook automatisch elke assembly binaire cmdlet behandelen als een module.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="0a7bc-111">U kunt echter ook gebruiken een module (of meer specifiek, een module-manifest) als u wilt een complete oplossing samen te bundelen.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="0a7bc-112">De volgende scenario's beschreven wordt doorgaans gebruikt voor Windows PowerShell-modules.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="0a7bc-113">Bibliotheken</span><span class="sxs-lookup"><span data-stu-id="0a7bc-113">Libraries</span></span>

<span data-ttu-id="0a7bc-114">Modules kunnen worden gebruikt om te verpakken en distribueren samenhangend bibliotheken van de functies die veelvoorkomende taken uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="0a7bc-115">Normaal gesproken delen de namen van deze functies een of meer woorden die overeenkomen met de algemene taak die ze voor worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="0a7bc-116">Deze functies kunnen ook worden die vergelijkbaar is met .NET Framework-klassen in dat ze kunnen openbare en privé-leden hebben.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="0a7bc-117">Een bibliotheek mag bijvoorbeeld een set functies voor bestandsoverdrachten.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="0a7bc-118">In dit geval het zelfstandig naamwoord zetten op basis van de algemene taak mogelijk 'file'.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="0a7bc-119">Configuratie</span><span class="sxs-lookup"><span data-stu-id="0a7bc-119">Configuration</span></span>

<span data-ttu-id="0a7bc-120">Modules kunnen worden gebruikt voor het aanpassen van uw omgeving door toe te voegen bepaalde cmdlets, providers, functies en variabelen.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="0a7bc-121">Gecompileerde Code-ontwikkeling en distributie</span><span class="sxs-lookup"><span data-stu-id="0a7bc-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="0a7bc-122">Cmdlet en provider ontwikkelaars kunnen modules gebruiken om te testen en distribueren van hun gecompileerde code hoeft te maken van modules. Hoeft te maken en -modules registreren, kunnen ze de assembly die de gecompileerde code als een module (een binaire-module bevat) importeren.</span><span class="sxs-lookup"><span data-stu-id="0a7bc-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a7bc-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0a7bc-123">See Also</span></span>

[<span data-ttu-id="0a7bc-124">Wat is een Windows PowerShell-Module?</span><span class="sxs-lookup"><span data-stu-id="0a7bc-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="0a7bc-125">Over het schrijven van een PowerShell-Script-Module</span><span class="sxs-lookup"><span data-stu-id="0a7bc-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="0a7bc-126">Over het schrijven van een binaire waarde PowerShell-Module</span><span class="sxs-lookup"><span data-stu-id="0a7bc-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="0a7bc-127">Over het schrijven van een PowerShell-Module-Manifest</span><span class="sxs-lookup"><span data-stu-id="0a7bc-127">How to Write a PowerShell Module Manifest</span></span>](how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="0a7bc-128">Het installatiepad PSModulePath wijzigen</span><span class="sxs-lookup"><span data-stu-id="0a7bc-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="0a7bc-129">Een PowerShell-Module importeren</span><span class="sxs-lookup"><span data-stu-id="0a7bc-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="0a7bc-130">Een PowerShell-Module installeren</span><span class="sxs-lookup"><span data-stu-id="0a7bc-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
