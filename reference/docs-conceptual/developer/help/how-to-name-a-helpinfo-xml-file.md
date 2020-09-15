---
title: Een naam geven aan een HelpInfo-XML-bestand
ms.date: 09/12/2016
ms.openlocfilehash: 9505a7f66852a569d25ac0c1be86e68f870a7930
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892928"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>Een naam geven aan een HelpInfo-XML-bestand

In dit onderwerp wordt de vereiste naam indeling uitgelegd voor de Help-informatie bestanden die kunnen worden bijgewerkt, ook wel bekend als HelpInfo XML-bestanden.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Een naam geven aan een HelpInfo-XML-bestand

Een HelpInfo XML-bestand moet een naam hebben met de volgende indeling.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

De elementen van de naam zijn als volgt.

- `<ModuleName>` -De waarde van de eigenschap **name** van het **ModuleInfo** -object dat door de cmdlet [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) wordt geretourneerd.

- `<ModuleGUID>` -De waarde van de **GUID** -sleutel in het module manifest.

Als de module naam bijvoorbeeld ' TestModule ' is en de module-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, zou de naam van het HelpInfo XML-bestand voor de module er als volgt uitziet:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`
