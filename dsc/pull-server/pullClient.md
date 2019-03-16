---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Een DSC-pull-client instellen
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054251"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="a9b14-103">Een DSC-pull-client instellen</span><span class="sxs-lookup"><span data-stu-id="a9b14-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="a9b14-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a9b14-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a9b14-105">De Pull-Server (Windows-functie *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om nieuwe functies en mogelijkheden bieden.</span><span class="sxs-lookup"><span data-stu-id="a9b14-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="a9b14-106">Het verdient aanbeveling om te beginnen met het overstappen clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen die zijn opgenomen [hier](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="a9b14-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="a9b14-107">Elk doelknooppunt is om te worden gemeld voor gebruik van pull-modus en de locatie-URL of bestand gegeven waar kunt contact opnemen met de pull-server om op te halen van configuraties en resources, en waar de gegevens moet worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="a9b14-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="a9b14-108">De volgende onderwerpen wordt uitgelegd hoe u pull-clients kunt instellen:</span><span class="sxs-lookup"><span data-stu-id="a9b14-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="a9b14-109">Een pull-client instellen met behulp van configuratienamen</span><span class="sxs-lookup"><span data-stu-id="a9b14-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="a9b14-110">Een pull-client instellen met behulp van het configuratie-id</span><span class="sxs-lookup"><span data-stu-id="a9b14-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> [!NOTE]
> <span data-ttu-id="a9b14-111">Deze onderwerpen zijn van toepassing op PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="a9b14-111">These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="a9b14-112">Als u een pull-client in PowerShell 4.0 instelt, Zie [instellen van een pull-client met behulp van configuratie-ID in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="a9b14-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>