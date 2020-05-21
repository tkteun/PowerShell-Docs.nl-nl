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
ms.openlocfilehash: a253f98d213f797a659affb1560907bb99a045d3
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560556"
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
