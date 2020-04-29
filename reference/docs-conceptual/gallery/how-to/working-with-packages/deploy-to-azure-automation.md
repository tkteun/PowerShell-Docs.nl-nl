---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: Implementeren naar Azure Automation
ms.openlocfilehash: 5d09a0777c59b642400d683c8cb6f881319fb881
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278700"
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="b620e-103">Implementeren naar Azure Automation</span><span class="sxs-lookup"><span data-stu-id="b620e-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="b620e-104">Met de knop implementeren op Azure Automation op de pagina pakket Details wordt het pakket van de PowerShell Gallery naar Azure Automation geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="b620e-104">The Deploy to Azure Automation button on the package details page will deploy the package from the PowerShell Gallery to Azure Automation.</span></span>

![De knop implementeren op Azure Automation](media/deploy-to-azure-automation/DeployToAzureAutomationButton.png)

<span data-ttu-id="b620e-106">Als u hierop klikt, wordt u omgeleid naar de Azure-Beheerportal, waar u zich aanmeldt met de referenties van uw Azure-account.</span><span class="sxs-lookup"><span data-stu-id="b620e-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="b620e-107">Als het pakket afhankelijkheden bevat, worden alle afhankelijkheden ook geïmplementeerd in Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="b620e-107">If the package includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="b620e-108">Als hetzelfde pakket en dezelfde versie al bestaan in uw Automation-account, wordt het pakket in uw Automation-account overschreven door het opnieuw te implementeren vanaf de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="b620e-108">If the same package and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the package in your Automation account.</span></span>

<span data-ttu-id="b620e-109">Als u een module implementeert, wordt deze weer gegeven in de sectie modules van Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="b620e-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="b620e-110">Als u een script implementeert, wordt dit weer gegeven in de sectie Runbooks van Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="b620e-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="b620e-111">U kunt de knop implementeren op Azure Automation uitschakelen door de tag AzureAutomationNotSupported toe te voegen aan de meta gegevens van het pakket.</span><span class="sxs-lookup"><span data-stu-id="b620e-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the package metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="b620e-112">Acceptatie van de licentie vereisen bij implementeren naar Azure Automation</span><span class="sxs-lookup"><span data-stu-id="b620e-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="b620e-113">Als de module die wordt geïmplementeerd op Azure Automation vereist acceptatie van de licentie, wordt in de portal-UI een disclaimer weer gegeven waarin wordt aangegeven dat deze module licentie acceptatie vereist.</span><span class="sxs-lookup"><span data-stu-id="b620e-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="b620e-114">Als u op OK klikt, gaat u akkoord met de licentie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="b620e-114">By clicking OK, you are accepting license terms.'</span></span>

![Implementeren naar Azure Automation vereist acceptatie van de licentie](media/deploy-to-azure-automation/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="b620e-116">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="b620e-116">More details</span></span>

- [<span data-ttu-id="b620e-117">Acceptatie van de licentie vereisen in PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="b620e-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="b620e-118">Acceptatie van de licentie vereisen in PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="b620e-118">Require License Acceptance in PowerShell Gallery</span></span>](packages-that-require-license-acceptance.md)
- [<span data-ttu-id="b620e-119">Azure Automation website</span><span class="sxs-lookup"><span data-stu-id="b620e-119">Azure Automation website</span></span>](https://azure.microsoft.com/services/automation/)
