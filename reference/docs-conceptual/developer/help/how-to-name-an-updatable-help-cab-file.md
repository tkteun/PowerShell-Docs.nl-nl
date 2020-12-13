---
ms.date: 09/12/2016
ms.topic: reference
title: CAB-bestand voor een Help die kan worden bijgewerkt een naam geven
description: CAB-bestand voor een Help die kan worden bijgewerkt een naam geven
ms.openlocfilehash: 57ea188d07a382d1a986a49c9ae22c5919dafa8e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658913"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>CAB-bestand voor een Help die kan worden bijgewerkt een naam geven

In dit onderwerp wordt de vereiste naam indeling voor de bij te werken cab- `.CAB` bestanden () beschreven.

## <a name="how-to-name-an-updatable-help-cab-file"></a>CAB-bestand voor een Help die kan worden bijgewerkt een naam geven

Een cab `.CAB` -bestand dat kan worden bijgewerkt, moet een naam hebben met de volgende indeling.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

De elementen van de naam zijn als volgt.

- `<ModuleName>` -De waarde van de eigenschap **name** van het **ModuleInfo** -object dat door de cmdlet [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) wordt geretourneerd.
- `<ModuleGUID>` -De waarde van de **GUID** -sleutel in het module manifest.
- `<UICulture>` -De UI-cultuur van de Help-bestanden in het CAB-bestand. Deze waarde moet overeenkomen met de waarde van een van de **uiCulture** -elementen in het HelpInfo XML-bestand voor de module.

Als de module naam bijvoorbeeld ' TestModule ' is, is de module-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 en de GEBRUIKERSINTERFACE cultuur ' en-US '. de naam van het CAB-bestand zou zijn:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
