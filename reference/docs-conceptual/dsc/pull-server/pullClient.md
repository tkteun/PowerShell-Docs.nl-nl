---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een DSC-pull-client instellen
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942795"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="34843-103">Een DSC-pull-client instellen</span><span class="sxs-lookup"><span data-stu-id="34843-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="34843-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="34843-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34843-105">De pull-server (Windows *-functie DSC-service*) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden.</span><span class="sxs-lookup"><span data-stu-id="34843-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="34843-106">Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.</span><span class="sxs-lookup"><span data-stu-id="34843-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="34843-107">Elk doel knooppunt moet worden weer gegeven om de pull-modus te gebruiken en de URL of de bestands locatie op te geven waar het een verbinding kan maken met de pull-server voor het ophalen van configuraties en resources, en waar de rapport gegevens moeten worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="34843-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="34843-108">In de volgende onderwerpen wordt uitgelegd hoe u pull-clients instelt:</span><span class="sxs-lookup"><span data-stu-id="34843-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="34843-109">Een pull-client instellen met behulp van configuratienamen</span><span class="sxs-lookup"><span data-stu-id="34843-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="34843-110">Een pull-client instellen met behulp van het configuratie-id</span><span class="sxs-lookup"><span data-stu-id="34843-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> [!NOTE]
> <span data-ttu-id="34843-111">Deze onderwerpen zijn van toepassing op Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="34843-111">These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="34843-112">Zie [een pull-client instellen met behulp van de configuratie-ID in Power shell 4,0](pullClientConfigID4.md)voor het instellen van een pull-client in power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="34843-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>