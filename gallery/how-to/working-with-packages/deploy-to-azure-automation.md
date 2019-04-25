---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Implementeren naar Azure Automation
ms.openlocfilehash: dc382b1cf3ceaa787f54c555d01e6bd9ba70e680
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084883"
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="4bfb9-103">Implementeren naar Azure Automation</span><span class="sxs-lookup"><span data-stu-id="4bfb9-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="4bfb9-104">De implementeren in Azure Automation-knop op de pagina met details van het pakket wordt het pakket vanuit de PowerShell Gallery voor Azure Automation te implementeren.</span><span class="sxs-lookup"><span data-stu-id="4bfb9-104">The Deploy to Azure Automation button on the package details page will deploy the package from the PowerShell Gallery to Azure Automation.</span></span>

![Implementeren naar Azure Automation-knop](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="4bfb9-106">Wanneer u klikt, wordt het u omgeleid naar de Azure-beheerportal, waar u zich aanmelden met behulp van de referenties van uw Azure-account.</span><span class="sxs-lookup"><span data-stu-id="4bfb9-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="4bfb9-107">Als het pakket afhankelijkheden bevat, wordt alle afhankelijkheden geïmplementeerd op Azure Automation ook.</span><span class="sxs-lookup"><span data-stu-id="4bfb9-107">If the package includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="4bfb9-108">Als het pakket en de versie al in uw Automation-account bestaat, wordt u deze opnieuw implementeert vanuit de PowerShell Gallery het pakket in uw Automation-account overschreven.</span><span class="sxs-lookup"><span data-stu-id="4bfb9-108">If the same package and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the package in your Automation account.</span></span>

<span data-ttu-id="4bfb9-109">Als u een module implementeert, wordt deze weergegeven in de sectie Modules van Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="4bfb9-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="4bfb9-110">Als u een script implementeert, wordt deze weergegeven in de sectie Runbooks in Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="4bfb9-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="4bfb9-111">De implementeren in Azure Automation-knop kan worden uitgeschakeld door de tag AzureAutomationNotSupported toe te voegen aan de pakketmetagegevens.</span><span class="sxs-lookup"><span data-stu-id="4bfb9-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the package metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="4bfb9-112">Acceptatie van de licentie vereisen bij implementeren naar Azure Automation</span><span class="sxs-lookup"><span data-stu-id="4bfb9-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="4bfb9-113">Als de implementatie voor Azure Automation-module acceptatie van de licentie vereist, de gebruikersinterface van portal ziet u een fragment met de melding ' deze module is de acceptatie van de licentie vereist.</span><span class="sxs-lookup"><span data-stu-id="4bfb9-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="4bfb9-114">Door te klikken op OK, u licentievoorwaarden accepteren.'</span><span class="sxs-lookup"><span data-stu-id="4bfb9-114">By clicking OK, you are accepting license terms.'</span></span>

![Implementeren in Azure Automation is de acceptatie van de licentie vereist](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="4bfb9-116">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="4bfb9-116">More details</span></span>

- [<span data-ttu-id="4bfb9-117">Vereisen van instemming met licentie vereisen in PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="4bfb9-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="4bfb9-118">Vereisen van instemming met licentie vereisen in PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="4bfb9-118">Require License Acceptance in PowerShell Gallery</span></span>](packages-that-require-license-acceptance.md)
- [<span data-ttu-id="4bfb9-119">Azure Automation-website</span><span class="sxs-lookup"><span data-stu-id="4bfb9-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)
