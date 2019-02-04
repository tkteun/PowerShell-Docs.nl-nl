---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685758"
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="28a05-102">Scheiding van knooppunt- en configuratie-id's</span><span class="sxs-lookup"><span data-stu-id="28a05-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="28a05-103">Overzicht</span><span class="sxs-lookup"><span data-stu-id="28a05-103">Overview</span></span>

<span data-ttu-id="28a05-104">Om te kunnen bieden een meer flexibele en een gestroomlijnde ervaring bij het gebruik van DSC in de Pull-modus, hebben we een aantal functies in deze release toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="28a05-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="28a05-105">Deze functies zijn bedoeld om u hebt de flexibiliteit om gemakkelijk instellen en implementeren van configuraties over meerdere knooppunten tijdens het bijhouden van de status en rapportagegegevens afzonderlijk voor elk knooppunt.</span><span class="sxs-lookup"><span data-stu-id="28a05-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="28a05-106">Deze functies zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="28a05-106">These features are as follows:</span></span>

* <span data-ttu-id="28a05-107">De configuratienaam van een waarin de configuratie voor een computer.</span><span class="sxs-lookup"><span data-stu-id="28a05-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="28a05-108">Deze naam kan worden gedeeld door meerdere doelknooppunten</span><span class="sxs-lookup"><span data-stu-id="28a05-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="28a05-109">Een agent-ID die één knooppunt wordt aangeduid</span><span class="sxs-lookup"><span data-stu-id="28a05-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="28a05-110">Een registratiestap die alleen een doelknooppunt de eerste keer plaatsvindt verbinding maakt met een pull-server</span><span class="sxs-lookup"><span data-stu-id="28a05-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="28a05-111">**Opmerking:** Deze functies en functionaliteiten zijn toegevoegd en de bestaande pull-functies en concepten niet vervangen.</span><span class="sxs-lookup"><span data-stu-id="28a05-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="28a05-112">U kunt deze nieuwe functies of de oudere zijn met de nieuwe pull-server worden verzonden in deze release.</span><span class="sxs-lookup"><span data-stu-id="28a05-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="28a05-113">Zie voor meer informatie, [instellen van een pull-client met behulp van configuratienamen](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span><span class="sxs-lookup"><span data-stu-id="28a05-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>
