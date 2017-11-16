---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 91f48fb43d7fb099e34ce5d3b3b632e3cb119d64
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
<a name="deploy-to-azure-automation"></a><span data-ttu-id="32070-103">Implementeren in Azure Automation</span><span class="sxs-lookup"><span data-stu-id="32070-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="32070-104">De implementeren in Azure Automation-knop op de detailpagina item implementeert het item uit de galerie PowerShell voor Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="32070-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Implementeren in Azure Automation-knop](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="32070-106">Wanneer u klikt, wordt deze omgeleid naar de Azure-beheerportal, waar u zich aanmelden met de referenties van uw Azure-account.</span><span class="sxs-lookup"><span data-stu-id="32070-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="32070-107">Als het item afhankelijkheden bevat, wordt alle afhankelijkheden geïmplementeerd voor Azure Automation ook.</span><span class="sxs-lookup"><span data-stu-id="32070-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="32070-108">Waarschuwing: Als het artikel en de versie nog in uw Automation-account bestaat, opnieuw implementeren van de PowerShell Gallery overschrijft het item in uw Automation-account.</span><span class="sxs-lookup"><span data-stu-id="32070-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="32070-109">Als u een module implementeert, wordt deze weergegeven in de sectie Modules van Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="32070-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="32070-110">Als u een script implementeert, wordt deze weergegeven in de sectie Runbooks van Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="32070-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="32070-111">De implementeren in Azure Automation-knop kan worden uitgeschakeld door de tag AzureAutomationNotSupported toe te voegen aan de itemmetagegevens.</span><span class="sxs-lookup"><span data-stu-id="32070-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="32070-112">Zie voor meer informatie over Azure Automation, de Azure Automation-website [Azure Automation-website](http://azure.microsoft.com/en-us/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="32070-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/en-us/services/automation/).</span></span>

