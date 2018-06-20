---
ms.date: 03/15/2018
keywords: DSC, powershell, configuratie, setup
title: DSC gebruiken op Microsoft Azure
ms.openlocfilehash: d35488c3f66895e930eaa84360f3d3ec9d74e9c7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221881"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="7895e-103">DSC gebruiken op Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="7895e-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="7895e-104">Gewenste State Configuration (DSC) wordt ondersteund in Microsoft Azure via de [Azure Desired State Configuration extensie handler](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) en via [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="7895e-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="7895e-105">Extensie-handler van Azure gewenst status configuratie</span><span class="sxs-lookup"><span data-stu-id="7895e-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="7895e-106">De extensie Azure DSC kunt virtuele machines die worden gehost in Microsoft Azure om te worden beheerd met DSC.</span><span class="sxs-lookup"><span data-stu-id="7895e-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="7895e-107">Zie voor meer informatie de volgende onderwerpen:</span><span class="sxs-lookup"><span data-stu-id="7895e-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="7895e-108">Extensie-handler van Azure gewenst status configuratie</span><span class="sxs-lookup"><span data-stu-id="7895e-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)
- [<span data-ttu-id="7895e-109">Windows VMSS en Desired State Configuration met Azure Resource Manager-sjablonen</span><span class="sxs-lookup"><span data-stu-id="7895e-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-template)
- [<span data-ttu-id="7895e-110">Referenties worden doorgegeven aan de handler Azure DSC-uitbreiding</span><span class="sxs-lookup"><span data-stu-id="7895e-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-credentials)
- [<span data-ttu-id="7895e-111">Geschiedenis van Azure gewenst status configuratie-uitbreiding</span><span class="sxs-lookup"><span data-stu-id="7895e-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="7895e-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="7895e-112">Azure Automation DSC</span></span>

<span data-ttu-id="7895e-113">De [Azure Automation-service](https://azure.microsoft.com/services/automation/) kunt u voor het beheren van DSC-configuraties, bronnen en beheerde knooppunten uit in Azure.</span><span class="sxs-lookup"><span data-stu-id="7895e-113">The [Azure Automation service](https://azure.microsoft.com/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="7895e-114">Zie voor meer informatie de volgende onderwerpen:</span><span class="sxs-lookup"><span data-stu-id="7895e-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="7895e-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="7895e-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="7895e-116">Aan de slag met Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="7895e-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="7895e-117">Computers voorbereiden voor beheer door Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="7895e-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)