---
ms.date: 03/22/2021
keywords: powershell,cmdlet
title: Wat is PowerShell?
description: Dit artikel bevat een inleiding tot de PowerShell-scriptomgeving en de functies ervan.
ms.openlocfilehash: ae2a5e311992e98045841a3992810e55390519ad
ms.sourcegitcommit: afbcc8675107ad9ec6afff91ef4a42b2953121cc
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/28/2021
ms.locfileid: "108121623"
---
# <a name="what-is-powershell"></a><span data-ttu-id="6447c-104">Wat is PowerShell?</span><span class="sxs-lookup"><span data-stu-id="6447c-104">What is PowerShell?</span></span>

<span data-ttu-id="6447c-105">PowerShell is een platformoverschrijdende oplossing voor taakautomatisering die bestaat uit een opdrachtregelshell, een scripttaal en een framework voor configuratiebeheer.</span><span class="sxs-lookup"><span data-stu-id="6447c-105">PowerShell is a cross-platform task automation solution made up of a command-line shell, a scripting language, and a configuration management framework.</span></span> <span data-ttu-id="6447c-106">PowerShell wordt uitgevoerd op Windows, Linux en macOS.</span><span class="sxs-lookup"><span data-stu-id="6447c-106">PowerShell runs on Windows, Linux, and macOS.</span></span>

## <a name="shell"></a><span data-ttu-id="6447c-107">Shell</span><span class="sxs-lookup"><span data-stu-id="6447c-107">Shell</span></span>

<span data-ttu-id="6447c-108">PowerShell is een moderne opdrachtshell met de beste functies van andere populaire shells.</span><span class="sxs-lookup"><span data-stu-id="6447c-108">PowerShell is a modern command shell that includes the best features of other popular shells.</span></span> <span data-ttu-id="6447c-109">In tegenstelling tot de meeste shells die alleen tekst accepteren en retourneren, accepteert en retourneert PowerShell .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="6447c-109">Unlike most shells that only accept and return text, PowerShell accepts and returns .NET objects.</span></span> <span data-ttu-id="6447c-110">De shell bevat de volgende functies:</span><span class="sxs-lookup"><span data-stu-id="6447c-110">The shell includes the following features:</span></span>

- <span data-ttu-id="6447c-111">Robuuste [opdrachtregelgeschiedenis][]</span><span class="sxs-lookup"><span data-stu-id="6447c-111">Robust command-line [history][]</span></span>
- <span data-ttu-id="6447c-112">Tab-voltooiing en opdrachtvoorspelling [(zie about_PSReadLine][])</span><span class="sxs-lookup"><span data-stu-id="6447c-112">Tab completion and command prediction (See [about_PSReadLine][])</span></span>
- <span data-ttu-id="6447c-113">Ondersteunt opdracht- en [parameteraliassen][]</span><span class="sxs-lookup"><span data-stu-id="6447c-113">Supports command and parameter [aliases][]</span></span>
- <span data-ttu-id="6447c-114">[Pijplijn][] voor het aaneenketenen van opdrachten</span><span class="sxs-lookup"><span data-stu-id="6447c-114">[Pipeline][] for chaining commands</span></span>
- <span data-ttu-id="6447c-115">Help-systeem [][] in de console, vergelijkbaar met UNIX-pagina's `man`</span><span class="sxs-lookup"><span data-stu-id="6447c-115">In-console [help][] system, similar to Unix `man` pages</span></span>

## <a name="scripting-language"></a><span data-ttu-id="6447c-116">Scripttaal</span><span class="sxs-lookup"><span data-stu-id="6447c-116">Scripting language</span></span>

