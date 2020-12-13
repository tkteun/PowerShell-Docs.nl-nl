---
ms.date: 09/13/2016
ms.topic: reference
title: Een Windows PowerShell-module maken
description: Een Windows PowerShell-module maken
ms.openlocfilehash: 29394ebcd2f7c4a547aabcb88685ff494b2c381d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657267"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Een Windows PowerShell-module maken

Een Windows Power shell-module biedt een mechanisme voor het registreren van sets cmdlets en een andere Windows Power shell-provider met de shell, waardoor de functionaliteit van de shell wordt uitgebreid. Een Windows Power shell-module kan alle cmdlets en providers in één assembly registreren, of kan een specifieke lijst met cmdlets en providers registreren.

Module-assembly's moeten worden geïnstalleerd in een beveiligde map, net als bij andere besturings systemen. Als dat niet het geval is, kunnen kwaadwillende gebruikers een assembly vervangen door onveilige code.

## <a name="windows-powershell-snap-in-classes"></a>Windows Power shell-module klassen

Alle Windows Power shell-module klassen worden afgeleid van de klassen [System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) of [System. Management. Automation. Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .

## <a name="examples"></a>Voorbeelden

[Een Windows Power shell-module schrijven](./writing-a-windows-powershell-snap-in.md): in dit voor beeld ziet u hoe u een module maakt die wordt gebruikt voor het registreren van alle cmdlets en providers in een assembly.

[Een aangepaste Windows Power shell-module schrijven](./writing-a-custom-windows-powershell-snap-in.md): in dit voor beeld ziet u hoe u een aangepaste module maakt die wordt gebruikt voor het registreren van een specifieke set cmdlets en providers die mogelijk niet in één assembly bestaan of aanwezig zijn.

## <a name="see-also"></a>Zie ook

[System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)

[System. Management. Automation. Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[Cmdlets registreren](./registering-cmdlets.md)

[Windows Power shell shell SDK](../windows-powershell-reference.md)
