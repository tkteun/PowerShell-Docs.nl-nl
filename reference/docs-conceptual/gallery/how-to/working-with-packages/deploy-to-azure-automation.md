---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: Implementeren naar Azure Automation
ms.openlocfilehash: 707691e24a77647064e60da0d9a31ad5eece1c59
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328775"
---
# <a name="deploy-to-azure-automation"></a>Implementeren naar Azure Automation

Met de knop implementeren op Azure Automation op de pagina pakket Details wordt het pakket van de PowerShell Gallery naar Azure Automation geïmplementeerd.

![De knop implementeren op Azure Automation](../../Images/DeployToAzureAutomationButton.png)

Als u hierop klikt, wordt u omgeleid naar de Azure-Beheerportal, waar u zich aanmeldt met de referenties van uw Azure-account.
Als het pakket afhankelijkheden bevat, worden alle afhankelijkheden ook geïmplementeerd in Azure Automation.

> [!WARNING]
> Als hetzelfde pakket en dezelfde versie al bestaan in uw Automation-account, wordt het pakket in uw Automation-account overschreven door het opnieuw te implementeren vanaf de PowerShell Gallery.

Als u een module implementeert, wordt deze weer gegeven in de sectie modules van Azure Automation.  Als u een script implementeert, wordt dit weer gegeven in de sectie Runbooks van Azure Automation.

U kunt de knop implementeren op Azure Automation uitschakelen door de tag AzureAutomationNotSupported toe te voegen aan de meta gegevens van het pakket.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Acceptatie van de licentie vereisen bij implementeren naar Azure Automation

Als de module die wordt geïmplementeerd op Azure Automation vereist acceptatie van de licentie, wordt in de portal-UI een disclaimer weer gegeven waarin wordt aangegeven dat deze module licentie acceptatie vereist. Als u op OK klikt, gaat u akkoord met de licentie voorwaarden.

![Implementeren naar Azure Automation vereist acceptatie van de licentie](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Meer details

- [Acceptatie van de licentie vereisen in PowerShellGet](../../concepts/module-license-acceptance.md)
- [Acceptatie van de licentie vereisen in PowerShell Gallery](packages-that-require-license-acceptance.md)
- [Azure Automation website](https://azure.microsoft.com/services/automation/)