<span data-ttu-id="6447c-117">Als scripttaal wordt PowerShell vaak gebruikt voor het automatiseren van het beheer van systemen.</span><span class="sxs-lookup"><span data-stu-id="6447c-117">As a scripting language, PowerShell is commonly used for automating the management of systems.</span></span> <span data-ttu-id="6447c-118">Het wordt ook gebruikt voor het bouwen, testen en implementeren van oplossingen, vaak in CI/CD-omgevingen.</span><span class="sxs-lookup"><span data-stu-id="6447c-118">It is also used to build, test, and deploy solutions, often in CI/CD environments.</span></span> <span data-ttu-id="6447c-119">PowerShell is gebouwd op de .NET Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="6447c-119">PowerShell is built on the .NET Common Language Runtime (CLR).</span></span> <span data-ttu-id="6447c-120">Alle invoer en uitvoer zijn .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="6447c-120">All inputs and outputs are .NET objects.</span></span> <span data-ttu-id="6447c-121">Het is niet nodig om tekstuitvoer te parseren om informatie uit de uitvoer te extraheren.</span><span class="sxs-lookup"><span data-stu-id="6447c-121">No need to parse text output to extract information from output.</span></span> <span data-ttu-id="6447c-122">De PowerShell-scripttaal bevat de volgende functies:</span><span class="sxs-lookup"><span data-stu-id="6447c-122">The PowerShell scripting language includes the following features:</span></span>

- <span data-ttu-id="6447c-123">Uit te voeren via [functies,][] [klassen,][] [scripts][]en [modules][]</span><span class="sxs-lookup"><span data-stu-id="6447c-123">Extensible through [functions][], [classes][], [scripts][], and [modules][]</span></span>
- <span data-ttu-id="6447c-124">Uitvouwbaar [opmaaksysteem voor][formatting] eenvoudige uitvoer</span><span class="sxs-lookup"><span data-stu-id="6447c-124">Extensible [formatting system][formatting] for easy output</span></span>
- <span data-ttu-id="6447c-125">Extensible [type system voor][types] het maken van dynamische typen</span><span class="sxs-lookup"><span data-stu-id="6447c-125">Extensible [type system][types] for creating dynamic types</span></span>
- <span data-ttu-id="6447c-126">Ingebouwde ondersteuning voor algemene gegevensindelingen zoals [CSV,][] [JSON][]en [XML][]</span><span class="sxs-lookup"><span data-stu-id="6447c-126">Built-in support for common data formats like [CSV][], [JSON][], and [XML][]</span></span>

## <a name="configuration-management"></a><span data-ttu-id="6447c-127">Configuratiebeheer</span><span class="sxs-lookup"><span data-stu-id="6447c-127">Configuration management</span></span>

<span data-ttu-id="6447c-128">PowerShell Desired State Configuration[(DSC)][]is een beheerkader in PowerShell waarmee u uw bedrijfsinfrastructuur kunt beheren met configuratie als code.</span><span class="sxs-lookup"><span data-stu-id="6447c-128">PowerShell Desired State Configuration ([DSC][]) is a management framework in PowerShell that enables you to manage your enterprise infrastructure with configuration as code.</span></span> <span data-ttu-id="6447c-129">Met DSC kunt u het volgende doen:</span><span class="sxs-lookup"><span data-stu-id="6447c-129">With DSC, you can:</span></span>

- <span data-ttu-id="6447c-130">Declaratieve [configuraties en aangepaste][] scripts maken voor herhaalbare implementaties</span><span class="sxs-lookup"><span data-stu-id="6447c-130">Create declarative [configurations][] and custom scripts for repeatable deployments</span></span>
- <span data-ttu-id="6447c-131">Configuratie-instellingen afdwingen en rapporteren over configuratiedrift</span><span class="sxs-lookup"><span data-stu-id="6447c-131">Enforce configuration settings and report on configuration drift</span></span>
- <span data-ttu-id="6447c-132">Configuratie implementeren met [push- of pull-modellen][push-pull]</span><span class="sxs-lookup"><span data-stu-id="6447c-132">Deploy configuration using [push or pull][push-pull] models</span></span>

## <a name="next-steps"></a><span data-ttu-id="6447c-133">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="6447c-133">Next steps</span></span>

### <a name="getting-started"></a><span data-ttu-id="6447c-134">Aan de slag</span><span class="sxs-lookup"><span data-stu-id="6447c-134">Getting started</span></span>

<span data-ttu-id="6447c-135">Bent u niet bekend met PowerShell en weet u niet waar u moet beginnen?</span><span class="sxs-lookup"><span data-stu-id="6447c-135">Are you new to PowerShell and don't know where to start?</span></span> <span data-ttu-id="6447c-136">Bekijk deze resources.</span><span class="sxs-lookup"><span data-stu-id="6447c-136">Take a look at these resources.</span></span>

