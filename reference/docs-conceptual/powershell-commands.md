---
title: Wat is een PowerShell-opdracht?
description: Opdrachten voor PowerShell worden cmdlets genoemd (uitgesproken als command-lets)
ms.date: 03/31/2021
ms.openlocfilehash: 3980ed53f0e0c6f86a5ebab7b6ca64aeee6b173e
ms.sourcegitcommit: d63769de0e59d117d90171799bda6544bf2f2f0b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2021
ms.locfileid: "107855563"
---
# <a name="what-is-a-powershell-command-cmdlet"></a>Wat is een PowerShell-opdracht (cmdlet)?

Opdrachten voor PowerShell worden cmdlets genoemd (uitgesproken als command-lets). Naast cmdlets kunt u met PowerShell elke opdracht uitvoeren die beschikbaar is op uw systeem.

## <a name="what-is-a-cmdlet"></a>Wat is een cmdlet?

Cmdlets zijn native PowerShell-opdrachten, geen stand-alone uitvoerbare bestanden. Cmdlets worden verzameld in PowerShell-modules die op aanvraag kunnen worden geladen. Cmdlets kunnen worden geschreven in elke gecompileerde .NET-taal of in de PowerShell-scripttaal zelf.

## <a name="cmdlet-names"></a>Cmdlet-namen

PowerShell maakt gebruik van een _werkwoord-zelfstandig naampaar_ om cmdlets te noemen. De cmdlet die is opgenomen in PowerShell wordt bijvoorbeeld gebruikt om alle cmdlets op te halen `Get-Command` die zijn geregistreerd in de opdrachtshell. De werkwoord identificeert de actie die de cmdlet uitvoert en het zelfstandig naamwoord identificeert de resource waarop de cmdlet de actie uitvoert.

## <a name="next-steps"></a>Volgende stappen

Zie de PowerShell Bits-zelfstudie PowerShell ontdekken voor meer [](learn/tutorials/01-discover-powershell.md)informatie over PowerShell en het vinden van andere cmdlets.

Zie de volgende bronnen voor meer informatie over het maken van uw eigen cmdlets:

Cmdlets op basis van scripts

- [about_Functions_Advanced](/powershell/module/microsoft.powershell.core/about/about_functions_advanced)
- [about_Functions_CmdletBindingAttribute](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute)
- [about_Functions_Advanced_Methods](/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods)

Gecompileerde cmdlets (PowerShell SDK-documenten)

- [Overzicht van cmdlet](developer/cmdlet/cmdlet-overview.md)
