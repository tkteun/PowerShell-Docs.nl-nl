---
ms.date: 03/15/2018
keywords: DSC, Power shell, configuratie, installatie
title: DSC gebruiken op Microsoft Azure
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941948"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="70a56-103">DSC gebruiken op Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="70a56-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="70a56-104">De desired state Configuration (DSC) wordt ondersteund in Microsoft Azure via de [uitbrei ding Azure desired state Configuration extension](/azure/virtual-machines/extensions/dsc-overview) en via [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="70a56-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="70a56-105">Extensie-handler voor desired state Configuration van Azure</span><span class="sxs-lookup"><span data-stu-id="70a56-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="70a56-106">Met de Azure DSC-extensie kunnen Vm's die in Microsoft Azure worden gehost, worden beheerd met DSC.</span><span class="sxs-lookup"><span data-stu-id="70a56-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="70a56-107">Zie voor meer informatie de volgende onderwerpen:</span><span class="sxs-lookup"><span data-stu-id="70a56-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="70a56-108">Extensie-handler voor desired state Configuration van Azure</span><span class="sxs-lookup"><span data-stu-id="70a56-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="70a56-109">Configuratie van Windows VMSS en desired state met Azure Resource Manager sjablonen</span><span class="sxs-lookup"><span data-stu-id="70a56-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="70a56-110">Referenties door geven aan de Azure DSC-extensie-handler</span><span class="sxs-lookup"><span data-stu-id="70a56-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="70a56-111">Geschiedenis van de configuratie-extensie voor de gewenste Azure-status</span><span class="sxs-lookup"><span data-stu-id="70a56-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="70a56-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="70a56-112">Azure Automation DSC</span></span>

<span data-ttu-id="70a56-113">Met de [Azure Automation-Service](https://azure.microsoft.com/en-us/services/automation/) kunt u DSC-configuraties,-resources en beheerde knoop punten in azure beheren.</span><span class="sxs-lookup"><span data-stu-id="70a56-113">The [Azure Automation service](https://azure.microsoft.com/en-us/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="70a56-114">Zie voor meer informatie de volgende onderwerpen:</span><span class="sxs-lookup"><span data-stu-id="70a56-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="70a56-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="70a56-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="70a56-116">Aan de slag met Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="70a56-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="70a56-117">Onboarding van machines voor beheer door Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="70a56-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)