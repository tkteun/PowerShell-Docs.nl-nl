---
ms.date: 03/22/2021
keywords: powershell,cmdlet
title: Wat is PowerShell?
description: Dit artikel is een inleiding tot de Power shell-script omgeving en de bijbehorende functies.
ms.openlocfilehash: 3e1c2cae4b8d6507057ee8136265710a8dfe74f3
ms.sourcegitcommit: 719debaed3cc32ba463b1d4cc56a491d8ecbce26
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/24/2021
ms.locfileid: "105029686"
---
# <a name="what-is-powershell"></a><span data-ttu-id="122e0-104">Wat is PowerShell?</span><span class="sxs-lookup"><span data-stu-id="122e0-104">What is PowerShell?</span></span>

<span data-ttu-id="122e0-105">Power shell is een oplossing voor het automatiseren van meerdere platforms die bestaat uit een opdracht regel shell, een script taal en een configuratie beheer raamwerk.</span><span class="sxs-lookup"><span data-stu-id="122e0-105">PowerShell is a cross-platform task automation solution made up of a command-line shell, a scripting language, and a configuration management framework.</span></span> <span data-ttu-id="122e0-106">Power shell wordt uitgevoerd op Windows, Linux en macOS.</span><span class="sxs-lookup"><span data-stu-id="122e0-106">PowerShell runs on Windows, Linux, and macOS.</span></span>

## <a name="shell"></a><span data-ttu-id="122e0-107">Shell</span><span class="sxs-lookup"><span data-stu-id="122e0-107">Shell</span></span>

<span data-ttu-id="122e0-108">Power shell is een moderne opdracht shell die de beste functies van andere populaire shells bevat.</span><span class="sxs-lookup"><span data-stu-id="122e0-108">PowerShell is modern command shell that includes the best features of other popular shells.</span></span> <span data-ttu-id="122e0-109">In tegens telling tot de meeste shells die alleen tekst accepteren en retour neren, accepteert en retourneert Power shell .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="122e0-109">Unlike most shells that only accept and return text, PowerShell accepts and returns .NET objects.</span></span> <span data-ttu-id="122e0-110">De shell bevat de volgende functies:</span><span class="sxs-lookup"><span data-stu-id="122e0-110">The shell includes the following features:</span></span>

- <span data-ttu-id="122e0-111">Robuuste opdracht regel [geschiedenis][]</span><span class="sxs-lookup"><span data-stu-id="122e0-111">Robust command-line [history][]</span></span>
- <span data-ttu-id="122e0-112">Tabblad voltooiing en de voor spelling van opdrachten (Zie [about_PSReadLine][])</span><span class="sxs-lookup"><span data-stu-id="122e0-112">Tab completion and command prediction (See [about_PSReadLine][])</span></span>
- <span data-ttu-id="122e0-113">Ondersteunt opdracht-en parameter [aliassen][]</span><span class="sxs-lookup"><span data-stu-id="122e0-113">Supports command and parameter [aliases][]</span></span>
- <span data-ttu-id="122e0-114">[Pijp lijn][] voor het koppelen van opdrachten</span><span class="sxs-lookup"><span data-stu-id="122e0-114">[Pipeline][] for chaining commands</span></span>
- <span data-ttu-id="122e0-115">[Help][] -systeem in de console, vergelijkbaar met Unix- `man` pagina's</span><span class="sxs-lookup"><span data-stu-id="122e0-115">In-console [help][] system, similar to Unix `man` pages</span></span>

## <a name="scripting-language"></a><span data-ttu-id="122e0-116">Script taal</span><span class="sxs-lookup"><span data-stu-id="122e0-116">Scripting language</span></span>

