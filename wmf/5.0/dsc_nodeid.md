---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 6c036c2d8f97e559d20dd3ac40133fa06f5dab08
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="0917c-102">Scheiding van knooppunt- en configuratie-id's</span><span class="sxs-lookup"><span data-stu-id="0917c-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="0917c-103">Overzicht</span><span class="sxs-lookup"><span data-stu-id="0917c-103">Overview</span></span>

<span data-ttu-id="0917c-104">Om te kunnen bieden een flexibele en meer gestroomlijnde ervaring bij het gebruik van DSC in Pull-modus, hebben we een aantal functies in deze release toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="0917c-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="0917c-105">Deze functies zijn bedoeld om u de flexibiliteit eenvoudig instellen en configuraties implementeren op meerdere knooppunten terwijl u nog steeds bijhouden van de status en rapportage-informatie voor elk knooppunt afzonderlijk toestaan.</span><span class="sxs-lookup"><span data-stu-id="0917c-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="0917c-106">Deze functies zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="0917c-106">These features are as follows:</span></span>

* <span data-ttu-id="0917c-107">De configuratienaam van een die de configuratie voor een computer identificeert.</span><span class="sxs-lookup"><span data-stu-id="0917c-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="0917c-108">Deze naam kan worden gedeeld door meerdere doelknooppunten</span><span class="sxs-lookup"><span data-stu-id="0917c-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="0917c-109">Een agent-ID die een unieke identificatie van één knooppunt</span><span class="sxs-lookup"><span data-stu-id="0917c-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="0917c-110">Een registratiestap die alleen de eerste keer een doelknooppunt plaatsvindt verbinding maakt met een pull-server</span><span class="sxs-lookup"><span data-stu-id="0917c-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="0917c-111">**Opmerking:** deze functies en functionaliteit zijn toegevoegd en de bestaande pull-functies en -concepten niet vervangen.</span><span class="sxs-lookup"><span data-stu-id="0917c-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="0917c-112">U kunt deze nieuwe functies of de oudere met de nieuwe pull-server de back-upfunctie in deze release.</span><span class="sxs-lookup"><span data-stu-id="0917c-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="0917c-113">Zie voor meer informatie [een pull-client met behulp van configuratienamen instellen](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span><span class="sxs-lookup"><span data-stu-id="0917c-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>