- <span data-ttu-id="6447c-137">[PowerShell installeren][install]</span><span class="sxs-lookup"><span data-stu-id="6447c-137">[Installing PowerShell][install]</span></span>
- <span data-ttu-id="6447c-138">[PowerShell 101][PS101]</span><span class="sxs-lookup"><span data-stu-id="6447c-138">[PowerShell 101][PS101]</span></span>
- <span data-ttu-id="6447c-139">[PowerShell Bits-zelfstudies][tutorials]</span><span class="sxs-lookup"><span data-stu-id="6447c-139">[PowerShell Bits tutorials][tutorials]</span></span>
- <span data-ttu-id="6447c-140">[PowerShell Learn-modules][learn]</span><span class="sxs-lookup"><span data-stu-id="6447c-140">[PowerShell Learn modules][learn]</span></span>

### <a name="powershell-in-action"></a><span data-ttu-id="6447c-141">PowerShell in actie</span><span class="sxs-lookup"><span data-stu-id="6447c-141">PowerShell in action</span></span>

<span data-ttu-id="6447c-142">Bekijk hoe PowerShell wordt gebruikt in verschillende scenario's en op verschillende platforms.</span><span class="sxs-lookup"><span data-stu-id="6447c-142">Take a look at how PowerShell is being used in different scenarios and on different platforms.</span></span>

- <span data-ttu-id="6447c-143">[Externe communicatie van PowerShell via SSH][remoting]</span><span class="sxs-lookup"><span data-stu-id="6447c-143">[PowerShell remoting over SSH][remoting]</span></span>
- <span data-ttu-id="6447c-144">[Aan de slag met Azure PowerShell][azure]</span><span class="sxs-lookup"><span data-stu-id="6447c-144">[Getting started with Azure PowerShell][azure]</span></span>
- <span data-ttu-id="6447c-145">[Een CI/CD-pijplijn bouwen met DSC][devops]</span><span class="sxs-lookup"><span data-stu-id="6447c-145">[Building a CI/CD pipeline with DSC][devops]</span></span>
- <span data-ttu-id="6447c-146">[Microsoft Exchange beheren][exchange]</span><span class="sxs-lookup"><span data-stu-id="6447c-146">[Managing Microsoft Exchange][exchange]</span></span>

<!-- link references -->

[Geschiedenis]: /powershell/module/microsoft.powershell.core/about/about_history
[history]: /powershell/module/microsoft.powershell.core/about/about_history
[about_PSReadLine]: /powershell/module/psreadline/about/about_psreadline
[Aliassen]: /powershell/module/microsoft.powershell.core/about/about_aliases
[aliases]: /powershell/module/microsoft.powershell.core/about/about_aliases
[Pijplijn]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[Pipeline]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[Help]: /powershell/module/microsoft.powershell.core/get-help
[help]: /powershell/module/microsoft.powershell.core/get-help
[Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[Functies]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[functions]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[Klassen]: /powershell/module/microsoft.powershell.core/about/about_classes
[classes]: /powershell/module/microsoft.powershell.core/about/about_classes
[Scripts]: /powershell/module/microsoft.powershell.core/about/about_scripts
[scripts]: /powershell/module/microsoft.powershell.core/about/about_scripts
[formatting]: /powershell/module/microsoft.powershell.core/about/about_format.ps1xml
[types]: /powershell/module/microsoft.powershell.core/about/about_types.ps1xml
[CSV]: /powershell/module/microsoft.powershell.utility/convertfrom-csv
[JSON]: /powershell/module/microsoft.powershell.utility/convertfrom-json
[XML]: /powershell/module/microsoft.powershell.utility/convertto-xml
[Configuraties]: /powershell/scripting/dsc/configurations/configurations
[configurations]: /powershell/scripting/dsc/configurations/configurations
[Dsc]: /powershell/scripting/dsc/overview/dscforengineers
[DSC]: /powershell/scripting/dsc/overview/dscforengineers
[push-pull]: /powershell/scripting/dsc/pull-server/enactingconfigurations
[install]: /powershell/scripting/install/installing-powershell
[PS101]: /powershell/scripting/learn/ps101/00-introduction
[tutorials]: /powershell/scripting/learn/tutorials/00-introduction
[learn]: /learn/browse/?terms=PowerShell
[azure]: /powershell/azure/get-started-azureps
[devops]: /azure/devops/pipelines/release/dsc-cicd
[exchange]: /powershell/exchange/exchange-management-shell
[remoting]: /powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core
