---
ms.date: 03/15/2018
keywords: DSC, Power shell, configuratie, installatie
title: DSC gebruiken op Microsoft Azure
ms.openlocfilehash: 6d71b69eea78e775a3e5aaac64bccfa10092b8e6
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870826"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="cc8c1-103">DSC gebruiken op Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="cc8c1-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="cc8c1-104">De desired state Configuration (DSC) wordt ondersteund in Microsoft Azure via de [uitbrei ding Azure desired state Configuration extension](/azure/virtual-machines/extensions/dsc-overview) en via [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="cc8c1-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="cc8c1-105">Extensie-handler voor desired state Configuration van Azure</span><span class="sxs-lookup"><span data-stu-id="cc8c1-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="cc8c1-106">Met de Azure DSC-extensie kunnen Vm's die in Microsoft Azure worden gehost, worden beheerd met DSC.</span><span class="sxs-lookup"><span data-stu-id="cc8c1-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span> <span data-ttu-id="cc8c1-107">Zie voor meer informatie de volgende onderwerpen:</span><span class="sxs-lookup"><span data-stu-id="cc8c1-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="cc8c1-108">Extensie-handler voor desired state Configuration van Azure</span><span class="sxs-lookup"><span data-stu-id="cc8c1-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="cc8c1-109">Configuratie van Windows VMSS en desired state met Azure Resource Manager sjablonen</span><span class="sxs-lookup"><span data-stu-id="cc8c1-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="cc8c1-110">Referenties door geven aan de Azure DSC-extensie-handler</span><span class="sxs-lookup"><span data-stu-id="cc8c1-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="cc8c1-111">Geschiedenis van de configuratie-extensie voor de gewenste Azure-status</span><span class="sxs-lookup"><span data-stu-id="cc8c1-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="cc8c1-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="cc8c1-112">Azure Automation DSC</span></span>

<span data-ttu-id="cc8c1-113">Met de [Azure Automation-Service](https://azure.microsoft.com/services/automation/) kunt u DSC-configuraties,-resources en beheerde knoop punten in azure beheren.</span><span class="sxs-lookup"><span data-stu-id="cc8c1-113">The [Azure Automation service](https://azure.microsoft.com/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="cc8c1-114">Zie voor meer informatie de volgende onderwerpen:</span><span class="sxs-lookup"><span data-stu-id="cc8c1-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="cc8c1-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="cc8c1-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="cc8c1-116">Aan de slag met Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="cc8c1-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="cc8c1-117">Onboarding van machines voor beheer door Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="cc8c1-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)