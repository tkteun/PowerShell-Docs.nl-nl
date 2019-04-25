---
title: Naamconventies voor een CAB-bestand bij te werken Help | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082359"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>CAB-bestand voor een Help die kan worden bijgewerkt een naam geven

Dit onderwerp wordt uitgelegd dat de vereiste indeling voor het bij te werken Help CAB-bestand (. CAB-bestanden).

## <a name="how-to-name-an-updatable-help-cab-file"></a>CAB-bestand voor een Help die kan worden bijgewerkt een naam geven

Bij te werken CAB-bestand (. CAB-bestand)-bestand moet een naam met de volgende indeling hebben.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

De elementen van de naam zijn als volgt.

ModuleName de waarde van de **naam** eigenschap van de **ModuleInfo** object dat de [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet retourneert.

ModuleGUID de waarde van de **GUID** sleutel in de module-manifest.

De gebruikersinterface van UICulture cultuur van de help-bestanden in het CAB-bestand. Deze waarde moet overeenkomen met de waarde van een van de **UICulture** elementen in het HelpInfo XML-bestand voor de module.

Bijvoorbeeld als naam van de module "TestModule", 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, is de GUID van de module wordt en de gebruikersinterfacecultuur 'en-US' is, is de naam van het CAB-bestand:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`