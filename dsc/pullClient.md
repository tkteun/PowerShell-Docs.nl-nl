---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Instellen van een DSC-pull-client
ms.openlocfilehash: 4c56671313b93cc12ce9460ce41e1710e0d6a526
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="e5eca-103">Instellen van een DSC-pull-client</span><span class="sxs-lookup"><span data-stu-id="e5eca-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="e5eca-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e5eca-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5eca-105">De Pull-Server (Windows-onderdeel *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om de nieuwe functies en mogelijkheden bieden.</span><span class="sxs-lookup"><span data-stu-id="e5eca-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="e5eca-106">Het verdient aanbeveling om te beginnen met een overgang clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen vermeld [hier](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="e5eca-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="e5eca-107">Elk doelknooppunt heeft adviseert het gebruik van pull-modus en de URL of bestandslocatie opgegeven waarbij u kunt contact opnemen met de pull-server om op te halen van configuraties en resources en rapportgegevens moet worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="e5eca-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="e5eca-108">De volgende onderwerpen wordt uitgelegd hoe pull clients instellen:</span><span class="sxs-lookup"><span data-stu-id="e5eca-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="e5eca-109">Een pull-client instellen met behulp van configuratienamen</span><span class="sxs-lookup"><span data-stu-id="e5eca-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="e5eca-110">Een pull-client instellen met behulp van het configuratie-id</span><span class="sxs-lookup"><span data-stu-id="e5eca-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="e5eca-111">**Opmerking**: deze onderwerpen van toepassing op PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="e5eca-111">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="e5eca-112">Als u een pull-client in PowerShell 4.0 instelt, Zie [instellen van een pull-client met behulp van configuratie-ID in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="e5eca-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>