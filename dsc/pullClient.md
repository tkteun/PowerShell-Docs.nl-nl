---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Instellen van een DSC-pull-client
ms.openlocfilehash: 7f8758bd7145518e30e9c28b74d0db5d74dfaab3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="35c0e-103">Instellen van een DSC-pull-client</span><span class="sxs-lookup"><span data-stu-id="35c0e-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="35c0e-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="35c0e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35c0e-105">De Pull-Server (Windows-onderdeel *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om de nieuwe functies en mogelijkheden bieden.</span><span class="sxs-lookup"><span data-stu-id="35c0e-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="35c0e-106">Het verdient aanbeveling om te beginnen met een overgang clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen vermeld [hier](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="35c0e-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="35c0e-107">Elk doelknooppunt heeft adviseert het gebruik van pull-modus en de URL of bestandslocatie opgegeven waarbij u kunt contact opnemen met de pull-server om op te halen van configuraties en resources en rapportgegevens moet worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="35c0e-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="35c0e-108">De volgende onderwerpen wordt uitgelegd hoe pull clients instellen:</span><span class="sxs-lookup"><span data-stu-id="35c0e-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="35c0e-109">Een pull-client instellen met behulp van configuratienamen</span><span class="sxs-lookup"><span data-stu-id="35c0e-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="35c0e-110">Een pull-client instellen met behulp van het configuratie-id</span><span class="sxs-lookup"><span data-stu-id="35c0e-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="35c0e-111">**Opmerking**: deze onderwerpen van toepassing op PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="35c0e-111">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="35c0e-112">Als u een pull-client in PowerShell 4.0 instelt, Zie [instellen van een pull-client met behulp van configuratie-ID in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="35c0e-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>