---
title: Een HelpInfo XML-bestand benoemen | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 45e8a5bb0066f38c82cd3be8ec881383befd9c85
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560573"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>Een naam geven aan een HelpInfo-XML-bestand

In dit onderwerp wordt de vereiste naam indeling uitgelegd voor de Help-informatie bestanden die kunnen worden bijgewerkt, ook wel bekend als HelpInfo XML-bestanden.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Een naam geven aan een HelpInfo-XML-bestand

Een HelpInfo XML-bestand moet een naam hebben met de volgende indeling.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

De elementen van de naam zijn als volgt.

Module naam de waarde van de eigenschap **name** van het **ModuleInfo** -object dat door de cmdlet [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) wordt geretourneerd.

ModuleGUID de waarde van de **GUID** -sleutel in het manifest van de module.

Als de module naam bijvoorbeeld ' TestModule ' is en de module-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, zou de naam van het HelpInfo XML-bestand voor de module er als volgt uitziet:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`
