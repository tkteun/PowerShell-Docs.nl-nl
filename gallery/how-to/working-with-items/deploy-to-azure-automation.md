---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: Implementeren naar Azure Automation
ms.openlocfilehash: 1efdc289228d3a6962302d12ccf44143ce63a806
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: nl-NL
ms.lasthandoff: 05/10/2018
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="8a6b8-103">Implementeren naar Azure Automation</span><span class="sxs-lookup"><span data-stu-id="8a6b8-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="8a6b8-104">De implementeren in Azure Automation-knop op de detailpagina item implementeert het item uit de galerie PowerShell voor Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="8a6b8-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Implementeren in Azure Automation-knop](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="8a6b8-106">Wanneer u klikt, wordt deze omgeleid naar de Azure-beheerportal, waar u zich aanmelden met de referenties van uw Azure-account.</span><span class="sxs-lookup"><span data-stu-id="8a6b8-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="8a6b8-107">Als het item afhankelijkheden bevat, wordt alle afhankelijkheden geïmplementeerd voor Azure Automation ook.</span><span class="sxs-lookup"><span data-stu-id="8a6b8-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="8a6b8-108">Als het artikel en de versie nog in uw Automation-account bestaat, overschrijft opnieuw implementeren van de PowerShell Gallery het item in uw Automation-account.</span><span class="sxs-lookup"><span data-stu-id="8a6b8-108">If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="8a6b8-109">Als u een module implementeert, wordt deze weergegeven in de sectie Modules van Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="8a6b8-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="8a6b8-110">Als u een script implementeert, wordt deze weergegeven in de sectie Runbooks van Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="8a6b8-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="8a6b8-111">De implementeren in Azure Automation-knop kan worden uitgeschakeld door de tag AzureAutomationNotSupported toe te voegen aan de itemmetagegevens.</span><span class="sxs-lookup"><span data-stu-id="8a6b8-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="8a6b8-112">Acceptatie van de licentie vereisen bij implementeren naar Azure Automation</span><span class="sxs-lookup"><span data-stu-id="8a6b8-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="8a6b8-113">Als de module wordt geïmplementeerd op Azure Automation acceptatie van de licentie vereist, gebruikersinterface portal een disclaimer met de melding wordt weergegeven, deze module acceptatie van de licentie is vereist.</span><span class="sxs-lookup"><span data-stu-id="8a6b8-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="8a6b8-114">Op OK klikt, u kunt de licentievoorwaarden accepteren.'</span><span class="sxs-lookup"><span data-stu-id="8a6b8-114">By clicking OK, you are accepting license terms.'</span></span>

![Implementeren in Azure Automation acceptatie van de licentie is vereist](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="8a6b8-116">meer informatie</span><span class="sxs-lookup"><span data-stu-id="8a6b8-116">More details</span></span>

- [<span data-ttu-id="8a6b8-117">Acceptatie van de licentie in PowerShellGet vereisen</span><span class="sxs-lookup"><span data-stu-id="8a6b8-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="8a6b8-118">Vereisen dat gebruikers van de licentie in PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8a6b8-118">Require License Acceptance in PowerShell Gallery</span></span>](items-that-require-license-acceptance.md)
- [<span data-ttu-id="8a6b8-119">Azure Automation-website</span><span class="sxs-lookup"><span data-stu-id="8a6b8-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)
