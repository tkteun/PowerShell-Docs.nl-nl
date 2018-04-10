---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 8da4eabead6a419dc0c01c74335c06bf8be25d0c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
<a name="deploy-to-azure-automation"></a><span data-ttu-id="79e7f-103">Implementeren naar Azure Automation</span><span class="sxs-lookup"><span data-stu-id="79e7f-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="79e7f-104">De implementeren in Azure Automation-knop op de detailpagina item implementeert het item uit de galerie PowerShell voor Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="79e7f-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Implementeren in Azure Automation-knop](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="79e7f-106">Wanneer u klikt, wordt deze omgeleid naar de Azure-beheerportal, waar u zich aanmelden met de referenties van uw Azure-account.</span><span class="sxs-lookup"><span data-stu-id="79e7f-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="79e7f-107">Als het item afhankelijkheden bevat, wordt alle afhankelijkheden geïmplementeerd voor Azure Automation ook.</span><span class="sxs-lookup"><span data-stu-id="79e7f-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="79e7f-108">Waarschuwing: Als het artikel en de versie nog in uw Automation-account bestaat, opnieuw implementeren van de PowerShell Gallery overschrijft het item in uw Automation-account.</span><span class="sxs-lookup"><span data-stu-id="79e7f-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="79e7f-109">Als u een module implementeert, wordt deze weergegeven in de sectie Modules van Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="79e7f-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="79e7f-110">Als u een script implementeert, wordt deze weergegeven in de sectie Runbooks van Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="79e7f-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="79e7f-111">De implementeren in Azure Automation-knop kan worden uitgeschakeld door de tag AzureAutomationNotSupported toe te voegen aan de itemmetagegevens.</span><span class="sxs-lookup"><span data-stu-id="79e7f-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="79e7f-112">Zie voor meer informatie over Azure Automation, de Azure Automation-website [Azure Automation-website](http://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="79e7f-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/services/automation/).</span></span>