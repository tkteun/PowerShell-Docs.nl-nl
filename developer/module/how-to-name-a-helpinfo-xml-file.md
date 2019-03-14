---
title: Naamconventies voor een HelpInfo XML-bestand | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794804"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>Een naam geven aan een HelpInfo-XML-bestand

In dit onderwerp wordt uitgelegd dat de vereiste indeling voor de bestanden bij te werken Help-informatie, bekend als HelpInfo XML-bestanden.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Een naam geven aan een HelpInfo-XML-bestand

Een HelpInfo XML-bestand moet een naam met de volgende indeling hebben.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

De elementen van de naam zijn als volgt.

ModuleName de waarde van de **naam** eigenschap van de **ModuleInfo** object dat de [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet retourneert.

ModuleGUID de waarde van de **GUID** sleutel in de module-manifest.

Bijvoorbeeld, als de modulenaam van de is 'TestModule' en de GUID-module 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 is, zou de naam van het HelpInfo XML-bestand voor de module zijn:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`