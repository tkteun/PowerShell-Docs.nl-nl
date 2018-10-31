---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Implementeren naar Azure Automation
ms.openlocfilehash: dc382b1cf3ceaa787f54c555d01e6bd9ba70e680
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004038"
---
# <a name="deploy-to-azure-automation"></a>Implementeren naar Azure Automation

De implementeren in Azure Automation-knop op de pagina met details van het pakket wordt het pakket vanuit de PowerShell Gallery voor Azure Automation te implementeren.

![Implementeren naar Azure Automation-knop](../../Images/DeployToAzureAutomationButton.png)

Wanneer u klikt, wordt het u omgeleid naar de Azure-beheerportal, waar u zich aanmelden met behulp van de referenties van uw Azure-account.
Als het pakket afhankelijkheden bevat, wordt alle afhankelijkheden geïmplementeerd op Azure Automation ook.

> [!WARNING]
> Als het pakket en de versie al in uw Automation-account bestaat, wordt u deze opnieuw implementeert vanuit de PowerShell Gallery het pakket in uw Automation-account overschreven.

Als u een module implementeert, wordt deze weergegeven in de sectie Modules van Azure Automation.  Als u een script implementeert, wordt deze weergegeven in de sectie Runbooks in Azure Automation.

De implementeren in Azure Automation-knop kan worden uitgeschakeld door de tag AzureAutomationNotSupported toe te voegen aan de pakketmetagegevens.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Acceptatie van de licentie vereisen bij implementeren naar Azure Automation

Als de implementatie voor Azure Automation-module acceptatie van de licentie vereist, de gebruikersinterface van portal ziet u een fragment met de melding ' deze module is de acceptatie van de licentie vereist. Door te klikken op OK, u licentievoorwaarden accepteren.'

![Implementeren in Azure Automation is de acceptatie van de licentie vereist](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Meer informatie

- [Vereisen van instemming met licentie vereisen in PowerShellGet](../../concepts/module-license-acceptance.md)
- [Vereisen van instemming met licentie vereisen in PowerShell Gallery](packages-that-require-license-acceptance.md)
- [Azure Automation-website](http://azure.microsoft.com/services/automation/)
