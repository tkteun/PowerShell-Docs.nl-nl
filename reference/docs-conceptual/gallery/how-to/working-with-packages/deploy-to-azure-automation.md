---
ms.date: 06/12/2017
title: Implementeren naar Azure Automation
description: In dit artikel wordt beschreven hoe u de PowerShell Gallery kunt gebruiken om een pakket te implementeren op Azure Automation.
ms.openlocfilehash: e9de079ee6cc950c8a268423b9eabd515959b718
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662378"
---
# <a name="deploy-to-azure-automation"></a>Implementeren naar Azure Automation

Met de knop implementeren op Azure Automation op de pagina pakket Details wordt het pakket van de PowerShell Gallery naar Azure Automation geïmplementeerd.

![De knop implementeren op Azure Automation](media/deploy-to-azure-automation/DeployToAzureAutomationButton.png)

Als u hierop klikt, wordt u omgeleid naar de Azure-Beheerportal, waar u zich aanmeldt met de referenties van uw Azure-account. Als het pakket afhankelijkheden bevat, worden alle afhankelijkheden ook geïmplementeerd in Azure Automation.

> [!WARNING]
> Als hetzelfde pakket en dezelfde versie al bestaan in uw Automation-account, wordt het pakket in uw Automation-account overschreven door het opnieuw te implementeren vanaf de PowerShell Gallery.

Als u een module implementeert, wordt deze weer gegeven in de sectie modules van Azure Automation. Als u een script implementeert, wordt dit weer gegeven in de sectie Runbooks van Azure Automation.

U kunt de knop implementeren op Azure Automation uitschakelen door de tag AzureAutomationNotSupported toe te voegen aan de meta gegevens van het pakket.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Acceptatie van de licentie vereisen bij implementeren naar Azure Automation

Als de module die wordt geïmplementeerd op Azure Automation vereist acceptatie van de licentie, wordt in de portal-UI een disclaimer weer gegeven waarin wordt aangegeven dat deze module licentie acceptatie vereist. Als u op OK klikt, gaat u akkoord met de licentie voorwaarden.

![Implementeren naar Azure Automation vereist acceptatie van de licentie](media/deploy-to-azure-automation/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Meer informatie

- [Acceptatie van de licentie vereisen in PowerShellGet](../../concepts/module-license-acceptance.md)
- [Acceptatie van de licentie vereisen in PowerShell Gallery](packages-that-require-license-acceptance.md)
- [Azure Automation website](https://azure.microsoft.com/services/automation/)