<span data-ttu-id="122e0-117">Als script taal wordt Power shell doorgaans gebruikt voor het automatiseren van het beheer van systemen.</span><span class="sxs-lookup"><span data-stu-id="122e0-117">As a scripting language, PowerShell is commonly used for automating the management of systems.</span></span> <span data-ttu-id="122e0-118">Het wordt ook gebruikt om oplossingen te bouwen, te testen en te implementeren, vaak in CI/CD-omgevingen.</span><span class="sxs-lookup"><span data-stu-id="122e0-118">It is also used to build, test, and deploy solutions, often in CI/CD environments.</span></span> <span data-ttu-id="122e0-119">Power shell is gebaseerd op de .NET common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="122e0-119">PowerShell is built on the .NET Common Language Runtime (CLR).</span></span> <span data-ttu-id="122e0-120">Alle invoer en uitvoer zijn .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="122e0-120">All inputs and outputs are .NET objects.</span></span> <span data-ttu-id="122e0-121">Het is niet nodig om tekst uitvoer te parseren om informatie uit de uitvoer op te halen.</span><span class="sxs-lookup"><span data-stu-id="122e0-121">No need to parse text output to extract information from output.</span></span> <span data-ttu-id="122e0-122">De Power shell-script taal bevat de volgende functies:</span><span class="sxs-lookup"><span data-stu-id="122e0-122">The PowerShell scripting language includes the following features:</span></span>

- <span data-ttu-id="122e0-123">Uitbreidbaar tot [functies][], [klassen][], [scripts][]en [modules][]</span><span class="sxs-lookup"><span data-stu-id="122e0-123">Extensible through [functions][], [classes][], [scripts][], and [modules][]</span></span>
- <span data-ttu-id="122e0-124">Uitbreidbaar [systeem][formatting] voor eenvoudige uitvoer</span><span class="sxs-lookup"><span data-stu-id="122e0-124">Extensible [formatting system][formatting] for easy output</span></span>
- <span data-ttu-id="122e0-125">Uitbreidbaar [type systeem][types] voor het maken van dynamische typen</span><span class="sxs-lookup"><span data-stu-id="122e0-125">Extensible [type system][types] for creating dynamic types</span></span>
- <span data-ttu-id="122e0-126">Ingebouwde ondersteuning voor algemene gegevens indelingen, zoals [CSV][], [JSON][]en [XML][]</span><span class="sxs-lookup"><span data-stu-id="122e0-126">Built-in support for common data formats like [CSV][], [JSON][], and [XML][]</span></span>

## <a name="configuration-management"></a><span data-ttu-id="122e0-127">Configuratiebeheer</span><span class="sxs-lookup"><span data-stu-id="122e0-127">Configuration management</span></span>

<span data-ttu-id="122e0-128">Power shell desired state Configuration ([DSC][]) is een beheer raamwerk in Power shell waarmee u uw bedrijfs infrastructuur met configuratie als code kunt beheren.</span><span class="sxs-lookup"><span data-stu-id="122e0-128">PowerShell Desired State Configuration ([DSC][]) is a management framework in PowerShell that enables you to manage your enterprise infrastructure with configuration as code.</span></span> <span data-ttu-id="122e0-129">Met DSC kunt u het volgende doen:</span><span class="sxs-lookup"><span data-stu-id="122e0-129">With DSC, you can:</span></span>

- <span data-ttu-id="122e0-130">Declaratieve [configuraties][] en aangepaste scripts maken voor Herhaal bare implementaties</span><span class="sxs-lookup"><span data-stu-id="122e0-130">Create declarative [configurations][] and custom scripts for repeatable deployments</span></span>
- <span data-ttu-id="122e0-131">Configuratie-instellingen en rapport op configuratie-drift afdwingen</span><span class="sxs-lookup"><span data-stu-id="122e0-131">Enforce configuration settings and report on configuration drift</span></span>
- <span data-ttu-id="122e0-132">Configuratie implementeren met [push-of pull][push-pull] -modellen</span><span class="sxs-lookup"><span data-stu-id="122e0-132">Deploy configuration using [push or pull][push-pull] models</span></span>

## <a name="next-steps"></a><span data-ttu-id="122e0-133">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="122e0-133">Next steps</span></span>

### <a name="getting-started"></a><span data-ttu-id="122e0-134">Aan de slag</span><span class="sxs-lookup"><span data-stu-id="122e0-134">Getting started</span></span>

