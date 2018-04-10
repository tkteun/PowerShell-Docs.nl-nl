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
<a name="deploy-to-azure-automation"></a>Implementeren naar Azure Automation
===========================

De implementeren in Azure Automation-knop op de detailpagina item implementeert het item uit de galerie PowerShell voor Azure Automation.

![Implementeren in Azure Automation-knop](Images/DeployToAzureAutomationButton.png)

Wanneer u klikt, wordt deze omgeleid naar de Azure-beheerportal, waar u zich aanmelden met de referenties van uw Azure-account.
Als het item afhankelijkheden bevat, wordt alle afhankelijkheden geïmplementeerd voor Azure Automation ook.

Waarschuwing: Als het artikel en de versie nog in uw Automation-account bestaat, opnieuw implementeren van de PowerShell Gallery overschrijft het item in uw Automation-account.

Als u een module implementeert, wordt deze weergegeven in de sectie Modules van Azure Automation.  Als u een script implementeert, wordt deze weergegeven in de sectie Runbooks van Azure Automation.

De implementeren in Azure Automation-knop kan worden uitgeschakeld door de tag AzureAutomationNotSupported toe te voegen aan de itemmetagegevens.

Zie voor meer informatie over Azure Automation, de Azure Automation-website [Azure Automation-website](http://azure.microsoft.com/services/automation/).