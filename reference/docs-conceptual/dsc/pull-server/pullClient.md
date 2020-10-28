---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een DSC-pull-client instellen
description: Dit artikel bevat een overzicht van de informatie die beschikbaar is voor het instellen van de DSC pull-client.
ms.openlocfilehash: 584af3aee46d801e363422ae7a197348231a1442
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646814"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="20eff-104">Een DSC-pull-client instellen</span><span class="sxs-lookup"><span data-stu-id="20eff-104">Setting up a DSC pull client</span></span>

> <span data-ttu-id="20eff-105">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="20eff-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="20eff-106">De pull-server (Windows *-functie DSC-service* ) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden.</span><span class="sxs-lookup"><span data-stu-id="20eff-106">The Pull Server (Windows Feature *DSC-Service* ) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="20eff-107">Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.</span><span class="sxs-lookup"><span data-stu-id="20eff-107">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="20eff-108">Elk doel knooppunt moet worden weer gegeven om de pull-modus te gebruiken en de URL of de bestands locatie op te geven waar het een verbinding kan maken met de pull-server voor het ophalen van configuraties en resources, en waar de rapport gegevens moeten worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="20eff-108">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="20eff-109">In de volgende onderwerpen wordt uitgelegd hoe u pull-clients instelt:</span><span class="sxs-lookup"><span data-stu-id="20eff-109">The following topics explain how to set up pull clients:</span></span>

- <span data-ttu-id="20eff-110">[Een pull-client instellen met behulp van configuratie namen](pullClientConfigNames.md) 
\*- [Een pull-client instellen met behulp van de configuratie-ID](pullClientConfigID.md)</span><span class="sxs-lookup"><span data-stu-id="20eff-110">[Setting up a pull client using configuration names](pullClientConfigNames.md)
\*-[Setting up a pull client using configuration ID](pullClientConfigID.md)</span></span>

> [!NOTE]
> <span data-ttu-id="20eff-111">Deze onderwerpen zijn van toepassing op Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="20eff-111">These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="20eff-112">Zie [een pull-client instellen met behulp van de configuratie-ID in Power shell 4,0](pullClientConfigID4.md)voor het instellen van een pull-client in power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="20eff-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>