<span data-ttu-id="122e0-135">Bent u nieuw in Power shell en weet u niet waar u moet beginnen?</span><span class="sxs-lookup"><span data-stu-id="122e0-135">Are you new to PowerShell and don't know where to start?</span></span> <span data-ttu-id="122e0-136">Bekijk deze bronnen.</span><span class="sxs-lookup"><span data-stu-id="122e0-136">Take a look at these resources.</span></span>

- <span data-ttu-id="122e0-137">[PowerShell installeren][install]</span><span class="sxs-lookup"><span data-stu-id="122e0-137">[Installing PowerShell][install]</span></span>
- <span data-ttu-id="122e0-138">[PowerShell 101][PS101]</span><span class="sxs-lookup"><span data-stu-id="122e0-138">[PowerShell 101][PS101]</span></span>
- <span data-ttu-id="122e0-139">[Zelf studies voor Power shell-bits][tutorials]</span><span class="sxs-lookup"><span data-stu-id="122e0-139">[PowerShell Bits tutorials][tutorials]</span></span>
- <span data-ttu-id="122e0-140">[Power shell-modules voor leren][learn]</span><span class="sxs-lookup"><span data-stu-id="122e0-140">[PowerShell Learn modules][learn]</span></span>

### <a name="powershell-in-action"></a><span data-ttu-id="122e0-141">Power shell in actie</span><span class="sxs-lookup"><span data-stu-id="122e0-141">PowerShell in action</span></span>

<span data-ttu-id="122e0-142">Bekijk hoe Power shell wordt gebruikt in verschillende scenario's en op verschillende platforms.</span><span class="sxs-lookup"><span data-stu-id="122e0-142">Take a look at how PowerShell is being used in different scenarios and on different platforms.</span></span>

- <span data-ttu-id="122e0-143">[Externe communicatie van PowerShell via SSH][remoting]</span><span class="sxs-lookup"><span data-stu-id="122e0-143">[PowerShell remoting over SSH][remoting]</span></span>
- <span data-ttu-id="122e0-144">[Aan de slag met Azure PowerShell][azure]</span><span class="sxs-lookup"><span data-stu-id="122e0-144">[Getting started with Azure PowerShell][azure]</span></span>
- <span data-ttu-id="122e0-145">[Een CI/CD-pijp lijn bouwen met DSC][devops]</span><span class="sxs-lookup"><span data-stu-id="122e0-145">[Building a CI/CD pipeline with DSC][devops]</span></span>
- <span data-ttu-id="122e0-146">[Micro soft Exchange beheren][exchange]</span><span class="sxs-lookup"><span data-stu-id="122e0-146">[Managing Microsoft Exchange][exchange]</span></span>

<!-- link references -->

[transactie]: /powershell/module/microsoft.powershell.core/about/about_history
[history]: /powershell/module/microsoft.powershell.core/about/about_history
[about_PSReadLine]: /powershell/module/psreadline/about/about_psreadline
[aliassen]: /powershell/module/microsoft.powershell.core/about/about_aliases
[aliases]: /powershell/module/microsoft.powershell.core/about/about_aliases
[Pijplijn]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[Pipeline]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[Help]: /powershell/module/microsoft.powershell.core/get-help
[help]: /powershell/module/microsoft.powershell.core/get-help
[modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[vervullen]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[functions]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[instructeur]: /powershell/module/microsoft.powershell.core/about/about_classes
[classes]: /powershell/module/microsoft.powershell.core/about/about_classes
[scriptmap]: /powershell/module/microsoft.powershell.core/about/about_scripts
[scripts]: /powershell/module/microsoft.powershell.core/about/about_scripts
[formatting]: /powershell/module/microsoft.powershell.core/about/about_format.ps1xml
[types]: /powershell/module/microsoft.powershell.core/about/about_types.ps1xml
[CSV]: /powershell/module/microsoft.powershell.utility/convertfrom-csv
[JSON]: /powershell/module/microsoft.powershell.utility/convertfrom-json
[XML]: /powershell/module/microsoft.powershell.utility/convertto-xml
[configuraties]: /powershell/scripting/dsc/configurations/configurations
[configurations]: /powershell/scripting/dsc/configurations/configurations
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
