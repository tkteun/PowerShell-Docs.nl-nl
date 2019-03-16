---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Een DSC-pull-client instellen
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054251"
---
# <a name="setting-up-a-dsc-pull-client"></a>Een DSC-pull-client instellen

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> De Pull-Server (Windows-functie *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om nieuwe functies en mogelijkheden bieden. Het verdient aanbeveling om te beginnen met het overstappen clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen die zijn opgenomen [hier](pullserver.md#community-solutions-for-pull-service).

Elk doelknooppunt is om te worden gemeld voor gebruik van pull-modus en de locatie-URL of bestand gegeven waar kunt contact opnemen met de pull-server om op te halen van configuraties en resources, en waar de gegevens moet worden verzonden.

De volgende onderwerpen wordt uitgelegd hoe u pull-clients kunt instellen:

* [Een pull-client instellen met behulp van configuratienamen](pullClientConfigNames.md)
* [Een pull-client instellen met behulp van het configuratie-id](pullClientConfigID.md)

> [!NOTE]
> Deze onderwerpen zijn van toepassing op PowerShell 5.0. Als u een pull-client in PowerShell 4.0 instelt, Zie [instellen van een pull-client met behulp van configuratie-ID in PowerShell 4.0](pullClientConfigID4.md).