---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Instellen van een DSC-pull-client
ms.openlocfilehash: 7f8758bd7145518e30e9c28b74d0db5d74dfaab3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-dsc-pull-client"></a>Instellen van een DSC-pull-client

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> De Pull-Server (Windows-onderdeel *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om de nieuwe functies en mogelijkheden bieden. Het verdient aanbeveling om te beginnen met een overgang clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen vermeld [hier](pullserver.md#community-solutions-for-pull-service).

Elk doelknooppunt heeft adviseert het gebruik van pull-modus en de URL of bestandslocatie opgegeven waarbij u kunt contact opnemen met de pull-server om op te halen van configuraties en resources en rapportgegevens moet worden verzonden.

De volgende onderwerpen wordt uitgelegd hoe pull clients instellen:

* [Een pull-client instellen met behulp van configuratienamen](pullClientConfigNames.md)
* [Een pull-client instellen met behulp van het configuratie-id](pullClientConfigID.md)

> **Opmerking**: deze onderwerpen van toepassing op PowerShell 5.0. Als u een pull-client in PowerShell 4.0 instelt, Zie [instellen van een pull-client met behulp van configuratie-ID in PowerShell 4.0](pullClientConfigID4.md).