---
title: Een CAB-bestand voor bijwerk bare Help-namen geven | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357433"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>CAB-bestand voor een Help die kan worden bijgewerkt een naam geven

In dit onderwerp wordt de vereiste naam indeling voor het Help-Cabinet dat kan worden bijgewerkt (. CAB-bestanden).

## <a name="how-to-name-an-updatable-help-cab-file"></a>CAB-bestand voor een Help die kan worden bijgewerkt een naam geven

Een CAB-archief dat kan worden bijgewerkt (. CAB-bestand moet een naam hebben met de volgende indeling.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

De elementen van de naam zijn als volgt.

Module naam de waarde van de eigenschap **name** van het **ModuleInfo** -object dat door de cmdlet [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) wordt geretourneerd.

ModuleGUID de waarde van de **GUID** -sleutel in het manifest van de module.

UICulture de UI-cultuur van de Help-bestanden in het CAB-bestand. Deze waarde moet overeenkomen met de waarde van een van de **uiCulture** -elementen in het HelpInfo XML-bestand voor de module.

Als de module naam bijvoorbeeld ' TestModule ' is, is de module-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 en de GEBRUIKERSINTERFACE cultuur ' en-US '. de naam van het CAB-bestand zou zijn:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`