---
title: Wat is een Power shell-opdracht?
description: Met Power shell kunt u elke opdracht uitvoeren die beschikbaar is op uw systeem en een Power shell-specifieke opdracht die wordt aangeduid als cmdlets.
ms.date: 03/31/2021
ms.openlocfilehash: b6e54349ec15df3327c1f0525dce1a30ad35a6ac
ms.sourcegitcommit: eeedd4472b6cc6158494296c355579791e688baa
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/31/2021
ms.locfileid: "106104070"
---
# <a name="powershell-commands"></a>PowerShell-opdrachten

Met Power shell kunt u elke opdracht uitvoeren die beschikbaar is op uw systeem, met inbegrip van Power shell-opdrachten die worden aangeduid als cmdlets (uitgesp roken opdracht-staat).

## <a name="what-is-a-cmdlet"></a>Wat is een cmdlet?

Een cmdlet is één opdracht die deel uitmaakt van de pijp lijn semantiek van Power shell en retourneert meestal een .NET-object. Cmdlets zijn systeem eigen Power shell-opdrachten, geen zelfstandige uitvoer bare bestanden. Cmdlets worden verzameld in Power shell-modules die op aanvraag kunnen worden geladen. Cmdlets kunnen worden geschreven in elke gecompileerde .NET-taal of in de Power shell-script taal zelf.

## <a name="cmdlet-names"></a>Namen van cmdlets

Power shell gebruikt een combi natie van naam woorden en namen van _termen_ . De `Get-Command` cmdlet die is opgenomen in Power shell wordt bijvoorbeeld gebruikt om alle cmdlets op te halen die zijn geregistreerd in de opdracht shell. De opdracht geeft de actie aan die door de cmdlet wordt uitgevoerd en het zelfstandig naam woord identificeert de resource waarop de cmdlet de actie uitvoert.

## <a name="next-steps"></a>Volgende stappen

Meer informatie over Power shell en het vinden van andere cmdlets vindt u in de zelf studie Power shell-bits [Discover Power shell](learn/tutorials/01-discover-powershell.md).

Raadpleeg de volgende bronnen voor meer informatie over het maken van uw eigen cmdlets:

Op scripts gebaseerde cmdlets

- [about_Functions_Advanced](/powershell/module/microsoft.powershell.core/about/about_functions_advanced)
- [about_Functions_CmdletBindingAttribute](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute)
- [about_Functions_Advanced_Methods](/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods)

Gecompileerde cmdlets (Power shell SDK docs)

- [Overzicht van de cmdlet](developer/cmdlet/cmdlet-overview.md)
