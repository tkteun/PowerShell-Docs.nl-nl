---
title: Een Windows Power shell-module schrijven | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352848"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="8aa61-102">Een Windows PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="8aa61-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="8aa61-103">Dit document is geschreven voor beheerders, script ontwikkelaars en cmdlet-ontwikkel aars die hun Windows Power shell-cmdlets moeten inpakken en distribueren.</span><span class="sxs-lookup"><span data-stu-id="8aa61-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="8aa61-104">Met behulp van Windows Power shell-modules kunt u uw Windows Power shell-oplossingen verpakken en distribueren zonder een gecompileerde taal te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8aa61-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="8aa61-105">Met Windows Power shell-modules kunt u uw Windows Power shell-code partitioneren, ordenen en samen stellen in zelfstandige, herbruikbare eenheden.</span><span class="sxs-lookup"><span data-stu-id="8aa61-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="8aa61-106">Met deze herbruikbare eenheden kunt u uw modules eenvoudig rechtstreeks met anderen delen.</span><span class="sxs-lookup"><span data-stu-id="8aa61-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="8aa61-107">Als u een script ontwikkelaar bent, kunt u de modules van derden ook opnieuw inpakken om aangepaste toepassingen op basis van een script te maken.</span><span class="sxs-lookup"><span data-stu-id="8aa61-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="8aa61-108">Modules, vergelijkbaar met modules in andere script talen, zoals perl en Python, maken kant-en-klare script oplossingen mogelijk die gebruikmaken van herbruikbare, herdistribueerbare onderdelen, met het toegevoegde voor deel van het inschakelen van het opnieuw verpakken en samen voegen van meerdere onderdelen naar aangepaste oplossingen maken.</span><span class="sxs-lookup"><span data-stu-id="8aa61-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="8aa61-109">Windows Power shell behandelt op zijn meest eenvoudige wijze alle geldige Windows Power shell-script code die is opgeslagen in een. psm1-bestand als een module.</span><span class="sxs-lookup"><span data-stu-id="8aa61-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="8aa61-110">Power shell behandelt ook automatisch een binaire cmdlet-assembly als een module.</span><span class="sxs-lookup"><span data-stu-id="8aa61-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="8aa61-111">U kunt echter ook een module (of specifiek een module manifest) gebruiken om een volledige oplossing samen te bundelen.</span><span class="sxs-lookup"><span data-stu-id="8aa61-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="8aa61-112">In de volgende scenario's worden veelvoorkomende toepassingen voor Windows Power shell-modules beschreven.</span><span class="sxs-lookup"><span data-stu-id="8aa61-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="8aa61-113">Library</span><span class="sxs-lookup"><span data-stu-id="8aa61-113">Libraries</span></span>

<span data-ttu-id="8aa61-114">Modules kunnen worden gebruikt voor het inpakken en distribueren van samenhangende bibliotheken met functies die algemene taken uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="8aa61-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="8aa61-115">De namen van deze functies delen meestal een of meer zelfstandige naam woorden die overeenkomen met de algemene taak waarvoor ze worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8aa61-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="8aa61-116">Deze functies kunnen ook vergelijkbaar zijn met .NET Framework klassen, zodat ze open bare en privé-leden kunnen hebben.</span><span class="sxs-lookup"><span data-stu-id="8aa61-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="8aa61-117">Een bibliotheek kan bijvoorbeeld een set met functies voor bestands overdrachten bevatten.</span><span class="sxs-lookup"><span data-stu-id="8aa61-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="8aa61-118">In dit geval kan het zelfstandige naam woord dat de algemene taak weerspiegelt ' file ' zijn.</span><span class="sxs-lookup"><span data-stu-id="8aa61-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="8aa61-119">Configuratie</span><span class="sxs-lookup"><span data-stu-id="8aa61-119">Configuration</span></span>

<span data-ttu-id="8aa61-120">Modules kunnen worden gebruikt voor het aanpassen van uw omgeving door specifieke cmdlets, providers, functies en variabelen toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="8aa61-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="8aa61-121">Gecompileerde code ontwikkeling en-distributie</span><span class="sxs-lookup"><span data-stu-id="8aa61-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="8aa61-122">Cmdlets en provider ontwikkelaars kunnen modules gebruiken om hun gecompileerde code te testen en te distribueren zonder dat ze modules hoeven te maken. Ze kunnen de assembly met de gecompileerde code importeren als een module (een binaire module) zonder dat ze modules hoeven te maken en registreren.</span><span class="sxs-lookup"><span data-stu-id="8aa61-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="8aa61-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8aa61-123">See Also</span></span>

[<span data-ttu-id="8aa61-124">Informatie over een Windows Power shell-module</span><span class="sxs-lookup"><span data-stu-id="8aa61-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="8aa61-125">Een Power shell-script module schrijven</span><span class="sxs-lookup"><span data-stu-id="8aa61-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="8aa61-126">Een binaire Power shell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="8aa61-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="8aa61-127">Een Power shell-module manifest schrijven</span><span class="sxs-lookup"><span data-stu-id="8aa61-127">How to Write a PowerShell Module Manifest</span></span>](how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="8aa61-128">Het installatiepad van PSModulePath wijzigen</span><span class="sxs-lookup"><span data-stu-id="8aa61-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="8aa61-129">Een Power shell-module importeren</span><span class="sxs-lookup"><span data-stu-id="8aa61-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="8aa61-130">Een Power shell-module installeren</span><span class="sxs-lookup"><span data-stu-id="8aa61-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
